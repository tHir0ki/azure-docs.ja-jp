---
title: Azure Network Watcher 機能を使用するために必要なアクセス許可 | Microsoft Docs
description: Network Watcher 機能を使用するために必要な、Azure ロールベースのアクセス制御のアクセス許可について説明します。
services: network-watcher
documentationcenter: ''
author: jimdial
manager: jeconnoc
editor: ''
ms.assetid: ''
ms.service: network-watcher
ms.workload: ''
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/10/2018
ms.author: jdial
ms.openlocfilehash: 09f3a1e1d9c6796cb55ae8f0ab18bf8e1b3fa198
ms.sourcegitcommit: fc64acba9d9b9784e3662327414e5fe7bd3e972e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2018
ms.locfileid: "34077757"
---
# <a name="role-based-access-control-permissions-required-to-use-network-watcher-capabilities"></a>Network Watcher 機能を使用するために必要な、Azure ロールベースのアクセス制御のアクセス許可

Azure のロール ベース アクセス制御 (RBAC) を使用すると、割り当てられた職務を遂行する必要がある組織内のメンバーに特定のアクションのみを割り当てることができます。 Network Watcher 機能を使用するには、Azure にログインするアカウントを、[所有者](/role-based-access-control/built-in-roles.md?toc=%2fazure%2fnetwork-watcher%2ftoc.json#owner)、[共同作成者](/role-based-access-control/built-in-roles.md?toc=%2fazure%2fnetwork-watcher%2ftoc.json#contributor)、または[ネットワーク共同作業者](../role-based-access-control/built-in-roles.md?toc=%2fazure%2fnetwork-watcher%2ftoc.json#network-contributor)の組み込みのロールに割り当てるか、Network Watcher 機能の各セクションの下に一覧表示されているアクションが割り当てられている[カスタム ロール](../role-based-access-control/custom-roles.md?toc=%2fazure%2fnetwork-watcher%2ftoc.json)に割り当てる必要があります。 Network Watcher の機能の詳細については、「[Network Watcher とは](network-watcher-monitoring-overview.md)」を参照してください。

## <a name="network-watcher"></a>Network Watcher

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/read                              | Network Watcher を取得する                                          |
| Microsoft.Network/networkWatchers/write                             | Network Watcher を作成する                             |
| Microsoft.Network/networkWatchers/delete                            | Network Watcher を削除する                                       |

## <a name="nsg-flow-logs"></a>NSG フロー ログ

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/configureFlowLog/action           | フロー ログを構成する                                           |
| Microsoft.Network/networkWatchers/queryFlowLogStatus/action         | フロー ログのクエリ状態                                    |

## <a name="connection-troubleshoot"></a>接続のトラブルシューティング

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/queryTroubleshootResult/action    | 接続のトラブルシューティング テストのクエリ結果                |
| Microsoft.Network/networkWatchers/troubleshoot/action               | 接続のトラブルシューティング テストの実行                             |

## <a name="connection-monitor"></a>接続モニター

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/connectionMonitors/start/action   | 接続モニターを起動する                                     |
| Microsoft.Network/networkWatchers/connectionMonitors/stop/action    | 接続モニターを停止する                                      |
| Microsoft.Network/networkWatchers/connectionMonitors/query/action   | 接続モニターのクエリを実行する                                     |
| Microsoft.Network/networkWatchers/connectionMonitors/read           | 接続モニターを取得する                                       |
| Microsoft.Network/networkWatchers/connectionMonitors/write          | 接続モニターを作成する                                    |
| Microsoft.Network/networkWatchers/connectionMonitors/delete         | 接続モニターを削除する                                    |

## <a name="packet-capture"></a>パケット キャプチャ

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/packetCaptures/queryStatus/action | パケット キャプチャの状態のクエリを実行する                           |
| Microsoft.Network/networkWatchers/packetCaptures/stop/action        | パケット キャプチャを停止する                                          |
| Microsoft.Network/networkWatchers/packetCaptures/read               | パケット キャプチャを取得する                                           |
| Microsoft.Network/networkWatchers/packetCaptures/write              | パケット キャプチャを作成する                                        |
| Microsoft.Network/networkWatchers/packetCaptures/delete             | パケット キャプチャを削除する                                        |

## <a name="ip-flow-verify"></a>IP フロー検証

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/ipFlowVerify/action               | IP フローを確認する                                              |

## <a name="next-hop"></a>次のホップ

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/nextHop/action                    | VM から次ホップを取得する                                     |

## <a name="network-security-group-view"></a>ネットワーク セキュリティ グループ ビュー

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/securityGroupView/action          | セキュリティ グループを表示する                                           |

## <a name="topology"></a>トポロジ

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/topology/action                   | トポロジを取得する                                                   |

## <a name="reachability-report"></a>到達可能性レポート

| アクションを表示します。                                                              | Name                                                           |
| ---------                                                           | -------------                                                  |
| Microsoft.Network/networkWatchers/azureReachabilityReport/action    | Azure 到達可能性レポートを取得する                               |

## <a name="additional-actions"></a>追加のアクション

Network Watcher 機能には、次のアクションも必要です。

- Microsoft.Storage/Read
- Microsoft.Authorization/Read
- Microsoft.Resources/subscriptions/resourceGroups/Read
- Microsoft.Storage/storageAccounts/listServiceSas/Action
- Microsoft.Storage/storageAccounts/listAccountSas/Action
- Microsoft.Storage/storageAccounts/listKeys/Action
- Microsoft.Compute/virtualMachines/Read
- Microsoft.Compute/virtualMachines/Write
- Microsoft.Compute/virtualMachineScaleSets/Read
- Microsoft.Compute/virtualMachineScaleSets/Write
- Microsoft.Insights/alertRules/*
- Microsoft.Support/*