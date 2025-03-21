# Lab 8 AREP parte 2 / RAG

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

![image1.jpeg](images/image1.jpeg)

Esta arquitectura representa el flujo de trabajo de RAG (Retrieval-Augmented Generation), un enfoque que combina modelos de lenguaje grandes (LLM) con recuperación de información relevante desde una base de datos vectorial (Vector DB, como Pinecone) para mejorar la precisión y relevancia de las respuestas.

El proceso comienza cuando el usuario envía una query (pregunta o solicitud). Esta consulta pasa por un Prompt Template, que la estructura para que el sistema pueda procesarla de manera eficiente, generando un structured text. Luego, este texto estructurado se envía a la Vector DB (Pinecone), donde se recupera información relevante relacionada con la consulta, generando un Query + Relevant Context.

Esta consulta enriquecida con contexto se alimenta (feeds) al LLM, que la procesa y genera una respuesta basada en la información recuperada y en su conocimiento previo. Finalmente, la respuesta es devuelta al usuario.

El valor de esta arquitectura RAG es que permite que el modelo genere respuestas más precisas y actualizadas, ya que se basa en información recuperada en tiempo real en lugar de depender únicamente de su entrenamiento previo.

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
```

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
