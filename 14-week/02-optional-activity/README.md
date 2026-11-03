# Semana 14 · Publica y comparte tu informe

**Estudiante:** Juan José Horta Vanegas
**Asignatura:** Inteligencia de Negocios · Corte 3 · 2026-B
**Informe:** `Horta-Juan-semana14-movil.pbix` (dashboard de la tostadora de café de la Semana 12, ahora con vista móvil)

---

## 1. Publicación del informe (proceso documentado)

No cuento con una cuenta institucional con acceso al servicio de Power BI, así que documento el proceso paso a paso.

1. Abrir el `.pbix` en Power BI Desktop e iniciar sesión con la cuenta de la organización.
2. En la pestaña **Inicio**, pulsar **Publicar**.
3. Elegir el **área de trabajo** de destino. Para un informe de ventas usaría un área de trabajo del equipo comercial y no «Mi área de trabajo», porque en esta última nadie más lo ve.
4. Esperar el mensaje «Publicación correcta» y abrir el enlace que ofrece Desktop: el informe queda en app.powerbi.com.
5. Revisar en el navegador que los segmentadores, las tarjetas y el drill-down se comporten igual que en Desktop.
6. Si el informe va a una audiencia amplia, empaquetarlo como **app** del área de trabajo (solo lectura) y fijar los visuales clave en un dashboard del servicio.

## 2. Con quién lo compartiría, con qué permisos y por qué

| Con quién | Permiso | Por qué |
|---|---|---|
| Gerencia comercial | Lector (Visor), a través de la app | Toma decisiones con las cifras, pero no necesita modificar nada. |
| Responsables de ventas por ciudad | Lector, con seguridad a nivel de fila sobre `Dim_Cliente[ciudad]` | Cada uno debe ver solo su ciudad; así no se expone la venta de las demás. |
| Analista que mantiene el informe | Colaborador del área de trabajo | Es quien republica y ajusta el modelo; el permiso se le quita si deja el cargo. |

Criterios de seguridad: se comparte con personas o grupos concretos y nunca con un enlace abierto a toda la organización, porque el informe trae ventas, márgenes y presupuesto. El permiso por defecto es de lectura y no se activa el permiso para volver a compartir, de modo que el acceso solo lo reparte el dueño. Cada trimestre revisaría la lista de quién tiene acceso.

## 3. Actualización de datos

Estrategia: **actualización programada**, una vez al día a las 6:00 a. m., antes de que la gerencia abra el informe.

- Si la fuente es un archivo local (Excel o CSV en un computador), la nube no lo alcanza sola: se necesita una **puerta de enlace (gateway)** instalada en un equipo que esté encendido a esa hora, y la fuente se configura en el servicio con las credenciales del gateway.
- Si la fuente estuviera en la nube (SharePoint, OneDrive o una base de datos en línea), no hace falta gateway.
- Los pasos aplicados de Power Query se reaplican en cada actualización, por lo que la limpieza no se repite a mano.
- Si la actualización falla, el servicio envía un aviso al dueño del conjunto de datos. En ese caso se actualiza manualmente desde Desktop y se vuelve a publicar.

## 4. Vista móvil

Diseñada en la vista de diseño móvil de la página 1, en vertical, con lo que más se consulta desde el celular:

| Orden | Visual | Por qué va |
|---|---|---|
| 1 | Cuatro tarjetas en cuadrícula de 2×2: Ventas Totales, % Margen, % Cumplimiento y Ventas totales 2025 | Son los KPI; se leen sin tocar nada. |
| 2 | Segmentador de fecha (Entre) | Control grande, tocable con el dedo. |
| 3 | Segmentador de ciudad (desplegable) | Un solo toque abre la lista. |
| 4 | Gráfico de barras de ventas y presupuesto por categoría | Es el gráfico que resume el desempeño. |

El gráfico de columnas por categoría y producto, el de la página 2 y el resto del detalle se dejan solo para la vista web.

![Vista móvil](imagenes/vista-movil.png)
