# oneliners
A compilation of handy oneliners


## PCL Printing (Port 9100)
Convert the PDF to PCL.
```bash
cat input.pdf | gs -sDEVICE=pxlmono -q -dNOPAUSE -dPDFFitPage -dBATCH -sPAPERSIZE=a4 -sOutputFile=- -> output.pcl
```
Send to printer.
```bash
cat output.pcl | nc -w1 <ip> 9100
```
## Reducing the size of PDFs
```bash
input=test.pdf ; output=test_out.pdf; ghostscript -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile=/tmp/gs_output.pdf $input && pdf2ps /tmp/gs_output.pdf - | ps2pdf - $output
```
Requirements:
- Ghostscript

## Adding non-free / contrib sources (Debian)
```bash
sudo sed -i 's/main/main non-free contrib/g' /etc/apt/sources.list
```
## Enabling TearFree mode
```bash
xrandr --output HDMI-A-1 --set "TearFree" on
```
## Extract all files from current directory and subdirectories
```bash
mkdir ~/Desktop/Extracted && find . -type f | xargs -d '\n' cp -t  ~/Desktop/Extracted/
```
