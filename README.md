
# GenRole

`GenRolea` is an open source chatbot based on LLMs. It supports a wide range of language models including:

- Ollama served models
- OpenAI
- Azure OpenAI
- Anthropic
- Moonshot
- Gemini
- Groq

`GenRolea` supports multiple types of chat:

- Free chat with LLMs
- Chat with LLMs based on knowledge base

`GenRolea` feature list:
- Ollama models management
- Knowledge bases management
- Chat
- Commercial LLMs API keys management

## Join Our Community

If you are a user, contributor, or even just new to `GenRolea`, you are more than welcome to join our community on Discord by clicking the [invite link](https://discord.gg/TjhZGYv5pC).

If you are a contributor, the channel `technical-discussion` is for you, where we discuss technical stuff.

If you have any issue in `GenRolea` usage, please report to channel `customer-support`. We will help you out as soon as we can.

## Quick Start

As a user of `GenRolea`, please walk through the document below, to make sure you get all the components up and running before starting using `GenRolea`.

### Supported Vector Databases

`GenRolea` supported 2 types of vector databases: Milvus and Chroma.

Please refer to the `.env.example` for how to work with your vector database setup.

```
# Supported values: chroma, milvus
VECTOR_STORE=chroma
CHROMADB_URL=http://localhost:8000
MILVUS_URL=http://localhost:19530
```

By default `GenRolea` is using Chroma. If you'd like to use Milvus, set `VECTOR_STORE` to `milvus` and specify the corresponding URL. It works both in the development server and Docker containers.

### Use with Nuxt 3 Development Server

If you'd like to run with the latest code base and apply changes as needed, you can clone this repository and follow the steps below.

1. Install and run Ollama server

    You will need an Ollama server running. Follow the installation guide of [Ollama](https://github.com/ollama/ollama). By default, it's running on http://localhost:11434.    

2. Install Chroma

    Please refer to [https://docs.trychroma.com/getting-started](https://docs.trychroma.com/getting-started) for Chroma installation.

    We recommend you run it in a docker container:

    ```bash
    #https://hub.docker.com/r/chromadb/chroma/tags

    docker pull chromadb/chroma
    docker run -d -p 8000:8000 chromadb/chroma
    ```
    Now, ChromaDB is running on http://localhost:8000

3. GenRolea Setup

    Now, we can complete the necessary setup to run GenRolea.

    3.1 Copy the `.env.example` file to `.env` file:

    ```bash
    cp .env.example .env
    ```

    3.2 Make sure to install the dependencies:

    ```bash
    pnpm install
    ```

    3.3 Run a migration to create your database tables with Prisma Migrate

    ```bash
    pnpm prisma-migrate
    ```

4. Launch Development Server

    > Make sure both __[Ollama Server](#ollama-server)__ and __[ChromaDB](#install-chromadb-and-startup)__ are running.

    Start the development server on `http://localhost:3000`:

    ```bash
    pnpm dev
    ```


