# Erasmus RAG Chatbot

Ecosistema de chatbots inteligentes para la gestión del programa Erasmus+ en la Universidad de Huelva. Desarrollado como Trabajo de Fin de Grado (TFG) en Ingeniería Informática.

El sistema implementa dos chatbots complementarios:

- **Chat Erasmus (alumnos)** — chatbot RAG que permite consultar la documentación oficial del programa Erasmus en lenguaje natural. Incluye formulario de contacto automático con RRII y conversión de divisas vía MCP.
- **Chat RRII (secretaría)** — agente MCP que permite al personal administrativo consultar la base de datos operacional en lenguaje natural: tickets pendientes, historial de conversaciones, ficheros procesados, etc.

## Stack

- **n8n** — orquestador de workflows: pipeline de ingesta, agente RAG y agente MCP
- **PostgreSQL** — historial de conversaciones, tickets y registro de ficheros procesados
- **Qdrant** — base de datos vectorial para búsqueda semántica
- **Ollama** — modelos LLM y embeddings ejecutados en local
- **pgweb / Adminer** — administración de base de datos

## Instalación

```bash
git clone https://github.com/jjrmch/erasmus-rag-chatbot.git
cd erasmus-rag-chatbot
cp .env.example .env        # Rellenar con tus credenciales
docker compose --profile cpu up -d   # o gpu-nvidia / gpu-amd
```

## Acceso

| Servicio | URL |
|----------|-----|
| n8n | http://localhost:5678 |
| Qdrant | http://localhost:6333 |
| pgweb | http://localhost:8081 |
| Adminer | http://localhost:8080 |

## Configuración

Copia `.env.example` como `.env` y ajusta los valores.

> Las carpetas `shared/`, `correos_descartados/` y `procesar_sin_comprobar/` contienen un `.gitkeep` para que Git las rastree. Elimínalos con `find . -name ".gitkeep" -delete` antes de añadir contenido real.
