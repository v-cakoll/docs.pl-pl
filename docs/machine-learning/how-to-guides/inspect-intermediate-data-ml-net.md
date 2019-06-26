---
title: Sprawdzanie danych pośrednich podczas przetwarzania w strukturze ML.NET
description: Dowiedz się, jak przeprowadzać inspekcję danych pośrednich w strukturze ML.NET usługi machine learning potoku ładowania, przetwarzania i szkoleń modelowych kroków w strukturze ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: d6ddeb523fb229eb0ebc9c2f22809312060e4266
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402388"
---
# <a name="inspect-intermediate-data-during-processing"></a><span data-ttu-id="e03d1-103">Sprawdzanie danych pośrednich podczas przetwarzania</span><span class="sxs-lookup"><span data-stu-id="e03d1-103">Inspect intermediate data during processing</span></span>

<span data-ttu-id="e03d1-104">Dowiedz się, jak przeprowadzać inspekcję danych pośrednich podczas ładowania, przetwarzania i kroki szkolenie modelu w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e03d1-104">Learn how to inspect intermediate data during loading, processing, and model training steps in ML.NET.</span></span> <span data-ttu-id="e03d1-105">Pośrednie dane znajdują się dane wyjściowe każdego etapu w potoku uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="e03d1-105">Intermediate data is the output of each stage in the machine learning pipeline.</span></span>

<span data-ttu-id="e03d1-106">Pośrednich danych, takich jak jeden reprezentowane poniżej, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView) mogą być kontrolowane na różne sposoby, w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="e03d1-106">Intermediate data like the one represented below which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView) can be inspected in various ways in ML.NET.</span></span>
 
```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

## <a name="convert-idataview-to-ienumerable"></a><span data-ttu-id="e03d1-107">Konwertuj IDataView do interfejsu IEnumerable</span><span class="sxs-lookup"><span data-stu-id="e03d1-107">Convert IDataView to IEnumerable</span></span>

<span data-ttu-id="e03d1-108">Najszybszy sposób sprawdzić [ `IDataView` ](xref:Microsoft.ML.IDataView) jest, aby przekonwertować go pod kątem [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="e03d1-108">One of the quickest ways to inspect an [`IDataView`](xref:Microsoft.ML.IDataView) is to convert it to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span> <span data-ttu-id="e03d1-109">Aby przekonwertować [ `IDataView` ](xref:Microsoft.ML.IDataView) do [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) użyj [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody.</span><span class="sxs-lookup"><span data-stu-id="e03d1-109">To convert an [`IDataView`](xref:Microsoft.ML.IDataView) to [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) use the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span> 

<span data-ttu-id="e03d1-110">Aby zoptymalizować wydajność, ustaw `reuseRowObject` do `true`.</span><span class="sxs-lookup"><span data-stu-id="e03d1-110">To optimize performance, set `reuseRowObject` to `true`.</span></span> <span data-ttu-id="e03d1-111">To opóźnieniem spowoduje wypełnienie tego samego obiektu przy użyciu danych bieżącego wiersza, ponieważ jest szacowana w przeciwieństwie tworzenia nowego obiektu dla każdego wiersza w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="e03d1-111">Doing so will lazily populate the same object with the data of the current row as it's being evaluated as opposed to creating a new object for each row in the dataset.</span></span>

```csharp
// Create an IEnumerable of HousingData objects from IDataView
IEnumerable<HousingData> housingDataEnumerable =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: true);

// Iterate over each row
foreach (HousingData row in housingDataEnumerable)
{
    // Do something (print out Size property) with current Housing Data object being evaluated
    Console.WriteLine(row.Size);
}
```

## <a name="accessing-specific-indices-with-ienumerable"></a><span data-ttu-id="e03d1-112">Uzyskiwanie dostępu do określonych wskaźników za pomocą interfejsu IEnumerable</span><span class="sxs-lookup"><span data-stu-id="e03d1-112">Accessing specific indices with IEnumerable</span></span>

<span data-ttu-id="e03d1-113">Jeśli wymagane jest tylko dostęp do części danych lub określonych indeksów, użyj [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) i ustaw `reuseRowObject` wartości parametru `false` , nowy obiekt jest tworzony dla każdego z żądanych wierszy w zestawie danych.</span><span class="sxs-lookup"><span data-stu-id="e03d1-113">If you only need access to a portion of the data or specific indices, use [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) and set the `reuseRowObject` parameter value to `false` so a new object is created for each of the requested rows in the dataset.</span></span> <span data-ttu-id="e03d1-114">Następnie przekonwertować [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) do tablicy lub listy.</span><span class="sxs-lookup"><span data-stu-id="e03d1-114">Then, convert the [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) to an array or list.</span></span>

> [!WARNING]
> <span data-ttu-id="e03d1-115">Konwertowanie wynik [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) do tablicy lub listy załaduje wszystkie żądany [ `IDataView` ](xref:Microsoft.ML.IDataView) wierszy do pamięci, która może wpływać na wydajność.</span><span class="sxs-lookup"><span data-stu-id="e03d1-115">Converting the result of [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) to an array or list will load all the requested [`IDataView`](xref:Microsoft.ML.IDataView) rows into memory which may affect performance.</span></span>

<span data-ttu-id="e03d1-116">Po utworzeniu kolekcji można wykonywać operacje na danych.</span><span class="sxs-lookup"><span data-stu-id="e03d1-116">Once the collection has been created, you can perform operations on the data.</span></span> <span data-ttu-id="e03d1-117">Poniższy fragment kodu pobiera pierwszych trzech wierszy w zestawie danych i oblicza średnią cenę bieżącego.</span><span class="sxs-lookup"><span data-stu-id="e03d1-117">The code snippet below takes the first three rows in the dataset and calculates the average current price.</span></span>

```csharp
// Create an Array of HousingData objects from IDataView
HousingData[] housingDataArray =
    mlContext.Data.CreateEnumerable<HousingData>(data, reuseRowObject: false)
        .Take(3)
        .ToArray();

// Calculate Average CurrentPrice of First Three Elements
HousingData firstRow = housingDataArray[0];
HousingData secondRow = housingDataArray[1];
HousingData thirdRow = housingDataArray[2];
float averageCurrentPrice = (firstRow.CurrentPrice + secondRow.CurrentPrice + thirdRow.CurrentPrice) / 3;
``` 

## <a name="inspect-values-in-a-single-column"></a><span data-ttu-id="e03d1-118">Sprawdź wartości w jednej kolumnie</span><span class="sxs-lookup"><span data-stu-id="e03d1-118">Inspect values in a single column</span></span>

<span data-ttu-id="e03d1-119">W dowolnym momencie w modelu procesu tworzenia wartości w jednej kolumnie [ `IDataView` ](xref:Microsoft.ML.IDataView) można uzyskać dostęp za pomocą [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody.</span><span class="sxs-lookup"><span data-stu-id="e03d1-119">At any point in the model building process, values in a single column of an [`IDataView`](xref:Microsoft.ML.IDataView) can be accessed using the [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method.</span></span> <span data-ttu-id="e03d1-120">[ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Metoda zwraca wszystkie wartości w jedną kolumnę jako [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).</span><span class="sxs-lookup"><span data-stu-id="e03d1-120">The [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) method returns all of the values in a single column as an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).</span></span>

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a><span data-ttu-id="e03d1-121">Sprawdzanie IDataView wartości jeden wiersz w czasie</span><span class="sxs-lookup"><span data-stu-id="e03d1-121">Inspect IDataView values one row at a time</span></span>

<span data-ttu-id="e03d1-122">[`IDataView`](xref:Microsoft.ML.IDataView) opóźnieniem jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="e03d1-122">[`IDataView`](xref:Microsoft.ML.IDataView) is lazily evaluated.</span></span> <span data-ttu-id="e03d1-123">Iterowanie wierszy [ `IDataView` ](xref:Microsoft.ML.IDataView) bez konwersji [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) jak pokazano w poprzednich sekcjach tego dokumentu, tworzenie [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) przy użyciu [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) metody i przekazywanie w [DataViewSchema](xref:Microsoft.ML.DataViewSchema) z Twojej [ `IDataView` ](xref:Microsoft.ML.IDataView) jako parametr.</span><span class="sxs-lookup"><span data-stu-id="e03d1-123">To iterate over the rows of an [`IDataView`](xref:Microsoft.ML.IDataView) without converting to an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) as demonstrated in previous sections of this document, create a [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) by using the [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) method and passing in the [DataViewSchema](xref:Microsoft.ML.DataViewSchema) of your [`IDataView`](xref:Microsoft.ML.IDataView) as a parameter.</span></span> <span data-ttu-id="e03d1-124">Następnie Iterowanie wierszy, należy użyć [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) metoda kursora wraz z [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) delegatów, aby wyodrębnić odpowiednie wartości z każdej z kolumn.</span><span class="sxs-lookup"><span data-stu-id="e03d1-124">Then, to iterate over rows, use the [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) cursor method along with [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) delegates to extract the respective values from each of the columns.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e03d1-125">Ze względów wydajności poprzez nosicieli używane w strukturze ML.NET [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) zamiast kolekcji natywnych typów (oznacza to, że `Vector`,`float[]`).</span><span class="sxs-lookup"><span data-stu-id="e03d1-125">For performance purposes, vectors in ML.NET use [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) instead of native collection types (that is, `Vector`,`float[]`).</span></span> 

```csharp
// Get DataViewSchema of IDataView
DataViewSchema columns = data.Schema;

// Create DataViewCursor
using (DataViewRowCursor cursor = data.GetRowCursor(columns))
{
    // Define variables where extracted values will be stored to
    float size = default;
    VBuffer<float> historicalPrices = default;
    float currentPrice = default;

    // Define delegates for extracting values from columns
    ValueGetter<float> sizeDelegate = cursor.GetGetter<float>(columns[0]);
    ValueGetter<VBuffer<float>> historicalPriceDelegate = cursor.GetGetter<VBuffer<float>>(columns[1]);
    ValueGetter<float> currentPriceDelegate = cursor.GetGetter<float>(columns[2]);
    
    // Iterate over each row
    while (cursor.MoveNext())
    {
        //Get values from respective columns
        sizeDelegate.Invoke(ref size);
        historicalPriceDelegate.Invoke(ref historicalPrices);
        currentPriceDelegate.Invoke(ref currentPrice);
    }
}
```

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a><span data-ttu-id="e03d1-126">Podgląd wyników wstępnego przetwarzania lub szkolenia dla podzestawu danych</span><span class="sxs-lookup"><span data-stu-id="e03d1-126">Preview result of pre-processing or training on a subset of the data</span></span>

> [!WARNING]
> <span data-ttu-id="e03d1-127">Nie używaj `Preview` w środowisku produkcyjnym kod, ponieważ jest przeznaczona do debugowania i może zmniejszyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="e03d1-127">Do not use `Preview` in production code because it is intended for debugging and may reduce performance.</span></span>

<span data-ttu-id="e03d1-128">Model proces tworzenia jest iteracyjny i eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="e03d1-128">The model building process is experimental and iterative.</span></span> <span data-ttu-id="e03d1-129">Aby wyświetlić podgląd co danych będzie wyglądać po zakończeniu przetwarzania wstępnego lub szkolenie modelu uczenia maszynowego dla podzestawu danych, użyj [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) metoda, która zwraca [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview).</span><span class="sxs-lookup"><span data-stu-id="e03d1-129">To preview what data would look like after pre-processing or training a machine learning model on a subset of the data, use the [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) method which returns a [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview).</span></span> <span data-ttu-id="e03d1-130">Wynik jest obiekt z `ColumnView` i `RowView` właściwości, które są zarówno [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) i zawierać wartości w określonej kolumnie lub wierszu.</span><span class="sxs-lookup"><span data-stu-id="e03d1-130">The result is an object with `ColumnView` and `RowView` properties which are both an [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) and contain the values in a particular column or row.</span></span> <span data-ttu-id="e03d1-131">Określ liczbę wierszy, aby zastosować przekształcenie do przy użyciu `maxRows` parametru.</span><span class="sxs-lookup"><span data-stu-id="e03d1-131">Specify the number of rows to apply the transformation to with the `maxRows` parameter.</span></span>

![Obiekt danych po debugera (wersja zapoznawcza)](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

<span data-ttu-id="e03d1-133">Wynik sprawdzania [ `IDataView` ](xref:Microsoft.ML.IDataView) powinien wyglądać podobnie do poniższego:</span><span class="sxs-lookup"><span data-stu-id="e03d1-133">The result of inspecting an [`IDataView`](xref:Microsoft.ML.IDataView) would look similar to the following:</span></span>

![Widok wierszy podglądu debugera danych](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
