---
title: 'Instrukcje: Ładowanie danych w strukturze ML.NET'
description: Załaduj plik danych i danych przesyłanych strumieniowo w strukturze ML.NET
ms.date: 04/03/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 7702c626aa79c7b661638df5a5f0f90f821b32f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981271"
---
# <a name="how-to-learn-how-to-load-data-from-file-and-real-time-sources-in-mlnet"></a>Instrukcje: Dowiedz się, jak załadować dane z pliku i źródeł w czasie rzeczywistym w strukturze ML.NET

Niniejszy instruktaż przedstawia sposób ładowania danych do przetwarzania i szkolenia w strukturze ML.NET. Dane początkowo są przechowywane w plikach lub źródeł danych w czasie rzeczywistym / przesyłania strumieniowego.

## <a name="create-the-data-model"></a>Tworzenie modelu danych

Strukturze ML.NET umożliwia zdefiniowanie modele danych przy użyciu klas. Na przykład biorąc pod uwagę następujące dane wejściowe:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Utwórz model danych, który reprezentuje poniższy fragment kodu:

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

### <a name="annotating-the-data-model-with-column-attributes"></a>Dodawanie adnotacji do modelu danych przy użyciu atrybutów kolumny

Atrybuty zapewniają strukturze ML.NET dowiedzieć się więcej o modelu danych i źródła danych.

[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Atrybut określa swoje właściwości kolumny indeksów.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) jest wymagane tylko w przypadku ładowania danych z pliku.

Ładowanie kolumny jako: 
- Poszczególnych kolumn, takich jak `Size` i `CurrentPrices` w `HousingData` klasy.
- Wiele kolumn w czasie w postaci wektora, takich jak `HistoricalPrices` w `HousingData` klasy.

Jeśli właściwość, należy zastosować [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybutu do właściwości w modelu danych. Należy zauważyć, że wszystkie elementy w wektorze muszą być tego samego typu.

Operates strukturze ML.NET za pomocą nazw kolumn. Aby zmienić nazwę kolumny na coś innego niż nazwa właściwości, należy użyć [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu. Podczas tworzenia obiektów w pamięci, możesz nadal tworzyć obiektów przy użyciu nazwy właściwości. Jednak do przetwarzania danych i modeli uczenia maszynowego budynku strukturze ML.NET zastępuje i odwołuje się do właściwości z wartością w [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu.

## <a name="load-data-from-a-single-file"></a>Ładowanie danych z pojedynczego pliku

Ładowanie danych z użyciem pliku [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody oraz model danych do ładowania danych. Ponieważ `separatorChar` parametr jest rozdzielany tabulatorami domyślnie, zmiany dla pliku danych, zgodnie z potrzebami. Jeśli plik zawiera nagłówek, ustaw `hasHeader` parametr `true` zignorować pierwszy wiersz w pliku i rozpocząć do ładowania danych z drugiego wiersza.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Ładowanie danych z wielu plików

W przypadku, gdy dane są przechowywane w wielu plikach, tak długo, jak schemat danych jest taka sama, strukturze ML.NET umożliwia ładowanie danych z wielu plików, które są w tym samym katalogu lub wiele katalogów.

### <a name="load-from-files-in-a-single-directory"></a>Ładowanie z plików w jednym katalogu

W przypadku wszystkich plików danych w tym samym katalogu, użyj symboli wieloznacznych w [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Ładowanie z plików w wielu katalogach

Ładowanie danych z wieloma katalogami, użyj [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metodę w celu utworzenia [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader). Następnie należy użyć [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) metody i określ ścieżki poszczególnych plików (nie można używać symboli wieloznacznych).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-streaming-source"></a>Ładowanie danych ze strumieniowego źródła

Oprócz ładowania danych przechowywanych na dysku, strukturze ML.NET obsługuje ładowanie danych z różnych źródeł przesyłania strumieniowego, które obejmują, ale nie są ograniczone do:

- Kolekcje w pamięci
- JSON/XML
- Bazy danych

> [!IMPORTANT]
> Należy pamiętać, że podczas pracy z przesyłaniem strumieniowym źródeł, strukturze ML.NET oczekuje, że dane wejściowe, aby być w formie kolekcji w pamięci. W związku z tym podczas pracy z źródeł, takich jak JSON/XML, upewnij się sformatować dane do kolekcji w pamięci.

Biorąc pod uwagę następujące kolekcji w pamięci:

```csharp
HousingData[] inMemoryCollection = new HousingData[]
{
    new HousingData
    {
        Size =700f,
        HistoricalPrices = new float[]
        {
            100000f, 3000000f, 250000f
        },
        CurrentPrice = 500000f
    },
    new HousingData
    {
        Size =1000f,
        HistoricalPrices = new float[]
        {
            600000f, 400000f, 650000f
        },
        CurrentPrice=700000f
    }
};
```

Ładowanie kolekcji w pamięci do [ `IDataView` ](xref:Microsoft.ML.IDataView) z [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```