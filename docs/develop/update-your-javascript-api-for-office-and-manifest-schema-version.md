---
title: Office ライブラリ用の最新 JavaScript API、およびバージョン 1.1 のアドイン マニフェスト スキーマへの更新
description: Office アドイン プロジェクトで使用する JavaScript ファイル (Office.js ファイルとアプリに固有の .js ファイル) とアドイン マニフェスト検証ファイルをバージョン 1.1 に更新します。
ms.date: 12/04/2017
ms.openlocfilehash: 2ebfa5e908f278fd3abe754e536625fe6e7d9870
ms.sourcegitcommit: bc68b4cf811b45e8b8d1cbd7c8d2867359ab671b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/02/2018
ms.locfileid: "21703785"
---
# <a name="update-to-the-latest-javascript-api-for-office-library-and-version-11-add-in-manifest-schema"></a>Office ライブラリ用の最新 JavaScript API、およびバージョン 1.1 のアドイン マニフェスト スキーマへの更新

この記事では、Office アドイン プロジェクトに含まれる JavaScript ファイル (Office.js およびアプリに固有の .js ファイル) とアドイン マニフェスト検証ファイルをバージョン 1.1 に更新する方法について説明します。

## <a name="use-the-most-up-to-date-project-files"></a>最新のプロジェクト ファイルを使用する

Visual Studio を使用してアドインを開発するときに、JavaScript API for Office の[最新の API メンバー](https://dev.office.com/reference/add-ins/what's-changed-in-the-javascript-api-for-office)と[アドイン マニフェスト v1.1 の機能](../develop/add-in-manifests.md) (offappmanifest-1.1.xsd に対して検証される) を使用する場合は、[Visual Studio 2015 と最新の Office 開発者ツール](https://www.visualstudio.com/features/office-tools-vs)をダウンロードしてインストールする必要があります。

テキスト エディター、または Visual Studio 以外の IDE を使用してアドインを開発する場合は、Office.js に対する CDN への参照と、アドインのマニフェストで参照するスキーマのバージョンを更新する必要があります。

Office.js の新しい API や更新された API とアドインのマニフェスト機能を使用して開発したアドインを実行するには、ユーザー側で Office 2013 SP1 以降のオンプレミスの製品を実行し、該当する場合は SharePoint Server 2013 SP1 と関連するサーバー製品、Exchange Server 2013 Service Pack 1 (SP1)、または同等のオンライン ホスト製品である Office 365、SharePoint Online、および Exchange Online を実行している必要があります。

Office、SharePoint、Exchange SP1 の各製品をダウンロードするには、次を参照してください。

- [Microsoft Office 2013 および関連のデスクトップ製品のすべての Service Pack 1 (SP1) の更新プログラムの一覧](http://support.microsoft.com/kb/2850036)
    
- [製品 Microsoft SharePoint Server 2013 と関連するサーバー製品のすべての Service Pack 1 (SP1) の更新プログラムの一覧](http://support.microsoft.com/kb/2850035)
    
- [Exchange Server 2013 Service Pack 1 の説明](http://support.microsoft.com/kb/2926248)
    

## <a name="updating-an-office-add-in-project-created-with-visual-studio"></a>Visual Studio で作成した Office アドイン プロジェクトを更新する

JavaScript API for Office とアドイン マニフェスト スキーマの v1.1 のリリース前に作成されたプロジェクトの場合は、 **NuGet パッケージ マネージャー**を使用してプロジェクトのファイルを更新してから、それらを参照するようにアドインの HTML ページを更新できます。 

なお、この更新プロセスは _プロジェクトごと_ に適用する必要があることに注意してください。v1.1 の Office.js とアドイン マニフェスト スキーマを使用するアドイン プロジェクトごとに、この更新プロセスを繰り返します。


### <a name="update-the-javascript-api-for-office-library-files-in-your-project-to-the-newest-release"></a>プロジェクトの JavaScript API for Office ライブラリ ファイルを最新のリリースに更新する


1. Visual Studio 2015 で、**Office アドイン** プロジェクトを開くか、新規作成します。
    
      - 左側のウィンドウで、**[更新]** を選択してパッケージの更新プロセスを完了します。
    
      - 手順 6 に進みます。
    
2. [ **ツール**]  >  [ **NuGet パッケージ マネージャー**]  >  [ **ソリューションの Nuget パッケージの管理**] を選択します。
    
3. [ **NuGet パッケージ マネージャー**] で、[ **パッケージ ソース**] に [ **nuget.org**] を選択して、[ **フィルター**] に [ **アップグレードを利用可能**] を選択し、Microsoft.Office.js を選択します。
    
4. 左側のウィンドウで、**[更新]** を選択してパッケージの更新プロセスを完了します。
    
5. アドインの HTML ページの **head** タグ内で、既存の office.js スクリプトに対する参照をすべてコメント アウトするか削除して、更新した JavaScript API for Office ライブラリを次のように参照します。
    
    ```html
    <script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
    ```

   > [!NOTE] 
   > 注: CDN URL で `office.js` の前にある `/1/` は、Office.js のバージョン 1 内で最新の増分リリースを使用するように指定します。   


### <a name="update-the-manifest-file-in-your-project-to-use-schema-version-11"></a>プロジェクト内のマニフェスト ファイルがバージョン 1.1 のスキーマを使用するように更新する

アドインのマニフェスト ファイルで、**OfficeApp** 要素の **xmlns** 属性のバージョン値を `1.1` に変更して更新します (**xmlns** 以外の属性は変更しません)。
    
```xml
<?xml version="1.0" encoding="utf-8"?>
<OfficeApp xsi:type="ContentApp" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns="http://schemas.microsoft.com/office/appforoffice/1.1">
  
  <!-- manifest contents -->

</OfficeApp>
```

> [!NOTE] 
> 注: アドイン マニフェスト スキーマのバージョンを 1.1 に更新したら、**Capabilities** 要素と **Capability** 要素を削除し、それらを [Hosts](https://dev.office.com/reference/add-ins/manifest/hosts) 要素と [Host](https://dev.office.com/reference/add-ins/manifest/hosts) 要素または [Requirements 要素と Requirement 要素](specify-office-hosts-and-api-requirements.md)に置き換える必要があります。

## <a name="updating-an-office-add-in-project-created-with-a-text-editor-or-other-ide"></a>テキスト エディターまたは他の IDE で作成した Office アドイン プロジェクトを更新する

JavaScript API for Office とアドイン マニフェスト スキーマの v1.1 のリリース前に作成されたプロジェクトについては、v1.1 のライブラリの CDN を参照するようにアドインの HTML ページを更新し、スキーマ v1.1 を使用するようにアドインのマニフェスト ファイルを更新する必要があります。 

この更新プロセスは_プロジェクトごと_に適用します。そのため、v1.1 の Office.js とアドイン マニフェスト スキーマを使用するアドイン プロジェクトごとに、この更新プロセスを繰り返す必要があります。

Office アドインを開発するために、JavaScript API for Office ファイル (Office.js とアプリ固有の .js ファイル) のローカル コピーを用意する必要はありません (Office.js の CDN を参照すれば、実行時に必要なファイルがダウンロードされます)。それでも、ライブラリ ファイルのローカル コピーが必要な場合は、[NuGet コマンド ライン ユーティリティ](http://docs.nuget.org/consume/installing-nuget)の `Install-Package Microsoft.Office.js` コマンドを使用してダウンロードしてください。

> [!NOTE] 
> v1.1 アドイン マニフェストの XSD (XML スキーマ定義) のコピーの取得については、「[Office アドインのマニフェスト向けのスキーマ リファレンス (v1.1)](../develop/add-in-manifests.md)」の一覧を参照してください。


### <a name="update-the-javascript-api-for-office-library-files-in-your-project-to-use-the-newest-release"></a>最新のリリースを使用するようにプロジェクトの JavaScript API for Office ライブラリ ファイルを更新する

1. テキスト エディターまたは IDE でアドインの HTML ページを開きます。
    
2. アドインの HTML ページの **head** タグ内で、既存の office.js スクリプトに対する参照をすべてコメント アウトするか削除して、更新した JavaScript API for Office ライブラリを次のように参照します。
    
    ```html
    <script src="https://appsforoffice.microsoft.com/lib/1/hosted/Office.js" type="text/javascript"></script>
    ```

   > [!NOTE] 
   > 注: CDN URL で `office.js` の前にある `/1/` は、Office.js のバージョン 1 内で最新の増分リリースを使用するように指定します。   

### <a name="update-the-manifest-file-in-your-project-to-use-schema-version-11"></a>プロジェクト内のマニフェスト ファイルがバージョン 1.1 のスキーマを使用するように更新する

アドインのマニフェスト ファイルで、**OfficeApp** 要素の **xmlns** 属性のバージョン値を `1.1` に変更して更新します (**xmlns** 以外の属性は変更しません)。
    
```xml
<?xml version="1.0" encoding="utf-8"?>
<OfficeApp xsi:type="ContentApp" 
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
    xmlns="http://schemas.microsoft.com/office/appforoffice/1.1">
  
  <!-- manifest contents -->

</OfficeApp>
```

> [!NOTE] 
> 注: アドイン マニフェスト スキーマのバージョンを 1.1 に更新したら、**Capabilities** 要素と **Capability** 要素を削除し、それらを [Hosts](https://dev.office.com/reference/add-ins/manifest/hosts) 要素と [Host](https://dev.office.com/reference/add-ins/manifest/hosts) 要素または [Requirements 要素と Requirement 要素](specify-office-hosts-and-api-requirements.md)に置き換える必要があります。
    

## <a name="see-also"></a>関連項目

- [Office のホストと API の要件を指定する](specify-office-hosts-and-api-requirements.md) 
- [JavaScript API for Office について](understanding-the-javascript-api-for-office.md)    
- [JavaScript API for Office](https://dev.office.com/reference/add-ins/javascript-api-for-office)   
- [Office アドインのマニフェスト向けのスキーマ リファレンス (v1.1)](../develop/add-in-manifests.md)
    