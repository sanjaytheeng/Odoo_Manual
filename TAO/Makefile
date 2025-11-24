# LaTeX TAOation Makefile
# Usage:
#   make        - compile TAOation to PDF
#   make clean  - remove generated files
#   make view   - compile and open the PDF

# Compiler
LATEX = pdflatex
BIBTEX = bibtex

# Main TAO name (without .tex extension)
TAO = TAO

# Output directory
OUTPUT_DIR = build

# Source files
TEX_SOURCES = $(wildcard *.tex)
BIB_SOURCES = $(wildcard *.bib)
STY_SOURCES = $(wildcard *.sty)
CLS_SOURCES = $(wildcard *.cls)

# Generated files
PDF = $(TAO).pdf
AUX = $(TAO).aux
LOG = $(TAO).log
OUT = $(TAO).out
TOC = $(TAO).toc
LOT = $(TAO).lot
LOF = $(TAO).lof
NAV = $(TAO).nav
SNM = $(TAO).snm
BLG = $(TAO).blg
BBL = $(TAO).bbl

# Default target
all: $(PDF)

# Main PDF compilation
$(PDF): $(TEX_SOURCES) $(BIB_SOURCES) $(STY_SOURCES) $(CLS_SOURCES)
	@echo "Compiling LaTeX TAO..."
	$(LATEX) -interaction=nonstopmode $(TAO).tex
	@if [ -f $(TAO).bbl ]; then \
		echo "Running BibTeX..."; \
		$(BIBTEX) $(TAO); \
		$(LATEX) -interaction=nonstopmode $(TAO).tex; \
	fi
	$(LATEX) -interaction=nonstopmode $(TAO).tex
	@echo "Compilation complete: $(PDF)"

# Clean up generated files
clean:
	@echo "Cleaning generated files..."
	rm -f *.aux *.log *.out *.toc *.lot *.lof *.nav *.snm *.blg *.bbl
	rm -f $(PDF)
	@echo "Clean complete"

# View the PDF (macOS specific)
view: $(PDF)
	@echo "Opening PDF..."
	open $(PDF)

# Install LaTeX dependencies (macOS specific)
install-deps:
	@echo "Installing LaTeX dependencies..."
	@if ! command -v pdflatex >/dev/null 2>&1; then \
		echo "Installing BasicTeX..."; \
		brew install --cask basictex; \
		echo "Please run: sudo tlmgr update --self"; \
		echo "Please run: sudo tlmgr install collection-latexrecommended"; \
	else \
		echo "LaTeX is already installed"; \
	fi

# Help target
help:
	@echo "LaTeX TAOation Makefile"
	@echo ""
	@echo "Available targets:"
	@echo "  make           - Compile TAOation to PDF"
	@echo "  make clean     - Remove all generated files"
	@echo "  make view      - Compile and open the PDF"
	@echo "  make install-deps - Install LaTeX dependencies (macOS)"
	@echo "  make help      - Show this help message"
	@echo ""
	@echo "Requirements:"
	@echo "  - pdflatex (install with: make install-deps)"
	@echo "  - BasicTeX or MacTeX installed"

.PHONY: all clean view install-deps help

# Auto-recompile on changes (macOS with fswatch, Linux with inotifywait)
auto:
	@echo "Watching for changes in .tex, .bib, .sty, .cls..."
	@if command -v fswatch >/dev/null 2>&1; then \
		fswatch -o $(TEX_SOURCES) $(BIB_SOURCES) $(STY_SOURCES) $(CLS_SOURCES) | \
		while read; do \
			clear; \
			echo "Change detected. Recompiling..."; \
			$(MAKE) all; \
		done; \
	elif command -v inotifywait >/dev/null 2>&1; then \
		while inotifywait -e close_write $(TEX_SOURCES) $(BIB_SOURCES) $(STY_SOURCES) $(CLS_SOURCES); do \
			clear; \
			echo "Change detected. Recompiling..."; \
			$(MAKE) all; \
		done; \
	else \
		echo "No file watcher installed. Install fswatch (macOS) or inotify-tools (Linux)."; \
	fi
