---
title: Kontrola danych pośrednich podczas przetwarzania ML.NET
description: Dowiedz się, jak sprawdzać dane pośrednie podczas ładowania, przetwarzania i uczenia modelu ML.NET potoku uczenia maszynowego w ML.NET.
ms.date: 06/25/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 11df1d5caaa7b7974360d863f85afbff18985e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73977093"
---
# <a name="inspect-intermediate-data-during-processing"></a>Kontrola danych pośrednich podczas przetwarzania

Dowiedz się, jak sprawdzać dane pośrednie podczas ładowania, przetwarzania i modelowania kroków szkoleniowych w ML.NET. Dane pośrednie to dane wyjściowe każdego etapu w potoku uczenia maszynowego.

Dane pośrednie, takie jak ten przedstawiony [`IDataView`](xref:Microsoft.ML.IDataView) poniżej, który jest ładowany do można sprawdzić na różne sposoby w ML.NET.

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

## <a name="convert-idataview-to-ienumerable"></a>Konwertowanie widoku IDataView na numeryzowalne

Jednym z najszybszych sposobów, [`IDataView`](xref:Microsoft.ML.IDataView) aby sprawdzić jest [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601)konwersja go do . Aby przekonwertować [`IDataView`](xref:Microsoft.ML.IDataView) [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) do korzystania z metody.

Aby zoptymalizować `reuseRowObject` `true`wydajność, ustaw na . W ten sposób leniwie wypełnić ten sam obiekt z danymi bieżącego wiersza, jak to jest oceniane, w przeciwieństwie do tworzenia nowego obiektu dla każdego wiersza w zestawie danych.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Uzyskiwanie dostępu do określonych indeksów za pomocą numerywalnych

Jeśli potrzebujesz tylko dostępu do części danych lub określonych [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) indeksów, `reuseRowObject` należy `false` użyć i ustawić wartość parametru, aby nowy obiekt został utworzony dla każdego żądanego wiersza w zestawie danych. Następnie przekonwertuj je na [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) tablicę lub listę.

> [!WARNING]
> Konwersja wyniku [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) do tablicy lub listy załaduje wszystkie żądane [`IDataView`](xref:Microsoft.ML.IDataView) wiersze do pamięci, co może mieć wpływ na wydajność.

Po utworzeniu kolekcji można wykonywać operacje na danych. Poniższy fragment kodu przyjmuje pierwsze trzy wiersze w zestawie danych i oblicza średnią bieżącą cenę.

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

## <a name="inspect-values-in-a-single-column"></a>Sprawdzanie wartości w pojedynczej kolumnie

W dowolnym momencie procesu budowania modelu wartości w [`IDataView`](xref:Microsoft.ML.IDataView) jednej kolumnie an [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) są dostępne za pomocą metody. Metoda [`GetColumn`](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) zwraca wszystkie wartości w jednej kolumnie jako [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Sprawdzanie wartości IDataView po jednym wierszu naraz

[`IDataView`](xref:Microsoft.ML.IDataView)jest leniwie oceniane. Aby iterate przez wiersze [`IDataView`](xref:Microsoft.ML.IDataView) bez konwertowania [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) do jak pokazano w poprzednich sekcjach tego dokumentu, należy [`DataViewRowCursor`](xref:Microsoft.ML.DataViewRowCursor) utworzyć przy użyciu [`GetRowCursor`](xref:Microsoft.ML.IDataView.GetRowCursor*) metody i przekazywanie w [DataViewSchema](xref:Microsoft.ML.DataViewSchema) jako [`IDataView`](xref:Microsoft.ML.IDataView) parametr. Następnie, aby iterate nad wierszami, użyj [`MoveNext`](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) metody [`ValueGetter`](xref:Microsoft.ML.ValueGetter%601) kursora wraz z delegatów wyodrębnić odpowiednie wartości z każdej kolumny.

> [!IMPORTANT]
> Dla celów wydajności wektory [`VBuffer`](xref:Microsoft.ML.Data.VBuffer%601) w ML.NET używać zamiast `Vector`typów`float[]`kolekcji natywnych (tj.

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Podgląd wyniku wstępnego przetwarzania lub szkolenia w podzbiorze danych

> [!WARNING]
> Nie należy `Preview` używać w kodzie produkcyjnym, ponieważ jest przeznaczony do debugowania i może zmniejszyć wydajność.

Proces budowania modelu jest eksperymentalny i iteracyjny. Aby wyświetlić podgląd danych po wstępnym przetwarzaniu lub szkoleniu modelu uczenia maszynowego [`Preview`](xref:Microsoft.ML.DebuggerExtensions.Preview*) w podzbiorze danych, należy użyć metody, która zwraca wartość . [`DataDebuggerPreview`](xref:Microsoft.ML.Data.DataDebuggerPreview) Wynik jest obiekt `ColumnView` emi i `RowView` właściwości, [`IEnumerable`](xref:System.Collections.Generic.IEnumerable%601) które są zarówno i zawierają wartości w określonej kolumnie lub wierszu. Określ liczbę wierszy, do które `maxRows` mają zostać zastosowane transformację za pomocą parametru.

![Obiekt podglądu debugera danych](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Wynik kontroli [`IDataView`](xref:Microsoft.ML.IDataView) będzie wyglądać podobnie do następujących:

![Widok wiersza podglądu debugera danych](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
