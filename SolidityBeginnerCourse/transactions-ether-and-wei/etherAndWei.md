* Ether *（ETH）は暗号通貨です。 * Ether *は、* Ether *をアドレスに送信したり、Ethereumアプリケーションと対話したりする形でトランザクションを行うなど、Ethereumネットワークを使用するための料金を支払うためにも使用されます。

### Ether Units
*Ether*の単位を指定するには、リテラル番号に接尾辞 `wei`、` gwei`、または`ether`を追加できます。

#### `wei`
*Wei*は、*Ether*の最小のサブユニットであり、暗号学者[Wei Dai](https://en.wikipedia.org/wiki/Wei_Dai)にちなんで名付けられました。接尾辞のない*その他*の数字は`wei`として扱われます（7行目）。

#### `gwei`
1`gwei`（giga-wei）は1,000,000,000（10 ^ 9）`wei`に相当します。

#### `ether`
1`ether`は1,000,000,000,000,000,000（10 ^ 18）` wei`に等しい（11行目）。

<a href="https://www.youtube.com/watch?v=ybPQsjssyNw" target="_blank">EtherとWeiのビデオチュートリアルをご覧ください。</a>

## ⭐️課題
1. `oneGWei`という`public` `uint`を作成し、それを1`gwei`に設定します。
2. `isOneGWei`という`public` `bool`を作成し、1gweiと10^9の比較操作の結果に設定します。

ヒント：これがコントラクトの`gwei`と`ether`に対してどのように記述されているかを見てください。