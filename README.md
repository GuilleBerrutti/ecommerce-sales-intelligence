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