# AI methods

The course asks us to document every place where a model touched our results and how we checked it.
No language model labels, classifies or scores any data in this project. All measurements are TF-IDF
vectors, cosine similarities and standard network measures, computed with scikit-learn and NetworkX.
AI assistants were used to write code and to draft text. The table lists each use and the check
behind it.

| Where | What the AI did | How we checked it |
|---|---|---|
| Data collection (Sections 1, 8.2–8.4) | Wrote the code that downloads the season edge lists and calls the MediaWiki API | The character-to-article mapping in `Characters.xlsx` was curated by hand, not by a model. The notebook checks that every mapping matches a network identifier, that no two identifiers share an article and that no biography is empty (Section 8.5). We read sample biographies to confirm that the right section was extracted. |
| Text cleaning (Section 8.7) | Wrote the regular expressions that remove wiki boilerplate and *House of the Dragon* sections | The notebook counts the texts that still contain edit markers or season headings (all zero), and prints the word counts of the seven affected pages before and after cleaning. |
| Network analysis (Sections 2–7) | Wrote the code for degree, centrality, Louvain communities and the modularity null model | We compared the results with the storylines we know: the communities correspond to recognizable plotlines (Night's Watch, Essos, King's Landing, Arya). Degree and density were checked against the edge counts printed in Section 1. |
| TF-IDF and cosine similarity (Sections 9.1–9.3) | Wrote the vectorization and similarity code | The notebook checks that the matrix is symmetric, that the diagonal equals 1 and that the number of pairs equals n(n−1)/2. We read the most similar pairs to confirm that they make narrative sense. |
| Evaluation code (Sections 9.4–9.12) | Wrote the code for ROC-AUC, the degree-preserving null, the proper-noun masking, the baselines, the weight correlation and the community comparison | Before the real run, the whole pipeline was executed on a random network with the same number of edges. As expected, every score then gives ROC-AUC ≈ 0.5 and no effect against either null, so the method does not produce a signal on its own. The list of words flagged as proper nouns is printed (Section 9.9) and was inspected by hand; it also catches some capitalized common words (*House*, *Lord*, *White*), which we report as a limitation. |
| Validation (Section 9.14) | Drew the stratified sample of 50 pairs and extracted the sentences where one character mentions the other | The labels themselves are human. Both authors label every pair independently, without seeing the similarity score, and we report Cohen's kappa between the two annotators. |
| Interpretations and paper | Drafted the interpretation cells and the paper text | Every number in the text was checked against the notebook output. We read and edited all text, and the claims about specific characters (for example Gared and Waymar Royce, or Cohollo and Qotho) were checked against the biographies. |
