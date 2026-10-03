# Summer, on Screen — CSCI 5609 A1

SvelteKit + TypeScript + D3 implementation of the Summer Movies assignment.
This is the standalone A1 project repository. A0 remains in its own repository.

## Run

```sh
npm install
npm run dev
```

Open http://localhost:5173 (the root page shows A1).

```sh
npm run check
npm run build
npm run preview
```

The static build defaults to base `/A1`. Preview it at
http://localhost:4173/A1/.
For a different repository name, use `BASE_PATH=/your-repo npm run build`.
The included GitHub Actions workflow derives BASE_PATH from the repository name.
Published site: https://jason-2333.github.io/A1
Repository: https://github.com/jason-2333/A1
A0 project: https://github.com/jason-2333/A0

## Implemented requirements

- CSV fetched from `static/summer_movies.csv` through D3 and the SvelteKit base path.
- 899 distinct titles, 24 known genres, release years 1946–2024.
- Numeric fields parsed as numbers, years as Date objects, genres as arrays.
- Missing values: one unknown year and 56 unknown runtimes stay null;
  18 unknown genre lists become empty arrays. The starter TMovie type is
  extended with nullable year/runtime and the CSV's simple_title field.
- Distribution: sorted bars, both axis labels, values, hover/focus/click readouts.
- Q1: each year's top three recomputed from that year's movie counts;
  the chart does not track only the overall top three. Ties use alphabetical
  order to select exactly three. All genres are displayed, with year controls.
- Q2: all 24 genres in one co-occurrence matrix, including zero-count pairs.
  Gray diagonal cells show genre totals. Counts and conditional row shares
  are separate views with a color legend and hover/focus/click readouts.
- Dataset-derived insight paragraphs for both questions.
- Expandable design notebook: three distinct sketches for each question,
  encodings, comparisons, and explanations of the selected designs.
- Mobile layout with horizontally scrollable charts, keyboard interactions,
  reduced-motion support, loading/error states, and a retry button.

## Source and template

Instructions: https://github.com/UMN-CSCI5609/Assignments-Instructions/tree/main/A1-Visual-Encoding

The original instruction, loader, bar component, and type files are retained in
`reference/`. `Bar.svelte` keeps the starter props and D3 scale approach;
its rendering and axes are completed and adapted to the responsive design.
Data is the CSV included in the course's A1 instruction folder, from IMDb
non-commercial data. Genre totals include each genre of a multi-genre title.
Q1 excludes only unknown years; distribution and Q2 use all titles with genres.
Co-occurrence is an association count, not a Pearson correlation or causation.

## Local verification

- `npm run check`: zero errors and zero warnings.
- `npm run build`: adapter-static output successfully written to `build/`.
- Independently recounted all annual top-three rankings and all 576 matrix cells;
  verified symmetry, diagonal counts, unique IDs, and missing-value handling.
- Example totals: Drama 486; Comedy 270; Romance 189.
- Comedy + Drama: 108 movies (40% of Comedy movies).
- Drama ranks in the top three in 73 of 78 years with known genres.

## Report and deployment

The five-page PDF report is at `output/pdf/A1-Visual-Encoding-Report.pdf`. It
contains three sketches per question, encoding descriptions and comparisons,
design justifications, screenshots of both implemented visualizations,
data-backed answers, and the repository and Pages links.

The site is published using GitHub Actions. The existing A0 repository remains
public because this account’s GitHub Free plan does not allow Pages from a
private personal repository. Keep the site updated before the Canvas deadline.
