ERC20標準では、コントラクトに必要な必須機能およびオプションの機能のみが記述されていますが、機能を追加することもできます。

このセクションでは、OpenZeppelin拡張機能を使用して、トークンを書き込む機能と通貨を発行（ミント）する機能、およびコントラクトを一時停止する機能を追加しました。

もちろん、独自のERC20トークンコントラクトの実装または拡張機能を作成して、それらをコントラクトにインポートすることもできます。しかし、OpenZeppelinのコントラクトはセキュリティの専門家によって監査されており、必要な機能を追加するための優れた方法です。

### Mintable（発行機能）
mint関数を使用すると、コントラクトの作成者は、コントラクトがデプロイされた後に追加のトークンをミント（作成）できます（22行目）。この関数には、入力パラメーターとして、トークンが作成されるアドレスと、作成する必要のあるトークンの量が必要です。

mint関数はすでに<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/ERC20.sol" target =" _ blank">ERC20コントラクト</a>によるOpenZeppelinの実装の一部であるため、別のコントラクトから `mint（）`をインポートする必要はありません。

基本的なアクセス制御メカニズムとして、所有者が特定の機能に排他的にアクセスできるようにコントラクトモジュールである`Ownable`（7行目）をインポートします。このコントラクトでは、継承された `onlyOwner`修飾子を`mint`関数に追加し（22行目）、この関数へのアクセスを「owner」に制限します。

コントラクトは、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/access/Ownable.sol" target ="_blank">所有可能なコントラクト</a>から、アクセスを管理するために、owner（）、transferOwnership（）、renounceOwnership（）などの追加関数を継承します。 

### Burnable（破棄機能）
「ERC20Burnable」（5行目）をインポートし、その機能を継承する（9行目）ことにより、トークン所有者はトークンとアローワンス内のトークンを破棄できます。
詳細については、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/token/ERC20/extensions/ERC20Burnable.sol" target ="_blank">ERC20Burnableコントラクト</a>をご覧ください。 


### Pausable（停止機能）
「Pausable」一時停止可能コントラクトモジュール（6行目と9行目）を使用すると、所有者はコントラクトを一時停止（14行目）および一時停止解除（18行目）できます。一時停止状態では、トークンを転送できません。これは、緊急のシナリオで役立ちます。
詳細については、<a href="https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/contracts/security/Pausable.sol" target="_blank">一時停止可能なコントラクト</a>をご覧ください。


OpenZeppelins <a href="https://docs.openzeppelin.com/contracts/4.x/wizard" target="_blank">コントラクトウィザード</a>をご覧ください。これにより、機能を簡単に追加できます。 。


## ⭐️課題
1. Deploy後、アカウントにトークンを作成してみてください。 `totalSupply（）`と `balanceOf（）`を呼び出して、正しく実行されていることを確認します。
2. トークンを書き込んでから、 `totalSupply（）`と `balanceOf（）`を呼び出して、正しく実行されていることを確認します。
3. 所有者アカウントを使用してコントラクトを一時停止し、2番目のアカウントで転送を試みることにより、一時停止機能をテストします。トランザクションを実行できないようにする必要があり、「一時停止可能：一時停止」という例外がスローされます。