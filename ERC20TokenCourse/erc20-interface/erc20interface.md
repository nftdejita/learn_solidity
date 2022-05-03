ERC20（Ethereum Request for Comments 20）は、Ethereumブロックチェーン上の代替可能なトークンを管理するトークンコントラクトの標準です。

代替可能トークンはすべて互いに等しく、同じ値、動作、および権限を持っています。代替可能トークンは、通貨ETHやBTCのように、交換手段としてよく使用されます。ただし、議決権や評判などの他のユースケースもあります。

ERC20トークン標準について詳しく知りたい場合は、<a href="https://eips.ethereum.org/EIPS/eip-20" target="_blank">Ethereum改善提案 </a>の仕様を参照してください。

## インターフェース
ERC20トークンコントラクトに必要な機能の概要を理解するために、ERC20コントラクトと相互作用するインターフェイスを見ていきます。
このインターフェース（9行目）は、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/v4.4.0/contracts/token/ERC20/IERC20.sol" target =" _ blank ">OpenZeppelin</a>が提供するオープンソースコントラクトライブラリの一部です。。

## ERC20関数
ERC20標準に準拠するコントラクトでは、次の6つの機能を実装する必要があります。

### totalSupply
関数`totalSupply`（13行目）は、使用可能なトークンの合計量を返します。

### balanceOf
関数`balanceOf`（18行目）は、アドレス`account`を持つアカウントが所有するトークンの量を返します。

### transfer
関数`transfer`（27行目）は、トークンの`amount`をアドレス`recipient`に転送します。
この関数は、 `Transfer`イベント（以下を参照）を発行（生成）する必要があり、送信者が転送を行うのに十分なトークンを持っていない場合は例外をスローする必要があります。

### approve
関数`approve`（52行目）は、関数を呼び出すアカウントに代わって、アドレス`spender`がトークンの`amount`を転送するための許可を作成します。

### allowance
関数`allowance`（36行目）は、アドレス`spender`がアドレス`owner`のアカウントに代わって使用できるトークンの量を返します。

### transferFrom
関数`transferFrom`（63行目）は、アドレス`sender`に代わってアドレス`recipient`にトークンの`amount`を転送します。
この関数は、`Transfer`イベントを**発行する必要があります**。

## ERC20イベント
ERC20コントラクトは、次の2つのイベントも発行する必要があります。

### Transfer
`Transfer`（71行目）イベントは、`value`の量のトークンがアドレス`indexedfrom`から`indexedto`のアカウントから転送されるときに発行される必要があります。パラメータ`from`と`to`は`indexed`であり、インデックス付きパラメータをフィルタとして使用してこれらのイベントを検索できます。

### Approval
アカウントの「インデックス付き所有者」がアカウントの「インデックス付き支出者」に代わって`value`の量のトークンを転送することを承認した場合、`Approval`（77行目）イベントを発行する必要があります。

## ERC20オプション機能
必須の機能とイベントに加えて、ERC20標準で指定された3つのオプションの機能もあります。

### name
`function name() external view returns (string);`  
トークンの名前を返します。

### symbpl
`function symbol() external view returns (string);`　
トークンのシンボルを返します。

### decimals
`function decimals() external view returns (uint8);`　
トークンが使用する小数点以下の桁数を返します。

表示時にトークンを1.5ETHなどの任意の量に分割できるようにするには、小数を使用することをお勧めします。 EVM（Ethereum仮想マシン）は整数のみをサポートします。そのため、ERC20標準では、トークンの小数点以下の桁数を指定する小数点以下の機能を実装することが提案されています。**小数点以下18桁**が業界標準です。