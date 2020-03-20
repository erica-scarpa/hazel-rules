# Hazel Rules
Some rules I created for Hazel (http://www.noodlesoft.com/hazel.php)

## Markdown to PDF via pandoc-citeproc (hazel-md-to-pdf.hazelrules)
This rules converts markdown files to PDF via pandoc-citeproc. Drop the file in the folder for which the rule is active and hazel will activate the conversion through a script. Note that you have to modify the script according to your filepaths:
```script
title=$(basename "$1" .md)
/usr/local/bin/pandoc -s --filter=/usr/local/bin/pandoc-citeproc --pdf-engine=/Library/TeX/texbin/xelatex --number-sections --bibliography=/PATH/TO/YOUR/BIBLIOGRAPHY.bib --csl=/PATH/TO/YOUR/CSL.csl -o "$title".pdf "$1"
open "$title".pdf
```
Replace the capitalized filepaths with yours. This scripts will also trigger sections numbering (you can remove it by deleting `--number-sections`). Pandoc and LaTeX need to be installed.
This script has been inspired by [this post](https://raphaelkabo.com/blog/posts/markdown-to-word/).
