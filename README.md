# LLM Risk Reporter

A Python-based risk analysis tool that computes options Greeks 
using Black-Scholes and generates plain English risk summaries 
using the Anthropic API.

## What it does

- Takes a proposed options position as input (asset, direction, 
  strike, expiry, implied vol)
- Computes Delta, Gamma, Vega and Theta using Black-Scholes
- Passes validated Greeks to an LLM to generate a concise 
  plain English risk narrative
- Displays raw Greeks alongside the narrative for human verification

## Design decisions

- All numerical computation is done in Python before the LLM 
  is called — the LLM never does maths
- This mitigates hallucination risk in a financial context where 
  incorrect numbers could inform bad decisions
- Raw Greeks are always displayed alongside the LLM output so 
  a risk manager can sanity check the narrative

## Motivation

Built as a prototype of the kind of LLM tooling increasingly 
relevant to risk management workflows — specifically the use 
case of summarising a proposed trade's risk profile quickly 
for a risk manager.

Inspired by reviewing qrisklab by Bilal Bai, which provides 
strong quantitative foundations for risk analytics. This project 
adds a natural language layer on top of that kind of 
quantitative infrastructure.

## Tech stack

- Python
- scipy / numpy — Black-Scholes implementation
- Anthropic API — LLM narrative generation

## Usage

1. Open llm_risk_reporter.ipynb in Jupyter
2. Run Cell 1 to set your Anthropic API key
3. Update position inputs in Cell 3
4. Run all cells to generate the risk report

## Note on API key security

Never hardcode your API key in the notebook. Store it using 
os.environ as shown in Cell 1.
