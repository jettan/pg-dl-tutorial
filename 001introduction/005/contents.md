<!-- # 1. 学習対象のモデルを定義する (2) -->
# 1. Define the model to be learned (2)
<!-- Chainerでは学習可能なモデルをLinkとよびます。 -->
In Chainer, we call a model which can be learned Link.
<!-- ディープラーニングで利用される代表的なLinkは `chainer.links` でサポートされています。-->
Links which are commonly used in Deep Learning is supported in `chainer.links`.
<!-- また，自分で新しいLinkを作ることもできます。-->
You can generate a new Link by yourself.

<!--以降では，この `chainer.links` を `L` として使えるようにします。-->

For the following, we will use `chainer.links` as `L`.
```
from chainer import links as L
```

<!--もっと基本的なLinkはLinearとよばれるLinkです。-->
The most basic Link is called Linear.
<!--Linearは全ての入力と出力がつながっているようなニューラルネットワークを表します。-->
Linear is a neural network whose inputs and outputs are fully connected.
<!--Linearはニューラルネットワークの文脈では総結合層，数学の用語では線形変換，アフィン変換とよびます。-->
Linear is called fully connected layer in the context of neural network and, linear transformation or affine transformation in the context of math.
<!--たとえば，次の例では5個のユニットから，2個のユニットへの変換を表します。-->
For example, the following code represents the transformation which is from 5 units to 2 units.

```
lin = L.Linear(5, 2)
```

<!--この `lin` はLinkオブジェクトですが，次のように関数呼び出しをすることができます。-->
This `lin` is a Link object and you can do function call as follows:
<!--（この関数呼び出しは `__call__` で定義されており，演算子オーバーロードで実現されています。）-->
(This function call is defined in `__call__` and realized as operator overloading.)

```
import numpy as np
from chainer import Variable

lin = L.Linear(5, 2)
x = Variable(np.ones((3, 5), dtype=np.float32))
y1 = lin(x)
```
<!--この `numpy` ， `Variable` については後で詳しく説明します。-->
We will explain details about `numpy` and `Variable` later.
<!--この例である`np.ones((3, 5), dtype=np.float32)` は3行5列で全ての値が1であるような行列を作ります。-->
`np.ones((3,5), dtype=np.float32)` generates a 3 x 5 matrixall of whose elements are 1.
<!--`Variable` はその値に加えて学習に必要な情報が埋め込まれているオブジェクトとだけ覚えてください。-->
<!-- please remember ha chigau kamo..-->
Please remember `Variable` is an object which have information about learning in addition to the matrix itself.
<!-- TODO: fix nihongo -->
<!--つまりここでは3個の5次元のベクトルを用意し，それをVariableというオブジェクトにセットし，
はそれを `lin` の引数として与えて，出力を `y` として計算しています。-->
In the above example, we first prepare 3 of 5 dimensional vectors. 
We set them to the object, `Variable` and substitute `x` for it.
Then `x` is used for the parameter of `lin`.
The output is calculated as `y`.
<!--`lin`は5次元の入力を2次元の出力へ変換する関数なので，`y`は3個の2次元のベクトルになります。-->
Because `lin` is a function which transform the 5 dimensional input to 2 dimensional output, `y` is 3 of 2 dimensional vectors.


<!--- ## 線形変換，アフィン変換 (*)-->
## Linear transformation, Affine transformation (*)

<!--線形変換（アフィン変換）は次のように表される変換です。-->
Linear transformation (Affine transformation) is a transformation defined as follows:

```math
\begin{align}
f(x; θ) &= Wx + b \\
θ &= (W, b)
\end{align}
```

<!--例えば上記例のLinearは，5次元のベクトルから2次元のベクトルへの線形変換を表します。-->

In the above example, the function is a linear transformation from 5 dimensional vector to 2 dimensional vector.
<!---## 課題-->
## Exercise
<!--上記の例で，出力を4次元にし，それを出力してください。-->
With the function provided in the example above, adjust the output as 4 dimensional vector and check the output.
