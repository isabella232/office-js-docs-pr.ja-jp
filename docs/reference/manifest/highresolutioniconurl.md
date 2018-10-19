# <a name="highresolutioniconurl-element"></a><span data-ttu-id="87ad8-101">HighResolutionIconUrl 要素</span><span class="sxs-lookup"><span data-stu-id="87ad8-101">HighResolutionIconUrl element</span></span>

<span data-ttu-id="87ad8-102">高 DPI の画面での挿入 UX と Office ストアの Office アドインを表すために使用されるイメージの URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="87ad8-102">Specifies the URL of the image that is used to represent your Office Add-in in the insertion UX and Office Store on high DPI screens.</span></span>

<span data-ttu-id="87ad8-103">**アドインの種類:** コンテンツ、作業ウィンドウ、メール</span><span class="sxs-lookup"><span data-stu-id="87ad8-103">**Add-in type:** Content, Task pane, Mail</span></span>

## <a name="syntax"></a><span data-ttu-id="87ad8-104">構文</span><span class="sxs-lookup"><span data-stu-id="87ad8-104">Syntax</span></span>

```XML
<HighResolutionIconUrl DefaultValue="string" />
```

## <a name="can-contain"></a><span data-ttu-id="87ad8-105">含めることができるもの:</span><span class="sxs-lookup"><span data-stu-id="87ad8-105">Can contain:</span></span>

[<span data-ttu-id="87ad8-106">上書き</span><span class="sxs-lookup"><span data-stu-id="87ad8-106">Override</span></span>](override.md)

## <a name="attributes"></a><span data-ttu-id="87ad8-107">属性</span><span class="sxs-lookup"><span data-stu-id="87ad8-107">Attributes</span></span>

|<span data-ttu-id="87ad8-108">**属性**</span><span class="sxs-lookup"><span data-stu-id="87ad8-108">**Attribute**</span></span>|<span data-ttu-id="87ad8-109">**型**</span><span class="sxs-lookup"><span data-stu-id="87ad8-109">**Type**</span></span>|<span data-ttu-id="87ad8-110">**必須**</span><span class="sxs-lookup"><span data-stu-id="87ad8-110">**Required**</span></span>|<span data-ttu-id="87ad8-111">**説明**</span><span class="sxs-lookup"><span data-stu-id="87ad8-111">**Description**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="87ad8-112">DefaultValue</span><span class="sxs-lookup"><span data-stu-id="87ad8-112">DefaultValue</span></span>|<span data-ttu-id="87ad8-113">文字列 (URL)</span><span class="sxs-lookup"><span data-stu-id="87ad8-113">string (URL)</span></span>|<span data-ttu-id="87ad8-114">必須</span><span class="sxs-lookup"><span data-stu-id="87ad8-114">required</span></span>|<span data-ttu-id="87ad8-115">この設定の既定値を指定します。この値は、[DefaultLocale](defaultlocale.md) 要素に指定されるロケールを対象としています。</span><span class="sxs-lookup"><span data-stu-id="87ad8-115">Specifies the default value for this setting, expressed for the locale specified in the [DefaultLocale](defaultlocale.md) element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87ad8-116">注釈</span><span class="sxs-lookup"><span data-stu-id="87ad8-116">Remarks</span></span>

<span data-ttu-id="87ad8-p101">メール アドインの場合、アイコンは、**[ファイル]**  >  **[アドインの管理]** UI に表示されます。コンテンツ アドインまたは作業ウィンドウ アドインでは、アイコンは、**[挿入]**  >  **[アドイン]** UI に表示されます。</span><span class="sxs-lookup"><span data-stu-id="87ad8-p101">For a mail add-in, the icon is displayed in the  **File** > **Manage add-ins** UI . For a content or task pane add-in, the icon is displayed in the **Insert** > **Add-ins** UI.</span></span>

<span data-ttu-id="87ad8-119">イメージは推奨解像度が 64 x 64 ピクセルであり、次のファイル形式のいずれかである必要があります。GIF、JPG、PNG、EXIF、BMP、または TIFF。</span><span class="sxs-lookup"><span data-stu-id="87ad8-119">The image must be in one of the following file formats at a recommended resolution of 64 x 64 pixels: GIF, JPG, PNG, EXIF, BMP or TIFF.</span></span> <span data-ttu-id="87ad8-120">詳細については、「[AppSource および Office 内で効果的な一覧を作成する](https://docs.microsoft.com/office/dev/store/create-effective-office-store-listings) 」の 「_アプリに一貫性のあるビジュアル ID を作成する_ 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="87ad8-120">For more information, see the section  Create a consistent visual identity for your app in Create effective Office Store apps and add-ins.</span></span>