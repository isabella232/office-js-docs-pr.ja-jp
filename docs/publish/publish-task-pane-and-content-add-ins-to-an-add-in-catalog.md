---
title: 作業ウィンドウ アドインとコンテンツ アドインを SharePoint アプリ カタログに発行する
description: 組織内のユーザーが Office アドインにアクセスできるようにするために、管理者は組織のアプリ カタログに Office アドインのマニフェスト ファイルをアップロードできます。
ms.date: 07/07/2020
localization_priority: Normal
ms.openlocfilehash: 827c11c5c8666bc1478e36bb9568c536a61c1f63
ms.sourcegitcommit: c6308cf245ac1bc66a876eaa0a7bb4a2492991ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "47408797"
---
# <a name="publish-task-pane-and-content-add-ins-to-a-sharepoint-app-catalog"></a>作業ウィンドウ アドインとコンテンツ アドインを SharePoint アプリ カタログに発行する

アプリ カタログは、Office アドインと SharePoint アドインのドキュメント ライブラリをホストする SharePoint Web アプリケーションまたは SharePoint Online テナンシーの専用サイト コレクションです。組織内のユーザーが Office アドインにアクセスできるようにするために、管理者は組織のアプリ カタログに Office アドインのマニフェスト ファイルをアップロードできます。管理者がアプリ カタログを信頼できるカタログとして登録すると、ユーザーは Office クライアント アプリケーションで挿入 UI からアドインを挿入できます。

> [!IMPORTANT]
> - SharePoint のアプリ カタログでは、アドイン コマンドなど、[アドイン マニフェスト](../develop/add-in-manifests.md)の `VersionOverrides` ノードで実装されるアドイン機能がサポートされていません。
> - クラウド環境またはハイブリッド環境をターゲットにしている場合は、 [Microsoft 365 管理センターを使用](../publish/centralized-deployment.md) して、アドインを発行するために一元展開を使用することをお勧めします。
> - SharePoint のアプリ カタログは Office on Mac ではサポートされていません。 Office アドインを Mac クライアントに展開するには、そのアドインを [AppSource](/office/dev/store/submit-to-the-office-store) に提出する必要があります。

## <a name="create-an-app-catalog"></a>アプリ カタログを作成する

次のいずれかのセクションの手順を完了し、オンプレミス SharePoint サーバーまたは Office 365 を使用して、アプリ カタログを作成します。

### <a name="to-create-an-app-catalog-for-on-premises-sharepoint-server"></a>オンプレミス SharePoint サーバーでアプリ カタログを作成する

SharePoint アプリ カタログを作成するには、[web アプリケーションのアプリ カタログサイトを作成する](/sharepoint/administration/manage-the-app-catalog)を参照してください。

アプリ カタログを作成したら [Office アドインを発行する](#publish-an-office-add-in) 手順に従います。

### <a name="to-create-an-app-catalog-on-microsoft-365"></a>Microsoft 365 でアプリカタログを作成するには

SharePoint アプリカタログを作成するには、「 [アプリカタログサイトコレクションを作成](/sharepoint/use-app-catalog#step-1-create-the-app-catalog-site-collection)する」の手順に従ってください。 アプリカタログを作成したら、次のセクションの手順に従って、Office アドインを発行します。

## <a name="publish-an-office-add-in"></a>Office アドインの発行

次のいずれかのセクションの手順を実行して、Office アドインを Microsoft 365 またはオンプレミスの SharePoint Server 上のアプリカタログに発行します。

### <a name="to-publish-an-office-add-in-to-a-sharepoint-app-catalog-on-microsoft-365"></a>Microsoft 365 上の SharePoint アプリカタログに Office アドインを発行するには

1. [新しい SharePoint 管理センターの [アクティブなサイト] ページ](https://admin.microsoft.com/sharepoint?page=siteManagement&modern=true)に移動し、組織の[管理者権限](/sharepoint/sharepoint-admin-role)が付与されているアカウントでサインインします。

    > [!NOTE]
    > Microsoft 365 ドイツを使用している場合は、 [microsoft 365 管理センターにサインイン](https://go.microsoft.com/fwlink/p/?linkid=848041)し、SharePoint 管理センターを参照して、[その他の機能] ページを開きます。 <br>21Vianet が運用している Microsoft 365 (中国) を使用している場合は、 [microsoft 365 管理センターにサインイン](https://go.microsoft.com/fwlink/p/?linkid=850627)して、SharePoint 管理センターを参照し、[その他の機能] ページを開きます。

1. [URL] 列で URL を選択して、アプリカタログサイトを開きます。

    > [!NOTE]
    > 前のセクションでアプリカタログサイトを作成したばかりの場合は、サイトのセットアップが完了するまでに数分かかることがあります。

1. [**Office 用アプリを配信する**] を選択します。
1. [**Office 用アプリ**] ページで、[**新規**] を選択します。
1. [**ドキュメントの追加**] ダイアログで、[**ファイルの選択**] ボタンをクリックします。
1. アップロードする[マニフェスト](../develop/add-in-manifests.md) ファイルを見つけて指定し、[**開く**] を選択します。
1. [**ドキュメントの追加**] ダイアログで、[**OK**] を選択します。

### <a name="to-publish-an-add-in-to-an-app-catalog-with-on-premises-sharepoint-server"></a>オンプレミスの SharePoint サーバーでアプリ カタログにアドインを発行する

1. **[サーバーの全体管理]** ページを開きます。
1. 左側の作業ウィンドウで、[**アプリ**] を選択します。
1. **[アプリ]** ページの **[アプリの管理]** で **[アプリ カタログの管理]** を選択します。
1. **[アプリ カタログの管理]** ページの ** Web アプリケーション ** セレクターで正しい Web アプリケーションが選択されていることを確認します。
1. **サイト URL**の下にある URL を選び、アプリ カタログサイトを開きます。
1. [**Office 用アプリを配信する**] を選択します。
1. [**Office 用アプリ**] ページで、[**新規**] を選択します。
1. [**ドキュメントの追加**] ダイアログで、[**ファイルの選択**] ボタンをクリックします。
1. アップロードする[マニフェスト](../develop/add-in-manifests.md) ファイルを見つけて指定し、[**開く**] を選択します。
1. [**ドキュメントの追加**] ダイアログで、[**OK**] を選択します。

## <a name="insert-office-add-ins-from-the-app-catalog"></a>アプリ カタログから Office アドインを挿入する

オンライン Office アプリケーションの場合は、次の手順を実行してアプリ カタログから Office アドインを見つけることができます。

1. オンライン Office アプリケーション (Excel、PowerPoint、または Word) を開きます。
1. 文書を作成または開く。
1. **[挿入]** > **[アドイン]** を選択します。
1. [Office アドイン] ダイアログの **[自分の所属組織]** タブを選択します。Office アドインのリストが表示されます。
1. Office アドインを選択し、 **追加** を選択します。

デスクトップの Office アプリケーションの場合は、次の手順を実行してアプリ カタログから Office アドインを見つけることができます。

1. デスクトップ Office アプリケーション (Excel、Word、または PowerPoint) を開きます。
1. **[ファイル]**  >  **[オプション]**  >  **[セキュリティ センター]**  >  **[セキュリティ センターの設定]**  >  **[信頼できるアドイン カタログ]** の順に選択します。
1. [**カタログ URL** ] ボックスに SharePoint アプリ カタログの URL を入力し、**[カタログの追加]** を選択します。
    短い URL を使用します。 たとえば、SharePoint アプリ カタログの URL が次のような場合:
    - `https://<domain>/sites/<AddinCatalogSiteCollection>/AgaveCatalog`

    親サイト コレクションの URL のみを指定します。
    - `https://<domain>/sites/<AddinCatalogSiteCollection>`
1. Office アプリケーションを閉じてから、もう一度開きます。
1. **[挿入]** > **[アドインの取得]** の順に選択します。
1. [Office アドイン] ダイアログの **[自分の所属組織]** タブを選択します。Office アドインのリストが表示されます。
1. Office アドインを選択し、 **追加**を選択します。

または、管理者はグループ ポリシーを使用して SharePoint のアプリ カタログを指定できます。 関連するポリシー設定は、 [Microsoft 365 アプリ、office 2019、および Office 2016 の管理用テンプレートファイル (ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030) で使用でき、[ **User 構成用テンプレート Office 2016 \ Security 設定 \ 信頼できるカタログ**] にあります。
