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
# <a name="inspect-intermediate-data-during-processing"></a>Sprawdzanie danych pośrednich podczas przetwarzania

Dowiedz się, jak przeprowadzać inspekcję danych pośrednich podczas ładowania, przetwarzania i kroki szkolenie modelu w strukturze ML.NET. Pośrednie dane znajdują się dane wyjściowe każdego etapu w potoku uczenia maszynowego.

Pośrednich danych, takich jak jeden reprezentowane poniżej, który jest ładowany do [ `IDataView` ](xref:Microsoft.ML.IDataView) mogą być kontrolowane na różne sposoby, w strukturze ML.NET.
 
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

## <a name="convert-idataview-to-ienumerable"></a>Konwertuj IDataView do interfejsu IEnumerable

Najszybszy sposób sprawdzić [ `IDataView` ](xref:Microsoft.ML.IDataView) jest, aby przekonwertować go pod kątem [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601). Aby przekonwertować [ `IDataView` ](xref:Microsoft.ML.IDataView) do [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) użyj [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) metody. 

Aby zoptymalizować wydajność, ustaw `reuseRowObject` do `true`. To opóźnieniem spowoduje wypełnienie tego samego obiektu przy użyciu danych bieżącego wiersza, ponieważ jest szacowana w przeciwieństwie tworzenia nowego obiektu dla każdego wiersza w zestawie danych.

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

## <a name="accessing-specific-indices-with-ienumerable"></a>Uzyskiwanie dostępu do określonych wskaźników za pomocą interfejsu IEnumerable

Jeśli wymagane jest tylko dostęp do części danych lub określonych indeksów, użyj [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) i ustaw `reuseRowObject` wartości parametru `false` , nowy obiekt jest tworzony dla każdego z żądanych wierszy w zestawie danych. Następnie przekonwertować [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) do tablicy lub listy.

> [!WARNING]
> Konwertowanie wynik [ `CreateEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) do tablicy lub listy załaduje wszystkie żądany [ `IDataView` ](xref:Microsoft.ML.IDataView) wierszy do pamięci, która może wpływać na wydajność.

Po utworzeniu kolekcji można wykonywać operacje na danych. Poniższy fragment kodu pobiera pierwszych trzech wierszy w zestawie danych i oblicza średnią cenę bieżącego.

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

## <a name="inspect-values-in-a-single-column"></a>Sprawdź wartości w jednej kolumnie

W dowolnym momencie w modelu procesu tworzenia wartości w jednej kolumnie [ `IDataView` ](xref:Microsoft.ML.IDataView) można uzyskać dostęp za pomocą [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) metody. [ `GetColumn` ](xref:Microsoft.ML.Data.ColumnCursorExtensions.GetColumn*) Metoda zwraca wszystkie wartości w jedną kolumnę jako [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601).

```csharp
IEnumerable<float> sizeColumn = data.GetColumn<float>("Size").ToList();
```

## <a name="inspect-idataview-values-one-row-at-a-time"></a>Sprawdzanie IDataView wartości jeden wiersz w czasie

[`IDataView`](xref:Microsoft.ML.IDataView) opóźnieniem jest oceniany. Iterowanie wierszy [ `IDataView` ](xref:Microsoft.ML.IDataView) bez konwersji [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) jak pokazano w poprzednich sekcjach tego dokumentu, tworzenie [ `DataViewRowCursor` ](xref:Microsoft.ML.DataViewRowCursor) przy użyciu [ `GetRowCursor` ](xref:Microsoft.ML.IDataView.GetRowCursor*) metody i przekazywanie w [DataViewSchema](xref:Microsoft.ML.DataViewSchema) z Twojej [ `IDataView` ](xref:Microsoft.ML.IDataView) jako parametr. Następnie Iterowanie wierszy, należy użyć [ `MoveNext` ](xref:Microsoft.ML.DataViewRowCursor.MoveNext*) metoda kursora wraz z [ `ValueGetter` ](xref:Microsoft.ML.ValueGetter%601) delegatów, aby wyodrębnić odpowiednie wartości z każdej z kolumn.

> [!IMPORTANT]
> Ze względów wydajności poprzez nosicieli używane w strukturze ML.NET [ `VBuffer` ](xref:Microsoft.ML.Data.VBuffer%601) zamiast kolekcji natywnych typów (oznacza to, że `Vector`,`float[]`). 

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

## <a name="preview-result-of-pre-processing-or-training-on-a-subset-of-the-data"></a>Podgląd wyników wstępnego przetwarzania lub szkolenia dla podzestawu danych

> [!WARNING]
> Nie używaj `Preview` w środowisku produkcyjnym kod, ponieważ jest przeznaczona do debugowania i może zmniejszyć wydajność.

Model proces tworzenia jest iteracyjny i eksperymentalne. Aby wyświetlić podgląd co danych będzie wyglądać po zakończeniu przetwarzania wstępnego lub szkolenie modelu uczenia maszynowego dla podzestawu danych, użyj [ `Preview` ](xref:Microsoft.ML.DebuggerExtensions.Preview*) metoda, która zwraca [ `DataDebuggerPreview` ](xref:Microsoft.ML.Data.DataDebuggerPreview). Wynik jest obiekt z `ColumnView` i `RowView` właściwości, które są zarówno [ `IEnumerable` ](xref:System.Collections.Generic.IEnumerable%601) i zawierać wartości w określonej kolumnie lub wierszu. Określ liczbę wierszy, aby zastosować przekształcenie do przy użyciu `maxRows` parametru.

![Obiekt danych po debugera (wersja zapoznawcza)](./media/inspect-intermediate-data-ml-net/data-debugger-preview-01.png)

Wynik sprawdzania [ `IDataView` ](xref:Microsoft.ML.IDataView) powinien wyglądać podobnie do poniższego:

![Widok wierszy podglądu debugera danych](./media/inspect-intermediate-data-ml-net/data-debugger-preview-02.png)
