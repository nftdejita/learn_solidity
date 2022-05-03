このセクションでは、コントラクトがEtherを送受信する方法を学習します。

### Etherの送信
Etherを転送するには、 `transfer（）`、 `send（）`、 `call（）`の3つのオプションがあります。

#### **transfer**
`<支払われる住所>.transfer（uint256金額）`
* `transfer（）`は失敗時に例外をスローします
* 固定の2300ガス給付金を転送します

`transfer（）`の例は、 `SendEther`コントラクト（35行目）にあります。

**`Transfer（）`の使用はお勧めしません。**

#### **send**
`<支払われるアドレス>.send（uint256amount）は（bool）を返します`
* `send（）`は失敗するとfalseを返します
* 固定の2300ガス給付金を転送します

`send（）`の例は、 `SendEther`コントラクト（41行目）にあります。

**`Send（）`の使用はお勧めしません。**

#### **call**
`<address> .call（bytes memory）returns（bool、bytes memory）`
* `call（）`は失敗するとfalseを返します
* 最大量のガスを転送しますが、これは調整可能です

`call（）`の例は、 `SendEther`コントラクト（48行目）にあります。
現在、Etherを転送する場合は、 `Call（）`が推奨されます。

`transfer（）`と `send（）`が導入された理由は、転送されたガスを2300に制限することで、*再突入攻撃*を防ぐためでした。

前のセクションで説明したように、イーサリアムの各操作には特定のコストが関連付けられています。特定の操作は時間の経過とともによりコストがかかるようになったため、それらに関連するガスコストも上昇します。操作のガスコストが変更される可能性がある場合、transfer（）やsend（）のようにハードコードされたガス量を使用するのは適切ではありません。

そのため、Etherの送信には `transfer（）`ではなく `call（）`が推奨されるようになりました。

このテーマの詳細については、この<a href="https://consensys.net/diligence/blog/2019/09/stop-using-soliditys-transfer-now/" target="_blank">Consensysブログ投稿</a>をご覧ください。


### リエントラント攻撃
*再入可能攻撃*は、関数が信頼できないコントラクトを外部呼び出しし、攻撃者がそのコントラクトを使用して、実行が完了する前に元の関数に再帰呼び出しを行う場合に発生します。この方法により、攻撃者は資金を使い果たし、意図しない方法でデータを操作する可能性があります。

*再入可能攻撃*を防ぐために、外部コントラクトを呼び出す前にすべての状態変更を行う必要があります。これは、<a href="https://docs.soliditylang.org/en/latest/security-considerations.html#re-entrancy"  target="_blank">Checks-Effects-Interactions</a>パターンとも呼ばれます。 。

再入可能を防ぐ別の方法は、そのような呼び出しをチェックして拒否する*再入可能ガード*を使用することです。この例は、モディファイアセクションのコントラクト、または<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/ReentrancyGuardのよりガス効率の高いバージョンで確認できます。 .sol " target =" _ blank">Zepplinを開きます</a>。

### Receiving Ether
関数を呼び出さずにコントラクトがEtherを受信できるようにする場合は、 `receive`関数（22行目）または`fallback`関数（25行目）を作成する必要があります。それ以外の場合、Etherは拒否され、コントラクトは例外をスローします。

`receive`関数は、空のcalldataを使用する呼び出しで実行されます（たとえば、send（）またはtransfer（）を介したプレーンなEther転送）。一方、フォールバック関数は、calldataを使用する呼び出しで実行されます。受信関数は存在しないがフォールバック関数が存在する場合、calldataが空の呼び出しもフォールバック関数を使用します。

### Payable function modifier
`payable`関数修飾子を使用すると、関数はEtherを受け取ることができます。

`receive`関数（22行目）は`payable`である必要があります。 `payable`修飾子を削除すると、コンパイラからエラーが発生します。 `fallback`関数から`payable`修飾子を削除すると（25行目）、コンパイルされますが、Etherを受信できなくなります。
関数`sendViaTransfer`、` sendViaSend`、および `sendViaCall`（33、38、および45行目）も、Etherを受信するために`payable`である必要があります。

### Payable address
Solidityは、アドレスデータ型の2つの異なるフレーバー（アドレスと支払い可能なアドレス）を区別します。

`address`：20バイトの値を保持します。
`address payable`：20バイトの値を保持し、そのメンバーを介してEtherを受信できます：転送と送信。

関数`sendViaTransfer`および`sendViaSend`（33行目および38行目）のパラメータータイプを `payableaddress`から`address`に変更すると、 `transfer（）`（35行目）または`send（）`（41行目）。

<a href="https://www.youtube.com/watch?v=_5vGaqgzlG8" target="_blank">Etherの送信に関するビデオチュートリアルをご覧ください</a>。

## ⭐️課題
受益者が撤回できるEtherを受け取るチャリティーコントラクトを作成します。

1. `Charity`というコントラクトを作成します。
2. タイプaddressの`owner`と呼ばれるパブリックステート変数を追加します。
3. パラメータや関数コードなしで公開され、支払い可能な寄付関数を作成します。
4. 公開されている引き出し関数を作成し、コントラクトの合計残高を「所有者」アドレスに送信します。

ヒント：1つのアカウントからコントラクトを展開して、コントラクトをテストします。