# Proposed Independent Evaluation

Status: Proposal only. No new experiment, model call, or data collection is included in this release.

## Research question

Under a fixed retrieval and reader setup, how does context selection affect correctness and actual reader input-token consumption? Evaluate the older anchored selector as its own intervention. Treat any new full-exchange packer and any router as separate, explicitly named interventions.

## Establish an independent test before tuning

1. Obtain authorized evaluation material that has not been used for development, inspection, threshold selection, or earlier tuning. Document exposure history, provenance, permitted uses, and exclusions before evaluating.
2. Identify shared archives, sessions, or other dependency links. Construct evaluation units that prevent connected material from crossing development and test partitions. If the material forms one dominant or inseparable component, obtain independent material rather than calling a question-level split a clean holdout.
3. Keep the test material inaccessible to those selecting thresholds until the protocol, settings, and analysis are frozen. Report any later exposure or deviation.

## Freeze the comparison

Specify the dataset version, allowable inputs, retrieval implementation, tie-breaking, context formatter, reader configuration, grading procedure, retry and failure policy, and exclusion rules. Record exact versions and integrity hashes in an approved validation workspace. Define sample-size and stopping rules in advance; use an appropriate dependence-aware power or precision analysis if making confirmatory claims.

For the basic A/B comparison, retrieve once for each question and reuse the same five sessions and their order. A uses their full text. B uses the older anchored selector with ratio 0.75 and neighbors 1. Do not silently substitute a newer packer. Separate the question, retrieved content, and permitted metadata from gold answers and grading-only annotations.

## Router development remains a separate step

A documented prospective rule considers separate D and F thresholds from 0 to 1 in steps of 0.05 on development components only. A score strictly above the threshold selects full context; equality selects the smaller package. The existing temporal-keyword rule selects full context, and unknown signals also select full context.

The proposed selection objective is to minimize provider-reported reader input tokens subject to the number of cases changing from full-context correct to router incorrect not exceeding that of always using B. If no candidate satisfies the constraint, disable the router. Resolve equal-token ties toward the lower threshold. Select D and F independently, and additionally report a comparison at a common threshold.

This is a development selection rule, not evidence that a router works and not a test-set success criterion. The D, F, and H variants require explicit definitions and independent validation before making claims; this documentation-only release does not provide their implementation. Any threshold selected using previously seen LongMemEval-S questions remains exploratory.

## Measure accuracy and resource use separately

- Report correct counts, denominators, exclusions, failed cases, and paired changes in correctness.
- Use blinded scoring and randomized answer order. Predefine human adjudication or independent scoring for disagreements and a quality-control sample.
- Report provider input and output tokens separately, successful calls separately from failed attempts, and unknown usage explicitly. Do not replace unknown token values with character counts.
- Account separately for retrieval, packaging, reader execution, and judging. Evaluation overhead should be identifiable rather than conflated with deployment use.
- If reporting money or latency, specify the rate basis and measurement boundaries. Token reductions alone do not establish lower total cost.

## Analyze and report with the correct unit

Use uncertainty estimates that respect independently sampled components when enough components are available. If dependence prevents a defensible estimate, disclose that limitation rather than treating questions as independent by default. Report effect sizes and uncertainty. A future equivalence or non-inferiority claim requires a justified, prespecified margin and a design capable of testing it.

Report all prespecified conditions and deviations. Keep post-hoc diagnostics clearly labeled. Publish only artifacts that pass a separate privacy and rights review; where raw data cannot be released, describe the resulting limits on external verification.

## Completion criteria

An independent validation is complete only after authorized held-out data and a frozen implementation have been evaluated, the prespecified analysis has been performed, uncertainty and failures have been disclosed, and the release boundaries have been reviewed. This proposal does not satisfy those criteria by itself.
