メタデータ拡張はオプションです。これにより、ERC721トークンに追加情報を追加できます。名前、シンボル、およびJSON形式でさらに多くの情報を追加できるファイルを指すことができるURI（Uniform Resource Identifier）を指定できます。

## ERC721メタデータ関数

### name
関数`name`（16行目）は、トークンコレクションの名前を返します。トークンコレクションとは、ERC721トークンコントラクトの実装で作成されたすべてのトークンを意味します。このコレクション内のすべてのトークンには、tokenIdに関係なく、この名前が付けられます。

### symbol
関数`symbol`（21行目）は、トークンコレクションのシンボルを返します。

### tokenURI
関数`tokenURI`（26行目）は、IDが`tokenId`のトークンのURIを返します。この場合、それはコレクション全体のURIではなく、コレクション内の個々のトークンのURIです。

## ERC721メタデータJSONスキーマ
tokenURIが指すファイルは、<a href="https://eips.ethereum.org/EIPS/eip-721#specification" target="_blank">EIP-721</a>で指定されているメタデータJSONスキーマに準拠している必要があります。
 
```
{
    "title": "Asset Metadata",
    "type": "object",
    "properties": {
        "name": {
            "type": "string",
            "description": "Identifies the asset to which this NFT represents"
        },
        "description": {
            "type": "string",
            "description": "Describes the asset to which this NFT represents"
        },
        "image": {
            "type": "string",
            "description": "A URI pointing to a resource with mime type image/* representing the asset to which this NFT represents. Consider making any images at a width between 320 and 1080 pixels and aspect ratio between 1.91:1 and 4:5 inclusive."
        }
    }
}
```

ルート要素はオブジェクト型である必要があります。このルートオブジェクトには、name、description、imageのキーを持つプロパティが必要です。これらのプロパティはすべて文字列型である必要があります。

ERC721標準は非常に柔軟性があり、tokenURIはJSONドキュメントを指す必要はなく、JSONはすべてのプロパティを持っている必要はなく、多くの場合、追加のプロパティを持っています。
