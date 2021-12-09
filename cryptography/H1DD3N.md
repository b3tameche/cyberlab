გამოვიყენოთ ორობითის ლოგიკა სურათის სახელზე:

```python
filename = ',..,....,...,,,,,..,,.,.,..,...,,...,,,,,...,.,.,..,,..,,..,,..,'

bytes = ''

for each in filename:
    bytes += '0' if each==',' else '1'

a, b = len(bytes), 8
t = [ bytes[i:i+b] for i in range(0, a, b) ]
for each in t:
    print(chr(int(each, 2)), end='')
```
Output: [openpuff](https://embeddedsw.net/OpenPuff_Steganography_Home.html)

სურათის properties -> comments:
```
# A=WhenAnOrangeTastesLikeAnOnionT
# B=heKnifeTakesTheBlameButWhoHand
# C=edUsTheKnifeShouldBeQuestioned
# Z=33%
```

შევაგდებთ openpuff-ში სურათს და ამ მონაცემებს დავურთავთ, მივიღებთ: onions.txt ფაილს, რომელშიც წერია:
```
fi4uilokg3dfojalaudptap45vy4ynsy3kp47viprpvcwlsz6m7622id
```
Length = 56  
Clues: H1DD3N, onions სურათზე, "onions.txt"  

Google Search: Tor 56 character -> [Result](https://gitlab.torproject.org/legacy/trac/-/wikis/doc/HiddenServiceNames)  
Google Search: v3 onion address -> [Result1](https://gitweb.torproject.org/torspec.git/plain/rend-spec-v3.txt), [Result2](https://www.reddit.com/r/TOR/comments/bn4q72/explanations_of_v3_address/)

მოცემულ მისამართზე onion საიტი ამჟამად გათიშულია, იქ არსებული info: 
```
0x5a, 0x6d, 0x78, 0x68, 0x5a, 0x33, 0x74, 0x49, 0x4d, 0x57, 0x52, 0x6b,
0x4d, 0x30, 0x35, 0x66, 0x4d, 0x47, 0x34, 0x78, 0x54, 0x32, 0x35, 0x66,
0x4e, 0x7a, 0x51, 0x35, 0x4e, 0x44, 0x55, 0x32, 0x4f, 0x48, 0x30, 0x3d, 0x0a
```
Decoding hex + base64:
```python
import base64
a = [0x5a, 0x6d, 0x78, 0x68, 0x5a, 0x33, 0x74, 0x49, 0x4d, 0x57, 0x52, 0x6b, 0x4d, 0x30, 0x35, 0x66, 0x4d, 0x47, 0x34, 0x78, 0x54, 0x32, 0x35, 0x66, 0x4e, 0x7a, 0x51, 0x35, 0x4e, 0x44, 0x55, 0x32, 0x4f, 0x48, 0x30, 0x3d, 0x0a]
data = ''
for each in a:
    data += chr(int(each))
print(base64.b64decode(data))
```
Output:
```
b'flag{H1dd3N_0n1On_7494568}'
```
