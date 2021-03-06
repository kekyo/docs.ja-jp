---
title: "マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: d81091bf09d690f5d57ad9a30b5f16de1358ede6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/05/2017

---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>マイクロサービスで DDD と CQRS パターンを使ってビジネスの複雑さに取り組む

*ビジネス ドメインの理解を反映するマイクロソフトサービスまたはコンテキスト境界ごとのドメイン モデルを設計する*

このセクションでは、複雑なサブシステムへの取り組みが必要な場合に実装する高度なマイクロサービスについて、またドメイン専門家の知識と絶えず変化するビジネス ルールに由来するマイクロサービスについて説明します。 このセクションで使用するアーキテクチャ パターンは、図 9-1 に示すように、ドメイン駆動設計 (DDD: Domain-Driven Design) とコマンドクエリ責務分離 (CQRS: Command and Query Responsibility Segregation) の手法に基づいています。

![](./media/image1.png)

**図 9-1** 外部マイクロサービス アーキテクチャとマイクロサービスごとの内部アーキテクチャ パターンとの対比

ただし、ASP.NET Core Web API サービスの実装方法や Swashbuckle による Swagger メタデータの公開方法など、データ駆動型マイクロサービスのテクニックのほとんどは、DDD パターンで内部的に実装される高度なマイクロサービスにも適用されます。 前述した実施方法のほとんどはここでも、または任意の種類のマイクロ サービスにも適用されるため、このセクションは前のセクションの内容を増補するものとなっています。

このセクションでは、まず eShopOnContainers 参照アプリケーションで使用される簡略化された CQRS パターンの詳細を示します。 後で DDD 手法の概要を説明しますが、そこでは、アプリケーションで再利用できる一般的なパターンを確認できます。

DDD は、学習用に豊富な技術資料が提供されている大きなテーマです。 入門書としては、Eric Evans 著の『[Domain-Driven Design](https://domainlanguage.com/ddd/)』 (ドメイン駆動設計)、さらに Vaughn Vernon、Jimmy Nilsson、Greg Young、Udi Dahan、Jimmy Bogard の各氏、およびその他多くの DDD/CQRS の専門家による技術資料などを利用できます。 ただし、DDD 手法の適用方法の習得には何より、具体的なビジネス ドメイン内で専門家との対話、ホワイトボードを使った議論、ドメイン モデリングのセッションを利用する試みが必要です。

#### <a name="additional-resources"></a>その他の技術情報

##### <a name="ddd-domain-driven-design"></a>DDD (ドメイン駆動設計)

-   **Eric Evans。Domain Language (ドメイン言語)**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)

-   **Martin Fowler。Domain-Driven Design (ドメイン駆動設計)**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard。Strengthening your domain: a primer (ドメインの強化: 入門)**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>DDD 関連の書籍

-   **Eric Evans。Domain-Driven Design: Tackling Complexity in the Heart of Software (ドメイン駆動設計: ソフトウェアの核心にある複雑さに立ち向かう)**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans。Domain-Driven Design Reference: Definitions and Pattern Summaries (ドメイン駆動設計リファレンス: 定義とパターンの概要)**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon。Implementing Domain-Driven Design (実践ドメイン駆動設計)**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon。Domain-Driven Design Distilled (ドメイン駆動設計の本質)**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson。Applying Domain-Driven Design and Patterns (ドメイン駆動設計とパターンの適用)**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesar de la Torre。N-Layered Domain-Oriented Architecture Guide with .NET (.NET を使用した N 層のドメイン指向アーキテクチャのガイド)**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram および Floyd Marinescu。Domain-Driven Design Quickly (ドメイン駆動設計の要点)**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

DDD に関するトレーニング

-   **Julie Lerman および Steve Smith。Domain-Driven Design Fundamentals (ドメイン駆動設計の基礎)**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[前へ] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [次へ] (apply-simplified-microservice-cqrs-ddd-patterns.md)

