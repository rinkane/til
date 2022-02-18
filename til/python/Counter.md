# Counterの使い方について
collectionsという標準ライブラリにCounterというのがあり、  
これを使うとある要素(キー)とその要素の出現回数(バリュー)の辞書型クラスCounterが取得できるらしい。  

これを使うと、
```
cnt = {}
for l in list:
    if l in cnt:
        cnt += 1
    else:
        cnt[l] = 1
```
みたいなのが、
```
from collections import Counter

cnt = Counter(list)
```
だけで済む。
***
## 出現回数順にソート
### 降順
```
cnt = Counter(list).most_common()
```
とすると、出現回数が多い順にソートされたものが取得できる。  
これに対して
```
cnt[0]
```
で最も出現回数が多いものが、
```
cnt[-1]
```
で最も出現回数が少ないものが取得できる。  

これはPythonの言語仕様で、インデックスに-(マイナス)を指定すると末尾から何番目かの要素を取得できるかららしい。
### 昇順
```
cnt = Counter(list).most_common()[::-1]
```
とすると、出現回数が少ない順にソートされたものが取得できる。