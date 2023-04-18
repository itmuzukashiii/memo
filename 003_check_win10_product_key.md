# プロダクトキーの確認コマンド

## 手順

ベンダ製 Windows プレインストール製品だと Product key が本体に保存されている場合がある．
それを確認する方法:

```cmd
REM コマンドプロンプトから
wmic path SoftwareLicensingService get OA3xOriginalProductKey
```

```ps1
# PowerShell から
(Get-WmiObject -Class SoftwareLicensingService).OA3xOriginalProductKey
```

## 参考

- https://recoverit.wondershare.jp/windows-tips/windows-10-product-key-verification-and-activation.html
