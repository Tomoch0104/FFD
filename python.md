# scipy
scipyは高度な科学計算を行うためのライブラリ．<br>
numpyも似たような関数であるが，scipyではnumpyで行える配列や行列の演算を行うことができ，加えてさらに信号処理や統計といった計算ができるようになっている．<br>

scipyを使うにはnumpyが必要である．

## scipy.special.comb()
順列の総数を返す関数．<br>
```python
from scipy.special import comb

print(comb(4, 2))
# 6.0

print(comb(4, 2, exact=True))
# 6

print(comb(4, 0, exact=True))
# 1
```

scipy.special.perm()と同様に，デフォルトは第三関数exact=Falseで，浮動小数点数floatが返される．整数intで取得したい場合はexact=Trueとする必要があるため注意．<br>
第四引数repetitionで重複組み合わせの総数も取得可能．<br>

# numpy

## np.linspace
連番や，等差数列を生成するにはnp.arrange()かnp.linspace()を使う．arange()は間隔（交差）を指定，linspace()は要素数を指定という違いがある．
### 基本的な使い方
np.linspace()も等差数列を生成するが，間隔（交差）ではなく要素数を指定する．<br>

第一引数startに最初の値，第二引数に最後の値，第三引数numに要素数を指定する．それらに応じた間隔（交差）が自動的に算出される．<br>
```python
import numpy as np

print(np.linspace(0, 10, 3))
# [ 0. 5. 10.]

print(np.linspace(0, 10, 4))
# [0.  3.33333333 6.666666667  10.      ]

print(np.linspace(0, 10, 5))
# [0. 2.5  5.  7.5  10. ]
```

start > stopの場合も適切に処理してくれる
```python
print(np.linspace(10, 0, 5))
# [10.  7.5  5.  2.5  0. ]
```

データ型dtypeは自動的に選択されるが，引数dtypeで指定することもできる．
```python
print(np.linspace(0, 10, 3, dtype=int))
# [0  5  10]
```

<br>

## np.round
四捨五入を扱う関数．
任意の桁数で丸めたndarrayを新たに生成したい場合はnp.round()を使う．<br>
np.round()では第一引数に対象となるndarray，第二引数に小数点以下の桁数を指定する．桁数として負の値を使うと整数の桁で丸めることもできる．
```python
import numpy as np

a = np.array([12.3456, 0,123456789])

b = np.round(a, 2)
print(b)
# [12.35, 0.12]

b = np.round(a, -1)
print(b)
# [10. 0.]

b = np.round([1234.56, 123456.789], -2)
print(b)
# [ 1200. 123500.]
```