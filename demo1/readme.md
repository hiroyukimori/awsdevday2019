# Demo 1

## .NET CLI

### Install

* [Download .NET Core 3.0](http://dot.net/get-core3)
* [.NET Core コマンドラインインターフェース(CLI)ツール](https://docs.microsoft.com/ja-jp/dotnet/core/tools/?tabs=netcore2x)

``` commandline
dotnet --info
```

### `dotnet` と `dotnet new` の違い

``` CommandLine
dotnet -h
dotnet new -h
```

### ASP.NET MVC プロジェクトの作成

* 開発用証明書の追加

``` commandline
dotnet dev-certs https --trust
```

* ASP.NET Core MVCのプロジェクトテンプレートからプロジェクトの生成

``` commandline
dotnet new mvc
```

* VSCode で中身を確認

``` commandline
code .
```

* ローカル環境での実行

``` commandline
dotnet run
```

### 配布用モジュールの作成

``` commandline
dotnet publish
```
