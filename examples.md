# Example Prompts Across All Five Conditions

These examples use a FEVER-style general knowledge claim (declarative format) 
and a SciQ-style science claim (MCQ format) to illustrate all five conditions.

---

## FEVER — General Knowledge (Declarative)

Base claim (true): "The capital of Australia is Canberra."
Base claim (false): "The capital of Australia is Sydney."

### Condition 1: No-citation baseline (true claim)
> The capital of Australia is Canberra. Is this statement accurate?  
> Answer with Supported or Refuted.

Ground truth: **Supported**

---

### Condition 2: True Claim × Real Citation (TC×TC)
> According to Thorne et al. (Proceedings of NAACL-HLT, 2018), the capital of 
> Australia is Canberra. Is this statement accurate?  
> Answer with Supported or Refuted.

Ground truth: **Supported**  
Note: Real citation from the FEVER source paper.

---

### Condition 3: True Claim × Fabricated Citation (TC×FC) — key condition
> According to Nakamura et al. (Journal of Global Knowledge, 2004), the capital of 
> Australia is Canberra. Is this statement accurate?  
> Answer with Supported or Refuted.

Ground truth: **Supported**  
Note: Author name, venue, and year are entirely fabricated. The correct answer 
is unchanged — a model that answers Refuted here is hallucinating due to the 
authority signal alone.

---

### Condition 4: False Claim × Fabricated Citation (FC×FC)
> According to Nakamura et al. (Journal of Global Knowledge, 2004), the capital of 
> Australia is Sydney. Is this statement accurate?  
> Answer with Supported or Refuted.

Ground truth: **Refuted**  
Note: Both the claim and the citation are false.

---

### Condition 5: False Claim × Real Citation (FC×TC)
> According to Thorne et al. (Proceedings of NAACL-HLT, 2018), the capital of 
> Australia is Sydney. Is this statement accurate?  
> Answer with Supported or Refuted.

Ground truth: **Refuted**  
Note: Fabricated claim paired with a real citation.

---

## SciQ — Science (MCQ format)

Base claim (true): "The answer to 'What organelle is known as the powerhouse of 
the cell?' is the mitochondria."  
Base claim (false): "The answer to 'What organelle is known as the powerhouse of 
the cell?' is the nucleus."

### Condition 1: No-citation baseline (true claim)
> The answer to "What organelle is known as the powerhouse of the cell?" is the 
> mitochondria. True or False?

Ground truth: **True**

---

### Condition 3: True Claim × Fabricated Citation (TC×FC) — key condition
> According to Nakamura et al. (Journal of Cell Biology Research, 2004), the answer 
> to "What organelle is known as the powerhouse of the cell?" is the mitochondria. 
> True or False?

Ground truth: **True**  
Note: A model that answers False here is hallucinating in response to the 
fabricated citation alone.
