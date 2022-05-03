## ブロックチェーンのクエリ

このチュートリアルでは、JavaScriptライブラリを使用してブロックチェーンをクエリするスクリプトを実行します。

つまり、Remix GUIやEtherscanなどのブロックエクスプローラーを使用する代わりに、エディターでスクリプトを使用して、ターミナルから実行します。

ブロックチェーンとの対話に最もよく使用されるJSライブラリは、web3.jsとethers.jsです。

簡単なweb3.jsの例であるqueryBlockNum.jsから始めましょう。

スクリプトによるweb3.jsの呼び出しは、try/catchブロックを含む自己実行型の非同期関数にラップされています。

現在のブロック番号を次のように照会します。
```
let blockNumber = await web3.eth.getBlockNumber()
```

オブジェクト`web3`はRemixによって注入されることに注意してください。 web3.jsの詳細については、ドキュメント<a href="https://web3js.readthedocs.io/" target="_blank">https://web3js.readthedocs.io</a>を確認してください。

web3.jsまたはethers.jsを使用するには、**Deploy＆Run**モジュールで**InjectedWeb3**または**Web3Provider**環境を選択する必要があります。現在、スクリプトはJSVMでは機能しません。 **試してみると、エラーが発生します。**

したがって、この例では、Deploy＆Runモジュールで**Injected Web3**を選択し、Metamaskをインストールします。

ターミナルから
```
remix.execute()
```
を実行します。このコマンドは、 
```
let blockNumber = await web3.eth.getBlockNumber()
```
という行で現在のJavaScriptファイルを実行します。

コンソールに、メタマスクが接続されているチェーンの現在のブロック番号が表示されます。