<!-- # 2. 目的関数を定義する (1)-->
# 2. Define the objective function (1)

<!-- 次に目的関数を定義します。-->
Next we define the abjective function.

<!--目的関数は何を学習させたいのかを表す関数です。-->
The objective function is a function which represents what you want the model to learn.
<!-- 目的関数は一つの値を出力し，値が小さければ望ましい状態を表すような関数です。-->
The objective function outputs one value. Smaller output value is more desireble state.

<!-- 例えば，訓練データに対し学習対象モデルが予測をし，間違えた回数を $L$ とします。-->
For example, the learnable model estimates the trainig data. Let the number of mistake be $L$.

<!--この間違えた回数 $L$ を小さくするということは，学習対象モデルが訓練データをたくさん当てられるようにすることを意味します。-->
To minimize the number of mistake $L$ means to make the learnable model estimate correctly as much training data as possible.

<!-- この場合，目的関数は学習対象モデルを引数として受取り，間違えた数を返すような関数です。-->
In this case, the objective function recieves a learnable model as an argument and returns the number of mistake.

<!-- 次から，代表的な学習問題である分類教師あり学習の目的関数を例に考えていきます。-->
In the following sections, we take a look at an example of the objective function for classification supervised learning, which is representative learning problem.

