# LLMZIP Public Research Brief

**Exploratory context-selection research for independent review and collaboration**

Author: Halil Talha Ertan, independent researcher  
Release date: 16 October 2026  
Status: Documentation-only research snapshot

## Purpose

LLMZIP investigates how selecting a smaller portion of retrieved conversational context affects reader accuracy and input-token use. This release gives collaborators a self-contained account of one exploratory A/B pilot and a proposal for independent validation. It contains aggregate findings and methodological limitations.

The pilot recorded 419 correct answers with full retrieved sessions and 417 with a smaller anchored selection, across 487 previously seen questions. Successful final reader calls used 23.2% fewer input tokens with the smaller selection. These descriptive observations motivate further evaluation; they do not establish equivalent accuracy, generalization, state-of-the-art performance, or lower total cost.

## What was compared

Both conditions used the same five retrieved sessions in the same order. Retrieval was B1c, using BM25 and Snowball stemming with a stem cache.

| Condition | Context supplied to the reader |
| --- | --- |
| A — full top five | Full text of the five retrieved sessions |
| B — anchored 0.75 | The older lexical context selector, anchored mode, ratio 0.75, neighbors 1, applied to those same five sessions |

B was not the newer full-exchange packer. It can split a user–assistant exchange. The 0.75 setting describes the selector configuration; it is not a guarantee of exactly 25% fewer provider-reported input tokens.

The reader was gpt-6.1-sol with medium reasoning, tools and web disabled, and no fallback model. Answers were assessed using the official LongMemEval yes/no grading rule by Opus 5.5 (claude-opus-5-5), with condition labels hidden and answer order shuffled. The judge and coordinating agent belonged to the same model family. These are descriptions of the historical pilot, not instructions or claims about current model availability.

## Aggregate observations

| Measure | A — full top five | B — anchored 0.75 |
| --- | ---: | ---: |
| Evaluated questions | 487 | 487 |
| Correct answers | 419 | 417 |
| Accuracy, derived from counts | 86.04% | 85.63% |
| Input tokens from successful final reader calls | 7,309,577 | 5,610,870 |

The observed difference was −2 correct answers for B, or approximately −0.41 percentage points. The reported input-token reduction was 23.2%, rounded. This denominator covers only successful final reader calls. It excludes output tokens, failed attempts, retrieval, context packaging, and judging. It is not an end-to-end cost saving or a monetary estimate.

The candidate pool contained 500 LongMemEval-S questions. Thirteen were excluded under a prewritten rule, leaving 487. This release does not include question-level exclusions or materials, so an external reader cannot audit that rule from this package alone.

## How to interpret the pilot

- All 500 questions had previously been seen in the project. There was no clean holdout.
- Questions were linked through shared sessions into a single connected component. They must not be treated as 487 independent observations for confirmatory inference.
- A reliable component-level uncertainty estimate cannot be obtained from one connected component. No equivalence, non-inferiority, or “no accuracy loss” conclusion follows from the small observed difference.
- Router variants D, F, and H were not evaluated in this run. Router thresholds remain deferred and unvalidated.
- This comparison evaluates one older context selector under one setup. It does not validate the newer full-exchange packer or the wider LLMZIP system.

See [Limitations and data governance](docs/LIMITATIONS_AND_DATA_GOVERNANCE.md) for the release boundaries and [Proposed independent evaluation](docs/PROPOSED_EVALUATION.md) for the next research questions.

## What is included

- This research brief
- [Aggregate results in CSV](results/aggregate_results.csv) and [JSON](results/aggregate_results.json)
- Limitations and data-governance notes
- A proposed independent evaluation plan
- [A short Turkish summary](docs/TURKCE_OZET.md)
- A publication checklist and file checksums

The package contains no implementation, executable evaluation harness, dataset, individual question, prompt, answer, session record, or model-output file. It is not an executable reproducibility package. Its checksums establish file integrity only, not the validity of the experimental results.

## Collaboration

The intended use is methodological review and preparation for an independent evaluation: assessing the comparison, identifying leakage and dependence risks, defining held-out evaluation units, and measuring accuracy and token use under a frozen protocol. Independent validation would require separately approved implementation and data access, followed by a new execution. The proposed plan does not imply that such an execution has occurred or been scheduled.

A separate public repository or webpage can host this documentation snapshot without exposing the original private research workspace or its history. Publication, licensing, and any later code or data release require separate decisions.
