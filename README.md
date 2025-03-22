# Lab 8 AREP parte 2

Este documento proporciona una guía detallada sobre la implementación de Retrieval-Augmented Generation (RAG) utilizando LangChain y OpenAI para mejorar las respuestas de modelos de lenguaje con recuperación de documentos relevantes.

Para clonar el proyecto 

git clone  ´ https://github.com/lalaro/TALLER8AREP-2.git ´

### Prerrequisitos

Se necesita instalar las siguientes herramientas antes de comenzar:

1. Python 3.8 o superior.

2. OpenAI API Key (u otra API compatible con LangChain).

3. Pinecone como base de datos vectorial.

3. Instalar LangChain y dependencias necesarias con:

` pip install langchain openai pinecone-client `

## Arquitectura



## Uso de Retrieval-Augmented Generation (RAG)

Para ejecutar la implementación de RAG y obtener respuestas mejoradas:

```python
from langchain.chains import RetrievalQA
from langchain.vectorstores import Pinecone
from langchain.embeddings.openai import OpenAIEmbeddings
from langchain.llms import OpenAI

# Cargar documentos y procesarlos en Pinecone
vector_store = Pinecone.from_documents(documents, OpenAIEmbeddings())

# Crear el sistema RAG
qa_chain = RetrievalQA.from_chain_type(
    llm=OpenAI(), retriever=vector_store.as_retriever()
)

# Consultar el modelo
response = qa_chain.run("¿Qué es la inteligencia artificial?")
print(response)

## Construido con

* [LangChain]() - Framework para construir aplicaciones con LLMs.
* [OpenAI](https://platform.openai.com/docs/concepts) - API para modelos de lenguaje.
* [Python](https://docs.python.org/3/) - Lenguaje de programación.
* [Pinecone]() - Base de datos vectorial para almacenamiento y recuperación de documentos.

## Contribuyendo

Por favor, lee [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) para detalles sobre nuestro código de conducta y el proceso para enviarnos solicitudes de cambios (*pull requests*).

## Versionado

Usamos [SemVer](http://semver.org/) para el versionado.

## Autores

* **Laura Valentina Rodríguez Ortegón** - *Lab8 AREP - 2* - [Repositorio](https://github.com/lalaro/TALLER8AREP-2.git)

## Licencia

Este proyecto está licenciado bajo la Licencia MIT - consulta el archivo [LICENSE.md](LICENSE.md) para más detalles.

## Reconocimientos

* Agradecimientos a la Escuela Colombiana de Ingeniería
* La documentación de Git Hub
* Al profesor Luis Daniel Benavides
