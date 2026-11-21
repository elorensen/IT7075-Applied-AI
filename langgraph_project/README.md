# LangGraph Alert Triage Agent

**IT7075 – Applied AI for Cybersecurity**

## Project Overview

This project demonstrates a cybersecurity alert triage agent built using Python and LangGraph. The agent analyzes security alerts and determines whether they should be escalated for investigation or closed as routine activity. The project focuses on conditional routing, state management, tool usage, checkpointing, and the tradeoff between missed incidents and unnecessary escalations.

The agent was evaluated using 12 original, synthetic cybersecurity alerts: six requiring escalation and six representing routine activity. The scenarios include phishing, ransomware, suspicious PowerShell execution, MFA attacks, network activity, vulnerability scanning, and authorized administrative maintenance.

## Agent Architecture

The original LangGraph agent uses a keyword-based classification node to assign an initial risk level. A conditional edge then routes the alert to either an investigation node or a quick-close node. The investigation node calls a simulated threat-information lookup tool.

To improve classification, I added a `check_context` node between the original classification and routing steps. This node examines additional indicators of suspicious behavior and authorized activity before determining the final risk level.

**Original workflow:**

`Classify → Conditional Routing → Investigate / Quick Close → END`

**Improved workflow:**

`Classify → Check Context → Conditional Routing → Investigate / Quick Close → END`

The project also demonstrates state checkpointing using LangGraph's `MemorySaver` and thread identifiers.

## Experimental Results

The agent was tested against the same 12 labelled alerts using four configurations.

| Configuration | Caught | Missed | Over-Escalated |
|---|---:|---:|---:|
| Original keywords | 2/6 | 4/6 | 2/6 |
| Wider keywords | 5/6 | 1/6 | 3/6 |
| Original keywords + context | 6/6 | 0/6 | 0/6 |
| Wider keywords + context | 6/6 | 0/6 | 1/6 |

The original keyword-based agent missed four incidents and unnecessarily escalated two routine alerts. Expanding the keyword list reduced missed incidents but increased unnecessary escalations.

Adding the context-checking node improved performance on the custom dataset. The original keyword configuration combined with context checking caught all six incidents without unnecessarily escalating routine alerts.

## Limitations

This is a deterministic educational prototype, not a production-ready security system. The context rules were developed using the same 12 alerts used for evaluation, so the results do not demonstrate reliable performance on unfamiliar security events.

A production system would require larger and more diverse evaluation datasets, independent evidence of authorization, and additional testing for false negatives and false positives.

## Project Files

- `agent_notebook.ipynb` — Completed LangGraph implementation with saved outputs.
- `my_alerts.json` — Twelve original synthetic security alerts with expected decisions and justifications.
- `results_mine.csv` — Results from four controlled experiments.
- `SOURCES.md` — Documentation of the sources and origins of the alert scenarios.
- `README.md` — Project overview and experimental findings.

## Environment

The project was developed using Python 3.12, LangGraph, and Jupyter Notebook in Visual Studio Code.

All classification and tool operations run locally using deterministic Python functions. No external API, language model, GPU, or API key is required.
