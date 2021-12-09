'ი' -> 0
'ა' -> 1

```python
s = 'იაიაიიიიიააიააიიიააიააააიიააიიააიაიიიაიაიიაიიიააიააიაააიიააააიიაიაიიიიააიაააიაიაიიააიაიიიაიიააააიიააიიააიააიიააა'
t = ''

for each in s:
    t += '0' if each =='ი' else '1'

lenka, each = int(len(t)), 8
b = [ t[i:i+each] for i in range(0, lenka, each) ]

for each in b:
    print(chr(int(each, 2)), end='')
```

Output: Plo3E#nyCu4O3g -> ROT13 -> Cyb3R#alPh4B3t

Flag: Cyb3R#alPh4B3t
