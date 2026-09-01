# Inteligencia de Negocios · Semana 2

**Define un KPI para una organización real**
Juan José Horta Vanegas · Ingeniería de Sistemas · Unidad 1 · Corte 1 · 2026-B

---

## La organización

Escogí la universidad, y dentro de ella el programa de Ingeniería de Sistemas. Es la organización que conozco desde adentro, y tiene la ventaja de que sus cifras son públicas: el Ministerio de Educación las publica en el SNIES y el SPADIES, así que el indicador no se queda en el papel.

---

## El KPI: retención de la cohorte a primer año

Mide qué proporción de los estudiantes que ingresan a un programa siguen matriculados un año después. Es el reverso de la deserción, pero enunciado en positivo, que es como lo hace la mayoría de instituciones cuando se fija metas.

**Fórmula**

```
Retención a primer año (%) =
    (estudiantes de la cohorte matriculados en el tercer periodo académico
     ÷ estudiantes que ingresaron en esa cohorte) × 100
```

**Meta: ≥ 80%**

Es decir, que de cada diez estudiantes que entran, al menos ocho sigan ahí un año después. El umbral es un punto de partida, no una verdad: lo correcto sería calcular primero la línea base del programa con los datos del SNIES y ajustarlo a partir de esa cifra. Una meta muy por encima de lo que el programa logra hoy se incumpliría siempre y dejaría de servir como señal.

---

## Qué decisión habilita

Si una cohorte cierra su primer año por debajo del 80%, se reasignan las horas de monitoría y tutoría del semestre siguiente hacia las asignaturas donde se concentró la pérdida, en vez de repartirlas parejo entre todos los cursos como se hace por defecto.

Esa es la clave del indicador. No sirve para saber que hay deserción —eso ya se sabe— sino para decidir *dónde poner los recursos de apoyo, que son limitados*. Si el número cae, hay una acción concreta que ejecutar; si se mantiene sobre la meta, las horas siguen distribuidas como están. Un indicador que no cambia nada según su valor no es un KPI, es un dato en una diapositiva.

---

## La cadena detrás del indicador

**El dato** son los registros de matrícula: un estudiante, un programa, un periodo académico. Filas sueltas que por sí solas no dicen nada. `est_00412 · Ing. Sistemas · 2025-1`.

**La información** aparece al agrupar y comparar. Supongamos que de los estudiantes que ingresaron en 2025-1 el 74% seguía matriculado en 2026-1: ahí ya hay contexto —una cohorte, una ventana de tiempo, un porcentaje— y el número se puede contrastar contra la meta. La cifra real habría que calcularla con los registros del SNIES; la uso aquí solo para ilustrar el salto del dato a la información.

**El conocimiento** llega cuando el patrón se repite. Al revisar varias cohortes seguidas aparece que la caída no está repartida a lo largo del año: se concentra en el paso del primer al segundo semestre, y coincide con las asignaturas de fundamentos matemáticos. Eso ya no es un número, es una explicación que sirve para actuar.

---

## Tipo de analítica

En su forma básica el indicador es **descriptivo**: responde *¿qué pasó?* con la cohorte que ingresó hace un año.

Pero el valor real aparece al desagregarlo por semestre, por asignatura y por sede, y ahí pasa a ser **diagnóstico**, porque ya responde *¿por qué pasó?*: la pérdida se explica por un cuello de botella concreto y no por una deserción difusa. Esa distinción importa para la decisión que planteé arriba, porque no se pueden reasignar monitorías sin saber a qué cursos.

No llega a predictivo. Para estimar qué cohorte está en riesgo antes de que se vaya haría falta modelar variables de entrada de cada estudiante, y eso queda fuera del alcance de este indicador.
