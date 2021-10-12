# Optical Character recognition

## Tesseract

Install tesseract and mlayalam language pack

```
$ apt install tesseract-ocr tesseract-ocr-mal
```

Make sure tesseract is available with Malayalam support

```bash
$ tesseract --list-langs
List of available languages (4):
Malayalam
eng
mal
osd
```

Run OCR on an image. Assuming you have testocr.png as the image file to OCR. The out.txt is your output file

```bash
$ tesseract ~/testocr.png out.txt -l mal
```

The `out.txt` file will have the text recognized from image



## Tesseract OCR in browser

{% embed url="https://ocr.smc.org.in/" %}

![](<../.gitbook/assets/image (44).png>)

## Links

{% embed url="https://github.com/harish2704/pottan-ocr" %}

