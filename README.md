# Conversational RAG with Nvidia AI Foundation Endpoints, Haystack, and Gradio

This notebook demonstrates how to build a complete, state-of-the-art **Conversational RAG (Retrieval-Augmented Generation) Pipeline** utilizing Google Colab, **Haystack (v2.x)**, **Nvidia AI Foundation Models**, **Serper.dev** for web search fallback, and **Gradio** for an interactive web interface.

## 🚀 Features
- **Hybrid Retrieval System**: Checks local documents first before deciding whether to source external information.
- **Adaptive Fallback Routing**: Uses Haystack's `ConditionalRouter` to trigger a web search via **Serper.dev** whenever the local vector store cannot answer the user's query.
- **Conversational Query Rewriting**: Restructures follow-up questions into standalone queries using chat history to maintain strict conversational context.
- **Modern Haystack 2.x Architecture**: Uses the component-based pipeline framework to orchestrate embedding generators, document stores, prompt builders, routers, and generators seamlessly.
- **Interactive UI**: A functional web interface powered by **Gradio** to test and converse with the system in real time.

---

## 🛠️ System Architecture Diagram
1. **Query Rewriter**: Translates the user input + history context into a refined search query.
2. **Local Document Retriever**: Matches query embeddings against an `InMemoryDocumentStore` loaded with custom knowledge.
3. **Conditional Router**:
   - **Hit**: Passes local documents to the prompt builder and generator.
   - **Miss**: If `no_answer` is returned, routes the query to **Serper.dev Web Search** and answers using fetched online snippets.

---

## 🔑 Prerequisites & Configuration

To run this notebook, you need to set up Google Colab secrets ("🔑" icon in the left panel) with the following API keys:

1. `nvidia_key`: Your personal API Key from the [Nvidia API Catalog](https://developer.nvidia.com/nim).
2. `serper`: Your API Key from [Serper.dev](https://serper.dev) for Google search queries.
