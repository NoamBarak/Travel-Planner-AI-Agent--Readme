# AI Trip Planning Assistant✈️

This project showcases **enterprise-grade AI engineering** through an intelligent travel assistant built with Claude Sonnet, LangChain 0.3, and Python.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Claude](https://img.shields.io/badge/Claude-Sonnet%204.5-purple.svg)
![LangChain](https://img.shields.io/badge/LangChain-Framework-green.svg)
![Gradio](https://img.shields.io/badge/Gradio-4.20-orange.svg)
<img width="661" height="808" alt="image" src="https://github.com/user-attachments/assets/4665c4bf-6856-48d3-a3a7-6496a6316eee" />

---

## Executive Summary

This project demonstrates **production-grade AI engineering** through:
- ✅ **Parallel Tool Execution** - Advanced handling of Claude's multi-tool calling with proper result batching
- ✅ **Agentic Behavior** - Autonomous decision-making with real-time API integration (Amadeus, 400+ airlines)
- ✅ **State Management** - Stateful multi-turn conversations with memory persistence
- ✅ **Production-Ready Architecture** - Clean separation of concerns, type safety, async/await patterns

**Use Case**: AI-powered travel assistant that generates personalized itineraries and searches real-time flight pricing with flexible date options and intelligent cost optimization.

---

## Key Technical Achievements

**LangChain Integration**: The core LLM backbone is powered by LangChain's Expression Language (LCEL) — composing prompts, models, and memory using the `|` pipe operator. `RunnableWithMessageHistory` manages stateful multi-turn conversations automatically, replacing manual message list management. MCP tools are bridged into the LangChain pipeline via `StructuredTool` with Pydantic-validated input schemas.

**Agentic Architecture**: The assistant autonomously decides when to invoke the flight search tool, chains multiple API calls together, and performs multi-step reasoning to generate personalized travel itineraries — all driven by Claude's native tool-use capabilities via `bind_tools()`.

**Model Context Protocol (MCP)**: Tools are defined following Anthropic's standardized MCP specification — an abstract `Tool` base class, JSON Schema input definitions, and a singleton `ToolRegistry` for extensible tool management. Adding a new tool (hotels, weather) requires fewer than 30 lines of code.

**Real-Time Integration**: Leveraging the Amadeus platform, the system accesses live flight pricing across 400+ airlines and generates airline-specific deep-link booking URLs for direct reservations.

**Stateful Conversation Memory**: `InMemoryChatMessageHistory` persists typed `HumanMessage` / `AIMessage` objects across turns. History is injected automatically into every prompt via `MessagesPlaceholder`, enabling coherent multi-turn travel planning without any manual state tracking.

## Technology Foundation

The stack combines Python 3.8+, LangChain 0.3 (LCEL, `langchain-anthropic`, `langchain-core`), and the Anthropic SDK for the AI backbone. Gradio 4.20 powers the multi-tab web UI. `asyncio` with `run_in_executor` ensures non-blocking Amadeus API calls. Pydantic provides type-safe schema validation throughout the tool layer.

## Demonstrated AI Concepts

Beyond standard chatbot functionality, this implementation covers agentic behavior (autonomous tool invocation and multi-step reasoning), retrieval-augmented generation (real-time flight data instead of static knowledge), LangChain LCEL chain composition, MCP-based tool orchestration, and resilient async error handling.

The architecture is designed for extensibility — future enhancements include multi-modal vision for destination recommendations, Redis caching for flight results, specialized agent routing, and persistent cross-session memory storage.
---

## Contact

**Developed by**: Noam Barak
**LinkedIn**: [https://www.linkedin.com/in/noambarak/]


