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

![Dashboard Overview](https://github.com/GuilleBerrutti/ecommerce-sales-intelligence/blob/main/images/dashboard.png)

---

# 🔍 Hallazgos Principales

### 1. Alta eficiencia logística

El 97% de los pedidos fueron entregados exitosamente, indicando una operación logística estable y una baja tasa de incidencias.

### 2. Concentración de ingresos

Un grupo reducido de categorías concentra gran parte de la facturación total, lo que sugiere oportunidades de focalización estratégica en segmentos de alto impacto.

### 3. Comportamiento estacional

El volumen de ventas presenta variaciones mensuales asociadas a patrones de demanda y posibles eventos promocionales.

### 4. Base de clientes amplia

El marketplace cuenta con una base significativa de clientes únicos, evidenciando un buen nivel de alcance comercial.

### 5. Oportunidades de fidelización

El análisis de pedidos muestra una proporción relevante de clientes con compras únicas, lo que abre espacio para estrategias de retención.

---

# 💡 Decisiones de Negocio que Permite Tomar

Este dashboard está diseñado para apoyar decisiones como:

* Priorización de categorías de mayor contribución al ingreso.
* Detección de caídas o cambios en tendencias de ventas.
* Seguimiento del desempeño logístico en el tiempo.
* Evaluación del comportamiento de clientes.
* Identificación de segmentos con potencial de fidelización.
* Optimización de campañas comerciales y promociones.
* Mejora de la planificación de inventario y demanda.

---

# 📈 Análisis de Escenarios e Impacto Potencial

A partir del comportamiento observado en los KPIs, es posible plantear escenarios de mejora que sirven como guía para la toma de decisiones estratégicas.

Estos escenarios no representan predicciones, sino simulaciones basadas en la estructura del negocio:

| Escenario | Impacto Potencial |
|----------|------------------|
| Incremento del ticket promedio mediante estrategias de cross-selling | Aumento proporcional en ingresos sin necesidad de mayor adquisición de clientes |
| Mejora en la tasa de recompra de clientes | Mayor eficiencia del revenue por cliente existente |
| Optimización del rendimiento en categorías líderes | Mayor concentración de ingresos en segmentos estratégicos |
| Reducción de fricción en el proceso logístico | Mejora en la experiencia del cliente y retención |
| Incremento de la participación de clientes recurrentes | Estabilización del ingreso mensual |

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

# 📊 Business Logic & DAX Measures

### Ventas Totales

```dax
Ventas Totales =
SUM('Order Items'[price])
