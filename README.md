#Mavericksインストールディスクイメージの作成をワークフロー化
[https://github.com/ntkme/iesd](https://github.com/ntkme/iesd)

本来はターミナル.appを使用してコマンド入力してディスクイメージを作成するのですが
簡単に出来るようAutoMatorのワークフローを作成。


###事前準備
App StoreでOS X 10.9をダウンロードしておく。アプリケーションフォルダに「OS X Mavericks インストール.app」とあればOK。


###起動時の注意点
ダブルクリックで開くと「"iesd_automator.workflow"は開発元が未確認のため開けません。」となってしまうので、
右クリック or control+クリックして、［開く］を選択。


###Automatorのワークフロー「iesd_automator.workflow」の内容

1.[https://github.com/ntkme/iesd](https://github.com/ntkme/iesd)からZIP Download

2.デスクトップに解凍

3.確認ダイアログ表示

4.シェルスクリプト実行

5.デスクトップに"Mavericks.dmg"作成完了後、通知を表示

