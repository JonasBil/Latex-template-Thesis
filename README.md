# VUB LaTeX Template

A LaTeX template for academic reports using the VUB (Vrije Universiteit Brussel) official style with modular section files.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Features

- **VUB Official Branding**: VUB logo, colors, and fonts (TeX Gyre Adventor)
- **Modular Structure**: Separate section files for easy organization
- **VS Code Integration**: One-click compilation with green run button
- **Build Automation**: Organized build artifacts in dedicated folder
- **Ready to Use**: Just clone and start writing!

## Project Structure

```
latex-exercise3/
├── main.tex                    # Main LaTeX document
├── vub_logo_cmyk.pdf          # VUB official logo
├── README.md                  # This file
├── LICENSE                    # MIT License
├── .vscode/
│   └── settings.json          # VS Code LaTeX Workshop configuration
├── bib/
│   └── main.bib               # BibTeX bibliography file
├── styles/
│   └── vubprivate.sty         # VUB custom styling (colors, fonts, triangle)
├── sections/
│   ├── 01-introduction.tex    # Introduction section
│   ├── 02-methods.tex         # Methods section
│   ├── 03-results.tex         # Results section
│   ├── 04-discussion.tex      # Discussion section
│   └── 05-conclusion.tex      # Conclusion section
└── build/                     # Build artifacts (auto-generated, git-ignored)
    ├── main.aux               # Auxiliary file
    ├── main.bbl               # Bibliography output
    ├── main.blg               # Bibliography log
    ├── main.fdb_latexmk       # Latexmk database
    ├── main.fls               # File list
    ├── main.log               # Compilation log
    ├── main.pdf               # Final PDF output
    ├── main.synctex.gz        # SyncTeX for editor sync
    └── main.toc               # Table of contents
```

---

## Quick Start

### Prerequisites

- **LaTeX Distribution**: [MiKTeX](https://miktex.org/) (Windows) or [TeX Live](https://www.tug.org/texlive/) (Linux/Mac)
- **Perl**: Required by latexmk - [Strawberry Perl](http://strawberryperl.com/) (Windows)
- **VS Code** (recommended): With [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension

### Using This Template

#### Option 1: Clone and Start Writing (Recommended)

```bash
# Clone this repository
git clone https://github.com/JonasBil/Latex-template-VUB.git my-project
cd my-project

# Open in VS Code
code .

# Edit main.tex and section files, then press Ctrl+Alt+B to compile
```

#### Option 2: Manual Compilation

```bash
cd my-project
latexmk -pdf -interaction=nonstopmode -outdir=build main.tex
```

The compiled PDF will be in `build/main.pdf`.

---

## Recommended VS Code Extensions

The following extensions are recommended for a smooth LaTeX workflow in VS Code (you can create a new VS-code profile with these plugins to keep everything clean and organized):

- **[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)** — The core extension for LaTeX in VS Code. Provides one-click PDF compilation (`Ctrl+Alt+B`), real-time error highlighting, SyncTeX support (click in the PDF to jump to the source and vice versa), auto-completion for `\cite{}`, `\ref{}`, and LaTeX commands, and a built-in PDF viewer. This template's `.vscode/settings.json` is pre-configured for it.
- **[LTeX](https://marketplace.visualstudio.com/items?itemName=valentjn.vscode-ltex)** — Grammar and spell checking powered by LanguageTool. Works directly in `.tex` files and understands LaTeX syntax, so it won't flag commands as spelling errors. Supports multiple languages.
- **[LaTeX Utilities](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities)** — Adds quality-of-life features on top of LaTeX Workshop: live snippet previews, magic comments, and formatted paste (e.g., pasting a table from Excel auto-generates a `tabular` environment).
- **[Zotero LaTeX](https://marketplace.visualstudio.com/items?itemName=bnavetta.zoterolatex)** — Enables cite-as-you-write by searching your Zotero library directly from VS Code and inserting `\cite{}` keys.

To install all at once, run in a terminal:
```bash
code --install-extension James-Yu.latex-workshop
code --install-extension valentjn.vscode-ltex
code --install-extension tecosaur.latex-utilities
code --install-extension bnavetta.zoterolatex
```

---

## Writing Your Document

### 1. Update Document Information

Edit the preamble in `main.tex`:

```latex
%! Author = Your Name
%! Date = DD/MM/YYYY

\title{Your Document Title}
\faculty{Sciences and Bio-Engineering Sciences}  % Your VUB faculty
\author{Your Name}
```

Also update the footer:
```latex
\fancyfoot[LO, RE]{Your Name}  % Change to your name
```

### 2. Edit Section Files

Write your content in the separate section files:

- **`sections/01-introduction.tex`**: Introduction, background, research questions
- **`sections/02-methods.tex`**: Methodology, data, analysis
- **`sections/03-results.tex`**: Findings, figures, tables
- **`sections/04-discussion.tex`**: Interpretation, limitations, implications
- **`sections/05-conclusion.tex`**: Summary, contributions, future work

These files are automatically included in `main.tex` via:
```latex
\input{sections/01-introduction}
\input{sections/02-methods}
% ... etc
```

### 3. Add References

Add your references to `bib/main.bib`:

```bibtex
@article{author2025,
    title={Article Title},
    author={Last, First and Second, Author},
    journal={Journal Name},
    year={2025},
    volume={10},
    pages={123--145}
}
```

Cite in your text:
```latex
As shown by \cite{author2025}...
Or: \citeA{author2025} demonstrated that...
```

### 4. Automating Your Bibliography with Zotero + Better BibTeX

[Zotero](https://www.zotero.org/) can automatically manage your `.bib` file so you never have to write BibTeX entries by hand.

#### Install Zotero and Better BibTeX

1. Download and install [Zotero](https://www.zotero.org/download/) (free, open-source).
2. Install the [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/installation/) plugin — this adds robust BibTeX/BibLaTeX export and stable citation keys.
3. Restart Zotero after installing the plugin.

#### Collect References

Add references to your Zotero library using any of these methods:
- **Browser Connector**: Install the [Zotero Connector](https://www.zotero.org/download/) browser extension, then click the icon on any journal page, Google Scholar result, or arXiv page to save it instantly.
- **DOI/ISBN**: In Zotero, click the magic wand icon and paste a DOI or ISBN — metadata is fetched automatically.
- **Manual entry**: Add items by hand if needed.

#### Set Up Auto-Export to Your `.bib` File

1. In Zotero, select the collection (folder) you want to export, or select your entire library.
2. Go to **File → Export Library...** (or right-click a collection → **Export Collection...**).
3. Choose **Better BibTeX** as the format.
4. Check **Keep updated** — this enables auto-export so any new references you add are automatically written to the file.
5. Save to `bib/main.bib` in your project folder.

Now, every time you add or edit a reference in Zotero, it will automatically update `bib/main.bib`. No manual copying needed.

#### Cite in Your Document

Use the citation key generated by Better BibTeX (visible in Zotero's "Citation Key" column):

```latex
As demonstrated by \cite{desmet2020}...
```

With the Zotero LaTeX VS Code extension installed, you can also press `Ctrl+Shift+Z` to search your Zotero library and insert a citation key directly.

---

## Building Your Document

### VS Code (Recommended)

1. Open `main.tex` in VS Code
2. Press **`Ctrl+Alt+B`** or click the green **▶** button
3. PDF opens automatically in VS Code

### Command Line

```bash
# Full build with bibliography
latexmk -pdf -interaction=nonstopmode -outdir=build main.tex

# Clean build artifacts
latexmk -C -outdir=build

# Continuous preview (recompiles on save)
latexmk -pdf -pvc -interaction=nonstopmode -outdir=build main.tex
```

---

## VUB Styling

This template includes VUB official branding, provided by the [`texlive-vub`](https://gitlab.com/rubdos/texlive-vub) package created and maintained by **Ruben De Smet**.

The VUB LaTeX style files (`vub.sty`, `vubprivate.sty`, etc.) are licensed under the [LaTeX Project Public License (LPPL)](http://www.latex-project.org/lppl.txt), version 1.3 or later. The VUB logo is not covered by this license; you must obtain your own license for it.

If you have improvements to the `.sty` files, please consider contributing upstream via the [texlive-vub GitLab repository](https://gitlab.com/rubdos/texlive-vub).

### Colors

```latex
\textcolor{vubbleu}{Blue text}      % VUB blue (CMYK: 1,.8,.16,.03)
\textcolor{vuboranje}{Orange text}  % VUB orange (CMYK: 0,.78,1.,0)
```

### Fonts

The template uses **TeX Gyre Adventor** (similar to Avenir), the official VUB font. It works automatically with both pdfLaTeX and XeLaTeX/LuaLaTeX.

### Logo and Triangle

The VUB logo and orange triangle are automatically added to the title page via `\maketitle`.

---

## LaTeX Quick Reference

### Document Structure

```latex
\section{Title}              % Main section
\subsection{Subtitle}        % Subsection
\subsubsection{Detail}       % Sub-subsection
```

### Figures

```latex
\begin{figure}[h]
    \centering
    \includegraphics[width=0.8\textwidth]{figures/image.png}
    \caption{Your caption here}
    \label{fig:mylabel}
\end{figure}

% Reference it:
As shown in Figure~\ref{fig:mylabel}...
```

### Tables

```latex
\begin{table}[h]
    \centering
    \caption{Table caption}
    \label{tab:data}
    \begin{tabular}{|l|c|r|}
        \hline
        Column 1 & Column 2 & Column 3 \\
        \hline
        Data 1 & Data 2 & Data 3 \\
        \hline
    \end{tabular}
\end{table}

% Reference it:
See Table~\ref{tab:data} for details.
```

### Math

```latex
% Inline math
The equation $E = mc^2$ is famous.

% Display math
\begin{equation}
    \int_0^\infty e^{-x^2} dx = \frac{\sqrt{\pi}}{2}
\end{equation}
```

### Lists

```latex
% Bulleted list
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}

% Numbered list
\begin{enumerate}
    \item First step
    \item Second step
\end{enumerate}
```

### Citations

```latex
\cite{key}                   % (Author, Year)
\citeA{key}                  % Author (Year)
\citeyear{key}              % Year only
```

---

## Troubleshooting

### Common Issues

**Problem**: `File 'vub.sty' not found`
- **Solution**: Ensure the path `../archive/Latex/texlive-vub-v3.0.1/vub` exists, or update the path in `main.tex` line 11

**Problem**: `perl: command not found`
- **Solution**: Install [Strawberry Perl](http://strawberryperl.com/) and restart your terminal

**Problem**: Undefined references
- **Solution**: Compile twice. LaTeX needs two passes to resolve cross-references

**Problem**: Bibliography not showing
- **Solution**: Ensure you have at least one `\cite{}` command in your document

**Problem**: Fonts look wrong
- **Solution**: Install TeX Gyre Adventor fonts or they'll fall back to Computer Modern

---

## Additional Resources

### LaTeX Tutorials
- [Overleaf Documentation](https://www.overleaf.com/learn)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [The Not So Short Introduction to LaTeX](https://tobi.oetiker.ch/lshort/lshort.pdf)

### Bibliography Management
- [Google Scholar](https://scholar.google.com/) - Export BibTeX citations
- [JabRef](https://www.jabref.org/) - Reference management software
- [Zotero](https://www.zotero.org/) - Bibliography manager (see Zotero guide above)

---

## License

This template is licensed under the [MIT License](LICENSE).

The VUB styling files (under `styles/`) are by [Ruben De Smet](https://gitlab.com/rubdos/texlive-vub) and licensed under the [LaTeX Project Public License (LPPL)](http://www.latex-project.org/lppl.txt), version 1.3 or later.


## Author

**Jonas Bil**
- GitHub: [@JonasBil](https://github.com/JonasBil)

---

## Acknowledgments

- [Ruben De Smet](https://gitlab.com/rubdos/texlive-vub) for creating and maintaining the VUB LaTeX style package (`texlive-vub`)
- LaTeX Workshop team for the excellent VS Code extension
- The LaTeX community for continuous support

---

