# Limitations and Data Governance

## Evidence status

This release summarizes a completed exploratory pilot dated 15 October 2026. Its aggregate figures were transcribed from the author's pilot report and checked for arithmetic consistency. Underlying prompts, answers, grading records, and datasets are not included or independently re-audited here. Verification of a summary is not independent replication of its experiment.

## Scientific limitations

### Exposure and dependence

All 500 candidate LongMemEval-S questions had been seen previously in the project. The evaluated set contains 487 questions after 13 exclusions under a prewritten rule. It is unsuitable as a clean confirmatory holdout.

Shared sessions connect the questions into one component. A question-level confidence interval or significance calculation that assumes independent questions would not resolve this dependence. This release intentionally makes no confirmatory inference from such statistics and reports no equivalence or state-of-the-art claim.

### Scope of the intervention

The comparison holds retrieved sessions and their order fixed between A and B. It examines the older anchored lexical selector, configured with ratio 0.75 and neighbors 1. It does not test the newer full-exchange packer. The older selector can split exchanges and has existing fallback behavior; this package does not provide the code needed to audit those behaviors.

The router arms D, F, and H were absent from the completed pilot. Their usefulness and thresholds have not been validated by these results. Any future threshold selection on previously seen LongMemEval-S material remains exploratory.

### Measurement and judging

The 23.2% reduction refers only to provider-reported input tokens of successful final reader calls. Output tokens, failed attempts, retrieval, context packaging, and evaluation judging are excluded. Unknown usage for failed attempts prevents treating these totals as complete execution accounting. No total-cost, latency, monetary-saving, or energy-saving claim is made.

The historical evaluation used automated blinded judging. Blinding reduces direct access to the arm label but does not eliminate grading error or model-family effects. The judge and coordinator belonged to the same model family. Independent scoring and an agreed human-adjudication procedure would strengthen future validation.

Absence of an annotated answer-bearing turn from selected context is a proxy measurement. It does not by itself prove that all necessary evidence was removed or that a correct answer was hallucinated.

## Data release boundaries

This package contains only newly prepared documentation and aggregate counts. It excludes source code, repository history, datasets, question-level results, reader and judge prompts, generated answers, session identifiers, raw logs, transport caches, credentials, private correspondence, and machine-specific paths.

Access to a benchmark does not by itself establish permission to redistribute it or derived text. Any future dataset, prompt, output, or implementation release must undergo a separate rights and privacy review. Prospective evaluation data should be obtained through an authorized source under its own applicable terms. No rights in third-party models, datasets, or software are granted by this package.

No software or dataset license is supplied, and this documentation package does not assert an open-source license. The author should select and approve any documentation license before presenting it as openly licensed.

## Integrity and provenance

The public package is a fresh allowlisted export, without a copy of the private repository or its commit history. The historical report provides the observations; the evaluation plan is prospective. File hashes in SHA256SUMS.txt allow recipients to detect changes to these exported files. Those hashes cannot verify omitted experimental artifacts.
