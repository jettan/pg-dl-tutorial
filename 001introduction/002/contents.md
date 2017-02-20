<!---# Chainer Tutorial Bookについて-->
# About Chainer Tutorial Book

<!---はじめに，Chainer Tutorial Book (CTB）の仕組みについて簡単に紹介します。-->
We will first introduce how CTB works.

<!---CTBは，Sakuraのサーバーで稼働しているウェブサービスを利用しています。-->
CTB makes use of web services that run on Sakura servers.

<!---このウェブサービスはPythonのコードを受け取ると，サンドボックス内で実行し，実行結果の出力を返します。-->
Upon receiving a Python script, the web service executes this script in a sandbox and sends back the output and results of the execution.

<!---さっそく右側の画面を操作してみましょう。
Runをクリックすると右側に表示されているPythonコードを実行します。
プログラムは自由に編集可能です。プログラムを編集した後に再度Runをクリックすると編集後のプログラムを実行できます。
元々表示されていたプログラムに戻したい場合はResetをクリックします。
プログラムを強制的に停止させたい場合はAbortをクリックします。-->
Let's focus our attention on the right screen:
Inside the editor you can freely modify the code.
Click 'Run' to run the Python code shown inside the editor.
If you want to revert the program back to what was shown originally, click 'Reset'.
Finally, if for some reason you want to halt your program, click 'Abort'.
