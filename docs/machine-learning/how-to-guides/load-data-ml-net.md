---
title: Ładowanie danych
description: Załaduj plik danych i danych przesyłanych strumieniowo w strukturze ML.NET
ms.date: 05/03/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 6edcc92b610e2e1f5e21c371b9f0aefd0b216d31
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063653"
---
# <a name="load-data-from-file-and-in-memory-sources"></a><span data-ttu-id="30924-103">Ładowanie danych ze źródeł plików i w pamięci</span><span class="sxs-lookup"><span data-stu-id="30924-103">Load data from file and in-memory sources</span></span>

<span data-ttu-id="30924-104">Niniejszy instruktaż przedstawia sposób ładowania danych do przetwarzania i szkolenia w strukturze ML.NET.</span><span class="sxs-lookup"><span data-stu-id="30924-104">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="30924-105">Dane początkowo są przechowywane w plikach lub źródeł danych w czasie rzeczywistym / przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="30924-105">The data is originally stored in files or real-time / streaming data sources.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="30924-106">Tworzenie modelu danych</span><span class="sxs-lookup"><span data-stu-id="30924-106">Create the data model</span></span>

<span data-ttu-id="30924-107">Strukturze ML.NET umożliwia zdefiniowanie modele danych przy użyciu klas.</span><span class="sxs-lookup"><span data-stu-id="30924-107">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="30924-108">Na przykład biorąc pod uwagę następujące dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="30924-108">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="30924-109">Utwórz model danych, który reprezentuje poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="30924-109">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="30924-110">Dodawanie adnotacji do modelu danych przy użyciu atrybutów kolumny</span><span class="sxs-lookup"><span data-stu-id="30924-110">Annotating the data model with column attributes</span></span>

<span data-ttu-id="30924-111">Atrybuty zapewniają strukturze ML.NET dowiedzieć się więcej o modelu danych i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="30924-111">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="30924-112">[ `LoadColumn` ](xref:Microsoft.ML.Data.LoadColumnAttribute) Atrybut określa swoje właściwości kolumny indeksów.</span><span class="sxs-lookup"><span data-stu-id="30924-112">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30924-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) jest wymagane tylko w przypadku ładowania danych z pliku.</span><span class="sxs-lookup"><span data-stu-id="30924-113">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="30924-114">Ładowanie kolumny jako:</span><span class="sxs-lookup"><span data-stu-id="30924-114">Load columns as:</span></span> 
- <span data-ttu-id="30924-115">Poszczególnych kolumn, takich jak `Size` i `CurrentPrices` w `HousingData` klasy.</span><span class="sxs-lookup"><span data-stu-id="30924-115">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="30924-116">Wiele kolumn w czasie w postaci wektora, takich jak `HistoricalPrices` w `HousingData` klasy.</span><span class="sxs-lookup"><span data-stu-id="30924-116">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="30924-117">Jeśli właściwość, należy zastosować [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybutu do właściwości w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="30924-117">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="30924-118">Należy zauważyć, że wszystkie elementy w wektorze muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="30924-118">It's important to note that all of the elements in the vector need to be the same type.</span></span>

<span data-ttu-id="30924-119">Operates strukturze ML.NET za pomocą nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="30924-119">ML.NET Operates through column names.</span></span> <span data-ttu-id="30924-120">Aby zmienić nazwę kolumny na coś innego niż nazwa właściwości, należy użyć [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30924-120">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="30924-121">Podczas tworzenia obiektów w pamięci, możesz nadal tworzyć obiektów przy użyciu nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="30924-121">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="30924-122">Jednak do przetwarzania danych i modeli uczenia maszynowego budynku strukturze ML.NET zastępuje i odwołuje się do właściwości z wartością w [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30924-122">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="30924-123">Ładowanie danych z pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="30924-123">Load data from a single file</span></span>

<span data-ttu-id="30924-124">Ładowanie danych z użyciem pliku [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody oraz model danych do ładowania danych.</span><span class="sxs-lookup"><span data-stu-id="30924-124">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="30924-125">Ponieważ `separatorChar` parametr jest rozdzielany tabulatorami domyślnie, zmiany dla pliku danych, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="30924-125">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="30924-126">Jeśli plik zawiera nagłówek, ustaw `hasHeader` parametr `true` zignorować pierwszy wiersz w pliku i rozpocząć do ładowania danych z drugiego wiersza.</span><span class="sxs-lookup"><span data-stu-id="30924-126">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="30924-127">Ładowanie danych z wielu plików</span><span class="sxs-lookup"><span data-stu-id="30924-127">Load data from multiple files</span></span>

<span data-ttu-id="30924-128">W przypadku, gdy dane są przechowywane w wielu plikach, tak długo, jak schemat danych jest taka sama, strukturze ML.NET umożliwia ładowanie danych z wielu plików, które są w tym samym katalogu lub wiele katalogów.</span><span class="sxs-lookup"><span data-stu-id="30924-128">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="30924-129">Ładowanie z plików w jednym katalogu</span><span class="sxs-lookup"><span data-stu-id="30924-129">Load from files in a single directory</span></span>

<span data-ttu-id="30924-130">W przypadku wszystkich plików danych w tym samym katalogu, użyj symboli wieloznacznych w [ `LoadFromTextFile` ](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) metody.</span><span class="sxs-lookup"><span data-stu-id="30924-130">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="30924-131">Ładowanie z plików w wielu katalogach</span><span class="sxs-lookup"><span data-stu-id="30924-131">Load from files in multiple directories</span></span>

<span data-ttu-id="30924-132">Ładowanie danych z wieloma katalogami, użyj [ `CreateTextLoader` ](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metodę w celu utworzenia [ `TextLoader` ](xref:Microsoft.ML.Data.TextLoader).</span><span class="sxs-lookup"><span data-stu-id="30924-132">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="30924-133">Następnie należy użyć [ `TextLoader.Load` ](xref:Microsoft.ML.DataLoaderExtensions.Load*) metody i określ ścieżki poszczególnych plików (nie można używać symboli wieloznacznych).</span><span class="sxs-lookup"><span data-stu-id="30924-133">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-streaming-source"></a><span data-ttu-id="30924-134">Ładowanie danych ze strumieniowego źródła</span><span class="sxs-lookup"><span data-stu-id="30924-134">Load data from a streaming source</span></span>

<span data-ttu-id="30924-135">Oprócz ładowania danych przechowywanych na dysku, strukturze ML.NET obsługuje ładowanie danych z różnych źródeł przesyłania strumieniowego, które obejmują, ale nie są ograniczone do:</span><span class="sxs-lookup"><span data-stu-id="30924-135">In addition to loading data stored on disk, ML.NET supports loading data from various streaming sources that include but are not limited to:</span></span>

- <span data-ttu-id="30924-136">Kolekcje w pamięci</span><span class="sxs-lookup"><span data-stu-id="30924-136">In-memory collections</span></span>
- <span data-ttu-id="30924-137">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="30924-137">JSON/XML</span></span>
- <span data-ttu-id="30924-138">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="30924-138">Databases</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30924-139">Należy pamiętać, że podczas pracy z przesyłaniem strumieniowym źródeł, strukturze ML.NET oczekuje, że dane wejściowe, aby być w formie kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="30924-139">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="30924-140">W związku z tym podczas pracy z źródeł, takich jak JSON/XML, upewnij się sformatować dane do kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="30924-140">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="30924-141">Biorąc pod uwagę następujące kolekcji w pamięci:</span><span class="sxs-lookup"><span data-stu-id="30924-141">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="30924-142">Ładowanie kolekcji w pamięci do [ `IDataView` ](xref:Microsoft.ML.IDataView) z [ `LoadFromEnumerable` ](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:</span><span class="sxs-lookup"><span data-stu-id="30924-142">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
