# 02 — Pandas: Tablas Inteligentes

> **Módulo 1 · Fundamentos** | [← Portafolio principal](../../README.md) | [← 01 Numpy](../01-numpy/)

## 📋 Contenido

**Pandas** es la herramienta que más usarás en proyectos reales de Data Science. El 80% del tiempo en cualquier proyecto se va en limpiar, transformar y explorar datos — y Pandas es el estándar para eso. Construido sobre Numpy, agrega etiquetas, tipos mixtos y operaciones de tabla.

### Conceptos cubiertos

| Sección | Temas |
|---------|-------|
| **DataFrame y Series** | Crear desde diccionario, tipos, shape, dtypes |
| **Exploración inicial** | head, tail, info, describe, value_counts, isnull |
| **Selección de datos** | Columnas, filtrado booleano, iloc, loc |
| **Limpieza de datos** | fillna, dropna, drop_duplicates, astype |
| **Columnas calculadas** | Nueva columna, np.where, apply con función propia |
| **GroupBy** | groupby + agg, múltiples estadísticas, sort_values |
| **Merge** | left join, inner join, cruzar tablas como SQL |

---

## 📓 Notebooks

| Archivo | Descripción | Abrir en Colab |
|---------|-------------|----------------|
| `02_pandas_fundamentos.ipynb` | Teoría + ejemplos comentados | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `02_pandas_ejercicios.ipynb` | 3 ejercicios (básico/intermedio/avanzado) | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `02_pandas_soluciones.ipynb` | Soluciones explicadas línea a línea | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |

---

## 🏋️ Ejercicios

### Ejercicio 1 · Básico — Análisis de Empleados
DataFrame de 6 empleados con departamento, salario y años. Contar por departamento, promedio salarial, filtrar IT con más de 5 años, doble condición.

**Conceptos:** `value_counts`, `groupby`, `mean`, filtrado booleano con `&`

### Ejercicio 2 · Intermedio — Limpieza de Datos Reales
Dataset con nulos en nombre y compra. Detectar, rellenar con media/texto, eliminar duplicados, crear columna `compra_usd` y clasificar por tamaño.

**Conceptos:** `isnull().sum()`, `fillna`, `drop_duplicates`, `np.where`, columnas calculadas

### Ejercicio 3 · Avanzado — GroupBy y Merge
Dos DataFrames (empleados y ventas_mes). Calcular ventas por empleado, cruzar con `merge`, detectar quién supera su salario en ventas, mejor departamento.

**Conceptos:** `groupby + agg`, `merge`, `idxmax`, relaciones entre tablas

---

## 💡 Conceptos clave aprendidos

```python
import pandas as pd
import numpy as np

# Crear DataFrame
df = pd.DataFrame({
    'nombre':      ['Ana', 'Luis', 'Marta'],
    'departamento':['IT', 'Ventas', 'IT'],
    'salario':     [5500000, 3200000, 6000000]
})

# Exploración inicial — siempre primero
df.info()                        # tipos y nulos
df.describe()                    # estadísticas numéricas
df['departamento'].value_counts()# frecuencia por categoría
df.isnull().sum()                # nulos por columna

# Filtrado — igual que Numpy pero con columnas etiquetadas
df[df['salario'] > 4000000]
df[(df['departamento'] == 'IT') & (df['salario'] > 5000000)]

# Limpieza
df['salario'] = df['salario'].fillna(df['salario'].mean())
df = df.drop_duplicates()

# Columna calculada con condición
df['nivel'] = np.where(df['salario'] > 5000000, 'Senior', 'Junior')

# GroupBy — agrupar y resumir
df.groupby('departamento').agg({
    'salario': ['mean', 'max', 'count']
})

# Merge — unir dos tablas como SQL JOIN
resultado = tabla1.merge(tabla2, on='id', how='left')
```

---

## ⚠️ Errores comunes

```python
# ❌ Mal — SettingWithCopyWarning
df_it = df[df['depto'] == 'IT']
df_it['nuevo'] = 1              # puede no modificar el original

# ✅ Bien — usar .copy() si vas a modificar el subset
df_it = df[df['depto'] == 'IT'].copy()
df_it['nuevo'] = 1

# ❌ Mal — olvidar los paréntesis en condiciones
df[df['edad'] > 25 & df['salario'] > 3000000]  # error de precedencia

# ✅ Bien — SIEMPRE paréntesis en cada condición
df[(df['edad'] > 25) & (df['salario'] > 3000000)]
```

---

## 📈 Lo que sigue

**Siguiente módulo:** [03 — Matplotlib](../03-matplotlib/) — convertir DataFrames en gráficas que cualquier persona entiende.

Pandas tiene su propio método `.plot()` que usa Matplotlib internamente. En el siguiente módulo aprendemos a controlar ese visual completamente.

---

## 🔗 Recursos adicionales

- [Documentación oficial Pandas](https://pandas.pydata.org/docs/)
- [Pandas Cheat Sheet — DataCamp](https://www.datacamp.com/cheat-sheet/pandas-cheat-sheet-for-data-science-in-python)
- [10 minutes to Pandas](https://pandas.pydata.org/docs/user_guide/10min.html)

---

*Tiempo de estudio: ~4-5 horas · Dificultad: ⭐⭐⭐☆☆*
