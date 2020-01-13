---
layout: post
title: Global and Local Variable
subtitle: 
tags: [python, variable]
#image: /img/markdown.jpg
#bigimg: /img/markdown.jpg
#gh-repo: daattali/beautiful-jekyll
#gh-badge: [star, fork, follow]
comments: true
---

```python
a = 1

# Uses global because there is no local 'a' 
def f(): 
	print 'Inside f() : ', a 

# Variable 'a' is redefined as a local 
def g():	 
	a = 2
	print 'Inside g() : ',a 

# Uses global keyword to modify global 'a' 
def h():	 
	global a 
	a = 3
	print 'Inside h() : ',a 

# Global scope 
print 'global : ',a 
f() 
print 'global : ',a 
g() 
print 'global : ',a 
h() 
print 'global : ',a 
```
Output:

global :  1
Inside f() :  1
global :  1
Inside g() :  2
global :  1
Inside h() :  3
global :  3


Ref: https://www.geeksforgeeks.org/global-local-variables-python/


