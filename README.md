# py-sql-reporter
MySQLのデータを与えられたSQLから読み、
エクセル形式にした複数のファイルをzipファイルでまとめて
S3にアップロードするスクリプト。

## Design
- SQLと設定を元にスクリプトを読みエクセルファイルを作成してローカルに保存する
- 全てのファイルをzipに固め、ローカルに保存する
- S3にzipファイルをアップロードする
- ~~zipを取り出し、SESで送信する~~

## Memo
- AWSのSESを用いてメールを送信したかったが、現状限られたリージョンのみ使用可能で日本リージョンでは使えない。

## ToDo
- 設計を変えたい
  - binではオプション等を読み必要なserviceのコマンドを使う
  - serviceは何をするかというのが分かるメソッドにする
    - gatewayには外部サービスと連携するクラス群
    - mangerは対象を扱うUtil的なクラス群
  - databaseやexcel、S3を触る部分はgatewayというまとまりにする
- [x] Python 2系のライブラリに依存していたので修正したい。

## Usage
    sql-reporter retrieve
    sql-reporter compression
    sql-reporter upload (not yet created)
    sql-reporter all
    sql-reporter help