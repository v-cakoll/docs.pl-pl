---
title: Ładowanie danych z plików i innych źródeł
description: W tym przykładzie pokazano, jak załadować dane do przetwarzania i uczenia w programie ML.NET. Dane są początkowo przechowywane w plikach lub w innych źródłach danych, takich jak bazy danych, JSON, XML lub kolekcje w pamięci.
ms.date: 07/31/2019
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: f1fc99eb07af98b97484ee74e900b81342990cdb
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710200"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="f4ea1-104">Ładowanie danych z plików i innych źródeł</span><span class="sxs-lookup"><span data-stu-id="f4ea1-104">Load data from files and other sources</span></span>

<span data-ttu-id="f4ea1-105">W tym przykładzie pokazano, jak załadować dane do przetwarzania i uczenia w programie ML.NET.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="f4ea1-106">Dane są początkowo przechowywane w plikach lub w innych źródłach danych, takich jak bazy danych, JSON, XML lub kolekcje w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="f4ea1-107">Tworzenie modelu danych</span><span class="sxs-lookup"><span data-stu-id="f4ea1-107">Create the data model</span></span>

<span data-ttu-id="f4ea1-108">ML.NET umożliwia definiowanie modeli danych za pośrednictwem klas.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="f4ea1-109">Na przykład uwzględniając następujące dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="f4ea1-110">Utwórz model danych, który reprezentuje Poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="f4ea1-111">Dodawanie adnotacji do modelu danych z atrybutami kolumn</span><span class="sxs-lookup"><span data-stu-id="f4ea1-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="f4ea1-112">Atrybuty dają ML.NET więcej informacji na temat modelu danych i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="f4ea1-113">Ten [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) atrybut określa właściwości indeksów kolumn.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4ea1-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)jest wymagana tylko w przypadku ładowania danych z pliku.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="f4ea1-115">Załaduj kolumny jako:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-115">Load columns as:</span></span> 
- <span data-ttu-id="f4ea1-116">Pojedyncze kolumny, `Size` takie `CurrentPrices` jak i `HousingData` w klasie.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="f4ea1-117">Wiele kolumn w czasie w postaci wektora, tak jak `HistoricalPrices` `HousingData` w klasie.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="f4ea1-118">Jeśli masz Właściwość Vector, Zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do właściwości w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="f4ea1-119">Należy pamiętać, że wszystkie elementy w wektorze muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="f4ea1-120">Przechowywanie oddzielonych kolumn umożliwia łatwe i elastyczne Inżynieria funkcji, ale w przypadku bardzo dużej liczby kolumn działanie w poszczególnych kolumnach powoduje wpływ na wydajność.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes a performance impact.</span></span>

<span data-ttu-id="f4ea1-121">ML.NET działa za poorednictwem nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="f4ea1-122">Jeśli chcesz zmienić nazwę kolumny na inną niż nazwa właściwości, użyj [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="f4ea1-123">Podczas tworzenia obiektów w pamięci, nadal można tworzyć obiekty przy użyciu nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="f4ea1-124">Jednak w przypadku przetwarzania danych i kompilowania modeli uczenia maszynowego ml.NET zastąpień i odwołuje się do właściwości [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) o wartości podanej w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="f4ea1-125">Ładowanie danych z jednego pliku</span><span class="sxs-lookup"><span data-stu-id="f4ea1-125">Load data from a single file</span></span>

<span data-ttu-id="f4ea1-126">Aby załadować dane z pliku, [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) należy użyć metody wraz z modelem danych w celu załadowania danych.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="f4ea1-127">Ponieważ `separatorChar` parametr jest domyślnie rozdzielany tabulatorami, w razie potrzeby zmień go na plik danych.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="f4ea1-128">Jeśli plik ma nagłówek, ustaw `hasHeader` parametr na `true` , aby zignorować pierwszy wiersz w pliku i rozpocząć ładowanie danych z drugiego wiersza.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="f4ea1-129">Ładowanie danych z wielu plików</span><span class="sxs-lookup"><span data-stu-id="f4ea1-129">Load data from multiple files</span></span>

<span data-ttu-id="f4ea1-130">W przypadku, gdy dane są przechowywane w wielu plikach, pod warunkiem że schemat danych jest taki sam, ML.NET umożliwia ładowanie danych z wielu plików, które znajdują się w tym samym katalogu lub w wielu katalogach.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="f4ea1-131">Ładowanie z plików w jednym katalogu</span><span class="sxs-lookup"><span data-stu-id="f4ea1-131">Load from files in a single directory</span></span>

<span data-ttu-id="f4ea1-132">Gdy wszystkie pliki danych znajdują się w tym samym katalogu, Użyj symboli wieloznacznych [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) w metodzie.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="f4ea1-133">Ładowanie z plików w wielu katalogach</span><span class="sxs-lookup"><span data-stu-id="f4ea1-133">Load from files in multiple directories</span></span>

<span data-ttu-id="f4ea1-134">Aby załadować dane z wielu katalogów, użyj [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) metody w celu [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="f4ea1-135">Następnie użyj [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metody i określ poszczególne ścieżki plików (nie można używać symboli wieloznacznych).</span><span class="sxs-lookup"><span data-stu-id="f4ea1-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="f4ea1-136">Ładowanie danych z innych źródeł</span><span class="sxs-lookup"><span data-stu-id="f4ea1-136">Load data from other sources</span></span>

<span data-ttu-id="f4ea1-137">Oprócz ładowania danych przechowywanych w plikach, ML.NET obsługuje ładowanie danych ze źródeł, które obejmują, ale nie są ograniczone do:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-137">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="f4ea1-138">Kolekcje w pamięci</span><span class="sxs-lookup"><span data-stu-id="f4ea1-138">In-memory collections</span></span>
- <span data-ttu-id="f4ea1-139">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="f4ea1-139">JSON/XML</span></span>
- <span data-ttu-id="f4ea1-140">Bazy danych</span><span class="sxs-lookup"><span data-stu-id="f4ea1-140">Databases</span></span>

<span data-ttu-id="f4ea1-141">Należy pamiętać, że podczas pracy ze źródłami przesyłania strumieniowego ML.NET oczekuje, że dane wejściowe mają być w postaci kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-141">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="f4ea1-142">W związku z tym podczas pracy ze źródłami, takimi jak JSON/XML, pamiętaj, aby sformatować dane w kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-142">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="f4ea1-143">Nadana została następująca kolekcja w pamięci:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-143">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="f4ea1-144">Załaduj kolekcję znajdującą się w pamięci [`IDataView`](xref:Microsoft.ML.IDataView) do [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) metody:</span><span class="sxs-lookup"><span data-stu-id="f4ea1-144">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f4ea1-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)zakłada, że [`IEnumerable`](xref:System.Collections.IEnumerable) ładowanie z programu jest bezpieczne dla wątków.</span><span class="sxs-lookup"><span data-stu-id="f4ea1-145">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span> 

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```
