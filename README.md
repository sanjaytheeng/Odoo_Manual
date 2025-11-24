# LaTeX Odoo Project Documentation

This project contains multiple modules of documentation written in LaTeX. Each main folder corresponds to an independent module with its own LaTeX source and build instructions.

## Project Structure

- `Accounting/`  
- `Accounting final/`  
- `Administrative Management/`  
- `Business Simulation/`  
- `TAO/`  

Each of these directories contains LaTeX source files for their respective documentation along with a Makefile for building the PDF and a README.md with detailed instructions.

---

## Prerequisites

To build any of the documentation modules, you need:

- A LaTeX distribution installed on your system (e.g., TeX Live, MacTeX, BasicTeX)
- The `pdflatex` command available in your system PATH

---

## Building Documentation

Navigate to the respective directory and run:

```bash
make
```

This will compile the main `.tex` file and generate a PDF in that directory.

To clean generated files:

```bash
make clean
```

To auto-compile upon changes:

```bash
make auto
```

To view the PDF immediately (macOS only):

```bash
make view
```

---

## Installing LaTeX Dependencies (macOS)

If you do not have LaTeX installed, you can install BasicTeX using Homebrew:

```bash
make install-deps
```

After installation, update the TeX Live manager and install recommended packages:

```bash
sudo tlmgr update --self
sudo tlmgr install collection-latexrecommended
```

---

## Editing Documentation

Edit the main `.tex` file in each respective directory to modify the documentation content. You can use any LaTeX editor or a plain text editor.

---

## Detailed Instructions per Module

Please refer to the README.md file inside each folder for detailed and module-specific instructions:

- [Accounting/README.md](Accounting/README.md)  
- [Accounting final/README.md](Accounting final/README.md)  
- [Administrative Management/README.md](Administrative Management/README.md)  
- [Business Simulation/README.md](Business Simulation/README.md)  
- [TAO/README.md](TAO/README.md)  

---

## Additional Resources

- [LaTeX Project](https://www.latex-project.org/)  
- [Overleaf Online Editor](https://www.overleaf.com/)  
- [LaTeX Wikibook](https://en.wikibooks.org/wiki/LaTeX)  

---

## Recommended VSCode Extensions for LaTeX

- [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)  
- [LaTeX Snippets](https://marketplace.visualstudio.com/items?itemName=JeffersonQin.latex-snippets-jeff)  
- [LaTeX](https://marketplace.visualstudio.com/items?itemName=mathematic.vscode-latex)  
- [LaTeX Utilities](https://marketplace.visualstudio.com/items?itemName=tecosaur.latex-utilities)

---
