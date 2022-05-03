CODECOPYは、EVMによって実行される多くのオペコードの1つです。 <a href="https://ethervm.io/" target="_blank">https://ethervm.io/</a>でオペコードの完全なリストを確認してください。

CODECOPYは、**実行中のコード**（またはその一部）を取得し、それを`calldata`から`memory`にコピーします。

Solidityの実装は次のとおりです。**codecopy（t、f、s）**-**s**バイトを**f**の位置のコードから**t**の位置のメモリにコピーします。

すべてのコントラクト展開は**CODECOPY**を使用します。