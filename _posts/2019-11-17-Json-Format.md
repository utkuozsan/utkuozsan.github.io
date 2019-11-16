

```python
import json
```


```python
c = open(r"episodes.json").read()
```


```python
type(c)
```




    str




```python
d = json.loads(c)
```


```python
d.keys()
```




    dict_keys(['episodes', 'test'])




```python
episodes = d['episodes']
```


```python
from pprint import pprint
total_characters = []
total_character_n = []
for episode in episodes:
    scenes = episode['scenes']
    for scene in scenes:
        characters = scene['characters']
        for character in characters:
            total_character_n.append(character['name'])
            if character['name'] not in total_characters:
                total_characters.append(character['name'])
pprint(total_character_n)
pprint(len(total_characters))
```

    ['Gared',
     'Waymar Royce',
     'Will',
     'Gared',
     'Waymar Royce',
     'Will',
     'Will',
     'Wight Wildling Girl',
     'Will',
     '...'   
    555
    


```python
dict_of_elems = {}
for elem in total_character_n:
    if elem in dict_of_elems:
        dict_of_elems[elem] +=1
    else:
        dict_of_elems[elem] = 1
#pprint(dict_of_elems)

inverse = [(value, key) for key, value in dict_of_elems.items()]
#pprint(inverse)

#print(max(inverse)[1])

pprint(sorted(inverse, reverse = True))

```

    [(442, 'Jon Snow'),
     (392, 'Tyrion Lannister'),
     (320, 'Daenerys Targaryen'),
     (286, 'Cersei Lannister'),
     (281, 'Sansa Stark'),
     (259, 'Arya Stark'),
     (247, 'Jaime Lannister'),
     (210, 'Jorah Mormont'),
     (188, 'Bran Stark'),
     (173, 'Davos Seaworth'),
     (168, 'Samwell Tarly'),
     (161, 'Tormund Giantsbane'),
     (158, 'Theon Greyjoy'),
     (156, 'Sandor Clegane'),
     (145, 'Missandei'),
     (..., '...')]
    


```python
players = []
for item in d['episodes']:
    for item2 in item['scenes']:
        for item3 in item2['characters']:
            players.append(item3['name'])

final_list = {}

for item4 in players:
    final_list[item4] = 1
print(final_list)
            
```

```python
characters = []
for episode in json.loads(open(r"d:\directory_location\episodes.json").read())['episodes']:
    for scene in episode['scenes']:
        for character in scene['characters']:
            if character['name'] not in characters:
                characters.append(character['name'])
                
len(characters)
```




    555




```python
l = [
    ('sara',10),
    ('mustafa', 20),
    ('mina', 23),
    ('ali', 45),
    ('nima', 9),
    ('peyman', 0),
    
]

def hello(x):
    return len(x[0])

```


```python
new = sorted(l, key=hello)
print(new)
```

    [('ali', 45), ('sara', 10), ('mina', 23), ('nima', 9), ('peyman', 0), ('mustafa', 20)]
    


```python
def foo(x):
    print ('*', end='')
    return (x[1])

```


```python
new = sorted(l, key=foo, reverse = True)
print(new)
```

    ******[('ali', 45), ('mina', 23), ('mustafa', 20), ('sara', 10), ('nima', 9), ('peyman', 0)]
    
