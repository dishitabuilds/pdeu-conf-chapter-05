# PDEU Workshop — Chapter 5: Deep Agent + Skills

A financial-auditor workshop example that combines local ledger queries,
warehouse receipt checks, contract lookup, and a reusable penalty-calculation skill.

Built with Python, DeepAgents, and an OpenRouter model connection. This is a
local command-line teaching example; no hosted web interface is configured.

## Prerequisites

- Python **3.12 or newer**, matching [pyproject.toml](pyproject.toml).
- `uv` for dependency/environment management.
- An OpenRouter API key for model-backed invocations.

## Setup

```bash
git clone https://github.com/dishitabuilds/pdeu-conf-chapter-05.git
cd pdeu-conf-chapter-05
uv sync
cp .env.example .env
```

In PowerShell, use `Copy-Item .env.example .env` instead of `cp`.
Set `OPENROUTER_API_KEY` and `OPENROUTER_MODEL` in `.env`; keep credentials untracked.

## Run

```bash
uv run python main.py --self-check
uv run python main.py "Audit the account for Gujarat Steel Corp."
uv run pytest
```

The self-check is local and does not invoke a model. The audit prompt can make
provider API calls; availability and cost depend on the configured model.
These commands are documented entry points, not newly executed verification.

## Repository guide

- [main.py](main.py): command-line entry point.
- [audit_agent.py](audit_agent.py): agent setup and local data tools.
- `ap_ledger.db`, `warehouse_receipts_fy26.csv`, and `contracts/`: local workshop data.
- [Penalty skill](skills/penalty_logic/SKILL.md): reusable calculation rules.
- `tests/`: project tests.

## Scope

The example demonstrates tool and skill orchestration over the supplied workshop
fixtures. It is not a validated accounting or compliance system.
