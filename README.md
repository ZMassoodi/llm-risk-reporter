## Motivation
LLM usage is increasingly relevant to risk management workflows — specifically
summarising a proposed trade's risk profile quickly for a risk manager.

Inspired by reviewing qrisklab by Bilal Bai, who provides 
strong quant foundations for risk analytics. This project 
adds a natural language layer on top. It's useful to pair the results of this LLM
report with a stress test from qrisklab !

# LLM Risk Reporter
A Python-based risk analysis tool that computes options/Greeks 
using Black-Scholes formula and generates summaries using the Anthropic API.

## What it does
- Takes a proposed options position as input (asset, direction, 
  strike, expiry, implied vol)
- Computes Delta, Gamma, Vega and Theta using Black-Scholes
- Sends validated Greeks (JSON) to an LLM to generate a concise risk narrative
- Displays raw Greeks alongside the narrative for human verification

## Design decisions
- All numerical computation is done in Python 
- This reduces hallucination risk where bad numbers could inform bad decisions
- Raw Greeks are always displayed alongside the LLM output so 
  we can sanity check narrative

## Tech stack
- Python
- scipy / numpy — Black-Scholes implementation
- Anthropic API — LLM narrative generation

## Usage
1. Open llm_risk_reporter.ipynb in Jupyter
2. Run Cell 1 set with your Anthropic API key
3. Update position inputs in Cell 3
4. Run all cells to generate the risk report
