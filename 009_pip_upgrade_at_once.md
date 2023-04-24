# pip install --upgrade を全パッケージに対して一括実行する

## コマンド

```powershell
# $Env:http_proxy=http://<proxy-server>:<proxy-port>
# $Env:https_proxy=http://<proxy-server>:<proxy-port>
python -m pip install --upgrade (@(pip list --format freeze) | %{$_ -Replace '==.*$',''})
```
