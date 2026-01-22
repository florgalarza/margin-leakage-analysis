# Margin Leakage Analysis: Where Does Profitability Disappear?

## El Ejercicio

Me hice la siguiente pregunta: **¿En una operación de retail, dónde desaparece el margen?**

No es suficiente tener un 80% margen teórico si en la práctica es 60%. Algo está erosionando esa ganancia. Descuentos, logística cara, devoluciones. Este análisis identifica específicamente dónde y cuánto impacto tiene cada factor.

El objetivo es demostrar cómo abordaría una pregunta de negocio real: empezar con una métrica que no cierra, investigar las causas raíz, y terminar con recomendaciones cuantificadas en dinero.

---

## Los Datos

Usé el dataset **Superstore Sales Forecasting** disponible en Kaggle:
https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting

Es un dataset histórico de una empresa de retail estadounidense con:
- ~10,000 transacciones
- Múltiples categorías y subcategorías
- Información de descuentos aplicados
- Profit/Loss por transacción
- Segmentación por tipo de cliente y región

*Transparencia:* Los datos son educativos (Tableau públicos). El propósito es demostrar metodología, no hacer recomendaciones sobre operaciones reales.

---

## Qué Analizo

Para cada categoría y segmento, calculo:

### 1. Descuentos: ¿Cuánto regalamos de precio?
```
Leakage por Descuento = Precio Original - Precio Vendido
Impacto: Si descuento 20% pero solo gano 5% en volumen, me conviene?
```

### 2. Logística: ¿Qué cuesta enviar?
```
Proxy: Comparar margen por Shipping Mode
Same Day vs Standard: ¿Cuál es rentable?
```

### 3. Mix de Productos: ¿Qué vendemos?
```
Categorías con margen alto pero bajo volumen
Categorías con volumen alto pero margen negativo
El trade-off real
```

### 4. Segmentos de Cliente: ¿Quién genera pérdida?
```
¿Algunos segmentos tienen margen negativo después de descuentos?
¿Vale la pena mantenerlos?
```

### 5. Margen Leakage Total
```
Margen Teórico = Si vendemos todo a precio list sin descuentos
Margen Real = Profit / Sales actual
Diferencia = LEAKAGE
```

---

## Lo Que Voy a Buscar

Las preguntas que importan en retail:

**¿Estamos regalando dinero en descuentos?**
- Si descuentos promedio suben 5%, ¿impacta profit 10%?
- ¿Hay categorías donde el descuento es insostenible?

**¿La logística está comiendo margen?**
- ¿Algunos shipping modes son rentables, otros no?

**¿Hay productos/segmentos que pierden dinero?**
- ¿Vendemos algo a pérdida consistentemente?
- ¿Por qué seguimos vendiéndolo?

**¿Podemos recuperar margen sin perder volumen?**
- Si reducimos descuentos en categoría X, ¿cuánto volumen perdemos?
- Trade-off: -5% volumen pero +$50k profit. ¿Vale?

---

## Limitaciones

- Datos históricos (no predicción)
- No incluye costos operativos fijos (solo transaccionales)
- No incluye análisis de customer retention (¿el descuento trae clientes que vuelven?)
- Una sola empresa, un momento específico en el tiempo

---

## Archivos

- `queries/` → SQL scripts del análisis
- `results/` → CSVs con resultados
- `analysis/` → Notebooks o documentos con insights
- `README.md` → Este archivo

---

## Nota Final

La mayoría de análisis de retail mira números sin contexto: "Tenemos 60% margen." Ok, pero ¿por qué es 60% y no 80%? ¿Qué podríamos cambiar sin destruir el negocio?

Este análisis intenta responder eso. No es perfecto - es investigación. Pero es la investigación que importa.

