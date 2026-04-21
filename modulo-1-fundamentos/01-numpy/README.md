# 01 — Numpy: El Motor Numérico

> **Módulo 1 · Fundamentos** | [← Portafolio principal](../../README.md)

## 📋 Contenido

Este módulo cubre **Numpy** desde cero hasta nivel intermedio-avanzado. Es la librería base de todo el ecosistema de Data Science en Python — sin entenderla bien, Pandas, Scikit-Learn y PyTorch son cajas negras.

### Conceptos cubiertos

| Sección | Temas |
|---------|-------|
| **Arrays 1D** | Creación, dtype, shape, size, ndim |
| **Operaciones aritméticas** | Vectorización, broadcasting, módulo % |
| **Agregaciones** | sum, mean, median, std, argmax, cumsum |
| **Slicing** | inicio:fin:paso, índices negativos, múltiples índices |
| **Boolean Indexing** | Filtrado con condiciones, operadores & \| ~ |
| **Arrays 2D** | Matrices, axis=0 vs axis=1, selección de filas/columnas |
| **Funciones útiles** | where, sort, argsort, unique, reshape, flatten |

---

## 📓 Notebooks

| Archivo | Descripción | Abrir en Colab |
|---------|-------------|----------------|
| `01_numpy_fundamentos.ipynb` | Teoría + ejemplos comentados | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `01_numpy_ejercicios.ipynb` | 3 ejercicios (básico/intermedio/avanzado) | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `01_numpy_soluciones.ipynb` | Soluciones explicadas línea a línea | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |

---

## 🏋️ Ejercicios

### Ejercicio 1 · Básico — Análisis de Temperaturas
Dado un array de temperaturas de 14 días, calcular estadísticas, filtrar días calientes y comparar semanas.

**Conceptos practicados:** `mean`, `max`, `min`, `std`, `argmin`, slicing, boolean indexing

### Ejercicio 2 · Intermedio — Filtrado con Módulo
Filtrar números del 1 al 100 usando el operador `%` — múltiplos, impares, condiciones combinadas.

**Conceptos practicados:** `arange`, `%`, `&`, boolean indexing, `sum` sobre booleanos

### Ejercicio 3 · Avanzado — Análisis de Ventas 2D
Matriz de 4 vendedores × 3 meses. Total por mes, mejor vendedor, normalización con `keepdims`.

**Conceptos practicados:** `sum(axis=0)`, `mean(axis=1)`, `argmax`, broadcasting, `max(keepdims=True)`

---

## 💡 Conceptos clave aprendidos

```python
import numpy as np

# Vectorización — sin bucles for
a = np.array([1, 2, 3, 4, 5])
print(a * 2)           # [2 4 6 8 10] — se aplica a todos

# Boolean Indexing — filtrado poderoso
edades = np.array([18, 22, 15, 35, 28, 14])
print(edades[edades >= 18])    # [18 22 35 28]

# Múltiples condiciones — SIEMPRE con paréntesis
jovenes = edades[(edades >= 18) & (edades <= 25)]

# axis en matrices — la confusión más común
M = np.array([[1,2,3],[4,5,6]])
print(np.mean(M, axis=0))  # [2.5 3.5 4.5] — prom por columna
print(np.mean(M, axis=1))  # [2.  5. ] — prom por fila
```

---

## 📈 Lo que sigue

**Siguiente módulo:** [02 — Pandas](../02-pandas/) — tablas con texto, fechas y tipos mixtos.

Numpy maneja números puros. Pandas usa Numpy internamente pero agrega etiquetas, tipos mixtos y operaciones de tabla. Es la transición natural.

---

## 🔗 Recursos adicionales

- [Documentación oficial Numpy](https://numpy.org/doc/stable/)
- [Numpy Cheat Sheet — DataCamp](https://www.datacamp.com/cheat-sheet/numpy-cheat-sheet-data-analysis-in-python)

---

*Tiempo de estudio: ~3-4 horas · Dificultad: ⭐⭐☆☆☆*
