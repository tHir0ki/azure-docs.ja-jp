---
title: Azure Import/Export ツールのトラブルシューティング | Microsoft Docs
description: Azure Import/Export ツールを使用する際によく見られるいくつかの問題と対処方法について説明します。
author: muralikk
manager: syadav
editor: tysonn
services: storage
documentationcenter: ''
ms.assetid: b91ca5eb-c557-460a-9afc-0590b38471f9
ms.service: storage
ms.workload: storage
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 01/15/2017
ms.author: muralikk
ms.openlocfilehash: 7bfda602dbc0ea47828a7c9243b8b9b09ec78432
ms.sourcegitcommit: 6699c77dcbd5f8a1a2f21fba3d0a0005ac9ed6b7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/11/2017
ms.locfileid: "23059367"
---
# <a name="troubleshooting-the-azure-importexport-tool"></a>Azure Import/Export ツールのトラブルシューティング
Microsoft Azure Import/Export ツールでは、問題が発生するとエラー メッセージが返されます。 この記事では、ユーザーがよく経験する問題について説明します。  
  
## <a name="a-copy-session-fails-what-i-should-do"></a>コピー セッションが失敗しました。どうすればよいですか?  
 コピー セッションが失敗した場合、2 つの対処方法があります。  
  
 ネットワーク シェアが一時的にオフラインだったが、今はオンラインに戻っているなど、エラーが再試行可能な場合、コピー セッションを再開できます。 コマンド ライン パラメータ―に誤ったソース ファイル ディレクトリを指定したなど、エラーが再試行できない場合、コピー セッションを中断する必要があります。 コピー セッションの再開と中断に関する詳細は、「[インポート ジョブ用のハード ドライブを準備する](../storage-import-export-tool-preparing-hard-drives-import-v1.md)」をご覧ください。  
  
## <a name="i-cant-resume-or-abort-a-copy-session"></a>コピー セッションを中断または再開できません。  
 ドライブのコピー セッションがはじめての場合、「The first copy session cannot be resumed or aborted (最初のコピー セッションを再開または中断できません) 」というエラー メッセージが表示されます。 この場合、古いジャーナル ファイルを削除し、コマンドを再実行できます。  
  
 ドライブのコピー セッションが 2 回目以降の場合、常に再開または中断できます。  
  
## <a name="i-lost-the-journal-file-can-i-still-create-the-job"></a>ジャーナル ファイルを失ってしまいましたが、ジョブを作成できますか?  
 ドライブのジャーナル ファイルには、ドライブへのデータ コピーに関するすべての情報が格納されており、ドライブにファイルを追加する際に必要であるほか、インポート ジョブの作成にも使用されます。 ジャーナル ファイルが失われた場合、ドライブのすべてのコピー セッションを再実行する必要があります。  
  
## <a name="next-steps"></a>次のステップ
 
* [Azure Import/Export ツールの設定](../storage-import-export-tool-setup-v1.md)   
* [インポート ジョブ用のハード ドライブを準備する](../storage-import-export-tool-preparing-hard-drives-import-v1.md)   
* [コピー ログ ファイルによるジョブの状態の確認](../storage-import-export-tool-reviewing-job-status-v1.md)   
* [インポート ジョブの修復](../storage-import-export-tool-repairing-an-import-job-v1.md)   
* [エクスポート ジョブの修復](../storage-import-export-tool-repairing-an-export-job-v1.md)
