Behavior: დასაშიფრი ტექსტიდან იღებს ასოს და key-ს შესაბამის ასოს უსაბამებს, მაგალითად:
```
Plaintext:    AAAAAAAAAAAAAAAAAAA... -> A A A A A...
Key:          ROBINSONROBINSONROB... -> R O B I N...
```
შემდეგ უმატებს alphabet-ში ამ წყვილების ინდექსებს (reduce) და result სტრინგს უმატებს მიღებულის 26-ზე გაყოფის ნაშთს.

Reverse algorithm: დაშიფრულ ტექსტს ისევ ვაწყვილებ cycle(key)-სთან და დაშიფრულის თითო ასოს alphabet-ში ინდექსს ვაკლებ key-ს თითო ასოს ინდექსს.
ვიმახსორებ მიღებულ ინდექსებს თუ დადებითია პირდაპირ, თუ უარყოფითია ინდექსს + 26 სახით. მიღებული ინდექსების 26-ზე ნაშთით (26 არ შეიძლება იყოს alphabet-ში ინდექსი)
ვიღებ Plaintext-ს.

```python
from itertools import cycle
from functools import reduce

a = 'abcdefghijklmnopqrstuvwxyz'
b = 0x1A

encrypted = "nsbzrlvrtvbucacaj"
key = "ROBINSON"

def encrypt(key, p):
    print ("I'm gonna do some crypting!")
    items = zip(p, cycle(key))
    result = ''

    for item in items:
        total = reduce(lambda u, v: a.index(u) + a.index(v), item)
        result += a[total % b]
    print (result.lower())

def decrypt(encrypted, key):
    s = []
    mapped = zip(encrypted, cycle(key))
    for each in mapped:
        s.append(reduce(lambda i, j: a.index(i) - a.index(j), each))
    
    temp = []
    for each in s:
        temp.append(each if each > 0 else each + 26)
    
    tiempo = ''
    for each in temp:
        tiempo += a[each%26]
    print(tiempo)

decrypt(encrypted, key.lower())
```
Flag: wearethechampions
