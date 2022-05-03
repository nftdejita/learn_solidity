このコントラクトでは、OpenZeppelinのERC721トークンコントラクトの実装を使用します（4行目）。

<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC721/ERC721.sol" target="_blank">ERC721コントラクト</a>の実装をご覧ください。 ERC721標準で指定されている機能とは別に、コントラクトは、後で説明する追加の機能を提供します。

## myToken
MyToken（7行目）と呼ばれる独自のコントラクトを作成します。これは、OpenZepplinの `ERC721`トークンコントラクト実装とインポートした`Ownable`（4行目）から機能を継承します（7行目）。所有可能なコントラクトモジュールを覚えていない場合は、ERC20拡張機能のセクションをご覧ください。

このERC721実装は、EIPで指定されているIERC721Metadata拡張機能を利用します。私たちのコントラクトは関数`name（）`と `symbol（）`を継承します
コントラクトのデプロイ中に値を設定できるようにするコンストラクターがあります（8行目）。
この場合、デフォルト値を使用します。トークンにコントラクト`"MyToken "`と同じ名前を付け、`"MTK"`をそのシンボルにします。

### Base URI
ERC721コントラクトを使用すると、それぞれが独自のtokenIdを持つさまざまなトークンを作成できます。 IERC721Metadataインターフェースで見たように、各トークンは独自の `tokenURI`を持つことができます。これは通常、名前、説明、画像リンクなどのメタデータを格納するJSONファイルを指します。

コントラクトが複数のトークンを作成する場合、ERC721実装は多くの場合、すべてのトークンのベース（ `baseURI`）として同じURIを使用し、連結によって最後に一意の`tokenId`を追加することによってのみそれらを区別します。次のパートでは、これが実際にどのように見えるかを見ていきます。

この例では、データをIPFSに保存しています。これについては次のセクションで詳しく説明します。 

baseURIは<a href="https://ipfs.io/ipfs/QmUYLUKwqX6CaZxeiYGwmAYeEkeTsV4cHNZJmCesuu3xKy/" target = "_ blank"> https://ipfs.io/ipfs/QmUYLUKwqX6CaZxeiYGwmAYeEkeTsV4c </a>　(11行目)となります。

このためIDが0のtokenURIは<a href="https://ipfs.io/ipfs/QmUYLUKwqX6CaZxeiYGwmAYeEkeTsV4cHNZJmCesuu3xKy/0" target="_blank"> https://ipfs.io/ipfs/QmUYLUKwqX6CaZxei/0</a>となり、

IDが1のtokenURIは<a href="https://ipfs.io/ipfs/QmUYLUKwqX6CaZxeiYGwmAYeEkeTsV4cHNZJmCesuu3xKy/1" target="_blank">https://ipfs.io/ipfs/QmUYLUKwqX6CaZxeiYGwmAYeEkeTsV4cHNZJmCesuu3xKy/1</a>となるでしょう。

IPFSを使用していて、「504ゲートウェイタイムアウト」エラーが発生した場合、データが利用可能になるまで待機して再試行する必要がある場合があります。

### safeMint
safeMint関数（14行目）を使用すると、コントラクトの展開後に、所有者が専用のトークンIDを使用して新しいトークンを作成できるようになります。
safeMint関数はOpenZeppelinのERC721実装の一部であり、アドレス`to`のアカウントにID`tokenId`のトークンを安全にミントすることができます。アクセス制御には、インポートしたOwnableアクセス制御コントラクトモジュールの `onlyOwner`修飾子を使用します（5行目）。

次のセクションでは、NFTのメタデータを作成してホストする方法を説明します。

## ⭐️課題
1. コントラクトの名前を`Geometry`に変更します。
2. トークンの名前を`Geometry`に変更します。
3. トークンのシンボルを`GEO`に変更します。
4. `_baseURI`を<a href="https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp/" target="_blank">https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp/</a>にします。