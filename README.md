# oneliners
A compilation of handy oneliners

## Reducing the size of PDFs
```bash
input=test.pdf ; output=test_out.pdf; ghostscript -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile=/tmp/gs_output.pdf $input && pdf2ps /tmp/gs_output.pdf - | ps2pdf - $output
```
Requirements:
- Ghostscript
