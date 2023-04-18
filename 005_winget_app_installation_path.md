# WinGet コマンドで入れたアプリのインストールパス

## WinMerge

- `%LOCALAPPDATA%\Programs\WinMerge\` としてインストールされる
- 実行ファイルは `WinMergeU.exe`
- `win + r` → `winmerge` で起動可能

## VSCode

- `%LOCALAPPDATA%\Programs\Microsoft VS Code` にインストールされる
- 実行ファイルは `Code.exe`
- `bin` にユーザ環境変数PATHが通っている
- `bin` 内には `code`, `code.cmd`, `code-tunnel.exe` が含まれている
    ```cmd
    C:\Users\DEVADMIN>where code
    C:\Users\DEVADMIN\AppData\Local\Programs\Microsoft VS Code\bin\code
    C:\Users\DEVADMIN\AppData\Local\Programs\Microsoft VS Code\bin\code.cmd
    ```
- `win + r` → `code` で起動可能
