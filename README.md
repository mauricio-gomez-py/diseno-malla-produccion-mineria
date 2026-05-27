# Diseño de Malla de Producción para Minería a Cielo Abierto

Implementación en Python del diseño empírico de mallas de perforación para minería a cielo abierto, utilizando los métodos de **Pearse-Borquéz** y **Chiappetta**.

## Propuesta de valor

El diseño de mallas de perforación se realiza tradicionalmente de forma manual con fórmulas en Excel o calculadoras, requiriendo conocimiento especializado en geomecánica y tronadura. Este proyecto automatiza ese proceso y agrega tres ventajas concretas:

- **Cálculo instantáneo**: ingresando las propiedades de la roca y el explosivo, se obtienen todos los parámetros de diseño (burden, espaciamiento, taco, carga) en segundos, sin riesgo de error manual.
- **Visualización 3D interactiva**: permite ver la distribución real de los pozos y sus zonas de carga en el espacio, algo que en el flujo tradicional simplemente no existe — se trabaja solo con tablas y planos 2D.
- **Reproducibilidad y trazabilidad**: cualquier cambio en los parámetros de entrada se propaga automáticamente a todos los resultados, y queda registro de cómo se calculó cada diseño.

**Usuario objetivo**: ingenieros de minas o especialistas en tronadura que necesitan evaluar múltiples escenarios rápidamente (distintos diámetros de pozo, densidades de explosivo, geometrías de malla) sin rehacerlo todo desde cero cada vez.

## Descripción

El notebook calcula los parámetros geométricos y de carga de una malla de perforación a partir de las propiedades del macizo rocoso y del explosivo, y genera una visualización 3D interactiva de los pozos con sus zonas de carga.

### Métodos implementados

- **Pearse-Borquéz**: cálculo del Burden óptimo en función del índice de volabilidad (Kv), el diámetro del pozo y la potencia de detonación del explosivo.
- **Chiappetta (Taco Crítico)**: determinación de la longitud mínima de taco para contener adecuadamente la energía del explosivo.

## Parámetros de entrada

| Parámetro | Descripción |
|---|---|
| `d` | Diámetro del pozo (pulgadas) |
| `de` | Densidad del explosivo (t/m³) |
| `vod` | Velocidad de detonación — VOD (m/s) |
| `h` | Altura del banco (m) |
| `dr` | Densidad de la roca (t/m³) |
| `rqd` | Rock Quality Designation — RQD (%) |
| `ucs` | Resistencia a la compresión uniaxial — UCS (psi) |
| `srb` | Relación espaciamiento/burden (B/E) |
| `rd` | Factor de corrección de discontinuidades |
| `x_inicio`, `x_final`, `y_inicio`, `y_final` | Dimensiones del área de la malla (m) |

## Resultados

El notebook entrega:

- **Burden** y **Espaciamiento** entre pozos
- **Taco crítico** y **Pasadura** (sobreperforación)
- **Carga explosiva** por pozo
- **Número de pozos** y **metros perforados** totales
- **Gráfico 3D interactivo** con los pozos coloreados por zona (Taco / Explosivo / Pasadura)
- **Tabla resumen** con todos los parámetros calculados

## Ejemplo de visualización

El gráfico 3D generado con Plotly muestra la distribución espacial de todos los pozos dentro del área definida, diferenciando con colores las tres zonas de cada pozo:

- **Taco**: sellado superior del pozo (material estéril)
- **Explosivo**: zona de carga activa
- **Pasadura**: sobreperforación inferior del banco

## Requisitos

```
pandas
numpy
plotly
nbformat>=4.2.0
```

Instalar dependencias:

```bash
pip install pandas numpy plotly nbformat
```

## Uso

1. Abrir `DISEÑO MALLA DE PRODUCCIÓN - PERFORACIÓN.ipynb` en Jupyter o VS Code
2. Modificar los parámetros de entrada en la **celda 1** según las condiciones del proyecto
3. Ejecutar todas las celdas (`Run All`)

## Referencias

- Pearse, G. E. & Borquéz, G. (1981). *Blastability and Blast Design*
- Chiappetta, R. F. (1998). *Blast Monitoring Instrumentation and Analysis Techniques*
