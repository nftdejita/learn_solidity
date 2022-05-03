このセクションでは、Metamask（Ethereumウォレット）を使用して、EthereumブロックチェーンのRinkebyテストネットにコントラクトを展開し、NFTを作成し、NFTマーケットプレイスOpenSeaで確認します。

### 1. Metamaskのインストール
**1.1**  <a href="https://metamask.io/" target="_blank">metamask.io</a>に移動します。

**1.2** ダウンロードボタンをクリックしてから、ブラウザ（Chromeなど）のインストールをクリックして、ブラウザに拡張機能を追加します。

**1.3** 説明に従ってウォレットを作成します。

### 2. Rinkebyのtestnetトークンの取得
テストネットでトランザクションを行うには、イーサリアムテストネットトークンが必要です。

**2.1**　メタマスクを「EthereumMainnetwork」から「RinkebyTestNetwork」に切り替えます。

**2.2**　<a href="https://faucet.paradigm.xyz/" target = "_ blank"> https://faucet.paradigm.xyz/ </a>に移動し、アカウントのアドレスを入力し、testnetETHを請求します。
<a href="https://faucet.paradigm.xyz/" target="_blank">https://faucet.paradigm.xyz/</a>や<a href="https://app.mycrypto.com/faucet" target =" _ blank "> https：//app.mycrypto.com/faucet</a>などの他のropsten faucetを使用することもできます。詳細については、<a href="https://ethereum.org/en/developers/docs/networks/#testnet-faucets" target="_blank">ethereum.org</a>に記載されているfausetをご覧ください。


### 3. ContractのDeploy
**3.1**　Remix IDEの「ENVIRONMENT」の下にある「DEPLOY＆RUN TRANSACTIONS」モジュールで、「InjectedWeb3」を選択します。次に、アカウントを接続するように求められます。これを確認する必要があります。次に、「InjectedWeb3」の下にRinkebyネットワークバッジが表示されます。

**3.2**　トークンコントラクトをデプロイし、Metamaskでトランザクションを確認します。

**3.3**　コントラクトは「展開されたコントラクト」セクションに表示されます。

### 4. NFTの発行（ミント）
**4.1**　IDEでコントラクトを展開して、機能のボタンが表示されるようにします。

**4.2**　safeMintボタンの横にある入力フィールドを展開します。 「to：」入力フィールドに、Remixに接続されているアカウントのEthereumアドレスを入力します。入力フィールド「tokenID：」に「0」を入力します。トランザクションをクリックします。

**4.3**　メタマスクでアセットをクリックし、[トークンのインポート]リンクをクリックして、コントラクトのアドレスを入力フィールドに貼り付けます。小数は0に設定できます。

これで、メタマスクの「アセット」ビューにトークンコントラクトのシンボル（GEOなど）の名前が表示されます。これらのトークンの1つが必要です。

### 5. OpenSeaでNFTを確認する
<a href="https://opensea.io/"
target = "_ blank"> OpenSea </a>は、NFTで最も人気のあるオンラインマーケットプレイスの1つです。 OpenSeaは、<a href="https://testnets.opensea.io/" target = "_ blank"> https://testnets.opensea.io/ </a>の下に、テストネット上のアセットを表示できるバージョンも提供しています。

**5.1**　<a href="https://testnets.opensea.io/login" target = "_ blank">https://testnets.opensea.io/login</a>に移動します。

**5.2**　メタマスクウォレットに接続します。 OpenSeaのアカウント<a href="https://testnets.opensea.io/account" target="_blank">https://testnets.opensea.io/account</a>ビューにリダイレクトする必要があります。 NFTが表示されるはずです。 NFTの画像が表示されます。それをクリックすると、名前、説明、およびプロパティの下に、作成した属性が表示されます。
