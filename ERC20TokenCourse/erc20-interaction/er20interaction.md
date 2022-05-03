このセクションでは、ブラウザにコントラクトをデプロイし、その機能をテストします。

### 1.コントラクトを展開します
**1.1**　RemixIDEの「Soliditycompiler」モジュールでEduCoinコントラクトをコンパイルします。

**1.2**　「トランザクションの展開と実行」モジュールで、コントラクト入力フィールドでコントラクト「EduCoin」を選択し、「展開」ボタンをクリックします。コントラクトセレクターの入力フィールドで、必ず正しいコントラクトを選択してください。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_compileAndDeploy.gif?raw=true" alt="コントラクトのコンパイルとデプロイ" width= "300" />

**GIF**　コンパイルからデプロイの手順

### 2.関数をテストします
IDEでトークンコントラクト関数を展開します。

#### 2.1 decimals
「decimals」ボタンをクリックして、decimals（）関数を呼び出します。
「18」を返すはずです。

#### 2.2 name
「name」ボタンをクリックして、name（）関数を呼び出します。
「EduCoin」を返す必要があります。

#### 2.3 symbol
「symbol」ボタンをクリックして、symbol（）関数を呼び出します。
「EDC」を返す必要があります。

#### 2.4 totalSupply
「totalSupply」ボタンをクリックして、totalSupply（）関数を呼び出します。
1000000000000000000000（1000 * 10 ** 18）を返す必要があります。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token
-course/erc20/erc20_test_functions.gif?raw=true" alt="伝達関数" width= "300" />

**GIF** decimals,name,symbolおよびtotalSupply関数のテスト



#### 2.5 バランス
**2.5.1** サイドバーの[アカウント]セクションに移動し、横にあるコピーアイコンを使用して、表示されているアドレスをコピーします。

**2.5.2** 「balanceOf」機能ボタンの横の入力フィールドにアドレスを貼り付けて、ボタンをクリックします。 
1000000000000000000000（1000 * 10 ** 18）を返す必要があります。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_balanceOf.gif?raw=true" alt="伝達関数のテスト" width= "300" />

**GIF** balanceOf関数のテスト


#### 2.6 Transfer
EduCoinを1つのアカウントから別のアカウントに転送します。

**2.6.1** サイドバーの[アカウント]セクションに移動し、表示されたアドレスをクリックします。これにより、ドロップダウンが開きます。表示された2番目のアドレスを選択し、そのアドレスをコピーします（アカウント2）。

**2.6.2** ドロップダウンを開き、最初のアカウント（アカウント1）を再度選択します。これは、転送に使用するアカウントであるためです。

**2.6.3** 「transfer」機能ボタンの横の入力フィールドにアドレスを貼り付け、番号500000000000000000000を入力して、ボタンをクリックします。

**2.6.4** アカウント1とアカウント2の残高を確認すると、両方とも金額500000000000000000000を返す必要があります。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_transfer.gif?raw=true" alt="伝達関数のテスト" width= "300" />

**GIF** transfer関数のテスト

#### 2.7 Approve
Approveで権限を与えることにより、アカウント1がアカウント2に代わってトークンを使用できるようになります。

**2.7.1**  [アカウント]セクションに移動し、アカウント1のアドレスをコピーして、アカウント2に再度設定します。

**2.7.2** Approve機能で、支出者の入力としてアカウント1のアドレスを入力し、金額を250000000000000000000に設定します。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_approve.gif?raw=true" alt="テスト承認関数" width= "300" />

**GIF** Approve機能のテスト

#### 2.8 Allowance
`Allowance`ボタンの横に、所有者としてアカウント2のアドレスを入力し、支出者としてアカウント1のアドレスを入力します。ボタンをクリックします。
1000000000000000000000を返す必要があります。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_allowance.gif?raw=true" alt="テスト許容値関数" width= "300" />

**GIF** Allowance関数のテスト

#### 2.9 TransferFrom
これで、アカウント1はアカウント2から自分のアカウントに250000000000000000000トークンを転送します。

**2.9.1**  [Account]セクションでアカウント1を選択します。

**2.9.2**  [transferFrom]ボタンの横に、送信者としてアカウント2のアドレスを入力し、受信者としてアカウント1を入力し、金額として250000000000000000000を入力して、ボタンをクリックします。

**2.9.3** アカウント2と1の残高を確認すると、250000000000000000000と750000000000000000000が返されます。

<img src = "https://github.com/dacadeorg/remixMedia/blob/main/token-course/erc20/erc20_transferFrom.gif?raw=true" alt="transferFrom関数のテスト" width= "300" />

**GIF** transferFrom関数のテスト
