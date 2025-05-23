# vtrans
[![GitHub
license](https://img.shields.io/github/license/mashape/apistatus.svg)](http://opensource.org/licenses/MIT)
[![PyPI
version](https://badge.fury.io/py/googletrans.svg)](https://pypi.org/project/vtrans/)

**vtrans** is a **self-updating**, **free**, and **unlimited** language
translating library. It works with the
[googletrans](https://pypi.org/project/googletrans2/) library.

Wait, but this is not like googletrans.
googletrans can't update its languages, so you can only
use limited languages. However, **vtrans** is different. It
updates itself every time you import it.

# Features

## Different from googletrans

-   update it self
-   You can use exatra langauges like sansrit,bhojpuri ect\...\.... .
-   but googletrans have not this languages
-   When the google update their google translator it automatically
    update it self
-   you can use extra languages compare to other translating library
-   what langauges are avaiable in google translator,you can use all the
    languages by this library

## Similarities with googletrans

-   Fast and reliable: It uses the same servers as
    translate.google.com.
-   Auto language detection
-   Bulk translations
-   HTTP/2 support
-   Similar structure

# How it works

vtrans is essentially a language-updatable version of
googletrans. It modifies the LANGUAGES
dictionary in constants.py of googletrans by
scraping the table from [google translator supported
langauges](https://cloud.google.com/translate/docs/languages). It
retrieves the values from the table and creates a new dictionary, which
replaces the existing LANGUAGES dictionary.

# Installing

To install the vtrans package, use the following command:

``` bash
$ pip install vtrans
```

# How to use this library (simple)

``` python
from vtrans import Translator

translator = Translator()
output = translator.translate("This library can translate languages", "ta")
```

# Find available languages

To find what languages are available in vtrans:

``` python
import vtrans

langs = vtrans.LANGUAGES
print(langs)  # It will give you a dictionary

# To find the number of available languages
print(len(langs))
```

# First importing of vtrans

If you import this library for the first time, it will take some time to
complete the configurations. It changes the LANGUAGES
variable in constants.py of googletrans to
match the current version of Google Translator. The first import will
display the following:

``` python
import vtrans

# Setup config file
# Checking for updates (auto-updating). If you want to stop auto-updating, use this code: `vtrans.config(auto_updating=False)`
# Please wait for a few seconds, the update is in progress...
# Update finished. Now you can use extra languages.
# Ready to translate
```

Once you have imported vtrans for the first time, you do
not need to use auto-updating. Auto-updating slows down the library, as
it searches for updates whenever you import vtrans.
Enabling or disabling auto-updating is based on your needs and choice.

# How to disable auto-update

If you want to disable auto-updating:

``` python
import vtrans

vtrans.config(auto_updating=False)
```

Now vtrans will not update whenever you import it.

# How to update manually

If you want to update manually, make sure you have disabled
auto-updating:

``` python
import vtrans

vtrans.update()
```

Now the languages are updated manually.

# How to disable unwanted printing

Whenever vtrans is initialized and ready to translate, it
prints \"Ready to translate\". If you want to disable this:

``` python
import vtrans

vtrans.remove_unwanted_printing()
```

You don\'t need to do this every time. Once you have changed the value,
it will make changes in the config.txt file.

# HTTP/2 support

This library uses httpx for HTTP requests, so HTTP/2 is
supported by default. You can check if HTTP/2 is enabled and working by
accessing the .\_response.http_version attribute of the
Translated or Detected object:

``` python
from vtrans import Translator
translator = Translator()
translator.translate('테스트')._response.http_version
# 'HTTP/2'
```

Basic Usage ==========

If the source language is not given, Google Translate attempts to detect
the source language.

``` python
from vtrans import Translator

translator = Translator()
translator.translate('안녕하세요.')
# <Translated src=ko dest=en text=Good evening. pronunciation=Good evening.>
translator.translate('안녕하세요.', dest='ja')
# <Translated src=ko dest=ja text=こんにちは。 pronunciation=Kon'nichiwa.>
translator.translate('veritas lux mea', src='la')
# <Translated src=la dest=en text=The truth is my light pronunciation=The truth is my light>
```

# Customize service URL

You can use a different Google Translate domain for translation. If
multiple URLs are provided, it randomly chooses a domain.

``` python
from vtrans import Translator

translator = Translator(service_urls=[
    'translate.google.com',
    'translate.google.co.kr',
])
```

# Advanced Usage (Bulk)

Arrays can be used to translate a batch of strings in a single method
call and a single HTTP session. The same method shown above also works
for arrays.

``` python
translations = translator.translate(['The quick brown fox', 'jumps over', 'the lazy dog'], dest='ko')
for translation in translations:
    print(translation.origin, ' -> ', translation.text)
# The quick brown fox  ->  빠른 갈색 여우
# jumps over  ->  이상 점프
# the lazy dog  ->  게으른 개
```

# Language detection

The detect method identifies the language used in a given
sentence.

``` python
from vtrans import Translator

translator = Translator()
translator.detect('이 문장은 한글로 쓰여졌습니다.')
# <Detected lang=ko confidence=0.27041003>
translator.detect('この文章は日本語で書かれました。')
# <Detected lang=ja confidence=0.64889508>
translator.detect('This sentence is written in English.')
# <Detected lang=en confidence=0.22348526>
translator.detect('Tiu frazo estas skribita en Esperanto.')
# <Detected lang=eo confidence=0.10538048>
```

# Note on library usage

DISCLAIMER: Yes, I am aware that most of the functions are similar to
googletrans because I worked with the base of
googletrans. However, vtrans can update its
languages, allowing you to use more languages. This is an unofficial
library that uses the web API of translate.google.com and is not
associated with Google.

-   The maximum character limit on a single text is 15k.
-   Due to limitations of the web version of Google Translate, this API
    does not guarantee stability at all times. Please use this library
    if you don\'t require stability.
-   If you encounter HTTP 5xx errors or errors like #6, it is likely
    because Google has banned your client IP address.

# License

Googletrans is licensed under the MIT License. The terms are as follows:

Copyright 2023 S.Vigneswaran

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be included
in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS
OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
