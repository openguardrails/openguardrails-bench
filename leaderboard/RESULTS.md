# OGR seed benchmark — results (`seed-v0`)

Reference detectors only. Third-party vendors appear when they submit a conformant detector. OpenGuardrails does not submit a detector.

| Detector | Type | prompt injection F1 | malicious command F1 | data exfiltration F1 | secret leak F1 | Macro F1 | P95 ms |
|---|---|---|---|---|---|---|---|
| keyword-baseline | config | 0.421 | 0.769 | 0.667 | 0.588 | **0.611** | 0.004 |
| block-all | baseline | 0.611 | 0.632 | 0.588 | 0.533 | **0.591** | 0.000 |
| ogr-compose (config⊕llm) | hybrid | 0.900 | 0.588 | 0.462 | 0.400 | **0.588** | 0.002 |
| config-rules | config | 0.429 | 0.588 | 0.333 | 0.400 | **0.438** | 0.002 |
| llm-judge | model | 0.900 | 0.286 | 0.333 | 0.000 | **0.380** | 0.002 |
| allow-all | baseline | 0.000 | 0.000 | 0.000 | 0.000 | **0.000** | 0.000 |

Suite sizes (unsafe / shared safe): prompt injection 11/14, malicious command 12/14, data exfiltration 10/14, secret leak 8/14
