# スライスについて
Pythonではリストに対して、
```
sliced = list[2:5:-1]
```
みたいな書き方で操作ができるようだ。  

これはPythonではリストとかの、"順番のある配列"で可能なスライスという操作らしい。  
C#でいうIEnumerableみたいな順番が保証されていないコレクションではできないということだろうと思う。  

文字通り配列を指定したインデックスで「切り取る」ことができるようだ。
```
[start : stop : step]
```
という書き方で、startは最初の要素のインデックス、stopは最後の要素のインデックス、stepは何個毎に切り取るかを表している。

stopより後ろは省略することができるようなので、
```
[start : stop]
```
という書き方もできる。  
startとstopも省略でき、
```
[: stop]
```
とか、
```
[start :]
```
みたいな書き方もできる。