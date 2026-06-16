# TODO — touri

**Version:** 0.1.0 (pyproject) · **Role:** manifest `*.uri.capability.yaml` → callable backends

> Audyt kod vs lista: 2026-06-16

## Zrobione

- [x] Primary backends: `python`, `shell`, `mock`, `uri_flow`, `uri_graph`, `uri2ops`
- [x] Redaction secret payload (`touri/redaction.py` → uri2ops)
- [x] `touri register` / `explain` integracja z uri3 (`touri/register.py`)
- [x] Fallback chain + uri2verify data quality (`fallbacks.py`, `data_quality.py`)
- [x] Markpact registry loader (`loaders/markpact_loader.py`)
- [x] Testy: uri_flow, uri2ops, register, voice (via tellmesh examples path)

## Otwarte

- [ ] JSON Schema validation — plik `schemas/uri_capability.schema.json` jest, kod używa ręcznej walidacji; brak extra `[jsonschema]`
- [ ] HTTP backend — handler primary istnieje (`backend_dispatch.py`); brak przykładów/testów w repo touri
- [ ] Docker backend — tylko fallback przez uri2run; brak primary handler + examples
- [ ] MCP backend — fallback przez uri2run; brak primary + examples w touri
- [ ] A2A backend — fallback przez uri2run; brak primary + examples w touri
- [ ] Voice: local whisper — kod w **uri2voice** (`stt_whisper.py`); brak piper; manifesty voice w tellmesh/examples/21, nie w touri/examples
- [ ] Voice: cloud STT/TTS z `env://` secrets (dziś `OPENAI_API_KEY` bezpośrednio)
- [ ] Voice pack: przenieść/przylinkować examples/21 do touri repo (uri2voice już osobna paczka)

## Uwagi audytu

- `https`, `stdio`, `sse`, `ws`, `ssh`, `docker`, `mcp`, `a2a` działają jako **fallback** (uri2run), nie jako primary `backend.type`
- Przykłady markpact/voice pełne są w `tellmesh/examples/`, testy touri ustawiają `repo_root` na monorepo
- Wersje: `pyproject` 0.1.0 vs README badge / CHANGELOG — do zsynchronizowania przy release
