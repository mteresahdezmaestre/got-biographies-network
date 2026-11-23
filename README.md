# What the wiki knows about who meets whom

Biography similarity and character interactions in *Game of Thrones*.
Final project for 02805 Social Graphs and Interactions, Technical University of Denmark (2026).

**Authors:** María Teresa Hernández Maestre and Santiago Mereles

## Question

To what extent does the textual similarity of two characters' Wiki biographies identify whether,
and how much, they interact in the series?

## Files

| File | What it is |
|---|---|
| `Game_of_Thrones_Social_Graphs.ipynb` | The full analysis, with outputs: network analysis, TF-IDF similarity, null models, baselines and validation |
| `Characters.xlsx` | Manually curated mapping from the 330 network identifiers to their Game of Thrones Wiki article |
| `got_character_biographies_only.csv` | The *Biography* section of each mapped article, retrieved via the MediaWiki API in November 2026 |
| `hand_labels.csv` | Stratified sample of 50 character pairs for independent hand labeling by both authors |
| `AI_METHODS.md` | Every place where an AI model touched the code or the results, and how we checked it |

## Data sources

- **Interaction network:** Andrew Beveridge, *Character Interaction Networks for the HBO Series Game of Thrones*,
  https://github.com/mathbeveridge/gameofthrones (CC BY-NC-SA 4.0). The notebook downloads the
  eight season files directly from that repository; they are not copied here.
- **Biographies:** Game of Thrones Wiki (Fandom), https://gameofthrones.fandom.com. Wiki text is
  licensed CC BY-SA by its contributors.

## How to run

Open the notebook in the same folder as `Characters.xlsx` and `got_character_biographies_only.csv` and
run all cells (Python 3 with pandas, networkx, scikit-learn, scipy, matplotlib, seaborn, requests,
beautifulsoup4 and openpyxl). The biographies are read from the CSV, so the Wiki API is only
called if the CSV is missing.
