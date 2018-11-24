# https://gist.githubusercontent.com/bertvv/e77e3a5d24d8c2a9bcc4/raw/6dd82e4f459f3d40e536c1c3f59f70262a53f0e8/pandoc.Makefile

# Generate PDFs from the Markdown source files
#
# In order to use this makefile, you need some tools:
# - GNU make
# - Pandoc
# - LuaLaTeX
# - DejaVu Sans fonts

# Directory containing source (Markdown) files
src_dir := ./

# Directory containing pdf files
out_dir := ./

# All markdown files in src/ are considered sources
src := pre.md $(sort $(wildcard $(src_dir)/ch*.md))
out := $(out_dir)/script.pdf

pandoc=pandoc
# solving  No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'file://' is therefore not allowed access.
# with https://stackoverflow.com/questions/25410701/how-do-i-include-meta-tags-in-pandoc-generated-html
pandoc_opts=	-t html5 --standalone -s \
		--wrap=none \
		--variable mainfont="DejaVu Sans" \
		--variable monofont="DejaVu Sans Mono" \
		--variable geometry:"top=1.5cm, bottom=2.5cm, left=1.5cm, right=1.5cm" \
		--variable fontsize=11pt \
		--variable geometry:a4paper \
		-f markdown+hard_line_breaks+lists_without_preceding_blankline
		# --number-sections \
		# --table-of-contents \
		# --wrap=preserve
		# --pdf-engine=lualatex
html2pdf=wkhtmltopdf
html2pdf_opts=--print-media-type --debug-javascript

all: $(out)

# Recipe for converting a Markdown file into PDF using Pandoc
$(out).html: $(src) Makefile
	cat $(src) > $@.md
	$(pandoc) $(pandoc_opts) --katex $@.md -o $@

$(out): $(out_dir)/%.pdf: $(out).html book.css
	$(html2pdf) $(html2pdf_opts) --javascript-delay 2000  $< $@

det3.pdf: %.pdf: det3.md Makefile
	cat det3.md > $@.md
	$(pandoc) $(pandoc_opts) --mathjax $@.md -o $@.html
	$(html2pdf) $(html2pdf_opts) --javascript-delay 5000 $@.html $@

.PHONY : clean

clean:
	rm -f $(output)/*.pdf
