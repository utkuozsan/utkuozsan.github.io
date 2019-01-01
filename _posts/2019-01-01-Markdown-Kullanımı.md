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

# 5. Images  
Resimleri yüklemek için ise 2 yöntemimiz var. Aynı link eklemede olduğu gibi resimleri de link ve referans vererek ekleyebiliyoruz.  
 1. Link vererek resim eklemek  
   \!\[Text for image\]\(Link to a image\) Burada "!" önemli bunu yapmazsak resimler görüntülenmiyor.  
   ![Crepe](https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg)
 2. Referans vererek resim eklemek  
   \!\[Text for image\]\[reference-name\]  
   \[reference-name\]: address    
   ![Crepe][Photo-1]  
   
   [Photo-1]:https://s3-media3.fl.yelpcdn.com/bphoto/cQ1Yoa75m2yUFFbY2xwuqw/348s.jpg
   
# 6. Blockquotos  
  Deyimleri ve sözleri özel ayrı bir formatta görüntülememize yarıyor."" ile biten sözlerin başına > işaretini koyuyuyoruz.
  >"Simplicity is the ultimate sophistication."
  
  >“I'm selfish, impatient and a little insecure. I make mistakes, I am out of control and at times hard to handle. But if you can't handle me at my worst, then you sure as hell don't deserve me at my best.” 
― Marilyn Monroe

# 7. Lists  
Listleri iki formatta kullanabiliyoruz. Unordered ve ordered şekilde.  
1. Unordered kullndığımız durumda "\*" işaretini her bir maddenin başına ekliyoruz.  
 * Item 1
    * Subitem 1
    * Subitem 2
 * Item 2 
 * Item 3  
2. Ordered kullandığımız durumda  
    1. Order1
    2. Order2
    3. Order3
 
# 8. Paragraphs  
Insert new line yapmazsak paragrafları birbirinden ayıramıyoruz.Yani **hard break**.  
Bir alt satıra geçip yazdığımız zamanki görünümü sağlayabilmemiz için 2 boşluk bırakıyoruz.Buna da **soft break** deniyor.

# 9. Diğer Faydalı Kullanımlar  
Burada kodları paylaşırken ve yorum satırları eklenirken kullanılabilicek formatlar bulunmaktadır.  

Here's a useless table:

| Number | Next number | Previous number |
| :------ |:--- | :--- |
| Five | Six | Four |
| Ten | Eleven | Nine |
| Seven | Eight | Six |
| Two | Three | One |

Here's a code chunk:

~~~
var foo = function(x) {
  return(x + 5);
}
foo(3)
~~~

And here is the same code with syntax highlighting:

```javascript
var foo = function(x) {
  return(x + 5);
}
foo(3)
```

And here is the same code yet again but with line numbers:

{% highlight javascript linenos %}
var foo = function(x) {
  return(x + 5);
}
foo(3)
{% endhighlight %}

## Boxes
You can add notification, warning and error boxes like this:

### Notification

{: .box-note}
**Note:** This is a notification box.

### Warning

{: .box-warning}
**Warning:** This is a warning box.

### Error

{: .box-error}
**Error:** This is an error box.


