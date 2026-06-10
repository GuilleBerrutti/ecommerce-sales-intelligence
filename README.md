# 📊 E-Commerce Sales Intelligence Dashboard

Dashboard ejecutivo desarrollado en **Power BI** para monitorear el desempeño comercial, comportamiento de clientes y eficiencia logística de un marketplace de e-commerce.

---

# 🎯 Problema de Negocio

Las organizaciones de comercio electrónico generan miles de transacciones diarias distribuidas entre productos, clientes, pagos y entregas.

Sin una visión consolidada resulta difícil:

* Detectar tendencias de ventas.
* Identificar categorías con mejor desempeño.
* Monitorear la evolución de clientes.
* Evaluar el rendimiento logístico.
* Detectar oportunidades de crecimiento comercial.

Este proyecto transforma datos transaccionales en indicadores estratégicos que facilitan la toma de decisiones basada en datos.

---

# 📈 Indicadores Clave de Rendimiento (KPIs)

| KPI             | Resultado |
| :-------------- | :-------: |
| Ventas Totales  |    91 M   |
| Pedidos Totales |    99 K   |
| Clientes Únicos |    96 K   |
| Ticket Promedio |    136    |
| Tasa de Entrega |    97%    |

> *Los resultados corresponden al dataset analizado y pueden variar según los filtros aplicados.*

---

# 📸 Dashboard

![Dashboard Overview](images/dashboard-overview.png)

---

# 🔍 Hallazgos Principales

### 1. Alta eficiencia logística

El 97% de los pedidos fueron entregados exitosamente, indicando una operación logística estable y una baja tasa de incidencias.

### 2. Concentración de ingresos

Un grupo reducido de categorías concentra gran parte de la facturación total, permitiendo identificar segmentos estratégicos para inversión y crecimiento.

### 3. Comportamiento estacional

El volumen de ventas presenta fluctuaciones mensuales que pueden asociarse a eventos promocionales y períodos de alta demanda.

### 4. Base de clientes amplia

El marketplace cuenta con una gran cantidad de clientes únicos, evidenciando alcance comercial y capacidad de adquisición.

### 5. Oportunidades de fidelización

El análisis de pedidos permite detectar segmentos con potencial para campañas de retención y recompra.

---

# 💡 Decisiones que Permite Tomar

Este dashboard puede utilizarse para:

* Priorizar categorías con mayor rentabilidad.
* Detectar caídas de ventas mensuales.
* Evaluar tendencias de crecimiento comercial.
* Monitorear indicadores logísticos.
* Analizar la evolución de clientes.
* Identificar oportunidades de fidelización.
* Optimizar campañas promocionales.
* Mejorar la planificación comercial.

---

# 🛠 Tech Stack

| Herramienta   | Uso                                     |
| ------------- | --------------------------------------- |
| Power BI      | Desarrollo de dashboards e informes     |
| Power Query   | Procesos ETL y transformación de datos  |
| DAX           | Métricas avanzadas y modelado analítico |
| Data Modeling | Construcción del modelo relacional      |
| Excel / CSV   | Fuente de datos                         |

---

# 🏗 Arquitectura del Modelo de Datos

El proyecto utiliza el dataset público **Olist E-Commerce**, uno de los marketplaces más grandes de Brasil.

Se implementó un modelo relacional optimizado para análisis de negocio compuesto por:

* Customers
* Orders
* Order Items
* Products
* Categories
* Order Payments
* Calendar Table

La Tabla Calendario fue desarrollada específicamente para habilitar análisis temporales avanzados como:

* Comparaciones Month-over-Month (MoM)
* Comparaciones Year-over-Year (YoY)
* Tendencias temporales
* Acumulados periódicos

---

# 📊 Principales Métricas DAX

### Ventas Totales

```dax
Ventas Totales =
SUM('Order Items'[price])
```

### Ticket Promedio

```dax
Ticket Promedio =
DIVIDE([Ventas Totales], [Pedidos])
```

### Ranking de Categorías

```dax
Ranking Categoría =
RANKX(
    ALL(Categories[product_category_name_english]),
    [Ventas Totales],
    ,
    DESC
)
```

Para consultar el repositorio completo de medidas:

📄 **docs/DAX-Guide.md**

---

# 📂 Estructura del Proyecto

```text
ecommerce-sales-intelligence/
│
├── dashboard/
│   └── EcommerceDashboard.pbix
│
├── data/
│   └── olist_dataset.csv
│
├── images/
│   └── dashboard-overview.png
│
├── docs/
│   └── DAX-Guide.md
│
├── README.md
└── LICENSE
```

---

# 🚀 Competencias Demostradas

* Business Intelligence
* Data Analytics
* Data Visualization
* KPI Design
* Data Modeling
* DAX
* Power Query
* ETL
* Dashboard Development
* Storytelling con Datos
* Toma de Decisiones Basada en Datos

---

# 📌 Dataset

Dataset público de Olist E-Commerce utilizado con fines educativos y de portfolio.

https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

---

### Autor

**Guillermo Berrutti**

Analista de Datos | Power BI | SQL | Excel | Business Intelligence

