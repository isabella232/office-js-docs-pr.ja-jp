# <a name="versionoverrides-element"></a><span data-ttu-id="78761-101">VersionOverrides 要素</span><span class="sxs-lookup"><span data-stu-id="78761-101">VersionOverrides element</span></span>

<span data-ttu-id="78761-p101">アドインによって実装されたアドイン コマンドに関する情報を格納するルート要素です。**VersionOverrides** は、マニフェスト内の [OfficeApp](./officeapp.md) 要素の子要素です。この要素は、マニフェスト スキーマ v1.1 以降でサポートされていますが、VersionOverrides v1.0 または v1.1 スキーマで定義されています。</span><span class="sxs-lookup"><span data-stu-id="78761-p101">The root element that contains information for the add-in commands implemented by the add-in. **VersionOverrides** is a child element of the [OfficeApp](./officeapp.md) element in the manifest. This element is supported in manifest schema v1.1 and later but is defined in the VersionOverrides v1.0 or v1.1 schema.</span></span>

## <a name="attributes"></a><span data-ttu-id="78761-105">属性</span><span class="sxs-lookup"><span data-stu-id="78761-105">Attributes</span></span>

|  <span data-ttu-id="78761-106">属性</span><span class="sxs-lookup"><span data-stu-id="78761-106">Attribute</span></span>  |  <span data-ttu-id="78761-107">必須</span><span class="sxs-lookup"><span data-stu-id="78761-107">Required</span></span>  |  <span data-ttu-id="78761-108">説明</span><span class="sxs-lookup"><span data-stu-id="78761-108">Description</span></span>  |
|:-----|:-----|:-----|
|  <span data-ttu-id="78761-109">**xmlns**</span><span class="sxs-lookup"><span data-stu-id="78761-109">**xmlns**</span></span>       |  <span data-ttu-id="78761-110">はい</span><span class="sxs-lookup"><span data-stu-id="78761-110">Yes</span></span>  |  <span data-ttu-id="78761-111">スキーマの場所。`xsi:type` が `VersionOverridesV1_0` の場合は `http://schemas.microsoft.com/office/mailappversionoverrides` にする必要があり、`xsi:type` が `VersionOverridesV1_1` の場合は `http://schemas.microsoft.com/office/mailappversionoverrides/1.1` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78761-111">The schema location, which must be `http://schemas.microsoft.com/office/mailappversionoverrides` when `xsi:type` is `VersionOverridesV1_0`, and `http://schemas.microsoft.com/office/mailappversionoverrides/1.1` when `xsi:type` is `VersionOverridesV1_1`.</span></span>|
|  <span data-ttu-id="78761-112">**xsi:type**</span><span class="sxs-lookup"><span data-stu-id="78761-112">**xsi:type**</span></span>  |  <span data-ttu-id="78761-113">はい</span><span class="sxs-lookup"><span data-stu-id="78761-113">Yes</span></span>  | <span data-ttu-id="78761-p102">スキーマのバージョン。現時点では、`VersionOverridesV1_0` および `VersionOverridesV1_1` のみが有効な値になります。</span><span class="sxs-lookup"><span data-stu-id="78761-p102">The schema version. At this time, the only valid values are `VersionOverridesV1_0` and `VersionOverridesV1_1`.</span></span> |

> [!NOTE]
> <span data-ttu-id="78761-116">メモ: 現時点では、Outlook 2016 のみが VersionOverrides v1.1 スキーマおよび `VersionOverridesV1_1` タイプをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="78761-116">Note: Currently only Outlook 2016 supports the VersionOverrides v1.1 schema and the `VersionOverridesV1_1` type.</span></span>

## <a name="child-elements"></a><span data-ttu-id="78761-117">子要素</span><span class="sxs-lookup"><span data-stu-id="78761-117">Child elements</span></span>

|  <span data-ttu-id="78761-118">要素</span><span class="sxs-lookup"><span data-stu-id="78761-118">Element</span></span> |  <span data-ttu-id="78761-119">必須</span><span class="sxs-lookup"><span data-stu-id="78761-119">Required</span></span>  |  <span data-ttu-id="78761-120">説明</span><span class="sxs-lookup"><span data-stu-id="78761-120">Description</span></span>  |
|:-----|:-----|:-----|
|  <span data-ttu-id="78761-121">**説明**</span><span class="sxs-lookup"><span data-stu-id="78761-121">**Description**</span></span>    |  <span data-ttu-id="78761-122">いいえ</span><span class="sxs-lookup"><span data-stu-id="78761-122">No</span></span>   |  <span data-ttu-id="78761-p103">アドインについての説明。これは、マニフェスト内の任意の親部分の `Description` 要素を上書きします。説明のテキストは、[Resources](./resources.md) 要素の **LongString** 要素の子要素に含まれています。**Description** 要素の `resid` の属性は、テキストを含む `String` 要素の `id` 属性の値に設定されています。</span><span class="sxs-lookup"><span data-stu-id="78761-p103">Describes the add-in. This overrides the `Description` element in any parent portion of the manifest. The text of the description is contained in a child element of the **LongString** element contained in the [Resources](./resources.md) element. The `resid` attribute of the **Description** element is set to the value of the `id` attribute of the `String` element that contains the text.</span></span>|
|  <span data-ttu-id="78761-127">**要件**</span><span class="sxs-lookup"><span data-stu-id="78761-127">**Requirements**</span></span>  |  <span data-ttu-id="78761-128">いいえ</span><span class="sxs-lookup"><span data-stu-id="78761-128">No</span></span>   |  <span data-ttu-id="78761-p104">アドインに必要な最小の Office.js のセットおよびバージョンを指定します。これは、マニフェストの親部分の `Requirements` 要素を上書きします。</span><span class="sxs-lookup"><span data-stu-id="78761-p104">Specifies the minimum requirement set and version of Office.js that the add-in requires. This overrides the  `Requirements` element in the parent portion of the manifest.</span></span>|
|  [<span data-ttu-id="78761-131">ホスト</span><span class="sxs-lookup"><span data-stu-id="78761-131">Hosts</span></span>](./hosts.md)                |  <span data-ttu-id="78761-132">はい</span><span class="sxs-lookup"><span data-stu-id="78761-132">Yes</span></span>  |  <span data-ttu-id="78761-p105">Office ホストのコレクションを指定します。子の Host 要素は、マニフェストの親部分の Host 要素を上書きします。</span><span class="sxs-lookup"><span data-stu-id="78761-p105">Specifies a collection of Office hosts. The child  Hosts element overrides the Hosts element in the parent portion of the manifest.</span></span>  |
|  [<span data-ttu-id="78761-135">資料</span><span class="sxs-lookup"><span data-stu-id="78761-135">Resources</span></span>](./resources.md)    |  <span data-ttu-id="78761-136">はい</span><span class="sxs-lookup"><span data-stu-id="78761-136">Yes</span></span>  | <span data-ttu-id="78761-137">マニフェストの他の要素によって参照されるリソースのコレクション (文字列、URL、画像) を定義します。</span><span class="sxs-lookup"><span data-stu-id="78761-137">Defines a collection of resources (strings, URLs, and images) that other manifest elements reference.</span></span>|
|  <span data-ttu-id="78761-138">**VersionOverrides**</span><span class="sxs-lookup"><span data-stu-id="78761-138">**VersionOverrides**</span></span>    |  <span data-ttu-id="78761-139">いいえ</span><span class="sxs-lookup"><span data-stu-id="78761-139">No</span></span>  | <span data-ttu-id="78761-p106">より新しいスキーマ バージョンでアドイン コマンドを定義します。詳細については、「[複数のバージョンを実装する](#implementing-multiple-versions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78761-p106">Defines add-in commands under a newer schema version. See [Implementing multiple versions](#implementing-multiple-versions) for details.</span></span> |
|  <span data-ttu-id="78761-142">**WebApplicationInfo**</span><span class="sxs-lookup"><span data-stu-id="78761-142">**WebApplicationInfo**</span></span>    |  <span data-ttu-id="78761-143">いいえ</span><span class="sxs-lookup"><span data-stu-id="78761-143">No</span></span>  | <span data-ttu-id="78761-144">アドインの関連 Web アプリケーションについての詳細を指定します。</span><span class="sxs-lookup"><span data-stu-id="78761-144">Specifies details about the add-in's associated Web application.</span></span> |



### <a name="versionoverrides-example"></a><span data-ttu-id="78761-145">VersionOverrides の例</span><span class="sxs-lookup"><span data-stu-id="78761-145">VersionOverrides example</span></span>
```xml
<OfficeApp>
...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides" xsi:type="VersionOverridesV1_0">
    <Description resid="residDescription" />
    <Requirements>
      <!-- add information on requirements -->
    </Requirements>
    <Hosts>
      <Host xsi:type="MailHost">
        <!-- add information on form factors -->
      </Host>
    </Hosts>
    <Resources>
      <!-- add information on resources -->
    </Resources>
  </VersionOverrides>
...
</OfficeApp>
```

## <a name="implementing-multiple-versions"></a><span data-ttu-id="78761-146">複数のバージョンを実装する</span><span class="sxs-lookup"><span data-stu-id="78761-146">Implementing multiple versions</span></span>

<span data-ttu-id="78761-p107">1 つのマニフェストで、複数のバージョンの `VersionOverrides` 要素を実装することで、異なるバージョンの VersionOverrides スキーマをサポートできます。これは、新しいスキーマの新機能をオプションでサポートしながら、新機能をサポートしていない古いクライアントもサポートすることで実現できます。</span><span class="sxs-lookup"><span data-stu-id="78761-p107">A manifest can implement multiple versions of the `VersionOverrides` element which support different versions of the VersionOverrides schema. This can be done to optionally support new features in a newer schema while still supporting older clients that do not support the new features.</span></span>

<span data-ttu-id="78761-149">複数のバージョンを実装するために、新しいバージョンの `VersionOverrides` 要素は、古いバージョンの `VersionOverrides` 要素の子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="78761-149">In order to implement multiple versions, the `VersionOverrides` element for the newer version must be a child of the `VersionOverrides` element for the older version.</span></span> <span data-ttu-id="78761-150">子の `VersionOverrides` 要素は、どの値も親から継承しません。</span><span class="sxs-lookup"><span data-stu-id="78761-150">The child `VersionOverrides` element doesn't inherit any values from the parent.</span></span>

<span data-ttu-id="78761-151">VersionOverrides v1.0 と v1.1 の両方のスキーマを実装するためのマニフェストは、次に示す例のようになります。</span><span class="sxs-lookup"><span data-stu-id="78761-151">To implement both the VersionOverrides v1.0 and v1.1 schema, the manifest would look similar to the following example:</span></span>

```xml
<OfficeApp>
...
  <VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides" xsi:type="VersionOverridesV1_0">
    <Description resid="residDescription" />
    <Requirements>
      <!-- add information on requirements -->
    </Requirements>
    <Hosts>
      <Host xsi:type="MailHost">
        <!-- add information on form factors -->
      </Host>
    </Hosts>
    <Resources>
      <!-- add information on resources -->
    </Resources>

    <VersionOverrides xmlns="http://schemas.microsoft.com/office/mailappversionoverrides/1.1" xsi:type="VersionOverridesV1_1">
      <Description resid="residDescription" />
      <Requirements>
        <!-- add information on requirements -->
      </Requirements>
      <Hosts>
        <Host xsi:type="MailHost">
          <!-- add information on form factors -->
        </Host>
      </Hosts>
      <Resources>
        <!-- add information on resources -->
      </Resources>
    </VersionOverrides>  
...
</OfficeApp>
```