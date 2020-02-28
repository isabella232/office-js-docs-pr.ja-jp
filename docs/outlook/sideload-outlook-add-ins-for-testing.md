---
title: テスト用に Outlook アドインをサイドロードする
description: サイドロードを使用して、最初にアドイン カタログに置かずに、テスト用に Outlook アドインをインストールします。
ms.date: 06/24/2019
localization_priority: Normal
ms.openlocfilehash: b177e6adbc4ac702b7bd9dcec38f2fe2d2f29cf1
ms.sourcegitcommit: a3ddfdb8a95477850148c4177e20e56a8673517c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "42166454"
---
# <a name="sideload-outlook-add-ins-for-testing"></a><span data-ttu-id="21270-103">テスト用に Outlook アドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="21270-103">Sideload Outlook add-ins for testing</span></span>

<span data-ttu-id="21270-104">サイドロードを使用すると、最初にアドイン カタログに置かなくても、テスト用に Outlook アドインをインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="21270-104">You can use sideloading to install an Outlook add-in for testing without having to first put it in an add-in catalog.</span></span>


## <a name="sideload-an-add-in-in-outlook-in-office-365"></a><span data-ttu-id="21270-105">Office 365 の Outlook のアドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="21270-105">Sideload an add-in in Outlook in Office 365</span></span>

<span data-ttu-id="21270-106">Office 365 の Outlook のアドインをサイドロードするプロセスは、新しい Outlook on the web を使用している場合と従来の Outlook on the web を使用している場合とで異なります。</span><span class="sxs-lookup"><span data-stu-id="21270-106">The process for sideloading an add-in in Outlook in Office 365 depends upon whether you are using the new Outlook on the web or classic Outlook on the web.</span></span>

- <span data-ttu-id="21270-107">メールボックスのツールバーが次の図のような場合、「[新しい Outlook on the web のアドインをサイドロードする](#sideload-an-add-in-in-the-new-outlook-on-the-web)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21270-107">If your mailbox toolbar looks like the following image, see [Sideload an add-in in the new Outlook on the web](#sideload-an-add-in-in-the-new-outlook-on-the-web).</span></span>

    ![新しい Outlook on the web の部分的なスクリーンショット](../images/outlook-on-the-web-new-toolbar.png)

- <span data-ttu-id="21270-109">メールボックスのツールバーが次の図のような場合、「[従来の Outlook on the web のアドインをサイドロードする](#sideload-an-add-in-in-classic-outlook-on-the-web)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21270-109">If your mailbox toolbar looks like the following image, see [Sideload an add-in in classic Outlook on the web](#sideload-an-add-in-in-classic-outlook-on-the-web).</span></span>

    ![従来の Outlook on the web の部分的なスクリーンショット](../images/outlook-on-the-web-classic-toolbar.png)

> [!NOTE]
> <span data-ttu-id="21270-111">組織のメールボックスのツールバーにロゴが含まれている場合、上の図に示されるものと表示が少し異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="21270-111">If your organization has included its logo in the mailbox toolbar, you might see something slightly different than shown in the preceding images.</span></span>

### <a name="sideload-an-add-in-in-the-new-outlook-on-the-web"></a><span data-ttu-id="21270-112">新しい Outlook on the web のアドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="21270-112">Sideload an add-in in the new Outlook on the web</span></span>

1. <span data-ttu-id="21270-113">[Office 365 の Outlook](https://outlook.office.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="21270-113">Go to [Outlook in Office 365](https://outlook.office.com).</span></span>

1. <span data-ttu-id="21270-114">Outlook on the web で新しいメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="21270-114">In Outlook on the web, create a new message.</span></span>   

1. <span data-ttu-id="21270-115">新しいメッセージの下部で [**...**] を選択し、表示されるメニューから [**アドインを取得**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-115">Choose **...** from the bottom of the new message and then select **Get Add-ins** from the menu that appears.</span></span>

    ![[アドインを取得] オプションが強調表示された Outlook on the web のメッセージ作成ウィンドウ](../images/outlook-on-the-web-new-get-add-ins.png)

1. <span data-ttu-id="21270-117">[**Outlook のアドイン**] ダイアログ ボックスで、[**個人用アドイン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-117">In the **Add-Ins for Outlook** dialog box, select **My add-ins**.</span></span>

    ![[個人用アドイン] が選択された 新しい Outlook on the web の [Outlook のアドイン] ダイアログ ボックス](../images/outlook-on-the-web-new-my-add-ins.png)

1. <span data-ttu-id="21270-119">ダイアログ ボックスの下部にある [**カスタム アドイン**] セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="21270-119">Locate the **Custom add-ins** section at the bottom of the dialog box.</span></span> <span data-ttu-id="21270-120">[**カスタム アドインを追加**] リンクを選択し、[**ファイルから追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-120">Select the **Add a custom add-in** link, and then select **Add from file**.</span></span>

    ![ファイル オプションからの追加を示すアドイン スクリーンショットの管理](../images/outlook-sideload-desktop-add-from-file.png)

1. <span data-ttu-id="21270-p102">カスタム アドインのマニフェスト ファイルを探してインストールします。インストール中にすべてのプロンプトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="21270-p102">Locate the manifest file for your custom add-in and install it. Accept all prompts during the installation.</span></span>

### <a name="sideload-an-add-in-in-classic-outlook-on-the-web"></a><span data-ttu-id="21270-124">従来の Outlook on the web のアドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="21270-124">Sideload an add-in in classic Outlook on the web</span></span>

1. <span data-ttu-id="21270-125">[Office 365 の Outlook](https://outlook.office.com) に移動します。</span><span class="sxs-lookup"><span data-stu-id="21270-125">Go to [Outlook in Office 365](https://outlook.office.com).</span></span>

1. <span data-ttu-id="21270-126">ツールバー右上のセクションにあるギア アイコンを選択し、[**アドインの管理**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-126">Choose the gear icon in the top-right section of the toolbar and select **Manage add-ins**.</span></span>

    ![[アドインの管理] オプションを示す Outlook on the web のスクリーンショット](../images/outlook-sideload-web-manage-integrations.png)

1. <span data-ttu-id="21270-128">**アドインの管理**ページで、**[アドイン]** を選択してから、**[個人用アドイン]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-128">On the **Manage add-ins** page, select **Add-Ins**, and then select **My add-ins**.</span></span>

    ![Outlook on the web の [ストア] ダイアログ ボックスで [個人用アドイン] を選択しているところ](../images/outlook-sideload-store-select-add-ins.png)

1. <span data-ttu-id="21270-130">ダイアログ ボックスの下部にある [**カスタム アドイン**] セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="21270-130">Locate the **Custom add-ins** section at the bottom of the dialog box.</span></span> <span data-ttu-id="21270-131">[**カスタム アドインを追加**] リンクを選択し、[**ファイルから追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-131">Select the **Add a custom add-in** link, and then select **Add from file**.</span></span>

    ![ファイル オプションからの追加を示すアドイン スクリーンショットの管理](../images/outlook-sideload-desktop-add-from-file.png)

1. <span data-ttu-id="21270-p104">カスタム アドインのマニフェスト ファイルを探してインストールします。インストール中にすべてのプロンプトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="21270-p104">Locate the manifest file for your custom add-in and install it. Accept all prompts during the installation.</span></span>

## <a name="sideload-an-add-in-in-outlook-on-the-desktop"></a><span data-ttu-id="21270-135">Outlook on the desktop のアドインをサイドロードする</span><span class="sxs-lookup"><span data-stu-id="21270-135">Sideload an add-in in Outlook on the desktop</span></span>

1. <span data-ttu-id="21270-136">Windows 用 Outlook 2013 以降、または Mac 用 Outlook 2016 以降を開きます。</span><span class="sxs-lookup"><span data-stu-id="21270-136">Open Outlook 2013 or later on Windows, or Outlook 2016 or later on Mac.</span></span>

1. <span data-ttu-id="21270-137">リボンで [**アドインを取得**] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-137">Select the **Get Add-ins** button on the ribbon.</span></span>

    ![[ストア] ボタンを示す Outlook 2016 リボン](../images/outlook-sideload-desktop-store.png)

    > [!NOTE]
    > <span data-ttu-id="21270-139">お使いのバージョンの Outlook で [**アドインを取得**] ボタンが表示されない場合、代わりに、リボンで [**ストア**] ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-139">If you don't see the **Get Add-ins** button in your version of Outlook, select the **Store** button on the ribbon instead.</span></span>

1. <span data-ttu-id="21270-140">[**アドイン**] を選択し、[**個人用アドイン**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-140">Select **Add-Ins**, and then select **My add-ins**.</span></span>

    ![Outlook 2016 の [ストア] ダイアログ ボックスで [個人用アドイン] を選択しているところ](../images/outlook-sideload-store-select-add-ins.png)

1. <span data-ttu-id="21270-142">ダイアログ ボックスの下部にある **[カスタム アドイン]** セクションに移動します。</span><span class="sxs-lookup"><span data-stu-id="21270-142">Locate the **Custom add-ins** section at the bottom of the dialog.</span></span> <span data-ttu-id="21270-143">**[カスタム アドインを追加]** リンクを選択し、**[ファイルから追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="21270-143">Select the **Add a custom add-in** link, and then select **Add from file**.</span></span>

    ![[ファイルから追加] オプションを示す [ストア] のスクリーンショット](../images/outlook-sideload-desktop-add-from-file.png)

1. <span data-ttu-id="21270-p106">カスタム アドインのマニフェスト ファイルを探してインストールします。インストール中にすべてのプロンプトを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="21270-p106">Locate the manifest file for your custom add-in and install it. Accept all prompts during the installation.</span></span>

## <a name="remove-a-sideloaded-add-in"></a><span data-ttu-id="21270-147">サイドロードアドインを削除する</span><span class="sxs-lookup"><span data-stu-id="21270-147">Remove a sideloaded add-in</span></span>

<span data-ttu-id="21270-148">サイドロードアドインを Outlook から削除するには、この記事で前述した手順を使用して、インストールされているアドインを一覧表示するダイアログボックスの [**カスタムアドイン**] セクションでアドインを検索します。`...`アドインの省略記号 () を選択し、[**削除**] を選択して、その特定のアドインを削除します。</span><span class="sxs-lookup"><span data-stu-id="21270-148">To remove a sideloaded add-in from Outlook, use the steps previously described in this article to find the add-in in the **Custom add-ins** section of the dialog box that lists your installed add-ins. Choose the ellipsis (`...`) for the the add-in and then choose **Remove** to remove that specific add-in.</span></span>