## 📊 Repositorio de Fórmulas DAX

A continuación se detallan las medidas calculadas clave implementadas en el modelo:

```dax
** 1. Facturación total del marketplace**
            Ventas Totales = SUM('Order Items'[price])

## Descripción

Suma todos los valores de una columna numérica.

### Uso en el proyecto

Calcular el volumen total de ventas generado por el marketplace

-- 2. Volumen de órdenes únicas
Pedidos = DISTINCTCOUNT(Orders[order_id])

# DISTINCTCOUNT

### Descripción

Cuenta valores únicos dentro de una columna.

### Uso en el proyecto

Calcular la cantidad total de pedidos sin duplicados.

-- 3. Total de clientes únicos
Clientes Únicos = DISTINCTCOUNT(Customers[customer_unique_id])

# DIVIDE

### Descripción

Realiza divisiones de forma segura evitando errores cuando el denominador es cero.

### Ejemplo

```

### Uso en el proyecto

Calcular el ingreso promedio por pedido.

-- 4. Gasto medio por pedido
Ticket Promedio = DIVIDE([Ventas Totales], [Pedidos])

# CALCULATE

### Descripción

Modifica el contexto de filtros para recalcular una medida bajo determinadas condiciones.

### Uso en el proyecto

Obtener ventas correspondientes únicamente a pedidos entregados.

-- 5. Facturación filtrada exclusivamente por pedidos entregados con éxito
Ventas Entregadas = 
CALCULATE(
    [Ventas Totales],
    Orders[order_status] = "delivered"
)

# DATEADD

### Descripción

Permite desplazar un período temporal hacia adelante o hacia atrás.

### Uso en el proyecto

Comparar ventas actuales contra el mes anterior.


-- 6. Análisis MoM (Month-over-Month) para comparar contra el mes previo
Ventas Mes Anterior = 
CALCULATE(
    [Ventas Totales],
    DATEADD(Calendario[Date], -1, MONTH)
)

# RANKX

### Descripción

Genera rankings dinámicos utilizando una medida.

### Uso en el proyecto

Identificar las categorías con mayor volumen de ventas.

-- 7. Ranking dinámico de categorías por volumen de ingresos
Ranking Categoría = 
RANKX(
    ALL(Categories[product_category_name_english]),
    [Ventas Totales],
    ,
    DESC
)

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
