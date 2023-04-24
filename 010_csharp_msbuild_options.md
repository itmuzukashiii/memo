# csproj のビルドオプション

## AssemblyName

publish 時の最終ファイルの名前を定義する．省略時はプロジェクト名になる．

## SelfContained

ランタイムを assembly に含めるか否か．含めた場合サイズが大きくなるが，.NET Runtime がインストールされていない環境でも動作させられるようになる．

## PublishReadyToRun

true にすると ReadyToRun ビルドとなり，.NET アプリケーションの起動時間と待機時間を向上させることができる．
Linux x64 や Windows x64 などの特定のランタイム環境 (RID) を対象とするアプリを発行するときにのみ使用可能．

https://learn.microsoft.com/ja-jp/dotnet/core/deploying/ready-to-run

## EnableCompressionInSingleFile

true にすると exe サイズを圧縮することができる．ただしアプリケーションの起動時にアセンブリをメモリに展開する必要があるためその分時間がかかる．

https://learn.microsoft.com/ja-jp/dotnet/core/deploying/single-file/overview?tabs=cli

