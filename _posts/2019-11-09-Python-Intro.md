
 a değişkenine 14 değeri veriliyor. Memoryde 14 değeri ile a nin yeri aynı noktayı işaret ediyor. Bu yüzden id(a) ve id(14) aynı
 değerleri gösteriyor.


```python
a = 14
```


```python
id(a)
```




    1731817344




```python
id(14)
```




    1731817344



a'ya farklı bir değer verildiğinde id tekrar değişiyor.


```python
a = 13

```


```python
id(a)
```




    1731817312



b = a diyerek aslında sadece yerini işaret etmiş oluyoruz. Yani b'de veya a'da yapılan her işlem memory'deki aynı alanı gösterdiği için ikiside değişiyor.


```python
b = a
```


```python
id(b)
```




    1731818048




```python
def foo(x):
    return x ** 2
b = foo(6)

print(b)
```

    36
    


```python
def foo(x):
    return x ** 2
a = foo
```


```python
id(a)
```




    1701770931872




```python
id(foo)
```




    1701770931872




```python
type(foo)
```




    function




```python
foo = 1
```


```python
id(foo)
```




    1731816928




```python
l = [4, 8, 0]
```


```python
id(l)
```




    1701771113992




```python
type(l)
```




    list




```python
t = l
```


```python
id(t)
```




    1701771113992




```python
l is t 
```




    True




```python
l.append('hello')
```


```python
l
```




    [4, 8, 0, 'hello']




```python
t
```




    [4, 8, 0, 'hello']




```python
l.append('utku')
```


```python
id(t)
```




    1701771113992




```python
id(l)
```




    1701771113992




```python
from copy import copy
```


```python
l = [0, 4, 6]
```


```python
l
```




    [0, 4, 6]




```python
t = copy(l)
```


```python
t
```




    [0, 4, 6]




```python
t is l
```




    False




```python
id(t)
```




    1701714789960




```python
id(l)
```




    1701771021000




```python
a = 0b11111111
# a = 0o36
# a = 0x10
```


```python
a
```




    255




```python
type(a)
```




    int




```python
hex(a)
oct(a)
bin(a)
```




    '0b11111111'




```python
s = 'hello utku'
```


```python
print(s)
```

    hello utku
    


```python
s = """hello
utku"""
```


```python
print(s)
```

    hello
    utku
    


```python
s = 'a\nb'
print(s)
```

    a
    b
    


```python
print(len(s))
```

    3
    


```python
s = 'a\\nb'
```


```python
print(len(s))
```

    4
    


```python
print(s)
```

    a\nb
    


```python
s = r'a\nb\nc\nd'
```


```python
print(s)
```

    a\nb\nc\nd
    


```python
print(len(s))
```

    10
    


```python
s1 = 'a\nb\nc\nd'
```


```python
print(len(s1))
```

    7
    


```python
a = [2, 66, 7]
```


```python
a
```




    [2, 66, 7]




```python
a = [None, True, 7, 'hello', 3.4]
```


```python
a
```




    [None, True, 7, 'hello', 3.4]




```python
len(a)
```




    5




```python
print(a[3])
```

    hello
    


```python
a = [None, True, 7, 'hello', 3.4 , [5, 8, 9,]]
```


```python
print(a[5][1])
```

    8
    


```python
a.pop(4)
```




    3.4




```python
a
```




    [None, True, 7, 'hello', [5, 8, 9]]




```python
a.remove('hello')
```


```python
a
```




    [None, True, 7, [5, 8, 9]]




```python
a.insert(4, 200)
```


```python
a
```




    [None, True, 7, [5, 8, 9], 200]




```python
a.insert(2, 5)
```


```python
a
```




    [None, True, 5, 7, [5, 8, 9], 200]




```python
b = ['mina', 'sara']
```


```python
a.extend(b)
```


```python
a
```




    [None, True, 5, 7, [5, 8, 9], 200, 'mina', 'sara']




```python
c = a+b
```


```python
c 
```




    [None, True, 5, 7, [5, 8, 9], 200, 'mina', 'sara', 'mina', 'sara']




```python
names = ['mina', 'sara', 'ali', 'peyman', 'nima']
```


```python
#a.pop()
#a.remove()
#a.append()
#a.insert(4, 100)
#a.extend(b)
#c = a+b

```


```python
#iteration
for foo in names:
    print(foo)

```

    mina
    sara
    ali
    peyman
    nima
    


```python
#iteration
for foo in names:
    print(foo)

```

    mina
    sara
    ali
    peyman
    nima
    


```python
#not a good method
c = 0
while c < len(names):
    x = names[c]
    print(x)
    c +=1
```

    mina
    sara
    ali
    peyman
    nima
    
