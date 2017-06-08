<!-- # 目的関数を定義する (3)-->
# 2. Define the objective function (3)

<!-- 今回，学習したいモデルは入力 $x$ が与えられた時に出力 $y$ の条件付き確率 $p(y \mid x)$ を出力してくれるようなモデルです。-->
This case, given the input $x$, the model to be learned outputs the conditional probability of y, $p(y \mid x)$.

<!--例えば，入力$x$に犬が写っていれば $p(犬 \mid x) = 0.99, p(猫 \mid x) = 0.01$ となるようなモデルです。-->
For example, if a dog is in the input $x$, the model outputs $p(dog \mid x) = 0.99, p(cat \mid x)=0.01$.

<!--このようなカテゴリ値（離散値）に対する確率分布をモデル化するにはSoftmaxを利用します。-->
To model the probability distribution of the categorized value (discritized value), we use Softmax function.

<!--Chainerでは `chainer.functions` で `softmax` 関数が定義されているのでそれを使いましょう。-->
In Chainer, `softmax` function is defined in `chainer.function`. 

<!--例えば，入力`x`を何らかのモデルで変換しカテゴリ種類数と同じ次元数を持つベクトル`t`を作ります。-->
For example, we can transform input `x` by some kind of model into the vector `t`, which has same number of dimensions as the number of categories.

<!--次に（必ずしも確率分布となっていない）ベクトル`t`を`softmax`を使って確率分布に変換します。-->
Then, we transform the vector `t` , which is not necessarily the probability distribution, into the probability distribution using `softmax`.

```
t = model(x)
y = F.softmax(t)
```

## Softmax　(*)

<!--Softmax（または多クラスロジスティックスモデル）とは $d$ 次元の実数値ベクトルから，
$d$ 次元の確率分布を作る方法の一つです。-->
Softmax (or multi class logistic model) is one of the method which transform $d$ dimensional real-valued vector into $d$ dimensional probability distribution.

<!--$softmax(x)$ は，$x$ が $d$ 次元であり，各次元の値が $x[0], x[1], ..., x[d-1]$ の時，-->
$softmax(x)$ is represented as:

$$y[i]=\frac{\exp(x[i])}{\sum_i \exp(x[i])}$$

,where $x$ is $d$ dimensional and each dimensional value are $x[0], x[1], ..., x[d-1]$.
<!-- と表されます。-->

<!--あるベクトルvが確率分布となる条件として，-->
The conditions for a vector $v$ to the probability distribution are:

<!--
1. 各次元の値が非負
2. 合計値が1
-->
1. Every values are non-negative
2. The sum of the values is 1

<!--という条件があります。-->

<!--Softmaxは， $\exp$ が非負であることから1の条件を満たし，各次元の値を足した値で割っていることから2の条件を満たします。-->
Softmax meets the first condition because $\exp$ is non-negative. Softmax also meets the second condition because each values are devided by the sum of all values.
