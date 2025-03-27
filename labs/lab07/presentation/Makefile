# Укажите необходимые инструменты
PANDOC = pandoc
PDF_ENGINE = pdflatex

# Исходный файл
MD_FILE = presentation.md

# Целевые файлы
DOCX_FILE = presentation.docx
PDF_FILE = presentation.pdf

# Правила для конвертации
all: $(DOCX_FILE) $(PDF_FILE)

$(DOCX_FILE): $(MD_FILE)
	$(PANDOC) $(MD_FILE) -o $(DOCX_FILE)

$(PDF_FILE): $(MD_FILE)
	$(PANDOC) $(MD_FILE) -o $(PDF_FILE) --pdf-engine=$(PDF_ENGINE)

# Очистка
clean:
	rm -f $(DOCX_FILE) $(PDF_FILE)
