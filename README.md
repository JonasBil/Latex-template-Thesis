# KU Leuven Master Thesis Template

This is a LaTeX template for the master thesis Geography of the VUB/ KUL program using the [KU Leuven style guidelines](http://wet.kuleuven.be/studenten/mastersthesis/form), modified using the front page (that can be found on Toledo under the "Master" section) and guidelines for the master in Geography. The faculty guidelines doesn't specify the font size, which should be 11pt, with a line spacing of 1.5 and margins of 2.5-2.8 cm on all sides. 
I created this template to keep the document structure modular, work in VS Code, and have a good bibliography management (using APA style). While it is built with VS Code in mind, it remains simple enough to be used with Overleaf or any other LaTeX editor (such as TeXstudio) without issues.
I wrote this README to help you get started and correctly configure your environment. If you have any questions or suggestions for improvement, ask me or you can open an issue or pull request on the GitHub page.

There is also an official Latex template provided by the doctoral school of the KU Leuven, but it is not very user-friendly and doesn't include the specific styling for the Geography master's program, so I decided to create this one. This official template can be found here: https://people.cs.kuleuven.be/~wannes.meert/adsphd/, you can use this as a reference and to check if the formatting of this template is correct or change it to your liking. 

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) 

---

## Table of Contents
- [Quick Start](#quick-start)
- [Recommended VS Code Extensions](#recommended-vs-code-extensions)
- [Writing & Building Your Document](#writing--building-your-document)
- [Tips & Tricks](#tips--tricks)
- [KU Leuven Styling](#ku-leuven-styling)
- [LaTeX Quick Reference](#latex-quick-reference)
- [Troubleshooting](#troubleshooting)
- [License](#license)
---

## Quick Start

### Prerequisites
Before you can start writing, you have to make sure you have the necessary tools and packages installed. I recommend using a VS code based editor (such as [VS Code](https://code.visualstudio.com/), [VSconium](https://vscodium.com/)...), but you can also use other LaTeX editors or Overleaf. The main reasons why I recommend VS Code based editors are that there exists many useful extensions for Latex and it is very customizable. It also integrates well with Git for version control, you can easily manage your bibliography using Zotero and it also integrates AI quit well which can be really handy for formatting or debugging your LaTeX code (if you use this, make sure you acknowledge this in your thesis). I also included a settings.json file so that is should work in vs code as intended without to much hassle. For this guide I will focus on the VS Code setup, but I will also provide instructions for other editors (such as TeXstudio) and Overleaf.

So before you start, make sure you have the following installed:
- **LaTeX Distribution**: [MiKTeX](https://miktex.org/) (Windows) or [TeX Live](https://www.tug.org/texlive/) (Linux/Mac)
- **LaTeX Packages**: Ensure essential packages are installed in your TeX distribution (most are included in full installations, but make sure you check this before compiling!): `geometry`, `graphicx`, `xcolor`, `tikz`, `titlesec`, `fancyhdr`, `setspace`, `helvet`, `apacite`, `amsmath`, `array`, `subcaption`, `float`, `hyperref`, `booktabs`, `longtable`, `etoolbox`, `ifthen`, and `fontenc`.
- **Perl**: Required by latexmk. [Strawberry Perl](http://strawberryperl.com/) (Windows). On macOS and Linux, Perl is normally pre-installed (if not, install via your package manager, e.g., `sudo apt install perl` or `brew install perl`).
- **VS Code based editor** (you can also use other LaTeX editors): With [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension, below I added a list of other recommended extensions to enhance your LaTeX writing experience in VS Code.

### Installing This Template

#### Option 1: Use GitHub Template (Best Choice)
If you have a GitHub account, simply click the green [Use this template](https://github.com/new?template_name=Latex-template-Thesis&template_owner=JonasBil) button at the top right of the repository page. This creates a fresh repository under your own account. You can clone the repository to your local machine using Git open it directly in VS Code with the GitHub extension and start editing.

#### Option 2: Clone from the repository
For this you have to have [Git](https://git-scm.com/install/) installed. This can be done in the VS Code's terminal itself or any terminal of your choice:
```bash
# Clone this repository in a new folder called "my-project"
git clone https://github.com/JonasBil/Latex-template-Thesis.git my-project
cd my-project

```
Change `my-project` to whatever you want to name your project folder, if you want it in the folder itself you can change it to `.` so then you get:
```bash
# Clone this repository into the current folder
git clone https://github.com/JonasBil/Latex-template-Thesis.git .
```

#### Option 3: Manual Download
[Download the repository](https://github.com/JonasBil/Latex-template-Thesis/archive/main.zip) as a ZIP file, then extract the contents to your desired location and compile `main.tex` using the run button in vs code, or compile manually (see instructions below).


#### Option 4: Using Overleaf

1. Click the green **Code** button at the top of this [GitHub repository](https://github.com/JonasBil/Latex-template-Thesis) and select **Download ZIP**.
2. Go to [Overleaf](https://www.overleaf.com/) and click **New Project** $\rightarrow$ **Upload Project**.
3. Select the `.zip` file you downloaded.
4. Overleaf will automatically detect `main.tex` and compile your document. Both `pdfLaTeX` and `XeLaTeX` compilers will work correctly..

#### Option 5: Other LaTeX Editors (e.g., Texifier, TeXstudio, TeXShop)
I haven't tested this very well, but it should work fine as long as you set the main file to `main.tex` and ensure that your build sequence includes a BibTeX backend for the bibliography. The exact steps may vary depending on your editor, but generally:

1. Clone or download the repository to your local machine.
2. Open `main.tex` in your preferred editor.
3. Depending on your editor:
   - **Texifier / TeXstudio**: They will usually auto-detect your `main.tex` and let you build right away. Just make sure the build sequence runs a BibTeX backend (like Biber or standard BibTeX) along with `pdflatex` or `xelatex`.
   - **Build Configurations**: you can map the editor's build sequence to use the equivalent of `latexmk -pdf` to ensure both cross-references and bibliographies compile successfully.

---

## Recommended VS Code Extensions

The following extensions are recommended for a smooth LaTeX workflow in VS Code (In VS code you can create a new [**VS-code profile**](https://code.visualstudio.com/docs/editor/profiles) with these plugins, i really recommend doing this so you can easily switch between your LaTeX writing environment and your normal coding environment and this keeps everything organized):

- **[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)** — The core extension for LaTeX in VS Code. Provides one-click PDF compilation (using the **green run** button or `Ctrl+Alt+B`), real-time error highlighting, SyncTeX support (click in the PDF to jump to the source and vice versa), auto-completion for `\cite{}`, `\ref{}`, and LaTeX commands, and a built-in PDF viewer. This template's `.vscode/settings.json` is pre-configured for it and should not be deleted!.
- **[LTeX](https://marketplace.visualstudio.com/items?itemName=valentjn.vscode-ltex)** — Grammar and spell checking powered by LanguageTool. Works directly in `.tex` files and understands LaTeX syntax, so it won't flag commands as spelling errors. Supports multiple languages.
- **[LaTeX Utilities](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities)** — Adds quality-of-life features on top of LaTeX Workshop: live snippet previews (if you hover over f.e a image or equation snippet, you will see a preview), magic comments, and formatted paste (e.g., pasting a table from Excel auto-generates a `tabular` environment).
- **[Zotero LaTeX](https://marketplace.visualstudio.com/items?itemName=bnavetta.zoterolatex)** — Enables cite-as-you-write by searching your Zotero library directly from VS Code and inserting `\cite{}` keys, this is also included in the LateX Utilities extension but if you don't want to install the ultities extension you can just install this one for the Zotero integration. 

To install these extensions you can search them in the VS Code Extensions Marketplace or run the following commands in the terminal:
```bash
code --install-extension James-Yu.latex-workshop
code --install-extension valentjn.vscode-ltex
code --install-extension tecosaur.latex-utilities
code --install-extension bnavetta.zoterolatex
```

---

## Writing & Building Your Document
When everything is installed and set up, you can start writing your document by editing the `main.tex` file and the **section files** in the `sections/` folder. The template is structured to keep your content organized and modular, so you can focus on writing without worrying about formatting. The `main.tex` file serves as the **main entry point** and includes the preamble, title page setup, and the structure of your document. The **actual content** of each section is stored in separate `.tex` files within the `sections/` folder, which are included in `main.tex` using `\input{}` commands. If you want to add more sections, simply create a new `.tex` file in the `sections/` folder and include it in `main.tex` as the other sections. When compiling (or building) the document, the **resulting pdf** is generated together with the other output files in a `build/` folder (**this is created the first time you build the document**). Below is a step-by-step guide to get you started:

### 1. Update Document Information

Edit the preamble, title, and author information directly in `main.tex`:

```latex
%! author = Your Name
%! date = DD/MM/YYYY

\thesistitle{Your Thesis Title}
\thesissubtitle{Optional Subtitle}
\thesisauthor{Your Name}
\thesispromotor[Affiliation optional]{Prof.\ dr.\ Promotor Name}
\thesiscopromotor[Affiliation optional]{Prof.\ dr.\ Co-Promotor Name}
% \thesismentor[Affiliation optional]{Mentor Name}
\academicyear{2025--2026}
\copyrightinstitution{both} % Set to 'kul', 'vub', or 'both'
% \thesiscoverimage{images/cover} % optional cover image (max 10cm height)
```

**Customizing Metadata (Custom Commands)**
The template defines a custom style found in `styles/kuleuven-thesis.sty` that provides various commands to quickly format the official title page layout matching the KU Leuven Geography requirements.

Title Page Commands (use in `main.tex`):
- `\thesistitle{Title}`: The main title of your thesis.
- `\thesisauthor{Name}`: Your full name.
- `\thesispromotor[Affil]{Name}`: List your primary supervisor/promotor.
- `\academicyear{YYYY--YYYY}`: The academic year (e.g., `2025--2026`).
- `\thesisfacultykul{Name}`: Name of your KUL faculty.
- `\thesisfacultyvub{Name}`: Name of your VUB faculty.
- `\thesisdegree{Degree}`: The exact degree name you are pursuing.
- `\copyrightinstitution{institution}`: Choose between `kul`, `vub`, or `both` for the copyright information.
- `\thesiscoverimage{path/to/image}`: you can add an optional cover image (max height 10cm, adjust path as needed).

If you **add a cover image**, it will be placed on the title page according to the KU Leuven guidelines. Make sure to use a high-resolution image and adjust the path correctly (for example, if you put your image in the `images/` folder, the path would be `images/cover`). The template will automatically scale it to fit within the allowed dimensions. Sometimes things shift around when you add a cover image, so you might have to adjust the vertical spacing of the title page elements. You can do this by changing the `\vspace{}` values in the style file (`styles/kuleuven-thesis.sty`) under the `\maketitle` definition.

The official KU Leuven logos (and VUB equivalent) are automatically included and can be found/changed in the `styles/Style_assets` folder.

**Copyright Information and Disclaimer**
The `\copyrightinstitution{}` command allows you to specify the institution(s) that hold the copyright for your thesis. You can choose between: both, kul, or vub. This will automatically format the copyright notice on the first page.

If you are on the KU leuven program, this is mandatory, for the VUB I didn't find any specific guidelines about this, so I would recommend checking with your supervisor or the VUB guidelines to see if you need to include this and if so, which institution you should list. You can change the text of the copyright notice in the style file (`styles/kuleuven-thesis.sty`) if needed, but it should be correct for the KU Leuven program. 

The same is for the disclaimer, if you are in the KU Leuven program, you have to include the disclaimer, for the VUB I didn't find any specific guidelines, you can again change this disclaimer in the style file (`styles/kuleuven-thesis.sty`). 

### 2. Edit Section Files

Write your content in the separate section files located in the `sections/` folder, the sections that start with 00 are the front matter sections typically found before the main content and displayed with Roman numerals. The template includes some common sections to get you started, but you can modify them as needed. Here is a brief overview of the included section files:

- **`00-preface.tex`**: Foreword, general goals, and acknowledgments
- **`00-contribution.tex`**: Describe your own contribution and support received from others
- **`00-abstract-en.tex`**: English abstract (key objectives and conclusions)
- **`00-abstract-nl.tex`**: Dutch "Samenvatting" (if you're in the Dutch program, you have to add a Dutch version of the abstract here)
- **`00-abbreviations.tex`**: List of abbreviations used in your thesis
- **`01-introduction.tex`**: Introduction, background, and research questions
- **`02-methods.tex`**: Methodology, data, and analysis
- **`03-results.tex`**: Findings and outcomes
- **`04-discussion.tex`**: Interpretation, limitations, and implications
- **`05-conclusion.tex`**: Summary, key takeaways, and future work
- **`06-appendix.tex`**: Additional supplementary material

These files are automatically included in `main.tex` via:
```latex
\input{sections/01-introduction}
\input{sections/02-methods}
% ... etc
```
If you want to add more sections, simply create a new `.tex` file in the `sections/` folder and include it in `main.tex` as shown in the tex file. **Always make sure to keep the line `% !TeX root = ../main.tex` at the top** of each section file so that LaTeX Workshop knows which file is the main document for features like SyncTeX and also **ensure that their is a line `% File: sections/XX-sectionname.tex` at the top** of each section file and the name that maches the section such as `% Conclusion section` for the conclusion section. 

### 3. Add References
To manage your bibliography, you can use the `bib/main.bib` file. This is a **BibTeX file** where you can add all your references in the standard BibTeX format. Each entry should have a unique citation key that you will use to cite it in your document. You can do this manually by writing (or copying) the BibTeX entries yourself, or you can automate the process using a reference manager like Zotero, which can export your library directly to a `.bib` file and keep it updated automatically.

#### Manual BibTeX Entry
Open `bib/main.bib` and add your references in the following format:

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

#### Automating Your Bibliography with Zotero + Better BibTeX

[Zotero](https://www.zotero.org/) can automatically manage your `.bib` file so you never have to write BibTeX entries by hand, the same method can also be applied when you're using another Latex editor, just make sure to set the export path to your `bib/main.bib` file and enable auto-export. Below are the steps to set this up:

##### **1. Install Zotero and Better BibTeX**

1. Download and install [Zotero](https://www.zotero.org/download/).
2. Install the [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/installation/) plugin — this adds automatic BibTeX/BibLaTeX export and automatic generation of citation keys.
3. Go to Zotero's **Tools → Plugins**, click on the settings icon and **Install from file**, select the downloaded plugin file.
4. Restart Zotero after installing the plugin and make sure the plugin is enabled.

##### **2. Collect References**

Add references to your Zotero library using any of these methods:
- **Browser Connector**: Install the [Zotero Connector](https://www.zotero.org/download/) browser extension, then click the icon on any journal page, Google Scholar result, or arXiv page to save it instantly.
- **DOI/ISBN**: In Zotero, click the magic wand icon and paste a DOI or ISBN — metadata is fetched automatically.
- **Manual entry**: Add items by hand if needed.

##### **3. Set Up Auto-Export to Your `.bib` File**

1. In Zotero, select the collection (folder) you want to export, or select your entire library.
2. Go to **File → Export Library...** (or right-click a collection → **Export Collection...**).
3. Choose **Better BibTeX** as the format.
4. Check **Keep updated** — this enables auto-export so any new references you add are automatically written to the file.
5. Save to `bib/main.bib` in your **LaTeX project folder**.

Now, every time you add or edit a reference in Zotero, it will automatically update `bib/main.bib`. No manual copying needed.

### 4. Cite in Your Document
There are multiple ways to cite your references in your LaTeX document, you can use the standard `\cite{}` command, or you can use the commands provided by the LaTeX Workshop extension, the utilities extension or the zotero extension for easier citation management.

When you want to cite a reference, you have to use the citation key that corresponds to the reference you want to cite. If you are using Zotero with Better BibTeX, each reference will have a unique citation key that is automatically generated based on the author and year (or whatever pattern you set in Better BibTeX settings). You can find this citation key in the "Citation Key" column of your Zotero library. For example, if you have a reference with the citation key `smith2024`, you can cite it in your LaTeX document like this:

```latex
As demonstrated by \cite{smith2024}...

% if you want to display the citation as "Smith (2024) found that..." instead of "(Smith, 2024)":
\citeA{smith2024} found that... 
% if you want to display only the year like "(2024)":
\citeyear{smith2024} found that...

```
If you're typing in VS code, the LaTeX Workshop extension provides auto-completion for citation keys. When you type `\cite{`, a dropdown will appear showing all available citation keys from your `.bib` file, so you can easily select the one you want without having to remember the exact key. But you can also use a citation browser to search and insert a citation, their are 2 browsers you can use:

#### The lateX Workshop Citation Browser
This is the citation browser thats included in the latex workshop extension, you can open it by pressing `Ctrl+Shift+P` and searching for "LaTeX Workshop: Open Citation Browser". This will open a search bar where you can type the name of the author, title, or any keyword from your references, and it will show you a list of matching citation keys from your `.bib` file. You can then select the one you want to  into your document. You can also bind a shortcut to this command for faster access, for example `Alt+I`:
1. Open the Keyboard Shortcuts editor in VS Code (`Ctrl+K Ctrl+S` or go to **File → Preferences → Keyboard Shortcuts**).
2. Search for `latex-workshop.citation` (or "LaTeX Workshop: Open Citation Browser").
3. Double-click the command, press `Alt+I`, and hit **Enter**.
4. Now you can quickly open the citation browser with `Alt+I` and insert citations without leaving your keyboard!
   
This is a quick way to insert citations, but it is not connected to your Zotero Library, so you have to make sure that your `.bib` file is up to date with your Zotero library (which should be the case if you set up auto-export correctly).
Also this methods doesn't automatically add the `\cite{}` command, it just inserts the citation key, so you have to make sure to add the `\cite{}` command around the key yourself.

#### The Zotero LaTeX Extension Citation Browser
With the Zotero LaTeX VS Code extension or LaTeX Utilities extension installed, you can **search your Zotero library directly** and insert a citation key. By default, the extension might use `Alt+Z`, but this conflicts with VS Code's word wrap toggle! 

**To fix this and change the Zotero shortcut to f.e. `Alt+I`**:
1. Open the Keyboard Shortcuts editor in VS Code (`Ctrl+K Ctrl+S` or go to **File → Preferences → Keyboard Shortcuts**).
2. Search for `zotero.cite`.
3. Double-click the command, press `Alt+I`, and hit **Enter**.


### 5. Building Your Document
When you are ready to compile your document and generate the PDF, you can do this directly in VS Code or via the command line.

#### VS Code (Recommended)
1. Open `main.tex` in VS Code
2. Press **`Ctrl+Alt+B`** or click the green **▶** button
3. PDF opens automatically in VS Code

#### Using the Command Line
you can also compile your document manually using the command line with `latexmk`, if you prefer this.

```bash
# Full build with bibliography and SyncTeX
latexmk -synctex=1 -pdf -interaction=nonstopmode -outdir=build main.tex

# Clean build artifacts
latexmk -C -outdir=build

# Continuous preview (recompiles on save)
latexmk -synctex=1 -pdf -pvc -interaction=nonstopmode -outdir=build main.tex
```
---

## Tips & Tricks

**1. Word Wrap:**
When writing long paragraphs of text in LaTeX, it's highly recommended to enable "Word Wrap" so your text doesn't go off the screen. 
- **Shortcut:** Press `Alt+Z` to toggle word wrap exactly where you are.
- **Settings:** You can also enable it permanently by going to Settings (`Ctrl+,`), searching for "Word Wrap", and setting `Editor: Word Wrap` to `on`.


**2. Auto-save:**
When you enable **file → autosave**, the PDF will automatically recompile and update in the viewer amd you don't have to worry about saving your file every time you make a change. 


**3. SyncTeX (Jump between Code & PDF):**
With LaTeX Workshop, you don't have to scroll around to find your place!
- **Code $\rightarrow$ PDF:** Press `Ctrl+Alt+J` anywhere in your code to jump to the corresponding spot in the compiled PDF.
- **PDF $\rightarrow$ Code:** Hold `Ctrl` (or `Cmd` on Mac) and click on any text in the VS Code PDF viewer to immediately jump to the source code line. For this to work, make sure all sections have the line `% !TeX root = ../main.tex` at the top, so LaTeX Workshop knows which file is the main document.


**4. Word count**
The LaTeX Workshop extension also provides a word count feature that displays the number of words in your document. You can see this word count in the status bar at the bottom of VS Code when you have a `.tex` file open. It counts only the actual text content and ignores LaTeX commands, so you get an accurate word count for your writing.
If you want the word count of the whole document, you can see this by opening the main.tex file and looking at the status bar. 


**5. LaTeX-Workshop panel**
The LaTeX Workshop extension has a built-in panel that provides quick access to various handy features, you can find it on the left sidebar (the TeX icon) or open it with `Ctrl+Shift+P` and search for "LaTeX Workshop: Show LaTeX Workshop panel". Some useful features in this panel include:
- **Outline View**: Shows the structure of your document (sections, subsections, etc) and allows you to quickly navigate between them
- **Citations View**: Search and insert citations from your bibliography, you can also check which references are not cited yet
-  **Snippets View**: Browse and insert LaTeX snippets for common structures (figures, tables, math, etc.)
-  **Build View**: Access build commands and view compilation logs
-  **Math Symbols View**: Browse and insert math symbols easily
-  ...

Just explore the panel and see what features you find useful!


**6. Clear Build Files To Fix Errors:**
Sometimes, a LaTeX build fails because corrupted auxiliary files (`.aux`, `.bbl`, etc.) got left behind from a previous bad compile. 
- Open the VS Code Command Palette (`Ctrl+Shift+P`) and run **`LaTeX Workshop: Clean up auxiliary files`**, then build your document again. (The included `latexmk` script already clears most things, but this is a good failsafe).


**7. Hover Previews for Equations & Citations:**
If you hover your mouse over math blocks (like `\begin{equation}`) or references (`\cite{}`, `\ref{}`), LaTeX Workshop will display a pop-up preview of the rendered math equation, the bibliography entry, or the remote figure you are referencing!


**8. Multi-Cursor:**
In VS Code, you can:
- Hold `Alt` and click on multiple places to type in them simultaneously.
- Press `Ctrl+Alt+Up/Down` arrow keys to place cursors across multiple column rows at once (e.g., adding `&` dividers rapidly).

---

## Styling

This template automatically adheres to the [KU Leuven thesis formatting guidelines](https://wet.kuleuven.be/english/mastersthesis/form) provided by the faculty, with customizations that are specific to the Geography master's program. All custom colors and setups can be found in `styles/kuleuven-thesis.sty`.

You can find all the custom styling commands for the title page and other formatting in the `styles/kuleuven-thesis.sty` file, feel free to modify or add new commands as needed to fit your specific requirements.

### Colors

The template exposes official ku leuven colors you can use in text:
```latex
\textcolor{kulblue}{Science blue}           % KV Leuven blue (CMYK)
\textcolor{kulblack}{Standard black}
\textcolor{kulolivegrey}{Olive Grey}
```

### Fonts

The template enforces a Sans-Serif font structure (Helvetica-based), mirroring the standard KU Leuven brand typography (`\familydefault{\sfdefault}`). 

### Logo and styling elements

The KU Leuven and VUB logo header styling is automatically included and placed when invoking `\maketitle`. The logos are located in the `styles/Style_assets` folder, you can replace them with updated versions if needed. 

---

## LaTeX Quick Reference
This is a quick reference for common LaTeX commands and environments that you can use in your document. For more detailed information, check out the [Additional Resources](#additional-resources) section below.

### Document Structure

```latex
\section{Title}              % Main section
\subsection{Subtitle}        % Subsection
\subsubsection{Detail}       % Sub-subsection
```
Tip: If you add a star to the sectioning command (e.g., `\section*{Title}`), it will create an unnumbered section that won't appear in the table of contents.

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
You can also create subfigures using the `subfigure` package, which allows you to place multiple images side by side with individual captions. Make sure to include `\usepackage{subfigure}` in your main.tex preamble if you want to use this feature:

```latex
\begin{figure}[h]
    \centering
    \subfigure[First image]{\includegraphics[width=0.45\textwidth]{figures/image1.png}\label{fig:sub1}}
    \hfill
    \subfigure[Second image]{\includegraphics[width=0.45\textwidth]{figures/image2.png}\label{fig:sub2}}
    \caption{Two subfigures}
    \label{fig:main}
\end{figure}
````

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

l, c, and r in the `tabular` environment specify left, center, and right alignment for the respective columns, respectively. You can also use `p{width}` to create a column with a specific width that allows text wrapping.

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

**Problem**: `File 'styles/kuleuven-thesis.sty' not found`
- **Solution**: Ensure your document is being compiled with `main.tex` as the root and that the `styles` directory is located correctly next to it.

**Problem**: `perl: command not found`
- **Solution**: Install [Strawberry Perl](http://strawberryperl.com/) and restart your terminal

**Problem**: Undefined references
- **Solution**: Compile twice. LaTeX needs two passes to resolve cross-references

**Problem**: Bibliography not showing
- **Solution**: Ensure you have at least one `\cite{}` command in your document and are compiling with biber/bibtex configured properly.

**Problem**: Fonts look wrong
- **Solution**: The template relies on standard serif/sans-serif packages (`helvet`). If they fail, they will fall back to default Computer Modern. Make sure your TeX distribution is fully complete.

---

## Additional Resources

### LaTeX Tutorials
- [Overleaf Documentation](https://www.overleaf.com/learn)
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)
- [The not so short introduction to LaTeX](https://tobi.oetiker.ch/lshort/lshort.pdf)

---

## License

This template is provided as-is and licensed under the [MIT License](LICENSE). This means you are free to use, modify, and distribute it for any purpose, as long as you include the original license and attribution. If you make improvements or fixes, consider contributing back to the repository so others can benefit!

---

