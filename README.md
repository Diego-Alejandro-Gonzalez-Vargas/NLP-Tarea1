# NLP – Tarea 1 · Índice invertido (BSII) y Recuperación ranqueada (RRDV)

Este repositorio implementa dos enfoques de recuperación de información sobre un mismo corpus en formato **NAF**: 
1) **Búsqueda binaria** con índice invertido (operadores `AND` y `NOT`), y 
2) **Recuperación ranqueada** mediante **TF–IDF** y **similitud del coseno**.

Incluye utilidades para: preprocesamiento, construcción del índice invertido, generación de la **matriz TF–IDF** de documentos (con `idf = log(N/df)`, **sin suavizado** para permitir puntajes 0) y ejecución de **35 consultas** leyendo el texto de `<raw>` con el recorte `raw[9:-3]`.

---

## Estructura del repo

```
.
├─ Notebooks/        # cuadernos de exploración, ejecución y evaluación
├─ Informe/          # informe escrito (PDF / material de entrega)
├─ Resultados/       # salidas (TSV) de BSII y RRDV; métricas
└─ README.md         # este documento
```

> **Nota**: los nombres exactos de cuadernos/archivos pueden variar; consulta `Notebooks/` para ver ejemplos de uso end-to-end.

---

## Requisitos

- Python **3.10+**  
- Paquetes: `numpy`, `pandas`, `nltk`, `lxml`, `tqdm`  
- `gensim` para contrastar con su `TfidfModel`

Instalación rápida:

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# Linux/macOS
source .venv/bin/activate

python -m pip install -U pip
pip install numpy pandas nltk lxml tqdm gensim
python - <<'PY'
import nltk
nltk.download('punkt'); nltk.download('stopwords'); nltk.download('wordnet')
PY
```

---

## Datos

Organiza los NAF de la colección y las 35 consultas así:

```
data/
  docs/      # *.naf (documentos del corpus)
  queries/   # *.naf (consultas; se usará raw[9:-3])
```

### 4) Búsqueda binaria (AND/NOT)

En `Notebooks/` se incluye un ejemplo de **intersección de postings** (AND) y diferencia (NOT) con el mismo preprocesamiento que RRDV.


---

## Resultados

- Los archivos TSV producidos por BSII y RRDV se dejan en `Resultados/`.  
- Los cuadernos en `Notebooks/` muestran cómo reproducir **MAP**, **nDCG@k**, Precision/Recall@M y comparar BSII vs RRDV.

---



## Cómo reproducir (resumen)

1. Preparar entorno e instalar dependencias.  
2. Colocar NAF en `data/docs` y `data/queries`.  
3. Ejecutar el pipeline 1→4 (índice, TF–IDF, consultas, métricas).  
4. Verificar salidas en `Resultados/` y comparar con el informe.


---

## Autor

Santiago Martinez Novoa
Diego Alejandro González Vargas.

