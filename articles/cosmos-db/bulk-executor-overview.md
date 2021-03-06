---
title: Azure Cosmos DB BulkExecutor ライブラリの概要 | Microsoft Docs
description: Azure Cosmos DB BulkExecutor ライブラリおよびそれを使用する利点やアーキテクチャについて説明します。
keywords: Java Bulk Executor
services: cosmos-db
author: tknandu
manager: kfile
ms.service: cosmos-db
ms.workload: data-services
ms.topic: article
ms.date: 05/07/2018
ms.author: ramkris
ms.openlocfilehash: d395376ad6cf191f8f355f6308f27e525da2911f
ms.sourcegitcommit: e221d1a2e0fb245610a6dd886e7e74c362f06467
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="azure-cosmos-db-bulkexecutor-library-overview"></a>Azure Cosmos DB BulkExecutor ライブラリの概要
 
Azure Cosmos DB は高速で柔軟なグローバル分散データベース サービスであり、弾力的にスケールアウトして以下をサポートするように設計されています。 

* 読み取りと書き込みの大きなスループット (1 秒あたり数百万回の操作)。  
* 予測可能なミリ秒単位の待機時間での、大量のトランザクション データと運用データの格納 (数百テラバイトまたはそれ以上)。  

BulkExecutor ライブラリは、この大量のスループットとストレージを活用するのに役立ちます。BulkExecutor ライブラリを使うと、一括インポートと一括更新の API により、Azure Cosmos DB で一括操作を実行できます。 以下のセクションでは BulkExecutor ライブラリの機能についてさらに説明します。 

> [!NOTE] 
> 現時点では、BulkExecutor ライブラリはインポート操作と更新操作をサポートし、Azure Cosmos DB SQL API アカウントにおいてのみサポートされます。 ライブラリの更新については、[.NET](sql-api-sdk-bulk-executor-dot-net.md) および [Java](sql-api-sdk-bulk-executor-java.md) のリリース ノートをご覧ください。
 
## <a name="key-features-of-the-bulkexecutor-library"></a>BulkExecutor ライブラリの主な機能  
 
* コンテナーに割り当てられているスループットを最大限に利用するために必要なクライアント側計算リソースが大幅に減少します。 クライアント コンピューターの CPU を最大限に利用した状態で比較した場合、一括インポート API を使ってデータを書き込むシングル スレッド アプリケーションは、データを並列に書き込むマルチ スレッド アプリケーションの 10 倍の書き込みスループットを達成します。  

* ライブラリ内で効率的に処理することにより、要求スロットリング、要求タイムアウト、およびその他の一時的な例外を処理するアプリケーション ロジックを記述する単調なタスクを抽象化します。  

* 一括操作を実行するアプリケーションをスケールアウトするシンプルなメカニズムを提供します。Azure VM で実行する 1 つの BulkExecutor インスタンスは 500 K RU/秒以上を消費でき、個々のクライアント VM にインスタンスを追加することでより高いスループットを実現できます。  
 
* スケールアウト アーキテクチャを使用することで、1 時間以内に 1 テラバイトを超えるデータを一括インポートできます。  

* Azure Cosmos DB コンテナー内の既存のデータを、パッチとして一括更新できます。 
 
## <a name="how-does-the-bulk-executor-operate"></a>BulkExecutor の動作方法 

ドキュメントをインポートまたは更新する一括操作がエンティティのバッチでトリガーされると、最初に、その Azure Cosmos DB パーティション キーの範囲に対応するバケットにシャッフルされます。 パーティション キーの範囲に対応する各バケット内では、バケットがミニバッチに分割され、各ミニバッチはサーバー側でコミットされるペイロードとして機能します。 BulkExecutor ライブラリには、これらのミニバッチをパーティション キーの範囲内と範囲間の両方で同時実行するための最適化が組み込まれています。 次の図では、BulkExecutory が異なるパーティション キーにデータをバッチ処理する方法を示しています。  

![BulkExecutor のアーキテクチャ](./media/bulk-executor-overview/bulk-executor-architecture.png)

BulkExecutor ライブラリは、コレクションに割り当てられているスループットを最大限に活用します。 Azure Cosmos DB の各パーティション キー範囲に対して  [AIMD スタイルの輻輳制御メカニズム](https://tools.ietf.org/html/rfc5681)を使用し、スロットリングとタイムアウトを効率的に処理します。 

## <a name="next-steps"></a>次の手順 
  
* [.NET](bulk-executor-dot-net.md) と [Java](bulk-executor-java.md) で BulkExecutor ライブラリを使用するサンプル アプリケーションを試して、さらに詳しく学習してください。  
* [.NET](sql-api-sdk-bulk-executor-dot-net.md) と [Java](sql-api-sdk-bulk-executor-java.md) の BulkExecutor SDK 情報とリリース ノートを確認してください。
* BulkExecutor ライブラリは Cosmos DB Spark コネクタに統合されています。詳しくは、[Azure Cosmos DB Spark コネクタ](spark-connector.md)に関する記事をご覧ください。  
* BulkExecutor ライブラリは、データをコピーするために Azure Data Factory の [Azure Cosmos DB コネクタ](https://aka.ms/bulkexecutor-adf-v2)の新しいバージョンにも統合されています。
