# proxy.pac の Edge でのデバッグ

## 手順

- `edge://net-export/` にアクセスし `Start Logging` で json 出力を開始
- 別のタブでデバッグしたい通信を再現
- `Stop Logging`
- `https://netlog-viewer.appspot.com/#import` に json をロード

## 参考

- http://var.blog.jp/archives/74300162.html
