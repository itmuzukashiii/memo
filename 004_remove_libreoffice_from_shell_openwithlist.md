# Libre Office をインストールすると .txt の右クリックメニューがウザいことになる

## 事象と解決策

参考の `ask.libreoffice.org` に下記の投稿があった．同様の事象．

```
I am using LO 6.1.0.3 on Windows 10 Pro.

If I do a right click on a .txt (Notepad) and go to “Open with” LibreOffice shows up twice.

How do I find out how or why this is happening?
How do I remove one of them?
I uninstalled and reinstalled LO and it still comes up with two.

Is this normal?
```

下記のコメントが大変参考になった．

```
I had the same problem (LibreOffice 7), found these entries in the registry:

In HKEY_CLASSES_ROOT\.txt\OpenWithProgIDs: value "soffice.StarCalcDocument.6" REG_SZ "" and value "soffice.StarWriterDocument.6" REG_SZ ""

In HKEY_LOCAL_MACHINE\SOFTWARE\The Document Foundation\LibreOffice\7.0\Capabilities\FileAssociations: value ".txt" REG_SZ "soffice.StarWriterDocument.6"

Removed both "soffice.Star…" values from HKEY_CLASSES_ROOT\.txt\OpenWithProgIDs, problem solved, only one entry remaining in Open with… sub-menu (and still opens Writer).

To be safe (if you feel uncomfortable with RegEdit), export HKEY_CLASSES_ROOT\.txt\OpenWithProgIDs before modifying its content (right-clic context menu on OpenWithProgIDs within HKEY_CLASSES_ROOT\.txt, Export) in a file, if something goes wrong, double-clic the exported file (don’t forget where you saved it) to restore the removed values.

Afterthought: removing only soffice.StarCalcDocument.6 from HKEY_CLASSES_ROOT\.txt\OpenWithProgIDs was enough, no more duplicate. The supprising thing is that both entries opened Writer, one should have opened Calc (StarCalcDocument) instead ???
```

結論，下記のようにレジストリをいじったところ，きれいになった．

- `HKEY_CLASSES_ROOT\.txt\OpenWithProgIDs` は `VScode.txt` を残して削除
- `HKEY_LOCAL_MACHINE\SOFTWARE\The Document Foundation\LibreOffice\7.5\Capabilities\FileAssociations` から `.txt` を削除
- `HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.txt\OpenWithList` は下記のように編集
    ```ini
    [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.txt\OpenWithList]
    "a"="NOTEPAD.EXE"
    "MRUList"="bca"
    "b"="sakura.exe"
    "c"="scalc.exe"
    ```

## 参考

- https://ask.libreoffice.org/t/open-with-lo-shows-up-twice/35036
- https://superuser.com/questions/1303165/editing-the-open-with-menu-in-windows-10
