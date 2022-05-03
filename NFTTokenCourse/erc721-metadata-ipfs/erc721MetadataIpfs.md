このセクションでは、メタデータを作成し、分散して保存します。

IPFS（InterPlanetary File System）は、ファイルを分散して保存するためのピアツーピアネットワークです。 Pinata.cloudは、ユーザーがIPFSネットワーク上でファイルを簡単にホストできるようにするピン留めサービスです。

画像とJSONファイルをそれらのメタデータとともにIPFSでホストしたいと考えています。

### 画像フォルダを作成する
この例では、3つのトークンのメタデータを作成します。以下に示すように、フォルダに保存した3つの画像を作成します。
`` `
geo-img
├──geo_1.png
├──geo_2.png
├──geo_3.png
`` `

### ピニャータに登録
ここで、これらの画像をどこかにホストして、トークンのメタデータでそれらを指すことができるようにします。分散型の方法でそれを行い、Pinataを使用してIPFSでそれらをホストしましょう。

まず、ピニャータのアカウントが必要です。 <a href="https://app.pinata.cloud/register" target="_blank"> Pinata.cloud </a>にアクセスして、アカウントを作成します。 Pinataでは、最大1GBのデータを無料でアップロードできます。

サインアップすると、ピンマネージャービューが表示されます。

<img src = "https://i.imgur.com/yKpD65m.png" alt="ピンマネージャーピニャータ" width= "300" />


### 画像をIPFSにアップロードする
アップロードボタンをクリックして、画像を含むフォルダをアップロードします。
フォルダをアップロードすると、フォルダの名前とそれに関連付けられているCID（コンテンツ識別子）が表示されます。フォルダのコンテンツが変更されると、CIDも変更されます。

IPFSでフォルダーにアクセスするには、このアドレス`https://ipfs.io/ipfs/`を入力してCIDを追加します。現在の例では、次を使用してフォルダにアクセスできます。
<a href="https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P" target = "_ blank">
    https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P
</a>

次を使用して特定の画像にアクセスできます。
<a href="https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P/geo_1.png" target = "_ blank">
    https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P/geo_1.png
</a>

### JSONファイルを作成する
3つのJSONファイルを格納する別のフォルダーを作成します。
```
geo-json
├── 0
├── 1
├── 2
```

JSONファイル内に、名前、説明、画像などのトークンのメタデータを作成します。
画像のURLには、IPFS上の画像のURLを使用します。必要に応じて、データを追加できます。この例では、トークンごとにいくつかの一意の属性を追加しました。

これは、最初のトークンのJSONがどのように見えるかを示しています。
```
{
    "name": "Geometry#0",
    "description": "Geometry is an NFT collection for educational purposes.",
    "image": "https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P/geo_1.png
",
    "attributes": [
        { "trait_type": "background", "value": "cyan" },
        { "trait_type": "color", "value": "red" },
        { "trait_type": "shape", "value": "circle" }
    ]
}
```

2番目のトークンのJSONは次のようになります。
```
{
    "name": "Geometry#1",
    "description": "Geometry is an NFT collection for educational purposes.",
    "image": "https://ipfs.io/ipfs/QmTJok2tju9zstjtAqESdZxTiUiFCBAyApHiDVj4maV75P/geo_2.png",
    "attributes": [
        { "trait_type": "background", "value": "magenta" },
        { "trait_type": "color", "value": "green" },
        { "trait_type": "shape", "value": "square" }
    ]
}
```

上記のように、この例のフォルダーは「geo-json」と呼ばれます。このフォルダー内には、3つのJSONファイルがあります。
最初のJSONファイルは「0」、2番目のJSONファイルは「1」、3番目のJSONファイルは「2」と呼ばれます。

JSONファイルにファイルの末尾がなく、対応するtokenIdのように名前が付けられていることを確認してください。
pinata.cloudのピンマネージャーで、アップロードボタンをクリックし、JSONファイルを含むフォルダーをアップロードします。

IPFSでフォルダーにアクセスするには、このアドレス`https://ipfs.io/ipfs/`を入力してCIDを追加します。
現在の例では、次を使用してフォルダにアクセスできます。
<a href="https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp" target="_blank">
    https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp
</a>
これがbaseURIになります。

次に、以下を使用してスラッシュとtokenIdを追加するだけで、特定のJSONファイルにアクセスできます。
<a href="https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp/0" target = "_ blank">
    https://ipfs.io/ipfs/QmVrsYxXh5PzTfkKZr1MfUN6PotJj8VQkGQ3kGyBNVKtqp/0
</a>

コントラクトで、baseURIを独自のbaseURIに置き換えます。この例では、baseURIはURLで構成されています
`https://ipfs.io/ipfs/`、JSONファイルを含むCID、および末尾のスラッシュ「/」。

これで、tokenIdをbaseURIに追加することで、トークンごとに個別のtokenURIが作成されます。これは、上記の例でJSONファイルにアクセスするために手動で行った方法とまったく同じです。