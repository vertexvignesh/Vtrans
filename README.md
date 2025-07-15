<div align="center">

# 🌐 vtrans

<p align="center">
  <a href="#"><img src="https://img.shields.io/badge/Made%20With-Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/></a>
  <a href="#"><img src="https://img.shields.io/badge/Type-🔤%20Language%20Translator-orange?style=for-the-badge"/></a>
  <a href="#"><img src="https://img.shields.io/badge/Auto--Update-Enabled-brightgreen?style=for-the-badge&logo=refresh&logoColor=black"/></a>
  <a href="#"><img src="https://img.shields.io/badge/Languages-100%2B-blue?style=for-the-badge&logo=googletranslate&logoColor=white"/></a>
  <a href="#"><img src="https://img.shields.io/badge/PyPI-vtrans-informational?style=for-the-badge&logo=pypi&logoColor=white"/></a>
  <a href="#"><img src="https://img.shields.io/badge/License-MIT-blueviolet?style=for-the-badge"/></a>
  <a href="#"><img src="https://img.shields.io/badge/Status-Active-success?style=for-the-badge&logo=git"/></a>
</p>


</div>

---

## 📌 About

**vtrans** is a **free**, **self-updating**, and **unlimited** language translating library built on top of [googletrans](https://pypi.org/project/googletrans2/). While googletrans gets outdated and stuck with limited languages, **vtrans** stays fresh by auto-updating itself every time you import it 😎

---

## ⚡ Features

### 🔄 Different from googletrans

- 🔥 Auto-updates language list directly from Google Translator's site  
- 🗣️ Supports extra languages like **Sanskrit**, **Bhojpuri**, etc.  
- 🔃 Keeps up with Google’s latest language support  
- 📡 Always fresh, always ready to translate like a beast  

### ✅ Similar to googletrans

- ⚡ Fast and reliable  
- 🌐 Auto language detection  
- 📦 Bulk translations  
- 🚀 HTTP/2 support  
- 🧱 Same familiar structure  

---

## 🛠️ How It Works

vtrans scrapes the latest language list from [Google Translate Supported Languages](https://cloud.google.com/translate/docs/languages) and replaces the old `LANGUAGES` dictionary in `googletrans`'s constants. This way, it's always up to date 💡

---

## 📦 Installation

```bash
pip install vtrans
````

---

## 🧪 Basic Usage

```python
from vtrans import Translator

translator = Translator()
output = translator.translate("This library can translate languages", "ta")
print(output.text)  # ➜ இந்த நூலகம் மொழிகளை மொழிபெயர்க்கக்கூடும்
```

---

## 🔍 Get Available Languages

```python
import vtrans

langs = vtrans.LANGUAGES
print(langs)        # Print the full dictionary
print(len(langs))   # Number of supported languages
```

---

## 🕐 First Import

On first use:

```python
import vtrans
# Setup config file
# Checking for updates...
# Please wait...
# Update finished! 🎉
# Ready to translate
```

---

## 📴 Disable Auto Update

```python
import vtrans
vtrans.config(auto_updating=False)
```

---

## 🔁 Manual Update

```python
import vtrans
vtrans.update()
```

---

## 🙊 Disable “Ready to translate” Message

```python
import vtrans
vtrans.remove_unwanted_printing()
```

> This change is saved permanently in your config file

---

## 📡 HTTP/2 Support

`httpx` is used for requests, so HTTP/2 works out-of-the-box:

```python
from vtrans import Translator

translator = Translator()
print(translator.translate('테스트')._response.http_version)  # ➜ 'HTTP/2'
```

---

## 🧠 Advanced Usage

### Bulk Translation

```python
texts = ['The quick brown fox', 'jumps over', 'the lazy dog']
translations = translator.translate(texts, dest='ko')
for t in translations:
    print(t.origin, '->', t.text)
```

---

## 🔎 Language Detection

```python
from vtrans import Translator

translator = Translator()

print(translator.detect('この文章は日本語で書かれました。'))
# ➜ <Detected lang=ja confidence=0.64>
```

---

## 🌍 Custom Google Domains

```python
translator = Translator(service_urls=[
    'translate.google.com',
    'translate.google.co.kr',
])
```

---

## ⚠️ Notes

* Max characters per translation: **15,000**
* Not officially supported by Google
* Can break if Google blocks your IP (5xx errors)
* Based on googletrans, but enhanced for more power ⚙️

---

## 📄 License

**MIT License** © 2023 **S.Vigneswaran**

Permission is granted, free of charge, to use, copy, modify, distribute, and sell this software with the included license text. No warranty or liability is provided.

---

Made with ❤️ by Vicky (S.Vigneswaran)


