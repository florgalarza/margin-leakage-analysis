# Análisis de Fugas de Margen: Dónde Desaparece la Rentabilidad

## El Problema Real

Mirás una operación retail y ves: "Nuestros productos tienen 75% de margen" pero la ganancia real es la mitad. Esa brecha no es un misterio contable. Es fuga.

Los descuentos que parecen pequeños se suman. El envío cuesta más de lo previsto. Algunas categorías de productos matan márgenes en silencio. Pero la mayoría de las empresas nunca lo cuantifican.

Este análisis investiga dónde exactamente se pierde esa rentabilidad—no con suposiciones, sino con números reales. La pregunta central es simple: si estamos perdiendo el 30% del margen potencial, ¿cuáles son las 5 decisiones que se lo comen? Y ¿qué cambiaría si arreglamos las 3 principales?

El punto no es solo analizar datos. Es pensar como alguien que gestiona un negocio: ¿qué decisión tomo con esta información? ¿Cuánto dinero se recupera? ¿Qué pierdo en el camino?

---

## La Pregunta de Negocio

Antes de cualquier SQL o visualización, necesitamos responder esto:

1. ¿Dónde está el dinero? Desglosá la brecha entre lo que deberíamos ganar y lo que realmente ganamos. Asignale un monto en pesos a cada fuga.

2. ¿Vale la pena descontar? Si descuentas 15%, ¿realmente vendés 15% más volumen? ¿O solo le regalás margen a clientes que hubieran comprado igual?

3. ¿El envío rápido justifica su costo? Suena premium, pero ¿nos hace ganar dinero o solo nos cuesta más?

4. ¿Qué segmento es realmente rentable? Algunos se ven bien por volumen, pero destruyen margen una vez que contabilizás descuentos y logística.

5. ¿Qué vale la pena cambiar? Si arreglamos la fuga más grande, ¿qué ganamos? ¿Qué perdemos?

---

## Cómo Lo Medí

### La Matemática

Margen Teórico (si vendiéramos todo a precio de lista):
- (Precio de Lista - Costo) / Precio de Lista

Margen Realizado (lo que realmente pasó):
- Ganancia Real / Ventas Reales

La Brecha = Fuga. Ahora la desglosamos:

1. Fuga por Descuentos
- Cuánto dejamos sobre la mesa en descuentos
- Si descuentas 20% pero solo subís 3% el volumen, esa es mala matemática
- Señal: ¿descuentas más en categorías de alto volumen o bajo margen?

2. Fuga por Envío (como proxy de costo logístico)
- Margen real para Envío Same-Day vs. Envío Estándar
- Nota importante: No podemos probar que Same-Day causa márgenes más bajos. Clientes premium podrían elegir Same-Day. Pero podemos ver la correlación.
- La pregunta es: ¿esa correlación es selección o causalidad?

3. Fuga por Mix de Productos
- Algunas categorías tienen alto volumen pero márgenes negativos
- Algunas tienen márgenes excelentes pero bajo volumen
- El mix que realmente vendés podría destruir rentabilidad

4. Fuga por Segmento de Cliente
- ¿Algunos tipos de cliente (Consumidor, Corporativo, Home Office) tienen márgenes sistemáticamente más bajos?
- ¿Estamos subsidiando segmentos no rentables?

5. Todo lo Demás
- Devoluciones, errores de precio, desperdicio operacional

---

## Análisis Planeado

1. Desglose de Fugas (en progreso)
En pesos y porcentajes, cuánto cuesta cada factor. Si los descuentos nos cuestan $500k, eso importa. Si cuestan $50k, es ruido.

Qué se pretende:
- Waterfall claro: margen teórico → margen real → desagregación de fugas
- Asignación en pesos de cada fuente de fuga
- Identificación de las 3 fugas más grandes

2. En Descuentos Específicamente (pendiente)
Qué se pretende:
- Qué categorías reciben descuentos pesados
- Correlación entre descuento y volumen (elasticidad)
- Identificar categorías donde el descuento es irracional

3. En Envío (pendiente)
Qué se pretende:
- Comparativa de margen real: Same-Day vs. Estándar
- Diferenciar entre efecto de selección y causalidad
- Conclusión sobre viabilidad de Same-Day como estrategia

4. Por Segmento de Cliente (pendiente)
Qué se pretende:
- Rentabilidad real de cada segmento (Consumidor, Corporativo, Home Office)
- Identificar qué segmentos subsidian a otros
- Recomendación sobre segmentos críticos

5. Escenarios de Recuperación (pendiente)
Qué se pretende:
- Modelado de "qué pasa si reducimos X fuga en 20%"
- Cuánto volumen podríamos perder y seguir ganando
- Trade-off analysis en números reales

---

## Los Datos

Fuente: Dataset Superstore Sales de Kaggle
Link: https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting

Qué contiene:
- ~10,000 transacciones de un retailer de EE.UU.
- Años 2014-2017
- 4 regiones, 3 segmentos de cliente, 17 subcategorías de productos
- Campos: monto de venta, cantidad, descuento %, ganancia real, método de envío, y más

Nota: Este es un dataset educativo (Tableau Public). El objetivo es mostrar el método, no hacer recomendaciones de negocio reales. Pero el método es real—así investigarías problemas de margen en cualquier empresa.

---

## Qué Voy a Entregar

1. Análisis Base (pendiente)
- EDA: exploración inicial, distribuciones, outliers
- Snapshot de margen por categoría, región, segmento
- Identificación de problem areas

2. Desglose de Fugas en Números (pendiente)
- Waterfall visual y tabla con desagregación
- Heatmap: fuga por categoría x segmento
- Impacto en pesos de cada fuente

3. Deep Dive en Descuentos (pendiente)
- Análisis de elasticidad precio-volumen
- Categorías con descuento irracional
- Recomendaciones por categoría

4. Economía del Envío (pendiente)
- Comparativa Same-Day vs. Estándar
- Análisis de selección vs. causalidad
- Viabilidad de la estrategia actual

5. P&L por Segmento (pendiente)
- Rentabilidad real por segmento de cliente
- Subsidios implícitos entre segmentos
- Recomendaciones de portafolio

6. Escenarios y Trade-offs (pendiente)
- Modelos de "qué pasa si"
- Break-even analysis
- Recomendaciones priorizadas

---

## Qué NO Es Este Análisis

- No afirmamos causalidad donde no la tenemos. Si Same-Day shipping se ve no rentable, podría ser porque clientes premium eligen Same-Day, no porque Same-Day nos cuesta dinero. Lo flagearé.

- No incluimos costos que no podemos medir. Sin asignación de overhead, sin costo de adquisición de cliente, sin análisis de retenciones. Solo ganancia a nivel transacción.

- No predecimos el futuro. Esto es historia. Podemos decir "en datos pasados, este patrón nos costó X", no "si implementas esto, la ganancia subirá 20%".

- No contabilizamos lealtad. Un descuento barato que trae de vuelta a un cliente recurrente vale más que lo que muestra la transacción. Pero no podemos medir tasas de repetición acá.

- No decimos que todos los segmentos no rentables deban desaparecer. A veces mantenés una unidad de bajo margen por razones estratégicas. Pero deberías saber que lo estás haciendo y cuánto te cuesta.

---

## Cómo Lo Construí

- SQL: Extracción de datos, cálculo de márgenes, agregaciones
- Python: Limpieza de datos, análisis estadístico, visualizaciones
- Librerías: Pandas, NumPy, Matplotlib, Seaborn
- Control de Versiones: Todo en GitHub para que veas el proceso

---

## Estructura del Repositorio

├── data/
│   └── superstore_sales.csv          # Dataset original
├── notebooks/
│   ├── 01_exploracion_inicial.ipynb  # EDA y limpieza
│   ├── 02_calculo_margenes.ipynb     # Lógica de margen teórico vs realizado
│   ├── 03_desglose_fugas.ipynb       # Análisis de cada tipo de fuga
│   ├── 04_analisis_descuentos.ipynb  # Deep dive en descuentos
│   └── 05_escenarios.ipynb           # Análisis de "qué pasa si"
├── visualizaciones/
│   ├── desglose_fugas.png
│   ├── margen_por_categoria.png
│   ├── elasticidad_descuentos.png
│   └── p&l_por_segmento.png
├── resultados/
│   └── resumen_ejecutivo.csv         # Números clave en formato table-friendly
└── README.md                          # Este archivo

---

## Cómo Usar Este Análisis

1. Para aprender el método: Revisá los notebooks en orden. Cada uno construye sobre el anterior.

2. Para replicarlo en tu negocio: Los notebooks están comentados. Cambiá los nombres de columnas, los umbrales de descuento, los segmentos—la lógica sigue siendo válida.

3. Para presentar a stakeholders: Usá las visualizaciones y el resumen ejecutivo. Los números específicos importan menos que el insight: "Acá hay dinero recuperable si hacemos X."

---

## Próximos Pasos

1. Extracción y Limpieza: Cargar datos, validar integridad, preparar para análisis
2. Cálculo de Márgenes: Definir margen teórico vs. realizado, construir bases de datos
3. Desglose de Fugas: Cuantificar cada fuente de fuga
4. Análisis Profundo: Descuentos, envío, segmentos, escenarios
5. Visualizaciones: Construir reportes ejecutivos
6. Síntesis: Resumen de hallazgos y recomendaciones

---