# Inteligencia de Negocios · Semana 6

**Define el grano y prepara datos de prueba**
Juan José Horta Vanegas · Ingeniería de Sistemas · Unidad 1 · Corte 2 · 2026-B

Continúa sobre el modelo estrella de matrículas diseñado en la semana 4.

---

## 1. El grano

> **Una fila de HECHOS_MATRICULA representa un estudiante, matriculado en un programa, en un periodo académico.**

Dicho de otro modo: la combinación `id_estudiante` + `id_tiempo` identifica una fila de forma única. Ningún estudiante puede aparecer dos veces en el mismo periodo.

### Por qué ese nivel y no otro

Tenía tres candidatos razonables y descarté los otros dos por razones distintas.

Un grano **más grueso** —una fila por programa y periodo, con el conteo de matriculados— sería más liviano, pero disolvería al estudiante dentro de un total. Y sin el estudiante identificable no hay forma de saber si los 120 matriculados de este semestre son los mismos 120 del anterior o gente completamente distinta. La retención dejaría de ser calculable.

Un grano **más fino** —una fila por materia inscrita— existe y es válido para otros análisis, pero para el mío estorba: un estudiante aparecería seis o siete veces por semestre y cualquier conteo de personas exigiría deduplicar antes de contar. Además arrastra un detalle que mi pregunta no usa.

El nivel estudiante-periodo es el punto exacto donde vive el fenómeno que quiero medir. La permanencia es una propiedad de una persona a lo largo del tiempo, así que la fila tiene que ser justamente eso: una persona en un momento.

### Una corrección al modelo de la semana 4

Fijar el grano dejó al descubierto un error de mi diseño anterior. Había puesto `semestre_cursado` como atributo de DIM_ESTUDIANTE, y no puede ir ahí: en una dimensión cada estudiante tiene una sola fila, mientras que el semestre que cursa cambia en cada periodo. Guardado en la dimensión, el valor solo podría reflejar el último estado conocido y falsearía cualquier consulta histórica.

Lo moví a la tabla de hechos, donde sí depende de la fila. Es un número que no se suma —sumar semestres no significa nada—, así que no es una medida sino un atributo degenerado: vive en los hechos porque solo tiene sentido a ese grano.

Lo que sí se queda en DIM_ESTUDIANTE es `cohorte_ingreso`, y por la razón contraria: es un valor que se fija cuando el estudiante entra y no cambia nunca.

---

## 2. Las medidas a ese grano

| Medida | Tiene sentido a este grano porque... |
|---|---|
| `matriculado` | Vale 1 en cada fila. Sumarlo da el número de matrículas del periodo; como el grano garantiza una fila por estudiante, ese conteo es directamente la población, sin deduplicar. |
| `creditos_inscritos` | Los créditos que ese estudiante inscribió en ese periodo. Se suma por programa, sede o periodo sin ambigüedad. |
| `valor_matricula` | El valor liquidado de esa matrícula. Aditivo en cualquier combinación de dimensiones. |

Y lo que **no** puede ir aquí:

Un **promedio de créditos** no se guarda, se calcula. Los promedios no son aditivos y el promedio de promedios no es el promedio real, así que se deriva dividiendo la suma de créditos entre el conteo de estudiantes.

Un **total anual de matriculados** no aplica al grano. Es una medida a nivel de año y esta tabla vive a nivel de periodo; meterla aquí sería mezclar granos y toda suma quedaría inflada.

El **número de materias perdidas del semestre** tampoco: es un dato del rendimiento académico, que es otro proceso de negocio con su propio grano.

---

## 3. Los datos de prueba

Archivo: **`datos_prueba_matriculas.xlsx`** · 14 filas en la hoja `HECHOS_MATRICULA`, más una hoja por cada dimensión.

No los armé al azar. Para que la tabla sirva de prueba real tenía que permitir calcular lo que el modelo promete, así que la poblé con casos deliberados:

- **Dos cohortes** (2025-1 y 2025-2), para poder compararlas entre sí.
- **Tres periodos** consecutivos, que es el mínimo para medir retención a primer año.
- **Estudiantes que permanecen** (E-001 y E-002 aparecen en los tres periodos) y **estudiantes que desertan** (E-003 solo aparece en 2025-1; E-005 entra en 2025-2 y no continúa). Sin ambos casos el indicador no tendría variación y no probaría nada.
- **Dos programas y tres sedes**, para verificar que el modelo permite comparar.

La coherencia con el grano se puede comprobar a simple vista: ninguna combinación de `id_estudiante` + `id_tiempo` se repite, ninguna fila contiene totales y todas las claves foráneas existen en su dimensión.

La hoja `VERIFICACION` calcula con fórmulas la retención a primer año de la cohorte 2025-1 de Ingeniería de Sistemas: ingresaron tres estudiantes, dos seguían tres periodos después, retención del 66,7%. No es una cifra real de nada, es la demostración de que el grano elegido permite calcular el indicador.

---

## 4. Qué perdería con un grano más grueso

Si la tabla guardara una fila por programa y periodo con el total de matriculados, ganaría espacio y perdería casi todo lo que me importa.

**Perdería la retención por completo**, que es el objetivo del proyecto. Con solo totales sabría que en 2025-1 hubo 120 matriculados y en 2026-1 hubo 110, pero no si esos 110 son los mismos o gente nueva que reemplazó a los que se fueron. Un programa puede mantener su matrícula estable mientras pierde a toda una cohorte, y el total no lo delataría.

**Perdería el análisis por cohorte**, porque la cohorte es un atributo del estudiante y sin estudiantes en la tabla no hay a qué asociarla.

**Perdería la posibilidad de cruzar por jornada o modalidad de admisión**, que también son atributos de la persona.

Y el detalle que lo vuelve una mala decisión y no solo una decisión limitada: es **irreversible**. Desde el grano fino siempre puedo agregar hacia arriba y obtener los totales por programa y periodo cuando los necesite. Desde los totales no hay forma de recuperar quién era cada quién. Si dentro de dos semestres alguien pide un análisis por cohorte, con grano fino se responde con una consulta y con grano grueso hay que esperar dos años a que se acumulen datos nuevos.
