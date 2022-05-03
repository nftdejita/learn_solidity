`Deploy＆Run`モジュールに切り替えます
![トランザクションの実行](images/remix_runtransaction.png "トランザクションの実行")

 - JavaScript VM環境を選択し、コンパイルされたコントラクトのリストで`sampleContract`コントラクトを選択します。

 - `Deploy`をクリックします
 
 コンソールに`creation of sample errored: <address> is not a valid address. Please check the provided address is valid.`のようにエラーが出力されますが、これは予想されることです。
 
 **`autoDeployLib`をfalseに設定したため、Remixは`<address>`だけでなくアドレスを持っていることを期待しています**

したがって、ライブラリをデプロイしてそのアドレスを取得する必要があります。

  - コンパイルされたコントラクトのリストでライブラリ`aLib`を選択し、`deploy`を押します
  
    ![Choose aLib](images/contract_alib.png "Choose aLib")

  - クリップボードアイコンをクリックして、ライブラリのアドレスをコピーします。

    ![コピーlib1](images/alib_copy.png "コピー")

  - **コントラクトサンプルの**メタデータJSONに貼り付けます。

  - `Runtransaction`モジュールで`sampleContract`コントラクトを再度選択し、デプロイを押します。

  - これでデプロイが成功するはずです。