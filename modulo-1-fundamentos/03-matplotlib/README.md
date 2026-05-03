# 03 — Matplotlib: Habla con Gráficas

> **Módulo 1 · Fundamentos** | [← Portafolio principal](../../README.md) | [← 02 Pandas](../02-pandas/)

## 📋 Contenido

Un análisis sin visualización es como un mapa sin dibujar. **Matplotlib** convierte tablas y arrays en imágenes que cualquier persona entiende en segundos — y es la base de Seaborn, Plotly y las gráficas de Pandas. Entenderla a fondo te da control total sobre cualquier visual.

### Conceptos cubiertos

| Sección | Temas |
|---------|-------|
| **Anatomía de una figura** | Figure, Axes, subplots, figsize |
| **Gráfica de línea** | plot, marker, color, linewidth, label, legend |
| **Gráfica de barras** | bar, barh, colores dinámicos por valor |
| **Histograma** | hist, bins, edgecolor, axvline para media |
| **Dispersión** | scatter, alpha, cmap para colores por categoría |
| **Subplots** | grid 2×2, tight_layout, suptitle |
| **Estilos y anotaciones** | axhline, axvline, fill_between, grid, text |
| **Guardar figuras** | savefig, dpi, bbox_inches |

---

## 📓 Notebooks

| Archivo | Descripción | Abrir en Colab |
|---------|-------------|----------------|
| `03_matplotlib_fundamentos.ipynb` | Teoría + ejemplos comentados | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `03_matplotlib_ejercicios.ipynb` | 2 ejercicios (intermedio/avanzado) | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |
| `03_matplotlib_soluciones.ipynb` | Soluciones con visualizaciones finales | [![Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/) |

---

## 🏋️ Ejercicios

### Ejercicio 1 · Intermedio — Dashboard de Ventas
Figura 2×2 con: gráfica de línea con promedio, barras verdes/rojas según rendimiento, histograma de distribución, pastel trimestral.

**Conceptos:** `subplots`, colores condicionales con list comprehension, `axhline`, `pie`

### Ejercicio 2 · Avanzado — Análisis Visual Completo con Pandas
Cargar un DataFrame de empleados, crear 4 visualizaciones conectadas: salario por departamento (barras), distribución de salarios (histograma), scatter edad vs salario coloreado por departamento, boxplot comparativo.

**Conceptos:** Integración Pandas + Matplotlib, `scatter` con `cmap`, paletas de color, `boxplot`

---

## 💡 Conceptos clave aprendidos

```python
import matplotlib.pyplot as plt
import numpy as np

# Estructura básica — siempre usa fig, ax (no plt directo en proyectos)
fig, ax = plt.subplots(figsize=(10, 5))
ax.plot(x, y, color='#2E75B6', lw=2, marker='o', label='Ventas')
ax.set_title('Ventas Mensuales', fontsize=14, fontweight='bold')
ax.set_xlabel('Mes')
ax.set_ylabel('Unidades')
ax.legend()
ax.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()

# Subplots — múltiples gráficas en una figura
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
# axes[fila][columna]

# Colores condicionales — patrón muy usado
valores = [450, 620, 380, 710, 590]
promedio = np.mean(valores)
colores = ['#27AE60' if v > promedio else '#E74C3C' for v in valores]
ax.bar(categorias, valores, color=colores)

# Línea de referencia — contexto visual
ax.axhline(promedio, color='black', linestyle='--', lw=1.5, label='Promedio')

# Guardar para el portafolio / LinkedIn
plt.savefig('dashboard_ventas.png', dpi=150, bbox_inches='tight')
```

---

## 📊 Galería de visualizaciones del módulo

> *Las imágenes aparecen aquí cuando el notebook está ejecutado y guardado*

| Tipo | Cuándo usarla |
|------|---------------|
| **Línea** | Tendencias en el tiempo — ventas, temperaturas, progreso |
| **Barras** | Comparar categorías — ventas por mes, score por modelo |
| **Histograma** | Distribución de una variable — ¿cómo están repartidos los datos? |
| **Dispersión** | Relación entre dos variables — ¿correlacionan? |
| **Pastel** | Proporciones del total — usar con moderación |
| **Boxplot** | Comparar distribuciones entre grupos |
| **Heatmap** | Matriz de correlación entre variables (con Seaborn) |

---

## ⚠️ Errores comunes

```python
# ❌ Mal — usar plt directamente en proyectos con múltiples gráficas
plt.plot(x, y)
plt.title('título')

# ✅ Bien — siempre fig, ax para tener control total
fig, ax = plt.subplots()
ax.plot(x, y)
ax.set_title('título')

# ❌ Mal — olvidar tight_layout → gráficas se superponen
fig, axes = plt.subplots(2, 2)
plt.show()  # las etiquetas se cortan

# ✅ Bien
fig, axes = plt.subplots(2, 2)
plt.tight_layout()
plt.show()

# ❌ Mal — colores sin contraste en el portafolio
ax.plot(x, y, color='yellow')  # invisible en fondo blanco

# ✅ Bien — paleta consistente en tu portafolio
COLORS = {
    'primary':   '#2E75B6',
    'success':   '#27AE60',
    'danger':    '#E74C3C',
    'warning':   '#F39C12',
    'neutral':   '#85929E'
}
```

---

## 🎨 Paleta de colores recomendada para el portafolio

Usar siempre los mismos colores en todos tus notebooks le da consistencia profesional al portafolio:

```python
# Pega esto al inicio de cada notebook con visualizaciones
COLORS = {
    'primary':  '#2E75B6',   # azul principal
    'success':  '#27AE60',   # verde — positivo / bueno
    'danger':   '#E74C3C',   # rojo — negativo / malo
    'warning':  '#F39C12',   # naranja — advertencia / neutro
    'purple':   '#8E44AD',   # violeta — alternativo
    'neutral':  '#85929E',   # gris — datos secundarios
}
BACKGROUND = '#FAFAFA'
```

---

## 📈 Lo que sigue

**Siguiente módulo:** [04 — ML Supervisado](../../modulo-2-machine-learning/04-ml-supervisado/) — aquí Matplotlib cobra todo su sentido: graficamos las curvas de aprendizaje, las matrices de confusión y la importancia de las features.

---

## 🔗 Recursos adicionales

- [Documentación oficial Matplotlib](https://matplotlib.org/stable/gallery/)
- [Matplotlib Cheat Sheet](https://matplotlib.org/cheatsheets/)
- [Seaborn](https://seaborn.pydata.org/) — librería construida sobre Matplotlib, más fácil para estadística

---

*Tiempo de estudio: ~3-4 horas · Dificultad: ⭐⭐☆☆☆*
