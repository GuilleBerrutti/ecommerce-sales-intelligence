# 📘 DAX Guide

Guía de las principales funciones DAX utilizadas en el proyecto.

---

# SUM

### Descripción

Suma todos los valores de una columna numérica.

### Ejemplo

```DAX
Ventas Totales =
SUM('Order Items'[price])
```

### Uso en el proyecto

Calcular el volumen total de ventas generado por el marketplace.

---

# DISTINCTCOUNT

### Descripción

Cuenta valores únicos dentro de una columna.

### Ejemplo

```DAX
Pedidos =
DISTINCTCOUNT(Orders[order_id])
```

### Uso en el proyecto

Calcular la cantidad total de pedidos sin duplicados.

---

# DIVIDE

### Descripción

Realiza divisiones de forma segura evitando errores cuando el denominador es cero.

### Ejemplo

```DAX
Ticket Promedio =
DIVIDE([Ventas Totales],[Pedidos])
```

### Uso en el proyecto

Calcular el ingreso promedio por pedido.

---

# CALCULATE

### Descripción

Modifica el contexto de filtros para recalcular una medida bajo determinadas condiciones.

### Ejemplo

```DAX
Ventas Entregadas =
CALCULATE(
    [Ventas Totales],
    Orders[order_status] = "delivered"
)
```

### Uso en el proyecto

Obtener ventas correspondientes únicamente a pedidos entregados.

---

# DATEADD

### Descripción

Permite desplazar un período temporal hacia adelante o hacia atrás.

### Ejemplo

```DAX
Ventas Mes Anterior =
CALCULATE(
    [Ventas Totales],
    DATEADD(
        Calendario[Date],
        -1,
        MONTH
    )
)
```

### Uso en el proyecto

Comparar ventas actuales contra el mes anterior.

---

# RANKX

### Descripción

Genera rankings dinámicos utilizando una medida.

### Ejemplo

```DAX
Ranking Categoría =
RANKX(
    ALL(Categories[product_category_name_english]),
    [Ventas Totales],
    ,
    DESC
)
```

### Uso en el proyecto

Identificar las categorías con mayor volumen de ventas.

---

# ALL

### Descripción

Elimina filtros de una tabla o columna.

### Ejemplo

```DAX
ALL(Categories[product_category_name_english])
```

### Uso en el proyecto

Comparar una categoría contra todas las demás al generar rankings.

---

# FILTER

### Descripción

Devuelve una tabla filtrada según una condición.

### Ejemplo

```DAX
FILTER(
    ALL(Categories),
    [Ranking Categoría] <= 5
)
```

### Uso en el proyecto

Analizar subconjuntos específicos de información.

---

# DATE

### Descripción

Construye una fecha a partir de año, mes y día.

### Ejemplo

```DAX
Fecha Pedido =
DATE(
    YEAR(Orders[order_purchase_timestamp]),
    MONTH(Orders[order_purchase_timestamp]),
    DAY(Orders[order_purchase_timestamp])
)
```

### Uso en el proyecto

Eliminar la hora de los pedidos para relacionarlos con la tabla calendario.

---

# YEAR

Extrae el año de una fecha.

```DAX
YEAR(Orders[order_purchase_timestamp])
```

---

# MONTH

Extrae el mes de una fecha.

```DAX
MONTH(Orders[order_purchase_timestamp])
```

---

# DAY

Extrae el día de una fecha.

```DAX
DAY(Orders[order_purchase_timestamp])
```

---

# Conclusión

Las funciones DAX utilizadas permitieron desarrollar indicadores comerciales, análisis temporales, rankings dinámicos y métricas operativas para la construcción de un dashboard ejecutivo orientado a la toma de decisiones.
