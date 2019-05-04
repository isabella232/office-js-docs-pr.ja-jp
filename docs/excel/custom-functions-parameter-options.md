---
ms.date: 04/30/2019
description: Excel 範囲、省略可能なパラメーター、呼び出しコンテキストなど、カスタム関数内でさまざまなパラメーターを使用する方法について説明します。
title: Excel カスタム関数のオプション (プレビュー)
localization_priority: Normal
ms.openlocfilehash: b5dba59431f4c6ec4ee08c563e7cb3affeb06608
ms.sourcegitcommit: 68872372d181cca5bee37ade73c2250c4a56bab6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2019
ms.locfileid: "33527318"
---
# <a name="custom-functions-parameter-options"></a><span data-ttu-id="4df66-103">カスタム関数のパラメータオプション</span><span class="sxs-lookup"><span data-stu-id="4df66-103">Custom functions parameter options</span></span>

<span data-ttu-id="4df66-104">カスタム関数は、パラメーターにさまざまなオプションを使用して構成できます。</span><span class="sxs-lookup"><span data-stu-id="4df66-104">Custom functions are configurable with many different options for parameters:</span></span> 
- [<span data-ttu-id="4df66-105">オプションのパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-105">Optional parameters</span></span>](#custom-functions-optional-parameters)
- [<span data-ttu-id="4df66-106">範囲パラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-106">Range parameters</span></span>](#range-parameters)
- [<span data-ttu-id="4df66-107">呼び出しコンテキストパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-107">Invocation context parameter</span></span>](#invocation-parameter)

## <a name="custom-functions-optional-parameters"></a><span data-ttu-id="4df66-108">カスタム関数の省略可能なパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-108">Custom functions optional parameters</span></span>

<span data-ttu-id="4df66-109">通常のパラメーターは必須ですが、省略可能なパラメーターは必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="4df66-109">Whereas regular parameters are required, optional parameters are not.</span></span> <span data-ttu-id="4df66-110">ユーザーが Excel で関数を呼び出すと、角かっこで囲まれた省略可能なパラメーターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-110">When a user invokes a function in Excel, optional parameters appear in brackets.</span></span> <span data-ttu-id="4df66-111">次の例では、add 関数で3番目の番号を追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4df66-111">In the following sample, the add function can optionally add a third number.</span></span> <span data-ttu-id="4df66-112">この関数は Excel `=CONTOSO.ADD(first, second, [third])`のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-112">This function appears as `=CONTOSO.ADD(first, second, [third])` in Excel.</span></span>

```js
/**
 * Add two numbers
 * @customfunction 
 * @param {number} first First number.
 * @param {number} second Second number.
 * @param {number} [third] Third number to add. If omitted, third = 0.
 * @returns {number} The sum of the numbers.
 */
function add(first, second, third) {
  if (third === undefined) {
    return first + second + third;
  }
  return first + second;
}
CustomFunctions.associate("ADD", add);
```

<span data-ttu-id="4df66-113">関数の定義時に 1 つ以上の省略可能なパラメーターを含める場合は、省略可能なパラメーターが未定義のときの処理を指定しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4df66-113">When you define a function that contains one or more optional parameters, you should specify what happens when the optional parameters are undefined.</span></span> <span data-ttu-id="4df66-114">次の例の `zipCode` と `dayOfWeek` は、どちらも `getWeatherReport` 関数の省略可能なパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="4df66-114">In the following example, `zipCode` and `dayOfWeek` are both optional parameters for the `getWeatherReport` function.</span></span> <span data-ttu-id="4df66-115">`zipCode`パラメーターが定義されていない場合、既定値`98052`はに設定されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-115">If the `zipCode` parameter is undefined, the default value is set to `98052`.</span></span> <span data-ttu-id="4df66-116">`dayOfWeek` パラメーターが未定義の場合は、Wednesday が設定されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-116">If the `dayOfWeek` parameter is undefined, it is set to Wednesday.</span></span>

```js
/**
 * Gets a weather report for a specified zipCode and dayOfWeek
 * @customfunction
 * @param {number} zipCode Zip code. If omitted, zipCode = 98052.
 * @param {string} dayOfWeek Day of the week. If omitted, dayOfWeek = Wednesday.
 * @returns {string} Weather report for the day of the week in that zip code.
 */
function getWeatherReport(zipCode, dayOfWeek)
{
  if (zipCode === undefined) {
      zipCode = "98052";
  }

  if (dayOfWeek === undefined) {
    dayOfWeek = "Wednesday";
  }

  // Get weather report for specified zipCode and dayOfWeek.
  // ...
}
```

## <a name="range-parameters"></a><span data-ttu-id="4df66-117">範囲パラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-117">Range parameters</span></span>

<span data-ttu-id="4df66-118">カスタム関数は、入力パラメーターとして範囲のセルデータを受け入れることができます。</span><span class="sxs-lookup"><span data-stu-id="4df66-118">Your custom function may accept a range of cell data as an input parameter.</span></span> <span data-ttu-id="4df66-119">関数は、データの範囲を返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="4df66-119">A function can also return a range of data.</span></span> <span data-ttu-id="4df66-120">Excel は、セルデータの範囲を2次元配列として渡します。</span><span class="sxs-lookup"><span data-stu-id="4df66-120">Excel will pass a range of cell data as a two-dimensional array.</span></span>

<span data-ttu-id="4df66-121">例えば、関数が Excel に保存されている数値の範囲から 2 番目に大きい値を返すとします。</span><span class="sxs-lookup"><span data-stu-id="4df66-121">For example, suppose that your function returns the second highest value from a range of numbers stored in Excel.</span></span> <span data-ttu-id="4df66-122">次の関数は、`Excel.CustomFunctionDimensionality.matrix` 型の `values` パラメーターを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="4df66-122">The following function accepts the parameter `values`, which is of type `Excel.CustomFunctionDimensionality.matrix`.</span></span> <span data-ttu-id="4df66-123">この関数の JSON メタデータでは、パラメーターの`type`プロパティがに`matrix`設定されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="4df66-123">Note that in the JSON metadata for this function, the parameter's `type` property is set to `matrix`.</span></span>

```js
/**
 * Returns the second highest value in a matrixed range of values.
 * @customfunction
 * @param {[][]} values Multiple ranges of values.  
 */
function secondHighest(values){
  let highest = values[0][0], secondHighest = values[0][0];
  for(var i = 0; i < values.length; i++){
    for(var j = 0; j < values[i].length; j++){
      if(values[i][j] >= highest){
        secondHighest = highest;
        highest = values[i][j];
      }
      else if(values[i][j] >= secondHighest){
        secondHighest = values[i][j];
      }
    }
  }
  return secondHighest;
}
CustomFunctions.associate("SECONDHIGHEST", secondHighest);
```

## <a name="invocation-parameter"></a><span data-ttu-id="4df66-124">呼び出しパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-124">Invocation parameter</span></span>

<span data-ttu-id="4df66-125">すべてのカスタム関数には、 `invocation`最後の引数として引数が自動的に渡されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-125">Every custom function is automatically passed an `invocation` argument as the last argument.</span></span> <span data-ttu-id="4df66-126">この引数は、呼び出し元のセルのアドレスなど、追加のコンテキストを取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="4df66-126">This argument can be used to retrieve additional context, such as the address of the calling cell.</span></span> <span data-ttu-id="4df66-127">また、関数[をキャンセル](custom-functions-web-reqs.md#stream-and-cancel-functions)する関数ハンドラーなど、Excel に情報を送信するために使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="4df66-127">Or it can be used to send information to Excel, such as a function handler for [canceling a function](custom-functions-web-reqs.md#stream-and-cancel-functions).</span></span> <span data-ttu-id="4df66-128">パラメーターを宣言しない場合でも、カスタム関数にはこのパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="4df66-128">Even if you declare no parameters, your custom function has this parameter.</span></span> <span data-ttu-id="4df66-129">この引数は、Excel のユーザーには表示されません。</span><span class="sxs-lookup"><span data-stu-id="4df66-129">This argument doesn't appear for a user in Excel.</span></span> <span data-ttu-id="4df66-130">カスタム関数でを使用`invocation`する場合は、最後のパラメーターとして宣言します。</span><span class="sxs-lookup"><span data-stu-id="4df66-130">If you want to use `invocation` in your custom function, declare it as the last parameter.</span></span>

<span data-ttu-id="4df66-131">次のコードサンプルでは、 `invocation`コンテキストが参照に対して明示的に指定されています。</span><span class="sxs-lookup"><span data-stu-id="4df66-131">In the following code sample, the `invocation` context is explicitly stated for your reference.</span></span>

```js
/**
 * Add two numbers.
 * @customfunction 
 * @param {number} first First number.
 * @param {number} second Second number.
 * @returns {number} The sum of the two (or optionally three) numbers.
 */
function add(first, second, invocation) {
  return first + second;
}
CustomFunctions.associate("ADD", add);
```

<span data-ttu-id="4df66-132">このパラメーターを使用すると、呼び出し元のセルのコンテキストを取得できます。これは、[カスタム関数を呼び出すセルのアドレスを検索](#addressing-cells-context-parameter)するなどの一部のシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4df66-132">The parameter allows you to get the context of the invoking cell, which can be helpful in some scenarios including [discovering the address of a cell which invoke a custom function](#addressing-cells-context-parameter).</span></span>

### <a name="addressing-cells-context-parameter"></a><span data-ttu-id="4df66-133">アドレス指定セルのコンテキストパラメーター</span><span class="sxs-lookup"><span data-stu-id="4df66-133">Addressing cell's context parameter</span></span>

<span data-ttu-id="4df66-134">場合によっては、カスタム関数を呼び出したセルのアドレスを取得する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4df66-134">In some cases you need to get the address of the cell that invoked your custom function.</span></span> <span data-ttu-id="4df66-135">これは、次の種類のシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="4df66-135">This is useful in the following types of scenarios:</span></span>

- <span data-ttu-id="4df66-136">範囲の書式設定: セルのアドレスをキーとして使用して、 [Office](/office/dev/add-ins/excel/custom-functions-runtime#storing-and-accessing-data)に情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="4df66-136">Formatting ranges: Use the cell's address as the key to store information in [Office.storage](/office/dev/add-ins/excel/custom-functions-runtime#storing-and-accessing-data).</span></span> <span data-ttu-id="4df66-137">Excel で [onCalculated](/javascript/api/excel/excel.worksheet#oncalculated) を使用して`Office.storage` からキーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="4df66-137">Then, use [onCalculated](/javascript/api/excel/excel.worksheet#oncalculated) in Excel to load the key from `Office.storage`.</span></span>
- <span data-ttu-id="4df66-138">キャッシュされた値を表示させる: 関数がオフラインで使用される場合、`onCalculated` を使用して `Office.storage` に格納されているキャッシュされた値を表示します。</span><span class="sxs-lookup"><span data-stu-id="4df66-138">Displaying cached values: If your function is used offline, display stored cached values from `Office.storage` using `onCalculated`.</span></span>
- <span data-ttu-id="4df66-139">調整: セル アドレスを使用して元のセルを検出し、処理が発生している場所での調整を行えます。</span><span class="sxs-lookup"><span data-stu-id="4df66-139">Reconciliation: Use the cell's address to discover an origin cell to help you reconcile where processing is occurring.</span></span>

<span data-ttu-id="4df66-140">関数内のアドレス指定セルのコンテキストを要求するには、次の例のように、関数を使用してセルのアドレスを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4df66-140">To request an addressing cell's context in a function, you need to use a function to find the cell's address, such as the one in the following example.</span></span> <span data-ttu-id="4df66-141">セルのアドレスに関する情報は、関数のコメント`@requiresAddress`にタグ付けされている場合にのみ公開されます。</span><span class="sxs-lookup"><span data-stu-id="4df66-141">The information about a cell's address is exposed only if `@requiresAddress` is tagged in the function's comments.</span></span>

```js
/**
 * Function that gets the address of a cell.
 * @customfunction
 * @param {CustomFunctions.Invocation} invocation Uses the invocation parameter present in each cell.
 * @requiresAddress
 * @returns {string} Returns address of cell.
 */

function getAddress(invocation) {
  return invocation.address;
}
CustomFunctions.associate("GETADDRESS", getAddress);
```

<span data-ttu-id="4df66-142">既定では、`getAddress` 関数が返す値は次の形式に従います: `SheetName!CellNumber`。</span><span class="sxs-lookup"><span data-stu-id="4df66-142">By default, values returned from a `getAddress` function follow the following format: `SheetName!CellNumber`.</span></span> <span data-ttu-id="4df66-143">たとえば、ある関数が Expenses という名前のシートのセル B2 から呼び出される場合の戻り値は `Expenses!B2` になります。</span><span class="sxs-lookup"><span data-stu-id="4df66-143">For example, if a function was called from a sheet called Expenses in cell B2, the returned value would be `Expenses!B2`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4df66-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="4df66-144">See also</span></span>

* [<span data-ttu-id="4df66-145">Excel でカスタム関数を作成する</span><span class="sxs-lookup"><span data-stu-id="4df66-145">Create custom functions in Excel</span></span>](custom-functions-overview.md)
* [<span data-ttu-id="4df66-146">カスタム関数のメタデータ</span><span class="sxs-lookup"><span data-stu-id="4df66-146">Custom functions metadata</span></span>](custom-functions-json.md)
* [<span data-ttu-id="4df66-147">カスタム関数のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="4df66-147">Custom functions best practices</span></span>](custom-functions-best-practices.md)
* [<span data-ttu-id="4df66-148">カスタム関数の変更ログ</span><span class="sxs-lookup"><span data-stu-id="4df66-148">Custom functions changelog</span></span>](custom-functions-changelog.md)
* [<span data-ttu-id="4df66-149">Excel カスタム関数のチュートリアル</span><span class="sxs-lookup"><span data-stu-id="4df66-149">Excel custom functions tutorial</span></span>](../tutorials/excel-tutorial-create-custom-functions.md)