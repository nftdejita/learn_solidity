ERC721は、イーサリアムブロックチェーン上の非代替トークン（NFT）を管理するトークンコントラクトの標準です。

各非代替トークンは一意であり、互換性はありません。 NFTは、さまざまなプロパティ、動作、または権限を持つことができます。非代替トークンは、アート、収集品、不動産などの固有のデジタルおよび物理的資産の所有権を表すために使用されます。

ERC721トークン標準について詳しく知りたい場合は、その<a href="https://eips.ethereum.org/EIPS/eip-721" target="_blank">Ethereum改善提案</a>の仕様を参照してください。 

## 基本仕様
ERC721標準はERC20標準よりも複雑で、オプションの拡張機能を備えています。 ERC721準拠のコントラクトは、少なくともERC721およびERC165インターフェイスを実装する必要があります。これについては、このセクションで説明します。

このインターフェース（11行目）は、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/IERC721.sol" target = "_ blank">OpenZeppelin</a>によって提供されるオープンソースコントラクトライブラリの一部です。

## IERC721関数
ERC20標準に準拠するコントラクトでは、次の機能を実装する必要があります。

### balanceOf
関数`balanceOf`（30行目）は、アドレス`owner`を持つアカウントが所有するトークンの量を返します。

### ownerOf
関数`ownerOf`（39行目）は、IDが`tokenId`のトークンを保持しているアカウントのアドレス`owner`を返します。

### safeTransferFrom
関数`safeTransferFrom`（55行目）は、アドレス`from`のアカウントからアドレス`to`のアカウントにID`tokenId`のトークンの所有権を譲渡します。

関数`safeTransferFrom`（137行目）は、関数` safeTransferFrom`（55行目）とほぼ同じです。唯一の違いは、この関数のペイロードが空でない`data`であるということです。

スマートコントラクトは、転送を受信する場合、ERC721TokenReceiverインターフェイスを実装する必要があります。これにより、コントラクトがERC721トークンの転送を処理できるようになり、トークンがロックできないコントラクトにロックされるのを防ぐことができます。

### transferFrom
関数`transferFrom`（55行目）は、IDが` tokenId`のトークンの所有権を、アドレスが`from`のアカウントからアドレスが`to`のアカウントに転送します。

**可能な限り、transferFromの代わりにsafeTransferFromを使用することをお勧めします。**
`transferFrom`関数は、転送の受信者であるスマートコントラクトがERC721TokenReceiverインターフェイスを実装しており、ERC721トークンを処理できるかどうかをチェックしないため、安全ではありません。

### approve
関数`approve`（94行目）は、アドレス` to`のアカウントに、関数を呼び出すアカウントに代わってID`tokenId`のトークンを管理する権限を与えます。

### getApproved
関数`getApproved`（103行目）は、IDが`tokenId`のトークンの管理が承認されているアカウントのアドレス`operator`を返します。

### setApprovalForAll
関数`setApprovalForAll`（115行目）は、関数を呼び出すアカウントのすべてのトークンを管理するために、アドレス` operator`を持つアカウントに権限（ `_authorized`）を付与または削除します。

### isApprovedForAll
関数`getApproved`（103行目）は、アドレス` operator`のアカウントが、アドレス `owner`のアカウントのすべてのトークンを管理することを承認された場合、ブール値trueを返します。

## IERC721イベント
ERC721コントラクトは、次のイベントも発行する必要があります。

### Transfer Event
IDが`tokenId`のトークンが、アドレスが`from`のアカウントからアドレスが`to`のアカウントに転送されるときに、 `Transfer`イベント（15行目）を発行する必要があります。

### Approval Event
`Approval`イベント（20行目）は、アドレス`owner`のアカウントがアドレス`spender`のアカウントを承認して、ID`tokenId`のトークンを管理するときに発行する必要があります。

### ApprovalForAll Event
`ApprovalForAll`イベント（25行目）は、アドレス` owner`のアカウントが、アドレス `operator`のアカウントにすべてのトークンを管理する許可（` _authorized`）を付与または削除したときに発行される必要があります。

## IERC165
ERC721インターフェースに加えて、ERC721準拠のコントラクトはERC165インターフェースも実装する必要があります。

ERC165インターフェースの実装により、コントラクトは特定のインターフェースのサポートを宣言できます。別のコントラクトと対話したいコントラクトは、トランザクションを行う前に、他のコントラクトがこのインターフェースをサポートしているかどうかを照会できます。サポートされていない可能性のあるトークンを送信します。

ここでのIERC721インターフェースは、IERC165インターフェースからインポート（6行目）および継承（11行目）します。

これは、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/utils/introspection/IERC165.sol" target="_blank">OpenZeppelinsの実装</a>の方法です。 ERC165インターフェースは次のようになります。

```
interface IERC165 {
    function supportsInterface(bytes4 interfaceId) external view returns (bool);
}
```

たとえば、EIP721で指定されているERC721インターフェイスのERC165識別子は「0x80ac58cd」です。インターフェイス識別子の計算方法と詳細については、<a href="https://eips.ethereum.org/EIPS/eip-165" target="_blank">改善提案</a>をご覧ください

## その他のインターフェース
安全な転送を受け入れるには、<a href="https://eips.ethereum.org/EIPS/eip-721#specification" target="_blank">IERC721TokenReceiver</a>インターフェースを実装する必要があります。

EIP721で指定されているERC721コントラクトには2つのオプションの拡張機能があります。

IERC721Enumerableを使用すると、コントラクトでトークンの完全なリストを公開し、それらを検出可能にすることができます。

IERC721Metadataを使用すると、コントラクトで追加情報をトークンに関連付けることができます。 これについては、次のセクションで詳しく説明します。