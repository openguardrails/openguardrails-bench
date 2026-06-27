# OGR seed benchmark — results (`seed-v0`)

Reference detectors only. Third-party vendors appear when they submit a conformant detector. OpenGuardrails does not submit a detector.

| Detector | Type | prompt injection F1 | malicious command F1 | data exfiltration F1 | secret leak F1 | Macro F1 | P95 ms |
|---|---|---|---|---|---|---|---|
| keyword-baseline | config | 0.400 | 0.800 | 0.667 | 0.667 | **0.634** | 0.004 |
| ogr-compose (config⊕llm) | hybrid | 0.889 | 0.667 | 0.545 | 0.400 | **0.625** | 0.002 |
| block-all | baseline | 0.625 | 0.625 | 0.571 | 0.571 | **0.598** | 0.000 |
| config-rules | config | 0.333 | 0.667 | 0.400 | 0.400 | **0.450** | 0.002 |
| llm-judge | model | 0.889 | 0.333 | 0.400 | 0.000 | **0.406** | 0.002 |
| allow-all | baseline | 0.000 | 0.000 | 0.000 | 0.000 | **0.000** | 0.000 |

Suite sizes (unsafe / shared safe): prompt injection 10/12, malicious command 10/12, data exfiltration 8/12, secret leak 8/12
