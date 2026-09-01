# Inteligencia de Negocios · Semana 1

**Puesta a punto del entorno y expectativas**
Juan José Horta Vanegas · Ingeniería de Sistemas · Unidad 0 · Corte 1 · 2026-B

---

## Qué espero del curso

Llego queriendo aprender a construir un tablero completo, de principio a fin: conectar una fuente real, limpiarla y llegar a algo que responda preguntas y no solo que se vea bonito. Me interesa sobre todo la parte de Power Query. Sospecho que ahí está el trabajo que nadie muestra pero del que depende todo lo demás, y prefiero pelearme con datos sucios ahora que descubrir a mitad del semestre que el tablero está bien hecho sobre información que no lo está.

---

## El problema que me gustaría resolver

La deserción en los programas de Ingeniería de Sistemas del Huila.

Se habla de ella todo el tiempo y en términos bastante generales, pero es difícil ver dónde ocurre realmente. No es lo mismo perder estudiantes en primer semestre que perderlos en quinto: las causas son distintas y lo que habría que hacer al respecto también. Tampoco hay una lectura fácil de cómo se compara una institución con otra dentro de la misma región.

Lo que quisiera armar es un tablero que cruce inscritos, matriculados y graduados por año, programa e institución, y que permita ubicar el punto exacto donde se concentra la pérdida. Es un problema que me toca de cerca porque estoy dentro de uno de esos programas, y además tiene la ventaja de que las cifras ya existen y son públicas.

---

## De dónde saldrían los datos

De dos sistemas del Ministerio de Educación Nacional.

El **SNIES** publica, por institución y por programa académico, cuántos estudiantes se inscriben, son admitidos, se matriculan y se gradúan, con corte anual y semestral. De ahí saldría el grueso de la información: el conteo de estudiantes en cada programa y en cada periodo.

El **SPADIES** es el sistema que hace seguimiento específico a la deserción, con tasas por cohorte. Complementa al anterior justo en la medida que me interesa, que es la que el SNIES por sí solo no entrega directa.

Ambos se descargan en formatos tabulares y están publicados también en el portal de datos abiertos del Estado, así que no dependo de conseguir información privada de ninguna institución.

Pensando ya en el modelo, los conteos de estudiantes por periodo serían la tabla de hechos, y alrededor quedarían las dimensiones por las que quiero filtrar: el tiempo (año y semestre), el programa (nombre, nivel, metodología) y la institución (carácter público o privado, sede, municipio). Con esa estructura, la pregunta de fondo —en qué semestre se pierde más gente y cómo se compara mi programa con los demás de la región— se responde combinando filtros.
