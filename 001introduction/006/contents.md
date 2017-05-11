
<!-- # 1. 学習対象のモデルを定義する (3) -->
# 1. Define the model to be learned (3)

<!-- Chainerでもう一つ重要なオブジェクトとしてFunctionがあります。-->
Another important object of Chainer is Function.
<!-- FuncitonはLinkとは違って，学習可能なパラメータを持ちません。-->
Unlike Link, Function does not have parameters which can be learned.
<!-- つまり，学習によって挙動を変えません。-->
<!-- This sentence is difficult to translate for me...-->
Function does not change its behavior by learning.

<!-- ディープラーニングで利用されている代表的な関数は `chainer.functions` で定義されています。 -->
Functions which are commonly used in deep learning are defined in `chainer.functions`.
<!-- また，自分で新しいFunctionを作ることもできます。-->
You can generate a new Function by yourself.

<!-- 以降では，この  `chainer.functions` をFとして使えるようにします。-->
<!-- TODO: Japanese wo naosu -->
For the following, we will use `chainer.functions` as `F`.

```
from chainer import functions as F
```

<!--例えば，ディープラーニングでよく使われるReLUとよばれる非線形関数 $f_{relu}$ は-->
For example, ReLU which is one of the most popular non linear function in deep learning field is defined as follows:

$$f_{relu}(x)=max(x,0)$$

<!--で定義されます。-->
<!--つまり，もし $x$ が $0$ よりも大きければ $x$ をそのまま返し，もし小さければ $0$ を返すような関数です。-->
That means if $x$ is larger than $0$, the function returns $x$ otherwise it returns $0$.

<!--Chainerでは次のように記述できます。-->
You can write this like following when you use Chainer.

```
from chainer import functions as F
...
y2 = F.relu(x)
```

<!--これらのLinkとFunctionを組みわせて複雑な関数を作ることができます。-->
You can generate a complex function using Link and Function.

<!--例えば，前回の例のLinearを適用した後にReLUを適用した結果は次のように計算されます。-->
For example, if you want to first use Linear (which is used in previous section) and then use ReLU, you can write the code as follows:

```
y3 = F.relu(lin(x))
```

<!-- ## 課題-->
## Exercise
<!--ReLUと並んで重要な非線形関数として，sigmoidがあります。-->
sigmoid function is also important non linear function as ReLU.
<!--例をsigmoidに変えて，その結果を表示してください。-->
Change ReLU to sigmoid in the example and output the result.

http://docs.chainer.org/en/stable/reference/functions.html


