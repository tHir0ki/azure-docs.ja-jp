---
title: リモート監視ソリューション アクセラレータについてよく寄せられる質問 | Microsoft Docs
description: リモート監視ソリューション アクセラレータについてよく寄せられる質問
services: iot-suite
suite: iot-suite
documentationcenter: ''
author: dominicbetts
manager: timlt
editor: ''
ms.assetid: cb537749-a8a1-4e53-b3bf-f1b64a38188a
ms.service: iot-suite
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: na
ms.date: 02/15/2018
ms.author: dobett
ms.openlocfilehash: a65f2a90aedf5aa50016a6c5e5019094f202bf55
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
---
# <a name="frequently-asked-questions-for-remote-monitoring-solution-accelerator"></a>リモート監視ソリューション アクセラレータについてよく寄せられる質問

一般的な [FAQ](iot-accelerators-faq.md) もご覧ください。

### <a name="how-much-does-it-cost-to-provision-the-new-remote-monitoring-solution"></a>新しいリモート監視ソリューションのプロビジョニング料金はいくらですか。

新しいソリューション アクセラレータでは、次の 2 つのデプロイ オプションを提供します。

* より少ない開発コストを求めている開発者向け、またはデモや概念実証を構築しようとする顧客向けに設計されている*基本*オプション。
* 実稼働の準備が完了したインフラストラクチャをデプロイしたい企業向けに設計されている*標準*オプション。

### <a name="how-can-i-ensure-i-keep-my-costs-down-while-i-develop-my-solution"></a>ソリューションの開発中にコストの抑制を確認する方法は?

新しいリモート監視ソリューションでは 2 つの差別化されたデプロイを提供するだけでなく、オンデマンドですべてのシミュレートされたデバイスを有効または無効にする設定があります。 シミュレーションを無効にすると、ソリューションに取り込まれるデータが減少し、そのため、全体的なコストも減少します。

### <a name="what-is-the-difference-between-the-basic-and-standard-deployment-options-how-do-i-decide-between-the-two-deployment-options"></a>基本デプロイ オプションと標準デプロイ オプションでは何が違いますか? 2 つのデプロイ オプションの違いは何ですか?

各デプロイ オプションは、異なったニーズに対応します。 基本デプロイは初心者用や PoC、小規模なパイロット開発用に設計されています。 最低限必要なリソースとコストの削減によって簡素化されたアーキテクチャを提供します。 標準のデプロイは、実稼働の準備が完了したソリューションを構築およびカスタマイズするために設計されており、それを実現するのに必要な要素をもつデプロイを提供します。 信頼性と拡張性のため、アプリケーション マイクロサービスは Docker コンテナーとして構築され、オーケストレーター (既定では Kubernetes) を使用してデプロイされます。 オーケストレーターは、デプロイ、拡張、およびアプリケーションの管理を担当します。 現在のニーズに基づいて、オプションを選択してください。 1 つ、または、プロジェクトのステージによって両方の組み合わせを使用する場合があります。

### <a name="how-do-i-configure-a-dynamic-map-on-the-dashboard"></a>ダッシュボードに動的マップを構成するにはどうすればよいですか?

詳細については、「[Upgrade map key to see devices on a dynamic map](https://github.com/Azure/azure-iot-pcs-remote-monitoring-dotnet/wiki/Developer-Reference-Guide#upgrade-map-key-to-see-devices-on-a-dynamic-map)」(マップ キーをアップグレードして動的マップ上にデバイスを表示する) を参照してください。

### <a name="next-steps"></a>次の手順

IoT ソリューション アクセラレータの他の機能についても学習できます。

* [リモート監視ソリューション アクセラレータの機能について知る](iot-accelerators-remote-monitoring-explore.md)
* [予測メンテナンスのソリューション アクセラレータの概要](../iot-suite/iot-suite-predictive-overview.md)
* [接続済みファクトリ ソリューション アクセラレータの概要](iot-accelerators-connected-factory-overview.md)
* [徹底的な IoT セキュリティ](../iot-suite/securing-iot-ground-up.md)
