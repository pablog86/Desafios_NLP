![FIUBA_logo](https://fi.uba.ar/images/logo-fiuba.png)

# Desafios Procesamiento del Lenguaje Natural
Entrega de desafios para la materia de NLP-CEIA 2025.

Este repositorio contiene las notebooks desarrolladas para los cuatro desafios
de la materia. A continuacion se resumen brevemente los objetivos abordados en
cada uno de ellos.

## Desafio 1: Clasificacion y similaridad
Notebook principal: `desafio1/desarrollo_desafio1.ipynb`

- Utilizacion del dataset **20 Newsgroups** para vectorizar documentos con
  TF‑IDF.
- Medicion de similaridad entre documentos y analisis de los pares mas
  cercanos.
- Entrenamiento de modelos **Naive Bayes** (Multinomial y Complement) para
  maximizar el *F1‑score* de clasificacion.
- Estudio de similaridad entre palabras a partir de la matriz
  termino‑documento.

## Desafio 2: Embeddings con Word2Vec
Notebook principal: `desafio2/desarrollo_desafio2.ipynb`

- Corpus conformado por los guiones de las peliculas de **Indiana Jones**.
- Preprocesamiento y entrenamiento de un modelo **Word2Vec** con Gensim.
- Exploracion de palabras de interes, calculo de similitudes y pruebas de
  analogias.
- Visualizacion de los embeddings mediante PCA/TSNE y discusion de resultados.

## Desafio 3: Modelo de lenguaje por caracteres
Notebook principal: `desafio3/desarrollo_desafio3.ipynb`

- Construccion de un corpus concatenando varias obras de **J. R. R. Tolkien**.
- Tokenizacion a nivel caracter y division en conjuntos de entrenamiento y
  validacion.
- Implementacion de redes **SimpleRNN**, **GRU** y **LSTM** con PyTorch.
- Entrenamiento guiado por la perplejidad, con registros guardados en
  `results/`.
- Generacion de texto por *greedy search* y *beam search*.

## Desafio 4: Traduccion automatica
Notebooks principales:
`desafio4/desarrollo_desafio4-keras.ipynb` y
`desafio4/pruebas_desafio4-pytorch.ipynb`

- Uso del corpus bilingue (ingles–espanol) para construir un
  traductor *seq2seq*.
- Implementacion en Keras de un modelo encoder‑decoder basado en LSTM.
- Pruebas en PyTorch con LSTM bidireccional, *teacher forcing*, atención y normalización. (sin éxito)
- Ejemplos de inferencia y diagramas de la arquitectura del modelo.

## Conclusiones por desafio

1. **Desafio 1:** Transponer la matriz TF-IDF permitio representar cada termino segun los documentos donde aparece. Se hallaron asociaciones fuertes como 'motorcycle' con 'wheelie' o 'cpu' con 'heatsink', aunque algunas no tuvieron sentido claro por la falta de contexto. TF-IDF no modela sintaxis ni orden, por lo que conviene utilizar word embeddings para capturar mejor la semantica.
2. **Desafio 2:** En las pruebas de analogias la relacion inversa no arrojo antonimos sino terminos poco vinculados en el embedding. Al referirse al Santo Grial como copa y no como diario, la similitud fue debil y lo mas cercano resulto 'Cristo'.
3. **Desafio 3:** El texto generado por greedy, temperature y beam search no resulto del todo coherente, pero mantiene el vocabulario caracteristico de "Lord of the Rings" en la generación de las oraciones.
4. **Desafio 4:** El entrenamiento en Keras se realizo en CPU y se omitio `to_categorical` para ahorrar memoria. Se usaron embeddings FastText, se evito el padding en el cross-entropy y se aumento el tamaño de las LSTM, aunque las traducciones solo mejoraron ligeramente. En PyTorch se probaron redes mas grandes, con dropout, atención y normalización por capas; pero se obtuvieron peores resultados que con la implementación con Keras. Esto demuestra que para mejor performance es mejor ir por una arquitectura encoder-decoder basada en Transformers.

## Comentarios finales

El conjunto de desafios cubre un abanico de tecnicas fundamentales del Procesamiento del Lenguaje Natural. A lo largo de la cursada se demostro como aplicar estas herramientas en casos concretos y se evidencio el potencial de seguir profundizando en el area a partir de estos cimientos.

CEIA-FIUBA