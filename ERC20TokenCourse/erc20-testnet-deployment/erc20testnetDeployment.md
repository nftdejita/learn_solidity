このセクションでは、Metamask（Ethereumウォレット）を使用して、Ethereumブロックチェーンのテストネットにコントラクトをデプロイします。このテストネットは実際のブロックチェーン（メインネット）と非常によく似た動作をしますが、トランザクションの支払いに実際のETHを必要としません。

### 1. Metamaskのインストール
**1.1**  <a href="https://metamask.io/" target="_blank">metamask.io</a>に移動します。

**1.2** ダウンロードボタンをクリックしてから、ブラウザ（Chromeなど）のインストールをクリックして、ブラウザに拡張機能を追加します。

**1.3** 説明に従ってウォレットを作成します。

### 2. testnetトークンの取得
testnetでトランザクションを行うにはtestnetトークンが必要です。これは*faucet*と呼ばれるサイトから受け取ることができます。

**2.1**　 [Ethereum Mainnetwork]ドロップダウンをクリックし、[Ropsten Test Network]を選択して、Metamaskネットワークを切り替えます。テストネットワークが表示されない場合は、[表示/非表示]リンクをクリックして、設定で[テストネットワークを表示]を有効にします。

**2.2**　 <a href="https://faucet.ropsten.be/" target="_blank"> https://faucet.ropsten.be/ </a>にアクセスし、アカウントのアドレスを入力します、およびtestnetETHを要求します。 <a href="https://faucet.paradigm.xyz/" target="_blank">https://faucet.paradigm.xyz/</a>や<a href="https://app.mycrypto.com/faucet " target =" _ blank "> https：//app.mycrypto.com/faucet</a>などの他のropsten蛇口を使用することもできます。 詳細については、<a href="https://ethereum.org/en/developers/docs/networks/#testnet-faucets" target="_blank">ethereum.org</a>に記載されている*faucet*をご覧ください。 。

### 3. Deploy
EduCoinコントラクトがコンパイルされていることを確認してください。

**3.1** RemixIDEの「ENVIRONMENT」の下にある「DEPLOY＆RUN TRANSACTIONS」モジュールで、「InjectedWeb3」を選択します。確認する必要があるアカウントを接続するように求められます。

**3.2** EduCoinコントラクトをデプロイし、Metamaskでトランザクションを確認します。

**3.3** コントラクトは「展開されたコントラクト」セクションに表示されます。コントラクトアドレスをコピーします。

**3.4** メタマスクで、アセットをクリックしてから、[トークンのインポート]リンクをクリックし、コントラクトのアドレスを入力フィールドに貼り付けます。

これで、ウォレットに1000EDCのバランスが表示されるはずです。

### 4. Transactionの発行
**4.1** Metamaskウォレットのidenticon（アドレスの視覚的表現）をクリックして、2番目のアカウント（アカウント2）を作成します。

**4.2** アカウント2のアドレスをコピーします。

**4.3** 最初のアカウント（アカウント1）に切り替えて、アカウント2に250 EDCを送信します。アカウント1とアカウント2の残高を確認します。アカウント2がトークンをインポートするには、トークンアドレスを再度追加する必要がある場合があります。このアカウントで取引を行う場合は、testethが必要になります。

Remixでコントラクトを確認し、アカウント1とアカウント2のアドレスを使用して `balanceOf`関数を呼び出すと、アカウントの残高を確認することもできます。