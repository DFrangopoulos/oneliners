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

## Check IOMMU Groups
```bash
#!/bin/bash
shopt -s nullglob
for g in /sys/kernel/iommu_groups/*; do
    echo "IOMMU Group ${g##*/}:"
    for d in $g/devices/*; do
        echo -e "\t$(lspci -nns ${d##*/})"
    done;
done;
```
## Export Mdadm config
```bash
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

# packages
A list of useful packages

* cryptsetup -> LUKS
* git 
* gvfs
* omxplayer -> can play media directly to framebuffer
* sqlitebrowser
* bmon
* filezilla
* wireshark
* qdristat
* virt-manager
* mdadm

# ressources

* https://www.frederickding.com/posts/2017/08/luks-encrypted-dvd-bd-data-disc-guide-273316/
