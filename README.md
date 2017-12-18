# DXRuby build tool for x64

[DKRuby](http://dxruby.osdn.jp/) 1.4.5 を x64 環境でコンパイルしてインストールするための諸々のセットです。x64版 RubyInstaller が対象になります。

## 環境

* Windows 10 1709 64-bit
* [RubyInstaller](https://rubyinstaller.org/) Ruby 2.4.2-2 (x64)
* [MSYS2](http://www.msys2.org/)
* DXRuby 1.4.5

MSYS2 によるコンパイル環境がセットアップされている必要があります。`ridk install` でセットアップしておいて下さい。

その他にソースをダウンロードするために `subversion` パッケージが必要です。MSYS2 上で下記を実行してインストールしておいて下さい。

```
pacman -S subversion
```

DXRuby を gem で入れないで下さい。dxruby 1.4.5 の gem は 2.4.x 未対応かつ x64 未対応とどうやっても動きません。

## コンパイルとインストール方法

最初にコンパイル環境を読み込んで `rake` を実行してきます。

```
ridk enable
rake
rake install
```

`{Rubyインストールフォルダ}\lib\ruby\site_ruby\2.4.0\x64-msvcrt` にインストールされます。gem での管理ではありませんので、削除したいときは手動で削除して下さい。

## その他

コンパイルや起動不具合のためのパッチが含まれます。パッチは自動であたります。

サンプルで一応動作確認していますが、真っ黒で何も表示されないのがあるなど、色々と不具合がある可能性がかなりあります。 **不具合があってもオリジナルの DXRuby へ問い合わせしないでください。** 問題はここの Iusses へ投げてください。

## ライセンス

MIT License
