# RAG-Bio
TP2 de la materia de DeepLearning

## Diagram
[Diagrama en excalidraw](https://excalidraw.com/#json=jTuHCrxs7qzgTRLK2Eqyx,vCg64mIbrfa9ltX6TR1BIQ)

## Descripción General

Este proyecto busca analizar datos provenientes de múltiples fuentes (Twitter, Wikipedia, transcripciones de video) utilizando técnicas de procesamiento de lenguaje natural (NLP) e inteligencia artificial. Incluye la creación de un vector store para realizar búsquedas y análisis de contenido.

## Datos

### 1. Datasets
- **Elon Musk Tweets:** Contiene tweets de Elon Musk. El dataset original fue obtenido de Kaggle y se encuentra en el repositorio en la carpeta `.`. Puedes encontrar el dataset en [Kaggle](https://www.kaggle.com/datasets/gpreda/elon-musk-tweets).
- **Donald Trump Tweets:** Contiene tweets de Donald Trump. El dataset original fue obtenido de Kaggle y se encuentra en el repositorio en la carpeta `.`. Puedes encontrar el dataset en [Kaggle Donald](https://www.kaggle.com/datasets/austinreese/trump-tweets)
  
### 2. Transcripciones
- **Video de Malena Pichot:** Se realizó la transcripción de un video de Malena Pichot utilizando la herramienta Whisper. El video original se puede encontrar en (https://www.youtube.com/watch?v=pCDHwlT7mPU)[YouTube]. La transcripción generada está almacenada en el archivo `male_feinmann.txt`.

### 3. Datos Adicionales
- **Wikipedia:** Se utilizó información de Wikipedia para obtener contenido adicional sobre las personas de interés (Elon Musk, Donald Trump, Malena Pichot, Eduardo Feinmann). Las consultas se hicieron a través de scraping con BeautifulSoup.

## Estructura del Proyecto

### 1. Requisitos
Se utilizó Python para el análisis de datos junto con las siguientes librerías:
- `openai`
- `langchain`
- `pinecone`
- `whisper`
- `pandas`
- `requests`
- `beautifulsoup4`

### 2. Preprocesamiento
- Se descargaron los tweets de los archivos CSV de Elon Musk y Donald Trump.
- Se seleccionaron los 5000 tweets más relevantes (basados en la cantidad de "favoritos") para cada persona.
- Se realizó la limpieza de texto utilizando expresiones regulares para remover caracteres innecesarios y anotaciones en la información extraída de Wikipedia.

### 3. Transcripción de Video
- Para el video de Male Pichot, se descargó el video de YouTube, se convirtió a audio y luego se transcribió utilizando Whisper.
- La transcripción fue almacenada en un archivo de texto (`male_feinmann.txt`) para su posterior análisis.

### 4. Creación del Vector Store
- Se usó Pinecone para crear un almacén vectorial (`vectorstore`) con embeddings de los tweets, transcripciones y contenido de Wikipedia.
- Se utilizó la librería `langchain` junto con `sentence-transformers` para generar embeddings.
- El vector store se utiliza para realizar búsquedas de similitud de los documentos almacenados.

### 5. Simulaciones y Conversaciones
- Se desarrolló una función para simular una conversación en Twitter entre Elon Musk y Donald Trump utilizando el vector store para generar respuestas contextuales.
- La conversación fue limitada a un formato similar a los tweets (300 caracteres).

## Ejecución
1. **Descarga de Datos:** Ejecutar el script que carga los datos desde Kaggle y Wikipedia.
2. **Transcripción de Video:** Correr el script para descargar y transcribir el video utilizando Whisper.
3. **Preprocesamiento:** Limpiar y formatear los datos utilizando las funciones de preprocesamiento definidas.
4. **Vector Store:** Inicializar el vector store con los documentos (tweets, transcripciones, datos de Wikipedia).
5. **Simulaciones:** Utilizar las funciones para generar simulaciones de conversaciones entre las personalidades.

## Referencias
- [Colab de Euge](https://colab.research.google.com/drive/1EhDlD33mz1_ltKVyig9SuDLbBi0TDH28?usp=sharing#scrollTo=QhxE8Ei4rhPg)
- [Whisper - GitHub](https://github.com/openai/whisper)

## TO-DO
- Agarrar los chunks y meterlos en una vector DB (PineCone)
- Hacer el retrieval de chunks parecidos
- Armar la respuesta usando un LLM
- Basicamente leer [este colab](https://colab.research.google.com/drive/1d-5n4sC0_hMR5gcurWmRrOYKoEgEvkBp?usp=sharing#scrollTo=VC_i5rFyHY9n) y ponerlo en el [nuestro](https://colab.research.google.com/drive/10Y89-frJh5hhTbTWZCuYQOhLtpmr8FqD#scrollTo=85n7WVTkTXdF) 
  
- Buscar formas alternativas de generar la KB (knowledge base) (Speech to text maybe) (Nice to have)
