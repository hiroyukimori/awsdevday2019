# .NET Core 3 - Blazor

## WebAssemblyについて

* Webブラウザーで実行可能なバイナリーコードによる処理を実行する仕組み
* コンパクトなバイナリー形式の言語で、ネイティブに近いパフォーマンスで動作
* HTML5の標準規格に含まれる機能でモダンなWebブラウザーが対応
* [WebAssembly](https://developer.mozilla.org/ja/docs/WebAssembly)
* [WebAssembly Design](https://github.com/WebAssembly/design)

### なぜ WebAssembly？

* Webにおける振る舞いはJavaScriptの役目
  * JavaScriptはインタープリター言語
  * 動的片付けを行っている → 構文解析に時間がかかる
  * 本来の用途はWebにおけるちょっとした飾り付け程度の処理
* 現在のJavaScriptの役目
  * 複雑なアニメーション
  * WebGLなどのグラフィック処理
  * 高速な演算が必要な処理

## Blazor

* BlazorとはC#でインタラクティブなWebユーザーインターフェースを記述するためのフレームワーク
* .NETの技術を利用して処理を記述することができるため、サーバーとクライアントでロジックの共有が可能
* WebAssemblyによってCoreCLRを実行する仕組みを実現しているため、モバイルブラウザーを含めた広範囲のブラウザーで動作する
* [Blazor](//blazor.net)
* [Blazorの概要](https://docs.microsoft.com/ja-jp/aspnet/core/blazor/?view=aspnetcore-3.0?WT.mc_id=DT-MVP-4000668)

### demo

Blazorのテンプレートを作成、実行

``` commandline
dotnet new blazor
dotnet run
```

VSCodeを起動

``` commandline
code .
```

1. PagesフォルダーのIndex.razorを開く
2. テーブルを追加

``` html
<table>
    <tr>
        <th>Datetime</th>
        <th>Memo</th>
    </tr>
    <tr>
        <td></td>
        <td></td>
    </tr>
</table>
```

1. コードを追加
2. 値を保持するための変数宣言を行う

``` razor
@code{
    Dictionary<string, string> memoItems = new Dictionary<string, string>();
    string memo = string.Empty;
}
```

1. コードの上にメモの入力用フォームを追加

``` html
<form>
    <input />
    <button>Add</button>
</form>
```

1. フォームのメモを追加するハンドラを追加


``` csharp
    void AddMemo()
    {
        memoItems.Add(DateTime.Now.ToLongTimeString(), memo);
        memo = string.Empty;
    }
```

1. inputにbindを追加
2. formにsubmit時の関数を指定

``` html
<form @onsubmit="AddMemo">
    <input @bind="memo"/>
    <button>Add</button>
</form>
```

1. tableに明細を表示するようコードを追加

``` razor
    @foreach (var item in memoItems)
    {
        <tr>
            <td>@item.Key</td>
            <td>@item.Value</td>
        </tr>
    }
```

### 完成

``` razor
@page "/"

<h1>Hello, world!</h1>

Welcome to your new app.

<table>
    <tr>
        <th>Datetime</th>
        <th>Memo</th>
    </tr>
    @foreach (var item in memoItems)
    {
        <tr>
            <td>@item.Key</td>
            <td>@item.Value</td>
        </tr>
    }
</table>

<form @onsubmit="AddMemo">
    <input @bind="memo"/>
    <button>Add</button>
</form>

@code{
    Dictionary<string, string> memoItems = new Dictionary<string, string>();
    string memo = string.Empty;

    void AddMemo()
    {
        memoItems.Add(DateTime.Now.ToLongTimeString(), memo);
        memo = string.Empty;
    }
}
```