---
title: "Azure Active Directory の条件付きアクセスの what if ツール - プレビュー | Microsoft Docs"
description: "Azure Active Directory の条件付きアクセス ポリシーの構成をテストする方法について説明します。"
services: active-directory
keywords: "アプリへの条件付きアクセス, Azure AD での条件付きアクセス, 企業リソースへの安全なアクセス, 条件付きアクセス ポリシー"
documentationcenter: 
author: MarkusVi
manager: mtillman
editor: 
ms.assetid: 8c1d978f-e80b-420e-853a-8bbddc4bcdad
ms.service: active-directory
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: na
ms.workload: identity
ms.date: 02/08/2018
ms.author: markvi
ms.reviewer: nigu
ms.openlocfilehash: 19ebb30164eee8e03a3cd8f18b6d575c6eee5438
ms.sourcegitcommit: 059dae3d8a0e716adc95ad2296843a45745a415d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="azure-active-directory-conditional-access-what-if-tool---preview"></a>Azure Active Directory の条件付きアクセスの what if ツール - プレビュー

[条件付きアクセス](active-directory-conditional-access-azure-portal.md)は、承認されたユーザーがクラウド アプリにアクセスする方法を制御できるようにする Azure Active Directory (Azure AD) の機能です。 環境内で条件付きアクセス ポリシーから予期される事柄を知るにはどうすればよいか。 この質問に答えるために、**条件付きアクセスの what-if ツール**を使用できます。

この記事では、このツールを使用して、条件付きアクセス ポリシーをテストする方法について説明します。

## <a name="what-it-is"></a>説明

**条件付きアクセスの what if ポリシー ツール**によって、条件付きアクセス ポリシーが環境に与える影響を理解することができます。 複数のサインインを手動で実行することでポリシーの適用をテストする代わりに、このツールを使用して、ユーザーのシミュレートされたサインインを評価できます。 シミュレーションでは、サインインがポリシーに与える影響を推定し、シミュレーション レポートが生成されます。 レポートには、適用された条件付きアクセス ポリシーだけではなく、[クラシック ポリシー](active-directory-conditional-access-migration.md#classic-policies)が存在する場合はそれらも一覧表示されます。    

what if ツールは、特定のユーザーに適用されるポリシーをすばやく判断する方法も提供します。 この情報は、たとえば問題をトラブルシューティングする必要がある場合に使用できます。  

## <a name="how-it-works"></a>動作のしくみ

**What-if ツールの条件付きアクセス** では、シミュレートするサインイン シナリオの設定を最初に構成する必要があります。 これらの設定には、以下が含まれます。

- テストするユーザー 

- ユーザーがアクセスを試みるクラウド アプリ

- 構成されたクラウド アプリへのアクセスが実行される条件
     
次の手順として、設定を評価するシミュレーションの実行を開始できます。 有効になっているポリシーのみが、評価実行の一部になります。


評価が完了すると、ツールは、影響を受けたポリシーのレポートを生成します。


## <a name="running-the-tool"></a>ツールの実行

**what if** ツールは、Azure Portal の **[[条件付きアクセス - ポリシー]](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ConditionalAccessBlade/Policies)** ページで見つけることができます。

ツールを起動するには、ポリシーの一覧の上部にあるツールバーで、**[What if]** をクリックします。

![What if](./media/active-directory-conditional-access-whatif/01.png)

評価を実行する前に、設定を構成する必要があります。

## <a name="settings"></a>設定

このセクションでは、シミュレーションの実行の設定について説明します。

![What if](./media/active-directory-conditional-access-whatif/02.png)


### <a name="user"></a>User

ユーザーは １ 人だけ選択できます。 これは唯一の必須フィールドです。

### <a name="cloud-apps"></a>クラウド アプリ

この設定の既定値は **[すべてのクラウド アプリ]** です。 既定の設定では、環境内で使用可能なすべてのポリシーの評価が実行されます。 特定のクラウド アプリに影響する範囲のポリシーに絞り込むことができます。


### <a name="ip-address"></a>IP アドレス

IP アドレスは、[場所の条件](active-directory-conditional-access-locations.md)を模倣するための 1 つの IPv4 アドレスです。 このアドレスは、ユーザーがサインインするために使用するデバイスのインターネット アドレスを表します。 デバイスの IP アドレスは、たとえば [What is my IP address](https://whatismyipaddress.com) に移動することで確認できます。    

### <a name="device-platforms"></a>デバイス プラットフォーム

この設定は、[デバイス プラットフォームの条件](active-directory-conditional-access-conditions.md#device-platforms)を模倣し、**[すべてのプラットフォーム (サポート対象外を含む)]** に相当します。 
### <a name="client-apps"></a>クライアント アプリ

この設定は、[クライアント アプリの条件](active-directory-conditional-access-conditions.md#client-apps)を模倣します。
既定では、この設定は、**[ブラウザー]** または **[モバイル アプリとデスクトップ クライアント]** のどちらかが選択されているか両方が選択されているすべてのポリシーを評価します。 **[Exchange ActiveSync (EAS)]** を適用するポリシーも検出されます。 以下を選択することで、この設定を絞り込むことができます。

- 少なくとも  **[ブラウザー]** が選択されているすべてのポリシーのみを評価するには **[ブラウザー]** を選択。 

- 少なくとも **[モバイルアプリとデスクトップ クライアント]** が選択されているすべてのポリシーのみを評価するには **[モバイル アプリとデスクトップ クライアント]** を選択。 


### <a name="sign-in-risk"></a>サインイン リスク

この設定は、[サインイン リスクの条件](active-directory-conditional-access-conditions.md#sign-in-risk)を模倣します。   


## <a name="evaluation"></a>評価 

**[What if]** をクリックして評価を開始します。 以下で構成されるレポートによって評価結果が示されます。 

![What if](./media/active-directory-conditional-access-whatif/03.png)

- 環境内にクラシック ポリシーが存在するかどうかを示すインジケーター
- ユーザーに適用されるポリシー
- ユーザーに適用されないポリシー


選択したクラウド アプリに適用される[クラシック ポリシー](active-directory-conditional-access-migration.md#classic-policies)が存在する場合は、インジケーターが表示されます。 インジケーターをクリックすると、クラシック ポリシー ページにリダイレクトされます。 クラシック ポリシー ページで、クラシック ポリシーを移行したり、単に無効にしたりできます。 このページを閉じることで、評価結果に戻ることができます。

選択したユーザーに適用されるポリシーの一覧で、ユーザーが満たす必要がある[許可コントロール](active-directory-conditional-access-controls.md#grant-controls)と[セッション](active-directory-conditional-access-controls.md#session-controls) コントロールの一覧も確認できます。

ユーザーに適用されないポリシーの一覧では、これらのポリシーが適用されない理由も確認できます。 表示されている各ポリシーの理由は、満たされていない最初の条件を表します。 ポリシーは、これ以上評価されないために無効なポリシーであるという理由で、適用されない場合があります。   



## <a name="next-steps"></a>次の手順

- 条件付きアクセスポリシーの構成方法については、「[Azure Active Directory での条件付きアクセスの基本](active-directory-conditional-access-azure-portal-get-started.md)」を参照してください。

- 環境に適用する条件付きアクセス ポリシーを構成する準備ができたら、「[Azure Active Directory の条件付きアクセスのベスト プラクティス](active-directory-conditional-access-best-practices.md)」を参照してください。 

- クラシック ポリシーを移行する場合は、「[Azure Portal でクラシック ポリシーを移行する](active-directory-conditional-access-migration.md)」を参照してください。  
