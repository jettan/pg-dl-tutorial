<!-- # 1. 学習対象のモデルを定義する (4) -->
# Define the model to be learned (4)

<!-- これまで扱ったLinkとFunctionを組み合わせて，学習対象のモデルを実際に作ってみましょう。-->
Let's make an actual model for learning using combination of Link and Function.

<!-- 以下に三層からなるニューラルネットワークの例をあげます。-->
Following is an example of 3 layers neural network.

```
class MLP(chainer.Chain): # MultiLayer Perceptron

    def __init__(self, n_units, n_out):
        super(MLP, self).__init__(
            # the size of the inputs to each layer will be inferred
            l1=L.Linear(None, n_units),  # n_in -> n_units
            l2=L.Linear(None, n_units),  # n_units -> n_units
            l3=L.Linear(None, n_out),  # n_units -> n_out
        )

    def __call__(self, x):
        h1 = F.relu(self.l1(x))
        h2 = F.relu(self.l2(h1))
        return self.l3(h2)
```

<!--各機能は今後詳細に説明されますので，ここでは概要だけ説明します。-->
Each functions will be explained in the later section, here we will see the briefly explaination of them.
<!--詳細は理解できなくてもそのまま飛ばして問題ありません。-->
If you cannot understand the detail, it's fine and read on.

<!--このMLPは，三つのLinear（l1, l2, l3）を学習可能なパラメータとして持ち，`__call__`でそれらのパラメータを利用して結果を計算します。-->
This MLP has 3 Linear (`l1`,`l2`,`l3`), which are learnable parameters and the result is calculated using these parameters in `__call__`.
<!-- なお，`L.Linear` の第一引数には `None` を指定することで実際の入力からユニット数を自動で設定してくれます。-->
If you specify `None` for the first argument of `L.Linear`, the number of units is automatically set by the actual input.

<!-- `__call__` では先ほど定義した層に入力`x`を与えて計算（順計算）を行います。-->
In `__call__`, forward computation is executed by inputing `x` to the layer which was defined before.

<!-- まず `l1` に大元の入力 `x` を与え，それをLinearで変換したものにReLUを適用します。-->
First, the input `x` is given to `l1` and transformed by Linear. Then, ReLU is used for the result.
<!--その計算結果 `h1` を次の層 `l2` に与え同様の計算を行います。-->
The computation result `h1` is given to `l2`. The similar computation as previous layer is executed.
<!--`l3` に関しても同様に前層の結果を元に計算を行います。-->
Just like `l2`, for `l3`, computation is executed using the previous layer's result.
<!-- 最終的に `l3` の結果を返すことで計算が完了します。-->
Finally, the function returns the result of `l3` and the calculation is completed.

<!--このように，(1)Linkを使って学習対象のパラメータを定義し，(2)次にそれらを使って順計算を定義することで学習対象のモデルを定義できます。-->
In this way, we can define the learnable model: (1) we define learnable parameters using Link (2) we define the forward computation.

