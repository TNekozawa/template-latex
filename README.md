# Ubuntu環境でLaTeX環境を構築する

## 0: VsCodeとWSLをインストール
各自でやって下さい

---
## 1: LaTeXを下記でインストール
```bash
sudo apt install texlive-full
```
超時間かかる上に多分途中で止まるので, 下記記事を参照にする<br/>
[Ubuntu22.04にtexliveをapt installする際にPregenerating ConTeXt MarkIV format. This may take some time...で停止する](https://qiita.com/Shiccho/items/e3d707f07fa23f1e74d0)
>...
Running mtxrun --generate. This may take some time... done.
Pregenerating ConTeXt MarkIV format. This may take some time... # ココで停止

Enter長押しでゴリ押ししたらなぜか"Done"になる(マジ意味わからん)

---
## 2: latexmkrc作成

下記を書き込んだ".latexmkrc"ファイルを, Ubuntuのhome/ユーザ名のディレクトリに置く
```bash
#!/usr/bin/env perl

$latex = 'uplatex -synctex=1 -interaction=nonstopmode -file-line-error %O %S';

$bibtex     = 'pbibtex %O %S';
$makeindex  = 'mendex %O %S';
$dvipdf     = 'dvipdfmx %O %S';
$pdf_mode   = 3;
$max_repeat = 5;

$pvc_view_file_via_temporary = 0;
$pdf_previewer = 'wsl-open %S'
```

---
## 3: .texファイルをコンパイル

設定ファイルは.vscode/settings.jsonファイルを参照

サンプルコードファイルはtex/master/master.texファイルを参照

後は右上の緑色でコンパイルできるはず