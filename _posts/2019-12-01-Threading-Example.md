---
layout: post
title: Threading Example
subtitle: Bir network subnetinde threading örneği 
tags: [python, threading]
#image: /img/markdown.jpg
#bigimg: /img/markdown.jpg
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---

```python
import threading
from ping3 import ping
from queue import Queue
from ipaddress import ip_network, ip_address
```


```python
hosts = [str(x) for x in ip_network('192.168.2.0/24').hosts()]
hosts_live = []
```


```python
q = Queue()
for host in hosts:
    q.put(host)
```


```python
def ping_host(host):
    if ping(host, timeout=1):
        return host
```


```python
def worker():
    while True:
        host = q.get()
        if host is None:
            break
        if ping_host(host):
            hosts_live.append(host)
        q.task_done()
        
```


```python
for i in range(64):
    t = threading.Thread(target=worker)
    t.deamon = True
    t.start()

q.join()

for host in hosts_live:
    print(host)
```

    192.168.2.1
    192.168.2.3
    192.168.2.4
    192.168.2.18
    


```python
for host in sorted(hosts_live, key=lambda x: ip_address(x).packed):
    print(host)
```
