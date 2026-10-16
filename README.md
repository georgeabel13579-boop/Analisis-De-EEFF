# Análisis de Regresión Lineal

Aplicativo frontend en **HTML + CSS + JS** para entrenar y usar modelos de
regresión lineal simple o múltiple sobre datos cargados desde el repositorio.

El proceso es totalmente local: el archivo no se envía a ningún servidor. Solo se
consumen librerías de CDN (Papaparse, SheetJS y Plotly.js) para leer archivos y
dibujar gráficas.

---

## ¿Qué hace?

1. **Carga datos** desde `.csv`, `.xlsx` o `.xls` (arrastrar o seleccionar).
2. **Reconoce automáticamente** las variables numéricas y categóricas.
3. Permite elegir:
   - Variable dependiente (Y).
   - Tipo de modelo: **simple** (una X) o **múltiple** (2 o más X).
   - Incluir o no la constante (intersección).
4. Entrena el modelo de regresión lineal.
5. Muestra métricas de desempeño:
   - R² (coeficiente de determinación)
   - RMSE (error cuadrático medio)
   - MAE (error absoluto medio)
   - MAPE (error medio porcentual)
   - n = número de observaciones
   - Constante
6. Grafica el modelo con opciones de escala logarítmica.
7. Permite hacer predicciones manuales con la ecuación del modelo.

---

## Estructura de archivos

```
Analisis_Regresion_HTML/
├── index.html      # Interfaz principal
├── style.css       # Estilos
├── main.js         # Lógica del análisis de regresión
└── README.md       # Este archivo
```

---

## Cómo usarlo

1. Abre `index.html` en cualquier navegador moderno.
2. Arrastra un archivo CSV o Excel al área indicada.
3. El sistema mostrará automáticamente:
   - Número de filas y columnas.
   - Variables numéricas detectadas.
   - Variables categóricas detectadas.
4. Selecciona:
   - La variable dependiente `Y`.
   - El tipo de modelo: `simple` o `multiple`.
   - La variable independiente `X` (o las variables adicionales para múltiple).
5. Presiona **Entrenar modelo**.
6. Visualiza las métricas, la gráfica y realiza predicciones con el modelo.

---

## Formatos de entrada

El aplicativo reconoce automáticamente variables por nombre y tipo. Se recomienda
usar columnas claras, por ejemplo:

| CODIGO | NOMBRE | TIPO | DEBE | HABER | SALDO_ABS | UDAI | Y_OBJ |
|---|---|---|---|---|---|---|---|

- `Y_OBJ` o cualquier columna numérica puede usarse como variable dependiente.
- Columnas numéricas como `UDAI`, `DEBE`, `HABER`, `SALDO_ABS` pueden usarse como
  variables independientes.
- Las variables de texto se convertirán en variables categóricas si se incluyen
  en el modelo múltiple.

---

## Métricas del modelo

| Métrica | Significado |
|---|---|
| `R²` | Bonanza de ajuste. Cuanto más cercano a 1, mejor. |
| `RMSE` | Error promedio ponderado por el cuadrado. Menor es mejor. |
| `MAE` | Error absoluto promedio. Interpretación sencilla. |
| `MAPE` | Error promedio porcentual. Útil cuando Y > 0. |
| `n` | Cantidad de observaciones usadas. |
| `Constante` | Intersección de la regresión. |

---

## Predicción

En el panel de predicciones puedes escribir una expresión como:

```
Y = 100 + 2.5*UDAI - 0.001*DEBE
```

El aplicativo reemplazará los nombres de variable y calculará el valor estimado
usando los coeficientes del modelo entrenado.

Ejemplo:

```
Y = 100 + 2.5*UDAI - 0.001*DEBE
```

Con `UDAI = 50000` y `DEBE = 10000`.

---

## Notas técnicas

- Los cálculos se hacen en el navegador con JavaScript puro (sin dependencias
  externas de corazón).
- Las variables categóricas se transforman internamente en indicadores.
- Si una variable independiente tiene variación prácticamente cero o multicolinealidad
  fuerte, el modelo puede mostrar un mensaje de advertencia sobre la matriz de diseño.
- Para gráficas múltiples, la visualización proyecta el efecto de las variables
  elegidas manteniedo las demás en su valor promedio o moda.

---

## Requisitos

- Navegador moderno.
- Conexión a Internet para cargar los CDNs:
  - PapaParse
  - SheetJS
  - Plotly.js

Sin esas conexiones, el sitio aún cargará pero no leerá archivos ni graficará.

---

## Licencia

Propósito docente y analítico. Uso libre.
