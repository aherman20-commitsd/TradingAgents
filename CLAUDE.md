# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

TradingAgents — a multi-agent LLM framework for financial trading research.
Specialized LLM agents (fundamental, sentiment, technical analysts; trader;
risk management) collaborate via LangGraph to analyze markets and produce
trading decisions. Research purposes only — not financial or trading advice.

## Commands

```bash
# setup
pip install -e ".[dev]"

# lint
ruff check .

# tests
pytest
pytest tests/some_test.py            # single file
pytest tests/some_test.py::test_name # single test
pytest -m unit                       # by marker (unit / integration / smoke)

# run
python main.py
tradingagents   # installed CLI entry point (cli.main:app)
```

## Architecture

```
tradingagents/   core package: agents, graph orchestration, data vendors
cli/             Typer-based command-line interface
tests/           pytest suite (unit / integration / smoke markers)
```

Agent orchestration is built on LangGraph, with per-agent LLM provider
configurable via `TRADINGAGENTS_*` env vars (see `.env.example`) — the
provider registry supports OpenAI, Anthropic, Google, DeepSeek, Qwen,
Bedrock, and any OpenAI-compatible endpoint.
