---
layout: post
title: Concurrent Futures Examples
subtitle: 
tags: [python, threading]
#image: /img/markdown.jpg
#bigimg: /img/markdown.jpg
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---

```python
import concurrent.futures
import time
from pprint import pprint
```


```python
start = time.perf_counter()

def power(n, desc1, desc2):
                                                                                                                    
    return f'{desc1} {n}^2 {desc2} = {n*n}' 
```

Concurrent calculation with submit method. In this method the result are given when the thread is finished. It doesn't wait the other threads to finish.


```python
with concurrent.futures.ThreadPoolExecutor() as executor:
    numbers = [5, 4, 3, 2, 1, ]
    
    #You can use multiple parameters like number1, number2 or a string
    results = [executor.submit(power, number, 'Power of a Number', '*****') for number in numbers]
    
    for f in concurrent.futures.as_completed(results):
        print(f.result())
```

    Power of a Number 4^2 ***** = 16
    Power of a Number 5^2 ***** = 25
    Power of a Number 1^2 ***** = 1
    Power of a Number 3^2 ***** = 9
    Power of a Number 2^2 ***** = 4
    

Concurrent with map method, it gives the results in the order they were started.


```python
def power1(n, ):
                                                                                                                    
    return f'{n}^2 = {n*n}' 
```


```python
with concurrent.futures.ThreadPoolExecutor() as executor:

    numbers = [5, 4, 3, 2, 1, ]
    results = executor.map(power1, numbers) 

    for result in results:
        print(result)

```

    5^2 = 25
    4^2 = 16
    3^2 = 9
    2^2 = 4
    1^2 = 1
    


```python
finish = time.perf_counter()

print(f'Finished in {round(finish-start, 2)} second(s)')
```

    Finished in 19.03 second(s)
    


```python

```
