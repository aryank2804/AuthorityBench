# Judge Configuration

Model:
- Qwen3-8B

Inference:
- Temperature: 0.0
- Max output tokens: 16
- Greedy decoding

Output format:
- JSON object with a single field:
  {
    "is_hallucination": 0
  }

Labels:
- 0 = Not hallucination
- 1 = Hallucination