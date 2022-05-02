前章では、コントラクトをコンパイルしました。つまり、solidity コードを Ethereum Virtual Machine (EVM) バイトコードの小さなチャンクに変換したことを意味します。

今度は、そのコードをテストブロックチェーンに載せてみましょう。

1. Deploy and Run icon ![deploy & run icon](https://raw.githubusercontent.com/ethereum/remix-workshops/master/Basics/3._Deploy_to_the_JavascriptVM/images/run.png "deploy & run icon")をクリックします。 

2. 2. Environment プルダウンから **JavaScript VM** を選択します。

4. 4. [デプロイ]ボタン(または拡張ビューの[トランザクション]ボタン)をクリックします。

5. 5. これで、コントラクトをJSVM（ブラウザウィンドウ内で実行されているシミュレーションブロックチェーン）にデプロイしました。 JSVMは、テストチェーンの中で最も単純で、最も速く、最も現実的ではありません。 これはGanacheに非常に似ています - あなたがTruffleに精通している場合。各トランザクションを承認する必要がないため、それほど現実的ではありません。 

他のテストチェーンやメインネットにデプロイすることができる。しかし、これを行うには別の**環境**に接続する必要があります - Injected Web3やWeb3 Providerのようなものです。 Injected Web3を使用する場合、MetaMaskをインストールする必要があります。MetaMaskはブラウザのプラグインであるウォレットです。   
