# ワークショップメモ！

## EC２上にVS Codeのサーバーを立ち上げる方法

以下のスタックファイルを使う

https://github.com/jaws-ug-cdk/cdk-conf-2024-contribute-workshop/blob/main/CdkConferenceStack.json

リソース(標準)で作成する。

→ Amazon linux2023でEC2インスタンスをSSMでアクセス可能とする。

**ここで作成されるリソース**
- VPC
- EC2インスタンス
- 接続用のエンドポイント


EC2インスタンスにアクセスして以下のコマンドを実行する

```bash
code tunnel service install
```

これでEC2インスタンスをVS Codeサーバーとすることが可能！！

## 着手できそうなIssueを決める！

以下のリポジトリのIssueをのぞいてみる

https://github.com/aws/aws-cdk/issues
