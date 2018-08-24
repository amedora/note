---
layout: post
title: Boostnote v0.11.8 に Markdown Table Formatter がマージされました
image: /img/hello_world.jpeg
---

2018年7月19日にリリースされた Boostnote の v0.11.8 に、[私が出していたPR](https://github.com/BoostIO/Boostnote/pull/2145)が取り込まれています。

- [公式ブログのリリースノート](https://boostlog.io/@kazup01/boostnote-v0118-release-5b5191365e5c4f005a805a7c)

このPRは、Markdown の中で書かれたテーブルを自動整形するものです。
私の素の実力ではとても実装できるような機能ではありませんでしたが、[実装を希望するIssue](https://github.com/BoostIO/Boostnote/issues/1444)でアイデアは提示されてましたので、それを参考に[susisu/mte-kernel](https://github.com/susisu/mte-kernel)を利用する形で実装できました。

OSSプロダクトに対して、これまでも typo の Fix や翻訳で貢献したことはありましたが、機能追加での貢献は初めてでしたので貴重な経験になりました。