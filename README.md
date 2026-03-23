# Kinebot LaTeX Report Template

LaTeX template for Kinebot company reports, formatted according to **ABNT** (Brazilian standards).

## ABNT Formatting (NBR 14724)

| Setting | Value | ABNT Requirement |
|---|---|---|
| Paper | A4 | A4 |
| Top margin | 3cm | 3cm |
| Bottom margin | 3cm* | 2cm |
| Left margin | 5cm | 3cm |
| Right margin | 2cm | 2cm |
| Font | Arial (Helvetica) 12pt | Arial or Times New Roman 12pt |
| Line spacing | 1.5 | 1.5 |
| Paragraph indent | 1.25cm | 1.25cm |
| First paragraph | Indented | Indented |
| Sections | Bold uppercase | Bold uppercase |
| Subsections | Bold | Bold |
| Subsubsections | Bold italic | Bold italic |
| Language | pt-BR | Portuguese |
| Page numbers | Top right, Arabic | Top right, starting from first content page |

> *Bottom margin is 5cm instead of the standard 2cm to accommodate the footer banner.

### Footer Banner

The company footer banner appears **only on content pages** (after the table of contents). The cover page and table of contents have no footer.

## Preview

### Cover Page

![Cover Page](images/cover_page.png)

### Table of Contents

![Table of Contents](images/sumario.png)

### Content

![Content](images/content.png)

## Prerequisites

A LaTeX distribution installed:

- **macOS**: [MacTeX](https://www.tug.org/mactex/)
- **Linux**: TeX Live (`sudo apt install texlive-full` or equivalent)
- **Windows**: [MikTeX](https://miktex.org/)

All packages used (`fancyhdr`, `geometry`, `graphicx`, `helvet`, `hyperref`, `xcolor`, `babel`, `setspace`, `titlesec`, `indentfirst`) are included in standard distributions.

## Project Structure

```
template_latex/
├── main.tex              # Main document (duplicate for each report)
├── kinebot.sty           # Style package (do not edit)
├── images/
│   └── footer_banner.png # Company banner (footer)
└── README.md
```

## How to Compile

Recommended method (automatically runs the required number of passes):

```bash
latexmk -pdf main.tex
```

Or manually (run twice to generate the table of contents):

```bash
pdflatex main.tex
pdflatex main.tex
```

To clean auxiliary files:

```bash
latexmk -c
```

## How to Use

1. Duplicate `main.tex` with the desired name (e.g., `report-project-x.tex`)

2. Edit the metadata at the top of the file:

```latex
\reporttitle{Report Title}
\reportsubtitle{Brief description}
\reportauthor{Author Name}
\reportdate{\today}
\reportref{v1.0}
\reportcity{Curitiba}
```

3. Write your content in sections:

```latex
\section{Introduction}
Your text here.

\subsection{Subsection}
More details.
```

4. Compile the PDF.

## Available Commands

| Command | Description |
|---|---|
| `\reporttitle{...}` | Report title (cover page) |
| `\reportsubtitle{...}` | Subtitle/description (cover page) |
| `\reportauthor{...}` | Report author(s) |
| `\reportdate{...}` | Date (default: `\today`) |
| `\reportref{...}` | Document version |
| `\reportcity{...}` | City (default: `Curitiba`) |
| `\makecover` | Generates the cover page |

## Customization

### Margins

Margins follow ABNT standards and are defined in `kinebot.sty`:

```latex
% In kinebot.sty (ABNT NBR 14724)
\RequirePackage[
  a4paper,
  top=3cm,
  left=3cm,
  right=2cm,
  bottom=3cm
]{geometry}
```

If the footer banner height changes, adjust `bottom` and `\footskip` proportionally.

### Including Figures

```latex
\begin{figure}[htbp]
  \centering
  \includegraphics[width=0.8\textwidth]{images/my-figure}
  \caption{Figure description.}
  \label{fig:my-figure}
\end{figure}
```

### Including Tables

```latex
\begin{table}[htbp]
  \centering
  \caption{Table description.}
  \begin{tabular}{lcc}
    \hline
    Column 1 & Column 2 & Column 3 \\
    \hline
    Data 1   & Data 2   & Data 3   \\
    \hline
  \end{tabular}
  \label{tab:my-table}
\end{table}
```
