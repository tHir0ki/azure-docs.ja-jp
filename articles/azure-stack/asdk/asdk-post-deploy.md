---
title: Azure Stack Development Kit (ASDK) のデプロイ後の構成 | Microsoft Docs
description: Azure Stack Development Kit (ASDK) をインストールした後に行うことをお勧めする構成変更について説明します。
services: azure-stack
documentationcenter: ''
author: jeffgilb
manager: femila
editor: ''
ms.assetid: ''
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 05/01/2018
ms.author: jeffgilb
ms.reviewer: misainat
ms.openlocfilehash: 4b58f3496b25e4fc04761b9df6e27f8313b35fe9
ms.sourcegitcommit: c47ef7899572bf6441627f76eb4c4ac15e487aec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33204634"
---
# <a name="post-asdk-installation-configuration-tasks"></a>ASDK インストール後の構成タスク
[ASDK をインストール](asdk-install.md)した後、推奨されるインストール後の構成変更がいくつかあります。 

## <a name="install-azure-stack-powershell"></a>Azure Stack PowerShell のインストール 
Azure Stack を使用するには、Azure Stack と互換性のある Azure PowerShell モジュールが必要です。

Azure Stack 用の PowerShell コマンドは、PowerShell ギャラリーを介してインストールされます。 PSGallery リポジトリを登録するには、PowerShell セッションを管理者特権で開き、次のコマンドを実行します。

``` Powershell
Set-PSRepository `
  -Name "PSGallery" `
  -InstallationPolicy Trusted
```

 Azure Stack と互換性のある AzureRM モジュールは、API バージョン プロファイルを使用してインストールされます。 Azure Stack には 2017-03-09-profile API バージョン プロファイルが必要です。このプロファイルは、AzureRM.Bootstrapper モジュールをインストールすることで利用できます。 
 
 ASDK ホスト コンピューターへのインターネット接続の有無にかかわらず、最新の Azure Stack PowerShell モジュールをインストールすることができます。

> [!IMPORTANT]
> 必要なバージョンをインストールする前に、必ず[既存の Azure PowerShell モジュールをアンインストールしてください](.\.\azure-stack-powershell-install.md#uninstall-existing-versions-of-powershell)。

- ASDK ホスト コンピューターからの**インターネット接続がある場合**。 次の PowerShell スクリプトを実行して、これらのモジュールを開発キット インストールにインストールします。

  ``` PowerShell
  # Install the AzureRM.Bootstrapper module. Select Yes when prompted to install NuGet 
  Install-Module `
    -Name AzureRm.BootStrapper

  # Install and import the API Version Profile required by Azure Stack into the current PowerShell session.
  Use-AzureRmProfile `
    -Profile 2017-03-09-profile -Force

  Install-Module `
    -Name AzureStack `
    -RequiredVersion 1.2.11
  ```
  インストールに成功した場合、出力に AzureRM および AzureStack モジュールが表示されます。

- ASDK ホスト コンピューターからの**インターネット接続がない場合**。 接続が切断されたシナリオでは、まず次の PowerShell コマンドを使って、インターネット接続が確立されたマシンに PowerShell モジュールをダウンロードします。

  ```PowerShell
  $Path = "<Path that is used to save the packages>"

  Save-Package `
    -ProviderName NuGet `
    -Source https://www.powershellgallery.com/api/v2 `
    -Name AzureRM `
    -Path $Path `
    -Force `
    -RequiredVersion 1.2.11

  Save-Package `
    -ProviderName NuGet `
    -Source https://www.powershellgallery.com/api/v2 `
    -Name AzureStack `
    -Path $Path `
    -Force `
    -RequiredVersion 1.2.11
  ```
  ここで、ダウンロードしたパッケージを ASDK コンピューターにコピーし、その場所を既定のリポジトリとして登録し、そのリポジトリから AzureRM および AzureStack モジュールをインストールします。

    ```PowerShell
    $SourceLocation = "<Location on the development kit that contains the PowerShell packages>"
    $RepoName = "MyNuGetSource"

    Register-PSRepository `
      -Name $RepoName `
      -SourceLocation $SourceLocation `
      -InstallationPolicy Trusted

    Install-Module AzureRM `
      -Repository $RepoName

    Install-Module AzureStack `
      -Repository $RepoName
    ```

## <a name="download-the-azure-stack-tools"></a>Azure Stack ツールをダウンロードする
[AzureStack-Tools](https://github.com/Azure/AzureStack-Tools) は PowerShell モジュールをホストする GitHub リポジトリで、リソースの管理と Azure Stack へのデプロイに使用できます。 これらのツールを入手するには、GitHub リポジトリを複製するか、次のスクリプトを実行して AzureStack-Tools フォルダーをダウンロードします。

  ```PowerShell
  # Change directory to the root directory. 
  cd \

  # Enforce usage of TLSv1.2 to download the Azure Stack tools archive from GitHub
  [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
  invoke-webrequest `
    https://github.com/Azure/AzureStack-Tools/archive/master.zip `
    -OutFile master.zip

  # Expand the downloaded files.
  expand-archive master.zip `
    -DestinationPath . `
    -Force

  # Change to the tools directory.
  cd AzureStack-Tools-master
  ```

## <a name="validate-the-asdk-installation"></a>ASDK インストールを検証する
ASDK のデプロイが成功したことを確認するには、次の手順に従って Test-AzureStack コマンドレットを使用できます。

1. ASDK ホスト コンピューターで AzureStack\CloudAdmin としてログインします。
2. PowerShell を (PowerShell ISE ではなく) 管理者として開きます。
3. 次のコマンドを実行します: `Enter-PSSession -ComputerName AzS-ERCS01 -ConfigurationName PrivilegedEndpoint`
4. 次のコマンドを実行します: `Test-AzureStack`

テストが完了するまでに数分かかります。 インストールが成功した場合、出力は次のようになります。

![test-azurestack](media/asdk-post-deploy/test-azurestack.png)

エラーがあった場合は、トラブルシューティング手順に従ってヘルプを取得します。

## <a name="activate-the-administrator-and-tenant-portals"></a>管理者およびテナント ポータルのアクティブ化
Azure AD を使用するデプロイの後は、Azure Stack の管理者とテナント ポータルの両方をアクティブにする必要があります。 アクティブにすることによって、ディレクトリの全ユーザーに関して適切なアクセス許可 (同意のページに一覧が表示されます) を Azure Stack ポータルと Azure Resource Manager に付与することに同意したことになります。

- 管理者ポータルの場合は、https://adminportal.local.azurestack.external/guest/signup に移動して情報を確認し、**[Accept]\(承諾\)** をクリックします。 同意後は、ディレクトリ テナント管理者ではないサービス管理者を追加することができます。

- テナント ポータルの場合は、https://portal.local.azurestack.external/guest/signup に移動して情報を確認し、**[Accept]\(承諾\)** をクリックします。 同意後は、ディレクトリのユーザーがテナント ポータルにサインインすることができます。 

> [!NOTE] 
> ポータルがアクティブにされていない場合は、ディレクトリ管理者だけがポータルにサインインし、使用することができます。 他のユーザーがサインインすると、管理者が他のユーザーにアクセス許可を付与していないことを示すエラーが表示されます。 Azure Stack の登録先ディレクトリに管理者がネイティブに属していない場合は、Azure Stack ディレクトリをアクティベーション URL に追加する必要があります。 Azure Stack が fabrikam.onmicrosoft.com に登録されており、管理者ユーザーが admin@contoso.com の場合は、https://portal.local.azurestack.external/guest/signup/fabrikam.onmicrosoft.com に移動してポータルをアクティブにします。 

## <a name="reset-the-password-expiration-policy"></a>パスワードの有効期限ポリシーのリセット 
開発キットのホストのパスワードが評価期間の終了前に期限切れにならないようにするには、ASDK のデプロイ後に次の手順を実行します。

### <a name="to-change-the-password-expiration-policy-from-powershell"></a>Powershell からパスワードの有効期限ポリシーを変更するには:
管理者特権の PowerShell コンソールで、次のコマンドを実行します。

```powershell
Set-ADDefaultDomainPasswordPolicy -MaxPasswordAge 180.00:00:00 -Identity azurestack.local
```

### <a name="to-change-the-password-expiration-policy-manually"></a>パスワードの有効期限ポリシーを手動で変更するには:
1. 開発キットのホストで、**[グループ ポリシーの管理]** (GPMC.MMC) を開き、**[グループ ポリシーの管理]**、**[フォレスト: azurestack.local]**、**[ドメイン]**、**[azurestack.local]** に移動します。
2. **[既定のドメイン ポリシー]** を右クリックし、**[編集]** をクリックします。
3. グループ ポリシー管理エディターで、**[コンピューターの構成]**、**[ポリシー]**、**[Windows の設定]**、**[セキュリティの設定]**、**[アカウント ポリシー]**、**[パスワード ポリシー]** の順に移動します。
4. 右側のウィンドウの **[パスワードの有効期間]** をダブルクリックします。
5. **[Maximum password age Properties]\(パスワードの有効期間プロパティ\)** ダイアログ ボックスで、**[パスワードの有効期限]** の値を **180** に変更し、**[OK]** をクリックします。

![グループ ポリシー管理コンソール](media/asdk-post-deploy/gpmc.png)


## <a name="next-steps"></a>次の手順
[ASDK の Azure への登録](asdk-register.md)
