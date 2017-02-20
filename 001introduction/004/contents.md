<!---# 1. 学習対象のモデルを定義する (1)-->
# Define the model to be learned (1)

<!---はじめに学習対象のモデルを定義します。-->

<!---ここでは，学習対象のモデルはいくつかのパラメータを使った関数だとします。
Pythonプログラムでいうと，学習対象のモデルはクラスのメソッドであり，パラメータはメンバ変数（インスタンス）のようなものです

例えば次のクラスFはパラメータ $a$ と $b$ を持ち，関数としては $ax + b$を表します。
この関数の挙動はパラメータ $a$ と $b$ を変えることで変わります。-->
Let's assume that the model to be learned is a function that has several parameters.
In Python, the model to be learned is written as a method of a class, while its parameters are member variables of that class.

For example, let's say we have a class F with parameters $a$ and $b$.
Also, let's have F represent the function $ax + b$.
By changing the values of the parameters $a$ and $b$, the behavior of the function also changes.

```
class F:
	def __init__(self, a, b):
		self.a = a
		self.b = b

	def __call__(self, x):
		return self.a * x + self.b

f = F(2.0, -1.0)
print(f(1.0)) # 1.0
print(f(2.0)) # 3.0
```

<!---同様に，学習対象のモデルも複数のパラメータを持ち，それらパラメータを調整することで望むような挙動をするようにさせます。-->
Like in our example, the model to be learned also has several parameters and by adjusting those parameters, we can make the model behave as desired.

<!---## パラメトリックモデル(*)-->
## Parametric Model (*)

<!---このようなパラメータで特徴づけられたモデルをパラメトリックモデルとよびます。
例えば，パラメータ $\theta$ で特徴付けられた関数は $y=f(x; \theta)$ です。
この関数の挙動がパラメータ $\theta$ で変わることを示すために，引数とは違って $;\theta$ と表します。-->
A model that is characterized by parameters is called a parametric model.
Let's say we have a function that is characterized by parameter $\theta$: $y = f(x; \theta)$.
To indicate that the behavior of this function changes depending on parameter $\theta$, we simply express the model as $\theta$ without any arguments.

<!--- ## 課題 -->
## Exercise

<!---上記例を-->
With the function provided in the example above, adjust $a$ and $b$ such that

f(1.0) = 5.0
f(2.0) = 8.0

<!---となるようにaとbを調整し
を書き換えてください。-->

```
f = F(2.0, -1.0)
```

(In other words, train the model manually by yourself).

<!---（つまり，あなた自身でモデルを学習させてください）-->
