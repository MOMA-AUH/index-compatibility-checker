# Index compatibility checker

A standalone browser tool for checking Illumina i7 + i5 index pairs for collisions and low Hamming distances before pooling samples.

No installation, account, or server is required: download `index-compatibility-checker.html` and open it in a modern browser.

## Use

1. Open `index-compatibility-checker.html`.
2. Paste the index list from Excel, CSV, or a text file.
3. Choose a distance rule and threshold.
4. Select **Validate and analyze**.
5. Review flagged pairs or download the CSV report.

The pasted list may contain:

- `index name`, `i7`, `i5` in three columns (recommended)
- `i7`, `i5` in two columns
- a joined pair such as `ACGTACGT+TGCATGCA`

Tabs, commas, semicolons, and spaces are accepted as column separators. Blank lines and a normal `i7`/`i5` header are ignored.

## Distance rules

- **Combined index pair** (default): calculates the Hamming distance after concatenating i7 and i5. This equals `distance(i7) + distance(i5)`.
- **Each index separately**: flags a pair if either the i7 or i5 distance is below the threshold. This is the more conservative rule.

The results table always shows the individual i7 and i5 distances as well as the combined-pair distance. Exact i7+i5 duplicates are reported as **Exact pair collisions**.

## Input validation

The checker requires indexes to contain only `A`, `C`, `G`, and `T`, and requires a consistent i7 length and i5 length across the pasted list. It does not upload or store pasted data.

## Important

This tool reports sequence distances; it does not determine the correct index-orientation convention for a particular library preparation, sequencer, or sample-sheet workflow. Confirm the applicable indexing convention and collision policy with your lab's protocol before making pooling decisions.
