# 📊 E-Commerce Sales Intelligence Dashboard

Dashboard ejecutivo desarrollado en Power BI para analizar ventas, clientes, pedidos y desempeño comercial de un marketplace de e-commerce.

---

## 🎯 Objetivo del Proyecto
Transformar datos transaccionales en indicadores de negocio que permitan monitorear el rendimiento comercial, identificar oportunidades de crecimiento y facilitar la toma de decisiones basada en datos.

---

## 📈 Resultados Clave

| KPI | Resultado |
| :--- | :--- |
| **Ventas Totales** | 91 M |
| **Pedidos** | 99 K |
| **Clientes Únicos** | 96 K |
| **Ticket Promedio** | 13,6 K |
| **Pedidos Entregados** | 97 % |

---

## 🛠 Herramientas Utilizadas
* Power BI
* DAX
* Power Query
* Modelado de Datos

---

## 📂 Dataset
Se utilizó el dataset público de **Olist E-Commerce**.

### Tablas principales:
* Customers
* Orders
* Order Items
* Products
* Categories
* Payments
* Sellers

---

## 🧩 Modelo de Datos
Se construyó un modelo relacional conectando las distintas entidades del negocio mediante claves únicas. Además, se desarrolló una tabla calendario para habilitar análisis temporales y comparaciones entre períodos.

### Relaciones principales
```text
Customers
    │
    └── Orders
            │
            ├── Order Items
            │       │
            │       └── Products
            │               │
            │               └── Categories
            │
            └── Order Payments

Calendario
    │
    └── Orders

📊 KPIs Desarrollados
Ventas Totales
Fragmento de código
Ventas Totales = 
SUM('Order Items'[price])
Pedidos
Fragmento de código
Pedidos = 
DISTINCTCOUNT(Orders[order_id])
Clientes Únicos
Fragmento de código
Clientes Únicos = 
DISTINCTCOUNT(Customers[customer_unique_id])
Ticket Promedio
Fragmento de código
Ticket Promedio = 
DIVIDE([Ventas Totales],[Pedidos])
Ventas Entregadas
Fragmento de código
Ventas Entregadas = 
CALCULATE(
    [Ventas Totales],
    Orders[order_status] = "delivered"
)
Ventas Mes Anterior
Fragmento de código
Ventas Mes Anterior = 
CALCULATE(
    [Ventas Totales],
    DATEADD(
        Calendario[Date],
        -1,
        MONTH
    )
)
Ranking Categoría
Fragmento de código
Ranking Categoría = 
RANKX(
    ALL(Categories[product_category_name_english]),
    [Ventas Totales],
    ,
    DESC
)
📈 Análisis Realizados
Evolución Temporal de Ventas: Análisis mensual de ingresos utilizando una tabla calendario y funciones de inteligencia temporal.

Categorías Más Rentables: Top categorías por volumen de ventas:

Health Beauty

Watches Gifts

Bed Bath Table

Sports Leisure

Computers Accessories

Estado de los Pedidos: Monitoreo del ciclo operativo de pedidos:

Delivered

Shipped

Processing

Invoiced

Canceled

Unavailable

📷 Dashboard
A continuación se muestra una captura de pantalla del dashboard interactivo:

📚 Conceptos Aplicados
Modelado Relacional

Inteligencia Temporal

DAX (Data Analysis Expressions)

Contexto de Filtro

KPIs de Negocio

Rankings Dinámicos

Storytelling con Datos

🚀 Aprendizajes
Durante este proyecto se desarrollaron habilidades clave en:

Construcción de dashboards ejecutivos orientados a negocio.

Diseño e implementación de métricas financieras y operacionales.

Modelado de datos robusto en Power BI (Esquema Estrella/Copo de Nieve).

Creación de medidas y cálculos avanzados en DAX.

Técnicas avanzadas de visualización de datos.

Análisis exploratorio de datos (EDA).

👤 Autor
Guillermo Berrutti Analista de Datos

Power BI | SQL | Excel | Data Visualization

LinkedIn: Agregar enlace

GitHub: Agregar enlace
