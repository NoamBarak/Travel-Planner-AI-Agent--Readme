# AI Trip Planning Assistant with Model Context Protocol (MCP) ✈️

> **Enterprise-grade agentic AI system** leveraging Anthropic's Model Context Protocol for real-time tool orchestration, stateful conversation management, and production-ready travel planning capabilities.

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![Claude](https://img.shields.io/badge/Claude-Sonnet%204.5-purple.svg)
![MCP](https://img.shields.io/badge/MCP-Enabled-green.svg)
![Gradio](https://img.shields.io/badge/Gradio-4.20-orange.svg)
<img width="661" height="808" alt="image" src="https://github.com/user-attachments/assets/4665c4bf-6856-48d3-a3a7-6496a6316eee" />

---

## Executive Summary

This project demonstrates **production-grade AI engineering** through:
- ✅ **Model Context Protocol (MCP) Implementation** - Extensible tool orchestration following Anthropic's standardized framework
- ✅ **Parallel Tool Execution** - Advanced handling of Claude's multi-tool calling with proper result batching
- ✅ **Agentic Behavior** - Autonomous decision-making with real-time API integration (Amadeus, 400+ airlines)
- ✅ **State Management** - Stateful multi-turn conversations with memory persistence
- ✅ **Production-Ready Architecture** - Clean separation of concerns, type safety, async/await patterns

**Use Case**: AI-powered travel assistant that generates personalized itineraries and searches real-time flight pricing with flexible date options and intelligent cost optimization.

---

## Architecture & Technical Highlights

### 🔧 Model Context Protocol (MCP) Implementation

This project implements Anthropic's **Model Context Protocol** - a standardized approach for AI models to interact with external tools and data sources.

### ⚡ Advanced Tool Orchestration - Parallel Execution

**Challenge**: Claude Sonnet 4.5 can invoke multiple tools simultaneously (parallel tool use), requiring sophisticated result batching to avoid API errors.

**Solution**: Implemented a **while-loop batching pattern** that collects all tool uses, executes them asynchronously, and returns results in a single message.

**Why This Matters**:
- ❌ **Wrong approach**: Sending each tool result individually → `400 error: tool_use ids were found without tool_result blocks`
- ✅ **Correct approach**: Batch all results → Claude receives complete context in one message

---

### 🧠 Stateful Conversation Management

**Multi-Turn Memory with Context Persistence**:


### 🌐 Real-Time API Integration - Amadeus Travel Platform

**Flight Search Tool with Async I/O**:

**Booking Link Generation** (Airline-Specific URLs)


### 🎯 Intelligent Prompt Engineering

**Flexible Date Search with Conditional Tool Use**:


**Critical Response Guidelines** (Prompt Engineering for Conciseness):

```python
CRITICAL RESPONSE GUIDELINES:
- Keep responses SHORT and CONCISE (3-5 sentences for flight results)
- For flight searches: List ONLY flight number, time, price, and booking link
- Be RELIABLE: Only state facts from tool results, never guess or estimate
- Format flight results as a numbered list with booking links
```

---

### 🎨 Production-Grade UI with Gradio 4.20

**HTML5 Date Picker via JavaScript Injection** (since gr.DateTime unavailable in 4.20)



## AI Engineering Concepts Demonstrated 👩🏻‍💻

### 1. Model Context Protocol (MCP)
- ✅ Standardized tool definition format
- ✅ Type-safe schema validation
- ✅ Extensible tool registry pattern
- ✅ Async execution with proper error handling

### 2. Agentic Behavior
- ✅ Autonomous decision-making (when to search flexible dates)
- ✅ Multi-step reasoning (search → compare → recommend)
- ✅ Tool chaining (multiple API calls in sequence)

### 3. Retrieval-Augmented Generation (RAG)
- ✅ Real-time data retrieval (flight prices)
- ✅ Structured output formatting
- ✅ Fact-based responses (no hallucination)

### 4. Prompt Optimization
- ✅ Chain-of-thought reasoning
- ✅ Conditional behavior (flexible vs direct search)
- ✅ Output formatting constraints

### 5. Error Handling & Resilience
- ✅ Graceful API failures
- ✅ Type validation
- ✅ Retry mechanisms (implicit in Anthropic SDK)

---


## System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     Gradio UI Layer                          │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐         │
│  │ Quick Plan  │  │ Chat Mode   │  │Flight Search│         │
│  └──────┬──────┘  └──────┬──────┘  └──────┬──────┘         │
└─────────┼─────────────────┼─────────────────┼───────────────┘
          │                 │                 │
          └─────────────────┴─────────────────┘
                            │
          ┌─────────────────▼─────────────────┐
          │     Message Handler (Core)        │
          │  • Conversation Management        │
          │  • Tool Orchestration             │
          │  • Response Processing            │
          └─────────────────┬─────────────────┘
                            │
          ┌─────────────────▼─────────────────┐
          │  Anthropic Claude API (Sonnet 4.5)│
          │  • Tool Use Detection             │
          │  • Parallel Tool Calling          │
          │  • Natural Language Understanding │
          └─────────────────┬─────────────────┘
                            │
          ┌─────────────────▼─────────────────┐
          │       Tool Registry (MCP)         │
          │  ┌──────────────────────────┐     │
          │  │  FlightSearchTool        │     │
          │  │  • Amadeus API Client    │     │
          │  │  • Async Execution       │     │
          │  │  • Booking Link Gen      │     │
          │  └──────────────────────────┘     │
          │  [Future: HotelTool, WeatherTool] │
          └───────────────────────────────────┘
                            │
          ┌─────────────────▼─────────────────┐
          │   External APIs & Services        │
          │  • Amadeus Travel Platform        │
          │  • Airline Booking Systems        │
          └───────────────────────────────────┘
```

---

## Technical Stack

| Component | Technology | Purpose |
|-----------|-----------|---------|
| AI Model | Claude Sonnet 4.5 | Reasoning, tool use, conversation |
| Protocol | Model Context Protocol (MCP) | Standardized tool integration |
| Backend | Python 3.8+, Anthropic SDK | Application logic, API client |
| Async I/O | asyncio, run_in_executor | Non-blocking tool execution |
| UI Framework | Gradio 4.20 | Rapid prototyping, event handling |
| Flight Data | Amadeus API | Real-time pricing, 400+ airlines |
| Type Safety | Python type hints | Static analysis, IDE support |
| Architecture | Clean Architecture | Separation: config/core/tools/ui |

---

## Future Enhancements

### Technical Roadmap
1. **Multi-Modal Integration** - Image analysis for destination recommendations (Claude's vision capabilities)
2. **Tool Chaining** - Flight search → Hotel search → itinerary generation in single workflow
3. **Caching Layer** - Redis for flight result caching (reduce API costs)
4. **Agent Routing** - Multiple specialized agents (flights, hotels, activities) with coordination
5. **Memory Persistence** - Database storage for conversation history across sessions
6. **Prompt Caching** - Anthropic's prompt caching for system prompts (reduce costs)

### Business Features
- **Price Alerts** - Monitor flight prices, notify on drops
- **Group Travel** - Multi-passenger coordination
- **Trip Sharing** - Export itineraries as PDFs/calendar events

---

## Contact

**Developed by**: Noam Barak
**LinkedIn**: [https://www.linkedin.com/in/noambarak/]


