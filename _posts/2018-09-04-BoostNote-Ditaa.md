---
layout: post
title: Boostnote v0.11.9 に Ditaa サポートがマージされました
image: /img/hello_world.jpeg
tags: [contribution, boostnote]
---

Boostnote のv0.11.9がリリースされました。この中に、[私が出していた DitaaサポートのPR](https://github.com/BoostIO/Boostnote/pull/2235)が取り込まれています。

- [公式ブログのリリースノート](https://medium.com/boostnote/boostnote-v0-11-9-is-out-188085822bb4)

Ditaa はPlantUMLが対応するグラフの1種です。Boostnote は PlantUML に対応するために [gmunguia/markdown-it-plantuml](https://github.com/gmunguia/markdown-it-plantuml) を利用しています。
markdown-it-plantuml 自体がまだ Ditaa に対応していなかったので、まず作者に「Ditaa に対応する予定はないか？」と[うかがいました。](https://github.com/gmunguia/markdown-it-plantuml/issues/9)
すると、予定を聞いただけなのに回答は「対応したぜ！提案ありがとう。」でした :)

結果的には markdown-it-plantuml 側の対応がなくとも実装はできたのですが、ライブラリ作者に要望を出して
その機能を実装してもらえるという経験は初めてでしたので、今回もOSSの醍醐味を体感できました。