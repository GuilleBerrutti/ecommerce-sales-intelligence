# 📊 E-Commerce Sales Intelligence Dashboard

Dashboard ejecutivo desarrollado en **Power BI** para analizar el desempeño comercial, ventas, clientes y logística de un marketplace de e-commerce.

---

## 🎯 Objetivo del Proyecto
Transformar datos transaccionales brutos en indicadores de negocio estratégicos (KPIs), permitiendo monitorear el rendimiento comercial en tiempo real, identificar oportunidades de crecimiento y facilitar la toma de decisiones basada en datos.

---

## 📈 Indicadores Clave de Rendimiento (KPIs)

| KPI | Resultado | Descripción |
| :--- | :---: | :--- |
| **Ventas Totales** | **91 Millones** | Facturación total acumulada en el marketplace. |
| **Pedidos Totales** | **99 Mill** | Volumen total de órdenes de compra procesadas. |
| **Clientes Únicos** | **96 Mill** | Total de consumidores únicos que realizaron transacciones. |
| **Ticket Promedio** | **13,6 Mill** | Valor medio de gasto por cada pedido realizado. |
| **Tasa de Entrega** | **97 %** | Porcentaje de pedidos completados con estado *Delivered*. |

---

## 🛠 Tech Stack & Herramientas
* **Power BI Desktop:** Construcción de reportes, diseño de UI y dashboards interactivos.
* **DAX (Data Analysis Expressions):** Modelado analítico y creación de métricas avanzadas.
* **Power Query:** Extracción, transformación y limpieza de datos (ETL).
* **Modelado de Datos:** Arquitectura y estructuración de esquemas relacionales eficientes.

---

## 📂 Arquitectura de Datos y Dataset

El proyecto utiliza el dataset público y real de **Olist E-Commerce** (el marketplace más grande de Brasil).

### 🧩 Estructura del Modelo Relacional
El modelo se diseñó bajo buenas prácticas de inteligencia de negocios, estructurando las entidades clave y desarrollando una **Tabla Calendario** a medida para habilitar análisis de inteligencia temporal:

* **Customers** ➔ Vinculado a **Orders** (Información demográfica del cliente).
* **Orders** ➔ Entidad central que conecta con **Order Items** y **Order Payments**.
* **Order Items** ➔ Conectado directamente a **Products** ➔ **Categories** (Detalle de productos y familias).
* **Calendario** ➔ Relación de uno a muchos con **Orders** (Gobernanza del tiempo).

---

## 📊 Repositorio de Fórmulas DAX

A continuación se detallan las medidas calculadas clave implementadas en el modelo:

```dax
-- 1. Facturación total del marketplace
Ventas Totales = SUM('Order Items'[price])

-- 2. Volumen de órdenes únicas
Pedidos = DISTINCTCOUNT(Orders[order_id])

-- 3. Total de clientes únicos
Clientes Únicos = DISTINCTCOUNT(Customers[customer_unique_id])

-- 4. Gasto medio por pedido
Ticket Promedio = DIVIDE([Ventas Totales], [Pedidos])

-- 5. Facturación filtrada exclusivamente por pedidos entregados con éxito
Ventas Entregadas = 
CALCULATE(
    [Ventas Totales],
    Orders[order_status] = "delivered"
)

-- 6. Análisis MoM (Month-over-Month) para comparar contra el mes previo
Ventas Mes Anterior = 
CALCULATE(
    [Ventas Totales],
    DATEADD(Calendario[Date], -1, MONTH)
)

-- 7. Ranking dinámico de categorías por volumen de ingresos
Ranking Categoría = 
RANKX(
    ALL(Categories[product_category_name_english]),
    [Ventas Totales],
    ,
    DESC
)
