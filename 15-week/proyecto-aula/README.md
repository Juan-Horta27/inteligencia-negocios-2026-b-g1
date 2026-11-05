# Proyecto de Aula · Corte 3

*Del dato a la decisión: un tablero de inteligencia de negocios para Andes Store*  
Electiva Inteligencia de Negocios · 2026-B · Ingeniería de Sistemas, CORHUILA

---

## Ficha del Proyecto (Fase 0)

| Campo | Detalle |
| :--- | :--- |
| **Integrantes** | Andres Felipe Gomez Anacona, Juan Jose Horta Vanegas, Laura Sofia Vallejo Oviedo y Maria Paula Barrios Fajardo |
| **Empresa y tipo** | Andes Store (Ficticia, comercio minorista en línea). |
| **Sector / Oferta** | Venta en línea de productos de consumo masivo en 8 categorías: lácteos, carnicería, panadería, frutas y verduras, congelados, bebidas, galletitas y snacks, y conservas. |
| **Problema de negocio** | Desconocimiento del impacto real de las categorías de productos y métodos de pago en las variaciones mensuales de ventas, lo que dificulta la planificación de promociones e inventario. |
| **Pregunta de negocio** | ¿Qué categorías de productos y qué métodos de pago explican las variaciones mensuales de las ventas en 2024? |
| **KPI Principal** | **Ventas Totales** = $\sum (\text{Cantidad} \times \text{Precio unitario})$ |
| **KPIs de Apoyo** | **Ticket Promedio** = $\frac{\text{Ventas Totales}}{\text{Número de transacciones}}$ <br> **Unidades Vendidas** = $\sum \text{Cantidad}$ |
| **Fuentes de Datos** | 5 archivos CSV (Kaggle): `ventas.csv` (3.031 filas, 31/01/2024 - 30/12/2024), `clientes.csv` (326), `productos.csv` (38), `categorias.csv` (8) y `metodos_pago.csv` (5). |
| **Autorización** | No aplica (Empresa ficticia). |

---

## Estructura del Repositorio

```text
proyecto-aula/
├── README.md                          # Documentación principal del proyecto
├── Datos.pbix                         # Modelo de datos y tablero interactivo en Power BI
├── INFORME TECNICO ANDES STORE.pdf    # Informe técnico detallado y correcciones del proyecto
├── categorias.csv                     # Catálogo de categorías de productos (8 registros)
├── clientes.csv                       # Directorio de clientes (326 registros)
├── metodos_pago.csv                   # Métodos de pago registrados (5 registros)
├── productos.csv                      # Catálogo de productos (38 registros)
└── ventas.csv                         # Histórico de transacciones (3.031 filas)
