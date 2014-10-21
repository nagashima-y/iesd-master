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


===============================================================
OS X Yosemiteのインストールディスクイメージ(.dmg)を作成

（１）iesd（https://github.com/ntkme/iesd/）をDownload ZIP

（２）ダウンロードしたzipファイルをデスクトップへ解凍（iesd-master）

（３）ターミナル.appで以下のコマンドを１行づつ実行


cd Desktop/iesd-master
iesd -i /Applications/Install\ OS\ X\ Yosemite.app -o yosemite.dmg -t BaseSystem
hdiutil convert yosemite.dmg -format UDSP -o yosemite.sparseimage
hdiutil mount /Applications/Install\ OS\ X\ Yosemite.app/Contents/SharedSupport/InstallESD.dmg
hdiutil attach yosemite.sparseimage -readwrite
cp /Volumes/OS\ X\ Install\ ESD/BaseSystem.* /Volumes/OS\ X\ Base\ System/
hdiutil detach /Volumes/OS\ X\ Install\ ESD/
hdiutil detach /Volumes/OS\ X\ Base\ System/
hdiutil convert yosemite.sparseimage -format UDZO -o yosemite_install.dmg

（４）iesd-masterフォルダ内に”yosemite_install.dmg”が作成
