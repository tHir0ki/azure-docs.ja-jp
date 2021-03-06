---
title: Azure IoT Central でデバイスを監視する | Microsoft Docs
description: オペレーターとして Azure IoT Central アプリケーションを使用して、デバイスを監視します。
services: iot-central
author: tanmaybhagwat
ms.author: tanmayb
ms.date: 04/16/2018
ms.topic: tutorial
ms.prod: microsoft-iot-central
manager: timlt
ms.openlocfilehash: a07c9e3c28fadaead8bfaaebe4d1ee06ac66a99e
ms.sourcegitcommit: eb75f177fc59d90b1b667afcfe64ac51936e2638
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2018
ms.locfileid: "34201389"
---
# <a name="use-azure-iot-central-to-monitor-your-devices"></a>Azure IoT Central を使用してデバイスを監視する

このチュートリアルでは、オペレーター向けに Microsoft Azure IoT Central アプリケーションを使用して、デバイスを監視し、設定を変更する方法について説明します。

このチュートリアルで学習する内容は次のとおりです。

> [!div class="checklist"]
> * 通知の受信
> * 問題の調査
> * 問題の修復

## <a name="prerequisites"></a>前提条件

始める前に、作成者が Azure IoT Central アプリケーションを作成する 3 つの作成者向けチュートリアルを完了する必要があります。

* [新しいデバイスの種類を定義する](tutorial-define-device-type.md)
* [デバイスのルールとアクションを構成する](tutorial-configure-rules.md)
* [オペレーターのビューをカスタマイズする](tutorial-customize-operator.md)

## <a name="receive-a-notification"></a>通知の受信

Azure IoT Central では、デバイスに関する通知を電子メール メッセージとして送信します。 作成者は、コネクテッド空調デバイスの温度がしきい値を超えたときに通知を送信するルールを追加しました。 作成者が通知の受信用に選択したアカウントに送信された電子メールを確認してください。

「[デバイスのルールとアクションを構成する](tutorial-configure-rules.md)」チュートリアルの最後で受信した電子メール メッセージを開きます。 電子メールの **[Click here to open your device]\(デバイスを開くにはここをクリック\)** をクリックします。

![アプリケーション ビルダーのルール](media/tutorial-monitor-devices/email.png)

前のチュートリアルで作成したシミュレートされたデバイス **Connected Air Conditioner-1** の **[デバイス]** ページがブラウザーで開きます。

![通知電子メール メッセージをトリガーしたデバイス](media/tutorial-monitor-devices/sourcedevice.png)

## <a name="investigate-an-issue"></a>問題の調査

オペレーターは、**[Measurements]\(測定\)**、**[設定]**、**[プロパティ]**、**[ルール]**、および **[ダッシュボード]** の各ページでデバイスに関する情報を確認できます。 作成者は、コネクテッド空調デバイスに関する重要な情報が表示されるよう、**[ダッシュボード]** をカスタマイズしました。

* **[ダッシュボード]** ビューを選択すると、デバイスに関する情報が表示されます。

    ![デバイス ダッシュボード](media/tutorial-monitor-devices/initial_screen.png)

    ダッシュボードのグラフには、デバイスの温度のプロットが表示されます。 **[Set target temperature]** タイルでは、デバイスの現在の目標温度を確認することもできます。 目標温度が高すぎると判断したとしましょう。

## <a name="remediate-an-issue"></a>問題の修復

デバイスの目標温度を変更するには、**[設定]** ページを使用します。

1. **[設定]** を選択します。 **[Set Temperature]** を 100 に設定します。 **[更新]** を選択して、新しい目標温度をデバイスに送信します。 設定の変更がデバイスによって確認されると、設定値の状態が**同期済み**に変わります。

    ![設定の更新](media/tutorial-monitor-devices/change_settings.png)

1. **[ダッシュボード]** を選択し、新しい設定値を確認します。

    ![更新されたデバイスのダッシュボード](media/tutorial-monitor-devices/new_settings.png)

## <a name="next-steps"></a>次の手順

このチュートリアルで学習した内容は次のとおりです。

> [!div class="nextstepaction"]
> * 通知の受信
> * 問題の調査
> * 問題の修復

ここでは、デバイスを監視しました。推奨される次の手順は、[デバイスの追加](tutorial-add-device.md)です。
