---
title: 'チュートリアル: Azure Active Directory と SmarterU の統合 | Microsoft Docs'
description: Azure Active Directory と SmarterU の間でシングル サインオンを構成する方法について説明します。
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.assetid: 95fe3212-d052-4ac8-87eb-ac5305227e85
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 06/23/2017
ms.author: jeedes
ms.openlocfilehash: a6845b023548c86ef90cac3aab35f22069daf34d
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2018
ms.locfileid: "34347256"
---
# <a name="tutorial-azure-active-directory-integration-with-smarteru"></a>チュートリアル: Azure Active Directory と SmarterU の統合

このチュートリアルでは、SmarterU と Azure Active Directory (Azure AD) を統合する方法について説明します。

SmarterU と Azure AD の統合には、次の利点があります。

- SmarterU にアクセスする Azure AD ユーザーを制御できます。
- ユーザーが自分の Azure AD アカウントで自動的に SmarterU にサインオン (シングル サインオン) できるように、設定が可能です。
- 1 つの中央サイト (Azure Portal) でアカウントを管理できます

SaaS アプリと Azure AD の統合の詳細については、「[Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

Azure AD と SmarterU の統合を構成するには、次のものが必要です。

- Azure AD サブスクリプション
- SmarterU でのシングル サインオンが有効なサブスクリプション

> [!NOTE]
> このチュートリアルの手順をテストする場合、運用環境を使用しないことをお勧めします。

このチュートリアルの手順をテストするには、次の推奨事項に従ってください。

- 必要な場合を除き、運用環境は使用しないでください。
- Azure AD の評価環境がない場合は、 [こちら](https://azure.microsoft.com/pricing/free-trial/)から 1 か月の評価版を入手できます。

## <a name="scenario-description"></a>シナリオの説明
このチュートリアルでは、テスト環境で Azure AD のシングル サインオンをテストします。 このチュートリアルで説明するシナリオは、主に次の 2 つの要素で構成されています。

1. ギャラリーからの SmarterU の追加
2. Azure AD シングル サインオンの構成とテスト

## <a name="adding-smarteru-from-the-gallery"></a>ギャラリーからの SmarterU の追加
Azure AD への SmarterU の統合を構成するには、ギャラリーから管理対象 SaaS アプリの一覧に SmarterU を追加する必要があります。

**ギャラリーから SmarterU を追加するには、次の手順に従います。**

1. **[Azure Portal](https://portal.azure.com)** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。 

    ![Active Directory][1]

2. **[エンタープライズ アプリケーション]** に移動します。 次に、**[すべてのアプリケーション]** に移動します。

    ![[アプリケーション]][2]
    
3. 新しいアプリケーションを追加するには、ダイアログの上部にある **[新しいアプリケーション]** をクリックします。

    ![[アプリケーション]][3]

4. 検索ボックスに、「**SmarterU**」と入力します。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_search.png)

5. 結果ウィンドウで **[SmarterU]** を選択し、**[追加]** をクリックして、アプリケーションを追加します。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_addfromgallery.png)

##  <a name="configuring-and-testing-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成とテスト
このセクションでは、"Britta Simon" というテスト ユーザーに基づいて、SmarterU で Azure AD のシングル サインオンを構成し、テストします。

シングル サインオンを機能させるには、Azure AD ユーザーに対応する SmarterU ユーザーが Azure AD で認識されている必要があります。 言い換えると、Azure AD ユーザーと SmarterU の関連ユーザーの間で、リンク関係が確立されている必要があります。

SmarterU で、Azure AD の **[ユーザー名]** の値を **[Username]\(ユーザー名\)** の値として割り当ててリンク関係を確立します。

SmarterU で Azure AD のシングル サインオンを構成してテストするには、次の構成要素を完了する必要があります。

1. **[Configuring Azure AD Single Sign-On](#configuring-azure-ad-single-sign-on)** - ユーザーがこの機能を使用できるようにします。
2. **[Azure AD のテスト ユーザーの作成](#creating-an-azure-ad-test-user)** - Britta Simon で Azure AD のシングル サインオンをテストします。
3. **[SmarterU テスト ユーザーの作成](#creating-a-smarteru-test-user)** - SmarterU で Britta Simon に対応するユーザーを作成し、Azure AD の Britta Simon にリンクさせます。
4. **[Azure AD テスト ユーザーの割り当て](#assigning-the-azure-ad-test-user)** - Britta Simon が Azure AD のシングル サインオンを使用できるようにします。
5. **[シングル サインオンのテスト](#testing-single-sign-on)** - 構成が機能するかどうかを確認します。

### <a name="configuring-azure-ad-single-sign-on"></a>Azure AD シングル サインオンの構成

このセクションでは、Azure Portal で Azure AD のシングル サインオンを有効にし、SmarterU アプリケーションでシングル サインオンを構成します。

**SmarterU で Azure AD シングル サインオンを構成するには、次の手順に従います。**

1. Azure Portal の **SmarterU** アプリケーション統合ページで、**[シングル サインオン]** をクリックします。

    ![[Configure Single Sign-On]][4]

2. **[シングル サインオン]** ダイアログで、**[モード]** として **[SAML ベースのサインオン]** を選択し、シングル サインオンを有効にします。
 
    ![[Configure Single Sign-On]](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_samlbase.png)

3. **[SmarterU のドメインと URL]** セクションで、次の手順を実行します。 

    ![[Configure Single Sign-On]](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_url.png)

    **[識別子]** ボックスに、URL として「`https://www.smarteru.com/`」と入力します。

4. **[SAML 署名証明書]** セクションで、**[Metadata XML (メタデータ XML)]** をクリックし、コンピューターにメタデータ ファイルを保存します。

    ![[Configure Single Sign-On]](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_certificate.png) 

5. **[保存]** ボタンをクリックします。

    ![[Configure Single Sign-On]](./media/active-directory-saas-smarteru-tutorial/tutorial_general_400.png)

6. 別の Web ブラウザー ウィンドウで、SmarterU 企業サイトに管理者としてログインします。

7. 上部のメニューで **[Account Settings]** をクリックします。
   
    ![Account Settings](./media/active-directory-saas-smarteru-tutorial/IC777326.png "Account Settings")

8. アカウント構成ページで、次の手順に従います。
   
    ![External Authorization](./media/active-directory-saas-smarteru-tutorial/IC777327.png "External Authorization") 
 
      a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[Enable External Authorization]** を選択します。
  
      b. **[Master Login Control]** セクションで、**[SmarterU]** タブを選択します。
  
      c. **[User Default Login]** セクションで、**[SmarterU]** タブを選択します。
  
      d. **[Enable Okta]** を選択します。
  
      e. ダウンロードしたメタデータ ファイルの内容をコピーし、 **[Okta Metadata]** テキスト ボックスに貼り付けます。
  
      f. **[Save]** をクリックします。

> [!TIP]
> アプリのセットアップ中、[Azure Portal](https://portal.azure.com) 内で上記の手順の簡易版を確認できるようになりました。  **[Active Directory] の [エンタープライズ アプリケーション]** セクションからこのアプリを追加した後、**[シングル サインオン]** タブをクリックし、一番下の **[構成]** セクションから組み込みドキュメントにアクセスするだけです。 組み込みドキュメント機能の詳細については、[Azure AD の組み込みドキュメント]( https://go.microsoft.com/fwlink/?linkid=845985)に関するページを参照してください。
> 

### <a name="creating-an-azure-ad-test-user"></a>Azure AD のテスト ユーザーの作成
このセクションの目的は、Azure Portal で Britta Simon というテスト ユーザーを作成することです。

![Azure AD ユーザーの作成][100]

**Azure AD でテスト ユーザーを作成するには、次の手順に従います。**

1. **Azure Portal** の左側のナビゲーション ウィンドウで、**[Azure Active Directory]** アイコンをクリックします。

    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/create_aaduser_01.png) 

2. **[ユーザーとグループ]** に移動し、**[すべてのユーザー]** をクリックして、ユーザーの一覧を表示します。
    
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/create_aaduser_02.png) 

3. ダイアログの上部にある **[追加]** をクリックして、**[ユーザー]** ダイアログを開きます。
 
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/create_aaduser_03.png) 

4. **[ユーザー]** ダイアログ ページで、次の手順を実行します。
 
    ![Azure AD のテスト ユーザーの作成](./media/active-directory-saas-smarteru-tutorial/create_aaduser_04.png) 

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[名前]** ボックスに「**BrittaSimon**」と入力します。

    b. **[ユーザー名]** ボックスに BrittaSimon の**電子メール アドレス**を入力します。

    c. **[パスワードを表示]** を選択し、**[パスワード]** の値をメモします。

    d. **Create** をクリックしてください。
 
### <a name="creating-a-smarteru-test-user"></a>SmarterU テスト ユーザーの作成

Azure AD ユーザーが SmarterU にログインできるようにするには、そのユーザーを SmarterU にプロビジョニングする必要があります。

SmarterU の場合、プロビジョニングは手動で行います。

**ユーザー アカウントをプロビジョニングするには、次の手順に従います。**

1. **SmarterU** テナントにログインします。

2. **[Users]** タブに移動します。

3. ユーザー セクションで、次の手順に従います。
   
    ![New User](./media/active-directory-saas-smarteru-tutorial/IC777329.png "New User")  

    a.[サインオン URL] ボックスに、次のパターンを使用して、ユーザーが RightScale アプリケーションへのサインオンに使用する URL を入力します。 **[+User]** をクリックします。
    
    b. 次のテキスト ボックスに、Azure AD のユーザー アカウントの関連する属性の値を入力します。**[Primary Email]**、**[Employee ID]**、**[Password]**、**[Verify Password]**、**[Given Name]**、**[Surname]**。
    
    c. **[Active]** をクリックします。 
    
    d. **[Save]** をクリックします。

>[!NOTE]
>SmarterU から提供されている他の SmarterU ユーザー アカウント作成ツールまたは API を使用して、AAD ユーザー アカウントをプロビジョニングできます。
> 

### <a name="assigning-the-azure-ad-test-user"></a>Azure AD テスト ユーザーの割り当て

このセクションでは、Britta Simon に SmarterU へのアクセスを許可することで、このユーザーが Azure シングル サインオンを使用できるようにします。

![ユーザーの割り当て][200] 

**SmarterU に Britta Simon を割り当てるには、次の手順に従います。**

1. Azure Portal でアプリケーション ビューを開き、ディレクトリ ビューに移動します。次に、**[エンタープライズ アプリケーション]** に移動し、**[すべてのアプリケーション]** をクリックします。

    ![ユーザーの割り当て][201] 

2. アプリケーションの一覧で **[SmarterU]** を選択します。

    ![[Configure Single Sign-On]](./media/active-directory-saas-smarteru-tutorial/tutorial_smarteru_app.png) 

3. 左側のメニューで **[ユーザーとグループ]** をクリックします。

    ![ユーザーの割り当て][202] 

4. **[追加]** ボタンをクリックします。 次に、**[割り当ての追加]** ダイアログで **[ユーザーとグループ]** を選択します。

    ![ユーザーの割り当て][203]

5. **[ユーザーとグループ]** ダイアログで、ユーザーの一覧から **[Britta Simon]** を選択します。

6. **[ユーザーとグループ]** ダイアログで **[選択]** をクリックします。

7. **[割り当ての追加]** ダイアログで **[割り当て]** ボタンをクリックします。
    
### <a name="testing-single-sign-on"></a>シングル サインオンのテスト

このセクションでは、アクセス パネルを使用して Azure AD のシングル サインオン構成をテストします。
 
アクセス パネルで [SmarterU] タイルをクリックすると、自動的に SmarterU アプリケーションにサインオンします。
アクセス パネルの詳細については、[アクセス パネルの概要](active-directory-saas-access-panel-introduction.md)に関する記事を参照してください。 


## <a name="additional-resources"></a>その他のリソース

* [SaaS アプリと Azure Active Directory を統合する方法に関するチュートリアルの一覧](active-directory-saas-tutorial-list.md)
* [Azure Active Directory のアプリケーション アクセスとシングル サインオンとは](manage-apps/what-is-single-sign-on.md)

<!--Image references-->

[1]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-smarteru-tutorial/tutorial_general_203.png

