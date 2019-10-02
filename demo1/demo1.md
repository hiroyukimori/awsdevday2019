# Demo 1 - .NET Core ～ ASP.NET Core

## .NET CLI

### Install

* [Download .NET Core 3.0](http://dot.net/get-core3)
* [.NET Core コマンドラインインターフェース(CLI)ツール](https://docs.microsoft.com/ja-jp/dotnet/core/tools/?WT.mc_id=DT-MVP-4000668)

``` commandline
dotnet --info
```

### `dotnet` と `dotnet new` の違い

* [dotnet / coreclr](https://github.com/dotnet/coreclr)
* [corehostのソースコード](https://github.com/dotnet/coreclr/tree/master/src/dlls/mscoree)
* [Hosting API](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts)

``` CommandLine
dotnet -h
dotnet new -h
```

### ASP.NET Core MVC プロジェクトの作成

[ASP.NET Core概要](https://docs.microsoft.com/ja-jp/aspnet/core/?WT.mc_id=DT-MVP-4000668)

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

* ローカル環境での実行 (VSCodeターミナルから)

``` commandline
dotnet run
```

### 配布用モジュールの作成

``` commandline
dotnet publish
```
