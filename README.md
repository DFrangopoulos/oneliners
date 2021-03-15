# oneliners
A compilation of handy oneliners


## PCL Printing (Port 9100)
Convert the PDF to PCL and send to pritner
```bash
cat input.pdf | gs -sDEVICE=pxlmono -q -dNOPAUSE -dPDFFitPage -dBATCH -sPAPERSIZE=a4 -sOutputFile=- - | nc -w1 <printer_ip> 9100
```
## Reducing the size of PDFs
```bash
input=test.pdf ; output=test_out.pdf; ghostscript -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/printer -dNOPAUSE -dQUIET -dBATCH -sOutputFile=/tmp/gs_output.pdf $input && pdf2ps /tmp/gs_output.pdf - | ps2pdf - $output
```
## Adding non-free / contrib sources (Debian)
```bash
sudo sed -i 's/main/main non-free contrib/g' /etc/apt/sources.list
```
## Enabling TearFree mode
```bash
xrandr --output HDMI-A-1 --set "TearFree" on
```
## Flattening a directory tree
```bash
mkdir ~/Desktop/Extracted && find . -type f | xargs -d '\n' cp -t  ~/Desktop/Extracted/
```

## Configuring git for SSH pushes
```bash
git remote set-url origin git@github.com:DFrangopoulos/<repo>.git
```

# cheatsheet
A compilation of randomness

## LUKS Encrypt a Drive
```bash
sudo cryptsetup luksFormat /dev/sd<x>
sudo cryptsetup luksOpen /dev/sd<x> vol1
sudo mkfs.ext4 -L <some_label> /dev/mapper/vol1
sudo cryptsetup luksClose vol1
```


# packages
A list of useful packages

* cryptsetup
* git
* gvfs
