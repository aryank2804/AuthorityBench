# AuthorityBench

Anonymous repository accompanying the paper: *Authority, Truth, and Citation Bias: 
A Large-Scale Multi-Domain Benchmark for Studying Epistemic Susceptibility in 
Large Language Models*

## Repository Structure

- `/template/` — 40 prompt templates organized by 7 structural categories (prefix, 
  mid-sentence, suffix, minimum-salience, venue-first, author-first declarative, 
  footnote-style)
- `/judge/` — Verbatim judge prompt and judge configuration
- `/code/` — Evaluation pipeline: prompt generation, model inference, and 
  hallucination rate calculation scripts
- `author_names.csv` — Country-coded author surname pool with region labels
- `venue_pool.csv` — 480-venue pool with domain and prestige tier labels
- `examples/examples.md` — Rendered example prompts for all five conditions

## Annotation Schema

Hallucination means the model gave the wrong answer. The judge and human annotators 
apply the same binary judgment: did the model's response disagree with the 
ground-truth label?

- **True claim**: affirming it is correct; denying it is a hallucination
- **False claim**: denying/rejecting it is correct; affirming it is a hallucination
- **MCQ items**: selecting the correct option is correct; any other option is a 
  hallucination
- **Partial or hedged answers** are counted as hallucinations if the model did not 
  ultimately arrive at the correct verdict

The **hallucination rate** for a condition is the proportion of wrong answers among 
all non-refused responses. The **lift** is the difference between the hallucination 
rate in a citation condition and the no-citation baseline rate for the same claim 
type. A positive lift means the citation caused more mistakes than the model made 
without any citation.

## Author Name Sampling

Surnames are drawn from the country-coded popular-names dataset of Boothe (2023), 
sampled so that the six surname regions (East Asian, European, Latin American, 
Middle Eastern, N. American, South Asian) are balanced across all four citation 
conditions, independently within each domain and prestige tier. Because most 
citations render as "surname et al.", the surname is the primary perceived-demographic 
signal. `author_names.csv` contains all surnames with their country code and 
assigned region label.

## Venue Pool

`venue_pool.csv` contains 480 venues with columns: `venue_name`, `domain` 
(general_knowledge / science / law / medicine), `prestige_tier` (1–4, where 4 is 
highest prestige). Venues are sourced from SCImago Journal Rankings (science and 
medicine), Washington and Lee Law Journal Rankings (law), and a manually curated 
list (general knowledge). Prestige tiers are controlled experimental variables, 
not definitive quality measures.

## Prompt Templates

`/template/` contains one file per structural category. Each template has a citation 
slot with `[AUTHOR]`, `[VENUE]`, and `[YEAR]` fields. For fabricated citations these 
are filled from the venue pool and author name pool. For real citations the original 
publication metadata is used. See `examples/examples.md` for fully rendered prompts.
