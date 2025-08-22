
# 🐼 Pandas Cheatsheet (Python)
Guía rápida y completa de Pandas para análisis de datos en Python.

---

## 📌 Importación y configuración
```python
import pandas as pd
import numpy as np

pd.set_option("display.max_columns", None)  # Mostrar todas las columnas
pd.set_option("display.max_rows", 100)      # Mostrar más filas
```

---

## 📌 Creación de objetos
```python
# Serie
s = pd.Series([1, 2, 3, np.nan, 5])

# DataFrame desde diccionario
df = pd.DataFrame({
    "A": [1, 2, 3],
    "B": ["a", "b", "c"]
})

# DataFrame desde NumPy
df_np = pd.DataFrame(np.random.randn(5, 3), columns=list("ABC"))
```

---

## 📌 Lectura y escritura de archivos
```python
# CSV
df = pd.read_csv("archivo.csv")
df.to_csv("salida.csv", index=False)

# Excel
df = pd.read_excel("archivo.xlsx", sheet_name="Hoja1")
df.to_excel("salida.xlsx", index=False)

# JSON
df = pd.read_json("archivo.json")
df.to_json("salida.json")

# SQL
import sqlite3
conn = sqlite3.connect("mi_db.sqlite")
df = pd.read_sql("SELECT * FROM tabla", conn)
```

---

## 📌 Exploración de datos
```python
df.head()       # Primeras filas
df.tail()       # Últimas filas
df.info()       # Resumen del DataFrame
df.shape        # (filas, columnas)
df.columns      # Nombres de columnas
df.dtypes       # Tipos de datos
df.describe()   # Estadísticas descriptivas
```

---

## 📌 Selección de datos
```python
df["columna"]           # Selección de columna
df[["A", "B"]]          # Varias columnas
df.iloc[0]              # Fila por índice
df.iloc[0:5, 0:2]       # Rango de filas y columnas
df.loc[0, "A"]          # Fila + columna por nombre
df.at[0, "A"]           # Acceso rápido a un valor
```

---

## 📌 Filtrado y ordenamiento
```python
df[df["A"] > 0]               # Filtrar
df[(df["A"] > 0) & (df["B"] < 5)]  # Varios filtros
df.sort_values("A")           # Ordenar por columna
df.sort_values(["A", "B"], ascending=[True, False])
```

---

## 📌 Manejo de valores nulos
```python
df.isnull().sum()     # Contar nulos
df.dropna()           # Eliminar filas con nulos
df.fillna(0)          # Rellenar nulos con 0
df["columna"].fillna(df["columna"].mean(), inplace=True)
```

---

## 📌 Operaciones comunes
```python
df["nueva"] = df["A"] * 2           # Crear columna
df.rename(columns={"A": "Alpha"}, inplace=True)
df.drop("B", axis=1, inplace=True)  # Eliminar columna
df.drop(0, axis=0, inplace=True)    # Eliminar fila
```

---

## 📌 Estadísticas y funciones
```python
df["A"].mean()
df["A"].sum()
df["A"].min()
df["A"].max()
df["A"].unique()
df["A"].nunique()
df["A"].value_counts()
```

---

## 📌 Agrupamiento y agregación
```python
df.groupby("columna").mean()
df.groupby("columna")["valor"].agg(["mean", "sum", "count"])
df.pivot_table(values="valor", index="col1", columns="col2", aggfunc="mean")
```

---

## 📌 Combinar DataFrames
```python
# Concatenar
df_concat = pd.concat([df1, df2], axis=0)

# Merge tipo SQL
df_merge = pd.merge(df1, df2, on="id", how="inner")  # inner, left, right, outer

# Join por índice
df_join = df1.join(df2, lsuffix="_left", rsuffix="_right")
```

---

## 📌 Funciones útiles
```python
df.apply(np.sqrt)                  # Aplicar función
df["col"].apply(lambda x: x**2)    # Función personalizada
df["col"].map({"a": 1, "b": 2})    # Reemplazar valores
df.replace({1: "uno", 2: "dos"})   # Reemplazar múltiples
```

---

## 📌 Exportar a otros formatos
```python
df.to_clipboard()   # Copiar al portapapeles
df.to_markdown()    # Exportar a markdown
df.to_html("tabla.html")
```

---

## ✅ Conclusión
Esta cheatsheet cubre las operaciones más comunes de Pandas.  
¡Úsala como referencia rápida para tus proyectos de análisis de datos! 🚀
