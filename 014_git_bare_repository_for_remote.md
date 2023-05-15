# ローカルファイルシステム上にリモートリポジトリを作成する

- ローカルリポジトリの作成&コミット

```git
mkdir D:\data\repository\myproject
cd D:\data\repository\myproject
git init .
git add .
git commit -m "first commit"
```

- リモートリポジトリの作成

```git
mkdir X:\remoterepository\myproject.git
cd X:\remoterepository\myproject.git
git init --bare .
```

- ローカルリポジトリでリモートリポジトリへの参照を追加

```git
git remote add origin X:\remoterepository\myproject.git
git remote -v
```

- リモートリポジトリにプッシュ

```git
git push --set-upstream origin main
```

## 備考

- 最初にリモートリポジトリを作成してから clone するほうが簡単ではある