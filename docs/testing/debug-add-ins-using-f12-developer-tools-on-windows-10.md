---
title: Windows 10 で F12 開発者ツールを使用してアドインをデバッグする
description: ''
ms.date: 01/23/2018
ms.openlocfilehash: 226773962fb1777a3a1f0e09445721ae2b8b5f5b
ms.sourcegitcommit: e1c92ba882e6eb03a165867c6021a6aa742aa310
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2018
ms.locfileid: "22925606"
---
# <a name="debug-add-ins-using-f12-developer-tools-on-windows-10"></a>Windows 10 で F12 開発者ツールを使用してアドインをデバッグする

Windows 10 に含まれている F12 開発者ツールにより、web ページのデバッグ、テスト、および高速化ができます。それらを使用すれば、Visual Studio などの IDE を使用していない場合や、アドインを IDE の外部で実行中に問題を調査する必要がある場合に、Office アドインの開発とデバッグを行うことも可能です。アドインの実行後、F12 開発者ツールを起動できます。

この記事では、Windows 10 で F12 開発者ツールのデバッガー ツールを使用して、Office アドインをテストする方法を説明します。AppSource からのアドイン、また他の場所から追加したアドインもテストできます。F12 ツールは独自のウィンドウに表示され、Visual Studio を使用しません。

> [!NOTE]
> デバッガーは、Windows 10 および Internet Explorer 上の F12 開発者ツールの一部です。Windows の以前のバージョンにはデバッガーは含まれません。 

## <a name="prerequisites"></a>前提条件

以下のソフトウェアが必要です。

- Windows 10 に含まれる F12 開発者ツール。 
    
- アドインをホストする Office クライアント アプリケーション。 
    
- アドイン。 

## <a name="using-the-debugger"></a>デバッガーの使用

次の例では、AppSource から Word と無料のアドインを使用します。

1. Word を起動し、空白の文書を選択します。 
    
2. アドイン グループの **[挿入]** タブで、**[ストア]** をクリックし、QR4Office アドインを選択します。(ストアやアドイン カタログから、追加のアドインを読み込むことができます。)
    
3. Office のバージョンに対応する F12 開発者ツールを起動します。
    
   - 32 ビット版の Office の場合は、C:\Windows\System32\F12\IEChooser.exe を使用します。
    
   - 64 ビット版の Office の場合は、C:\Windows\SysWOW64\F12\IEChooser.exe を使用します。
    
   IEChooser を起動すると、[デバッグするターゲットの選択] という名前の別ウィンドウに、デバッグの対象になりうるアプリケーションが表示されます。 デバッグするアプリケーションを選択します。 独自のアドインを記述している場合、アドインを展開した Web サイトを選択します。ローカル ホストの URL も選択できます。 
    
   たとえば、**home.html** を選択します。 
    
   ![IEChooser 画面、バブル アドインを示す](../images/choose-target-to-debug.png)

4. F12 ウィンドウで、デバッグするファイルを選択します。
    
   ファイルを選択するには、**スクリプト** (左側) ウィンドウの上にあるフォルダー アイコンを選択します。ドロップダウン リストに利用可能なファイルが表示されます。home.js を選択します。
    
5. ブレークポイントを設定します。
    
   home.js にブレークポイントを設定するには、_textChanged_ 関数内の行 144 を選択します。その行の左側と **[コールスタックとブレークポイント]** (右下) ウィンドウの対応する行に赤い点が表示されます。ブレークポイントを設定するその他の方法については、「[デバッガーを使用して実行中の JavaScript を検査する](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/samples/dn255007(v=vs.85))」を参照してください。 
    
   ![home.js ファイルのブレークポイントを含むデバッガー](../images/debugger-home-js-02.png)

6. アドインを実行して、ブレークポイントをトリガーします。
    
   [QR4Office] ウィンドウの上部にある [URL] テキスト ボックスを選択して、テキストを変更します。デバッガー内の **[コールスタックとブレークポイント]** ウィンドウで、ブレークポイントがトリガーされ、さまざまな情報を示していることがわかります。結果を確認するには、F12 ツールの更新が必要な場合があります。
    
   ![トリガーされるブレーキポイントの結果を持つデバッガー](../images/debugger-home-js-01.png)


## <a name="see-also"></a>関連項目

- [デバッガーを使用して実行中の JavaScript を検査する](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/samples/dn255007(v=vs.85))
- [F12 開発者ツールの使用](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))
    