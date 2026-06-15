# touri


## AI Cost Tracking

![PyPI](https://img.shields.io/badge/pypi-costs-blue) ![Version](https://img.shields.io/badge/version-0.1.31-blue) ![Python](https://img.shields.io/badge/python-3.9+-blue) ![License](https://img.shields.io/badge/license-Apache--2.0-green)
![AI Cost](https://img.shields.io/badge/AI%20Cost-$0.00-orange) ![Human Time](https://img.shields.io/badge/Human%20Time-1.0h-blue) ![Model](https://img.shields.io/badge/Model-openrouter%2Fqwen%2Fqwen3--coder--next-lightgrey)

- 🤖 **LLM usage:** $0.0001 (1 commits)
- 👤 **Human dev:** ~$100 (1.0h @ $100/h, 30min dedup)

Generated on 2026-06-15 using [openrouter/qwen/qwen3-coder-next](https://openrouter.ai/qwen/qwen3-coder-next)

---

`touri` maps new URI schemes/templates to reusable capabilities without creating a new library for every URI.

Core idea:

```txt
URI -> capability manifest -> backend -> service result
```

Example:

```yaml
version: 1
capability:
  id: weather.forecast.html
  scheme: weather
  uri_template: weather://forecast/{place}/{days}/html
  operation: generate
  kind: command
backend:
  type: python
  target: python://examples.hello_weather:handler
```

Run:

```bash
pip install -e packages/touri
touri validate examples/20_touri_capabilities/weather_forecast.uri.capability.yaml
touri list examples/20_touri_capabilities
touri call weather://forecast/Gdansk/14/html --registry examples/20_touri_capabilities
```

`touri` does not replace `uri3`, `uri2flow`, `uri2ops`, or hypervisor. It is the generic capability layer used when a URI should be backed by an existing function, shell script, HTTP service, Docker action, MCP tool, A2A skill, flow, or graph.
