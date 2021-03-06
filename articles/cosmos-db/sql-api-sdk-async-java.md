---
title: 'Azure Cosmos DB: SQL Async Java API、SDK、およびリソース | Microsoft Docs'
description: リリース日、提供終了日、Azure Cosmos DB SQL Async Java SDK の各バージョン間の変更など、SQL Async Java API と SDK に関するあらゆる詳細を提供します。
services: cosmos-db
documentationcenter: java
author: SnehaGunda
manager: kfile
ms.assetid: a452ffa2-c15d-4b0a-a8c1-ec9b750ce52b
ms.service: cosmos-db
ms.workload: data-services
ms.tgt_pltfrm: na
ms.devlang: java
ms.topic: article
ms.date: 05/18/2018
ms.author: sngun
ms.openlocfilehash: 9dae401bc007b78d8ee3c6993735650e3b26b9d1
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34359528"
---
# <a name="azure-cosmos-db-async-java-sdk-for-sql-api-release-notes-and-resources"></a>SQL API 用 Azure Cosmos DB Async Java SDK: リリース ノートとリソース
> [!div class="op_single_selector"]
> * [.NET](sql-api-sdk-dotnet.md)
> * [.NET Change Feed](sql-api-sdk-dotnet-changefeed.md)
> * [.NET Core](sql-api-sdk-dotnet-core.md)
> * [Node.js](sql-api-sdk-node.md)
> * [Async Java](sql-api-sdk-async-java.md)
> * [Java](sql-api-sdk-java.md)
> * [Python](sql-api-sdk-python.md)
> * [REST](https://docs.microsoft.com/rest/api/cosmos-db/)
> * [REST リソース プロバイダー](https://docs.microsoft.com/rest/api/cosmos-db-resource-provider/)
> * [SQL](https://msdn.microsoft.com/library/azure/dn782250.aspx)
> * [BulkExecutor - .NET](sql-api-sdk-bulk-executor-dot-net.md)
> * [BulkExecutor - Java](sql-api-sdk-bulk-executor-java.md)

SQL API Async Java SDK は、[Netty ライブラリ](http://netty.io/)をサポートした非同期操作が可能であるという点で、SQL API Java SDK とは異なります。 既存の [SQL API Java SDK](sql-api-sdk-java.md) では、非同期操作はサポートされません。 

<table>

<tr><td>**SDK のダウンロード**</td><td>[Maven](https://mvnrepository.com/artifact/com.microsoft.azure/azure-cosmosdb)</td></tr>

<tr><td>**API ドキュメント**</td><td>[Java API リファレンス ドキュメント](https://azure.github.io/azure-cosmosdb-java/)</td></tr>

<tr><td>**SDK への協力**</td><td>[GitHub](https://github.com/Azure/azure-cosmosdb-java)</td></tr>

<tr><td>**はじめに**</td><td>[Async Java SDK の開始](https://github.com/Azure-Samples/azure-cosmos-db-sql-api-async-java-getting-started)</td></tr>

<tr><td>**Code sample**</td><td>[Github](https://github.com/Azure/azure-cosmosdb-java#usage-code-sample)</td></tr>

<tr><td>**パフォーマンスに関するヒント**</td><td>[Github の Readme](https://github.com/Azure/azure-cosmosdb-java#guide-for-prod)</td></tr>

<tr><td>**サポートされている最小ランタイム**</td><td>[JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)</td></tr>
</table></br>

## <a name="release-notes"></a>リリース ノート

### <a name="a-name102102"></a><a name="1.0.2"/>1.0.2
* 一意なインデックス ポリシーのサポートが追加されました。
* フィード オプションに、応答継続トークンのサイズを制限するためのサポートが追加されました。
* クロス パーティション クエリに、パーティション分割のサポートが追加されました。
* Json のタイムスタンプ シリアル化のバグを修正しました ([github #32](https://github.com/Azure/azure-cosmosdb-java/issues/32))。
* Json 列挙型のシリアル化のバグを修正しました。
* サイズが 2 MB のドキュメントを管理する際のバグを修正しました ([github #33](https://github.com/Azure/azure-cosmosdb-java/issues/33))。
* バグのため、依存関係 com.fasterxml.jackson.core:jackson-databind が 2.9.5 にアップグレードされました ([jackson-databind: github #1599](https://github.com/FasterXML/jackson-databind/issues/1599))
* バグのため、rxjava-extras への依存関係が 0.8.0.17 にアップグレードされました ([rxjava-extras: github #30](https://github.com/davidmoten/rxjava-extras/issues/30))。
* pom ファイル内のメタデータの記述が、ドキュメントの残りの部分とインラインとなるように更新されました。
* 構文の改善 ([github #41](https://github.com/Azure/azure-cosmosdb-java/issues/41))、([github #40](https://github.com/Azure/azure-cosmosdb-java/issues/40))。

### <a name="a-name101101"></a><a name="1.0.1"/>1.0.1
* クエリでのバック プレッシャーのサポートが追加されました。
* クエリでのパーティション キーの範囲 ID のサポートが追加されました。
* 要求ヘッダーでより大規模な継続トークンを許可できるように修正しました (bugfix github #24)。
* メイン スレッドの終了後、JVM が確実にシャットダウンされるように、Netty 依存関係を 4.1.22.Final にアップグレードしました。
* マスター ソースを読み取るときに、セッション トークンを渡さないように修正しました。
* サンプルをさらに追加しました。
* ベンチマーク シナリオをさらに追加しました。
* 適切な java doc 生成のために Java ヘッダー ファイルを修正しました。

### <a name="a-name100100"></a><a name="1.0.0"/>1.0.0
* [Netty ライブラリ](http://netty.io/)をゲートウェイ モードで使用し、非ブロッキング IO をエンド ツー エンドでサポートする GA SDK。 

## <a name="release-and-retirement-dates"></a>リリース日と提供終了日
Microsoft は、新しい/サポートされるバージョンに速やかに移行する目的で、SDK の提供終了を少なくともその **12 か月** 前に通知します。

新しい機能や機能性、および最適化は、現在の SDK にのみ追加されます。 そのため、常にできるだけ早く最新の SDK バージョンにアップグレードすることをお勧めします。

提供終了の SDK を使用した Cosmos DB への要求は、サービスによって拒否されます。

<br/>

| バージョン | リリース日 | 提供終了日 |
| --- | --- | --- |
| [1.0.2](#1.0.2) |2018 年 5 月 18 日|--- |
| [1.0.1](#1.0.1) |2018 年 4 月 20 日|--- |
| [1.0.0](#1.0.0) |2018 年 2 月 27 日|--- |

## <a name="faq"></a>FAQ
[!INCLUDE [cosmos-db-sdk-faq](../../includes/cosmos-db-sdk-faq.md)]

## <a name="see-also"></a>関連項目
Cosmos DB の詳細については、[Microsoft Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db/) サービス ページをご覧ください。

