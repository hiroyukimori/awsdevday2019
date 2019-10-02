# Serverless

* サーバーのマシンリソースではなく、ロジックの実行などリクエストに応じた処理に対する請求をおこなうような実行モデル
* 物理サーバーがアプリケーションコードを実行するユーザーから抽象化されていることから「サーバーレス」と表現されている
* 敏しょう性や変更可能性の高さから人気のある「マイクロサービス」アーキテクチャの実行基盤としても利用されている

## Amazon Lambda

* 上記のような「サーバーレス」として利用されているFunction as a Service
* タイマーやHTTPのリクエスト、ストリーミングデータなどさまざまなイベント駆動型の関数実行
* 必要に応じてコードが実行されて、自動的にスケーリングされる
* コンピューティング時間に対して支払いを行う

### AWS Lambda ランタイム

* 関数を作成するとき、使用する言語にあわせてLambdaランタイムを選択
* 基盤となる実行環境はAmazon Linux, Amazon Linux 2のいずれか
* [Lambdaランタイム](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/lambda-runtimes.html)

## Demo

1. 下準備としてAWS CLI / AWS Toolkit for Visual Studio 2017 and 2019をインストール
   * [AWS CLI のインストールと設定](https://docs.aws.amazon.com/ja_jp/streams/latest/dev/kinesis-tutorial-cli-installation.html)
   * [AWS Toolkit for Visual Studio 2017 and 2019](https://marketplace.visualstudio.com/items?itemName=AmazonWebServices.AWSToolkitforVisualStudio2017)
2. AWS Lambdaのテンプレートをインストール

``` commandline
dotnet new -i Amazon.Lambda.Templates
```

1. インストールが完了するとテンプレートの一覧にLambdaのテンプレートが表示される

``` commandline
dotnet new -l
```

1. 空のLambdaテンプレートでプロジェクトを作成

``` commandline 
dotnet new lambda.EmptyFunction
```

なお、以下のようなオプションも指定できる

|option|説明|
|:-|:-|
|--name|関数の名前|
|--profile|AWS SDK for .NET認証情報ファイルにあるプロファイルの名前|
|--region|関数を作成する AWS リージョン|

* 他にもDeployするためのツールとしてAmazon.Lambda.Tools .NET Core Global Toolがある。
* [AWS Extensions for .NET CLI](https://github.com/aws/aws-extensions-for-dotnet-cli)
* インストールは以下の通り

``` commandline
dotnet tool install -g Amazon.Lambda.Tools
```

参考までにデプロイは以下のように行える

``` commandline
dotnet lambda deploy-function <関数名> --function-role <role>
```

* [C# による Lambda 関数のビルド](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/dotnet-programming-model.html)