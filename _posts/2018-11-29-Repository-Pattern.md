---
layout: post
title: トランザクションとリポジトリと Unit of Work
image: /img/hello_world.jpeg
tags: [aspnetcore, c#, ddd]
---

データの永続化とトランザクションについて、nrsさんの[『ボトムアップドメイン駆動設計 後編』の『3. トランザクション』](https://nrslib.com/bottomup-ddd-2/#outline__3)を基本にいくつかの解法を比較してみます。

『ボトムアップドメイン駆動設計』で例示されているのは、
- A) アプリケーションサービスでトランザクションスコープを定義するもの。
- B) Unit of Workパターンで、Unit of Workが複数のリポジトリを持ちながらトランザクションを制御するもの。

の2つ。

[MediatR](https://github.com/jbogard/MediatR) の作者の Jimmy Bogard が [ContosoUniversityCore](https://github.com/jbogard/ContosoUniversityCore) でやっているのは、

- Unit of Work として [SchoolContext](https://github.com/jbogard/ContosoUniversityCore/blob/master/src/ContosoUniversityCore/Infrastructure/SchoolContext.cs) を定義するよ、アプリケーション全体でそれを使うよ。
- 全体で使うからアクションフィルタでトランザクションの開始と終了を[コントロールするよ。](https://github.com/jbogard/ContosoUniversityCore/blob/master/src/ContosoUniversityCore/Infrastructure/DbContextTransactionFilter.cs)

というパターン。

[dotnet-architecture/eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) では、

- [リポジトリが Unit of Work を持つよ。](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Infrastructure/Repositories/OrderRepository.cs)
- この Unit of Work は Mediator のインスタンスを[持つよ。](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs)
  - Unit of Work で変更を保存する前に、この Mediator がそれまでに発生したドメインイベントを全てDBに反映するよ。

というパターン。

いちばんリッチなのは eShopOnContainers のやり方ですが、アプリケーションの規模に合わせて上手く実装したいですね。