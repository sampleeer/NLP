# Leakage Audit Notes

This project does not use leaked labels or hidden test labels for the final model. The following audit is included only to explain why extremely high Kaggle leaderboard scores should not be interpreted as reproducible NLP SotA.

The Kaggle Disaster Tweets dataset contains repeated and near-repeated messages. With canonicalized exact matching, the local audit found:

- Train rows: 7,613.
- Test rows: 3,263.
- Unique canonical train texts: 6,890.
- Unique canonical test texts: 3,087.
- Duplicate canonical text groups in train: 318.
- Conflicting duplicate groups in train: 72.
- Train-test exact text overlap groups: 284.
- Test rows whose label is inferable from an unambiguous train duplicate: 347, or 10.63% of test.

On the local stratified validation split, a duplicate-label lookup covers only 11.62% of validation rows. On the covered subset it reaches F1 = 0.931, but on the whole validation set it reaches only F1 = 0.296 because most examples are not covered. This shows that duplicate leakage can create locally near-perfect predictions for a subset of the data, but it is not a complete NLP solution.

For this reason, the report should avoid claiming SotA based on perfect or near-perfect leaderboard entries unless the solution is reproducible and does not depend on hidden-label reconstruction or competition-specific leakage. Our reported final approach should remain the RoBERTa + TF-IDF ensemble.

