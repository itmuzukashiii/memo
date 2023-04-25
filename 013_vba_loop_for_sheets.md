## VBA で For ループを特定条件でスキップする

ワークシートをループ処理しつつ，特定のシートはスキップさせる例．
VBA には `Continue` が無いため、`GoTo` を用いる．

```vb
Dim ws As Worksheet
For Each ws In Worksheets
  If ws.Name = "OLD" Then
    GoTo CONTINUE1
  End If
  '' <処理内容>
  
CONTINUE1:
Next ws
```
