---
layout: post
title: Markdown Kullanımı
---

Merhaba,
  bu dökümanda markdown üzerine aldığım kısa notlardan bahsedeceğim.

# 1. Italik ve Bold yazmak

1. Italik yazmak için "_" kullanıyoruz.  Bunu italik yazmak istediğimiz kelimenin başına ve sonuna ekliyoruz  \_italik\_.  
  Örneğin; "_italik_" 

2. Bold yazmak için ise "**" iki yıldız kullanıyoruz.\*\*bold\*\*.  
Örneğin; "**bold**"

3. Hem bold hem italik yazmak için ise \*\*\_bold and italik_\*\*.  
Örneğin; "**_bold and italik_**"

# 2. Header Kullanımı

\# Number One  
# Number One   
\#\# Number Two
## Number Two
\#\#\# Number Three
### Number Three
\#\#\#\# Number Four
#### Number Four
\#\#\#\#\# Number Five
##### Number Five
\#\#\#\#\#\# Number Six
###### Number Six

Hem header hem de italik istiyorsak ikisini de bir arada kullanabiliyoruz.

## _Denemeler Başlasın_

# 3. Links  
* Köşeli parantezin içine link atacağım kelimeyi, parantez içine de adresi yazıyoruz.  
\[Websitem\]\(http://www.utkuozsan.com\)  
[Websitem](http://www.utkuozsan.com)
* Koyu bir şekilde de yapabiliriz.  
\[\*\*Websitem\*\*\]\(http://www.utkuozsan.com\)  
[**Websitem**](http://www.utkuozsan.com)
* Header içinde de yazabiliyoruz.  
\#\#\#\[Websitem\]\(http://www.utkuozsan.com\)
  ### [Websitem](http://www.utkuozsan.com)

# 4. Reference Link Kullanımı
Yazıyı yazarken link kullanacağımız yerleri [some link ] [ another-link ] arasında belirtiyoruz. Sonrasında dosyanın sonunda referanslı linklerimizi [ another link ] : adres bilgisi olacak şekilde belirtiyoruz.  
Örneğin;  
\[in the text\]\[another-link\]

\[another-link\]:www.google.com

[in the text][another-link]

[another-link]:www.google.com
