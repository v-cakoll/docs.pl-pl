---
title: Ładowanie danych z plików i innych źródeł
description: W tym przykładzie pokazano, jak załadować dane do przetwarzania i uczenia w programie ML.NET. Dane są początkowo przechowywane w plikach lub w innych źródłach danych, takich jak bazy danych, JSON, XML lub kolekcje w pamięci.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 07b3e7f5302a03f5fa4c936679c8a3c00d19a7b0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740550"
---
# <a name="load-data-from-files-and-other-sources"></a><span data-ttu-id="84369-104">Ładowanie danych z plików i innych źródeł</span><span class="sxs-lookup"><span data-stu-id="84369-104">Load data from files and other sources</span></span>

<span data-ttu-id="84369-105">W tym przykładzie pokazano, jak załadować dane do przetwarzania i uczenia w programie ML.NET.</span><span class="sxs-lookup"><span data-stu-id="84369-105">This how-to shows you how to load data for processing and training into ML.NET.</span></span> <span data-ttu-id="84369-106">Dane są początkowo przechowywane w plikach lub w innych źródłach danych, takich jak bazy danych, JSON, XML lub kolekcje w pamięci.</span><span class="sxs-lookup"><span data-stu-id="84369-106">The data is originally stored in files or other data sources such as databases, JSON, XML or in-memory collections.</span></span>

## <a name="create-the-data-model"></a><span data-ttu-id="84369-107">Tworzenie modelu danych</span><span class="sxs-lookup"><span data-stu-id="84369-107">Create the data model</span></span>

<span data-ttu-id="84369-108">ML.NET umożliwia definiowanie modeli danych za pośrednictwem klas.</span><span class="sxs-lookup"><span data-stu-id="84369-108">ML.NET enables you to define data models via classes.</span></span> <span data-ttu-id="84369-109">Na przykład uwzględniając następujące dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="84369-109">For example, given the following input data:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

<span data-ttu-id="84369-110">Utwórz model danych, który reprezentuje Poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="84369-110">Create a data model that represents the snippet below:</span></span>

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

### <a name="annotating-the-data-model-with-column-attributes"></a><span data-ttu-id="84369-111">Dodawanie adnotacji do modelu danych z atrybutami kolumn</span><span class="sxs-lookup"><span data-stu-id="84369-111">Annotating the data model with column attributes</span></span>

<span data-ttu-id="84369-112">Atrybuty dają ML.NET więcej informacji na temat modelu danych i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="84369-112">Attributes give ML.NET more information about the data model and the data source.</span></span>

<span data-ttu-id="84369-113">Atrybut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) określa właściwości indeksów kolumn.</span><span class="sxs-lookup"><span data-stu-id="84369-113">The [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute specifies your properties' column indices.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84369-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) jest wymagana tylko w przypadku ładowania danych z pliku.</span><span class="sxs-lookup"><span data-stu-id="84369-114">[`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) is only required when loading data from a file.</span></span>

<span data-ttu-id="84369-115">Załaduj kolumny jako:</span><span class="sxs-lookup"><span data-stu-id="84369-115">Load columns as:</span></span>

- <span data-ttu-id="84369-116">Pojedyncze kolumny, takie jak `Size` i `CurrentPrices`, w klasie `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="84369-116">Individual columns like `Size` and `CurrentPrices` in the `HousingData` class.</span></span>
- <span data-ttu-id="84369-117">Wiele kolumn w czasie w postaci wektora, tak jak `HistoricalPrices` w klasie `HousingData`.</span><span class="sxs-lookup"><span data-stu-id="84369-117">Multiple columns at a time in the form of a vector like `HistoricalPrices` in the `HousingData` class.</span></span>

<span data-ttu-id="84369-118">Jeśli masz Właściwość Vector, zastosuj atrybut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) do właściwości w modelu danych.</span><span class="sxs-lookup"><span data-stu-id="84369-118">If you have a vector property, apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to the property in your data model.</span></span> <span data-ttu-id="84369-119">Należy pamiętać, że wszystkie elementy w wektorze muszą być tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="84369-119">It's important to note that all of the elements in the vector need to be the same type.</span></span> <span data-ttu-id="84369-120">Przechowywanie oddzielonych kolumn umożliwia łatwe i elastyczne Inżynieria funkcji, ale w przypadku bardzo dużej liczby kolumn działanie w poszczególnych kolumnach powoduje wpływ na szybkość uczenia się.</span><span class="sxs-lookup"><span data-stu-id="84369-120">Keeping the columns separated allows for ease and flexibility of feature engineering, but for a very large number of columns, operating on the individual columns causes an impact on training speed.</span></span>

<span data-ttu-id="84369-121">ML.NET działa za poorednictwem nazw kolumn.</span><span class="sxs-lookup"><span data-stu-id="84369-121">ML.NET Operates through column names.</span></span> <span data-ttu-id="84369-122">Jeśli chcesz zmienić nazwę kolumny na inną niż nazwa właściwości, Użyj atrybutu [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="84369-122">If you want to change the name of a column to something other than the property name, use the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span> <span data-ttu-id="84369-123">Podczas tworzenia obiektów w pamięci, nadal można tworzyć obiekty przy użyciu nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="84369-123">When creating in-memory objects, you still create objects using the property name.</span></span> <span data-ttu-id="84369-124">Jednak w przypadku przetwarzania danych i kompilowania modeli uczenia maszynowego ML.NET przesłania i odwołuje się do właściwości o wartości podanej w atrybucie [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="84369-124">However, for data processing and building machine learning models, ML.NET overrides and references the property with the value provided in the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute.</span></span>

## <a name="load-data-from-a-single-file"></a><span data-ttu-id="84369-125">Ładowanie danych z jednego pliku</span><span class="sxs-lookup"><span data-stu-id="84369-125">Load data from a single file</span></span>

<span data-ttu-id="84369-126">Aby załadować dane z pliku, użyj metody [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) wraz z modelem danych w celu załadowania danych.</span><span class="sxs-lookup"><span data-stu-id="84369-126">To load data from a file use the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method along with the data model for the data to be loaded.</span></span> <span data-ttu-id="84369-127">Ponieważ parametr `separatorChar` jest domyślnie rozdzielany tabulatorami, w razie potrzeby zmień go na plik danych.</span><span class="sxs-lookup"><span data-stu-id="84369-127">Since `separatorChar` parameter is tab-delimited by default, change it for your data file as needed.</span></span> <span data-ttu-id="84369-128">Jeśli plik ma nagłówek, ustaw parametr `hasHeader` na `true`, aby zignorować pierwszy wiersz w pliku i rozpocząć ładowanie danych z drugiego wiersza.</span><span class="sxs-lookup"><span data-stu-id="84369-128">If your file has a header, set the `hasHeader` parameter to `true` to ignore the first line in the file and begin to load data from the second line.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a><span data-ttu-id="84369-129">Ładowanie danych z wielu plików</span><span class="sxs-lookup"><span data-stu-id="84369-129">Load data from multiple files</span></span>

<span data-ttu-id="84369-130">W przypadku, gdy dane są przechowywane w wielu plikach, pod warunkiem że schemat danych jest taki sam, ML.NET umożliwia ładowanie danych z wielu plików, które znajdują się w tym samym katalogu lub w wielu katalogach.</span><span class="sxs-lookup"><span data-stu-id="84369-130">In the event that your data is stored in multiple files, as long as the data schema is the same, ML.NET allows you to load data from multiple files that are either in the same directory or multiple directories.</span></span>

### <a name="load-from-files-in-a-single-directory"></a><span data-ttu-id="84369-131">Ładowanie z plików w jednym katalogu</span><span class="sxs-lookup"><span data-stu-id="84369-131">Load from files in a single directory</span></span>

<span data-ttu-id="84369-132">Gdy wszystkie pliki danych znajdują się w tym samym katalogu, Użyj symboli wieloznacznych w metodzie [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) .</span><span class="sxs-lookup"><span data-stu-id="84369-132">When all of your data files are in the same directory, use wildcards in the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) method.</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a><span data-ttu-id="84369-133">Ładowanie z plików w wielu katalogach</span><span class="sxs-lookup"><span data-stu-id="84369-133">Load from files in multiple directories</span></span>

<span data-ttu-id="84369-134">Aby załadować dane z wielu katalogów, należy utworzyć [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)za pomocą metody [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) .</span><span class="sxs-lookup"><span data-stu-id="84369-134">To load data from multiple directories, use the [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) method to create a [`TextLoader`](xref:Microsoft.ML.Data.TextLoader).</span></span> <span data-ttu-id="84369-135">Następnie użyj metody [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) i określ poszczególne ścieżki plików (nie można używać symboli wieloznacznych).</span><span class="sxs-lookup"><span data-stu-id="84369-135">Then, use the [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) method and specify the individual file paths (wildcards can't be used).</span></span>

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a><span data-ttu-id="84369-136">Ładowanie danych z relacyjnej bazy danych</span><span class="sxs-lookup"><span data-stu-id="84369-136">Load data from a relational database</span></span>

<span data-ttu-id="84369-137">ML.NET obsługuje ładowanie danych z różnych relacyjnych baz danych obsługiwanych przez [`System.Data`](xref:System.Data) , które obejmują SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, postęp, IBM DB2 i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="84369-137">ML.NET supports loading data from a variety of relational databases supported by [`System.Data`](xref:System.Data) that include SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2, and many more.</span></span>

> [!NOTE]
> <span data-ttu-id="84369-138">Aby użyć `DatabaseLoader`, należy odwołać się do pakietu NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .</span><span class="sxs-lookup"><span data-stu-id="84369-138">To use `DatabaseLoader`, reference the [System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet package.</span></span>

<span data-ttu-id="84369-139">Nadana baza danych z tabelą o nazwie `House` i następującym schematem:</span><span class="sxs-lookup"><span data-stu-id="84369-139">Given a database with a table named `House` and the following schema:</span></span>

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

<span data-ttu-id="84369-140">Dane można modelować według klasy, takiej jak `HouseData`.</span><span class="sxs-lookup"><span data-stu-id="84369-140">The data can be modeled by a class like `HouseData`.</span></span>

```csharp
public class HouseData
{
    public float Size { get; set; }
    
    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

<span data-ttu-id="84369-141">Następnie w aplikacji Utwórz `DatabaseLoader`.</span><span class="sxs-lookup"><span data-stu-id="84369-141">Then, inside of your application, create a `DatabaseLoader`.</span></span>

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

<span data-ttu-id="84369-142">Zdefiniuj parametry połączenia oraz polecenie SQL do wykonania w bazie danych i Utwórz wystąpienie `DatabaseSource`.</span><span class="sxs-lookup"><span data-stu-id="84369-142">Define your connection string as well as the SQL command to be executed on the database and create a `DatabaseSource` instance.</span></span> <span data-ttu-id="84369-143">Ten przykład używa bazy danych LocalDB SQL Server z ścieżką do pliku.</span><span class="sxs-lookup"><span data-stu-id="84369-143">This sample uses a LocalDB SQL Server database with a file path.</span></span> <span data-ttu-id="84369-144">DatabaseLoader jednak obsługuje inne prawidłowe parametry połączenia dla baz danych lokalnie i w chmurze.</span><span class="sxs-lookup"><span data-stu-id="84369-144">However, DatabaseLoader supports any other valid connection string for databases on-premises and in the cloud.</span></span>

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

<span data-ttu-id="84369-145">Dane liczbowe, które nie są typu [`Real`](xref:System.Data.SqlDbType) , należy przekonwertować na [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="84369-145">Numerical data that is not of type [`Real`](xref:System.Data.SqlDbType) has to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="84369-146">Typ [`Real`](xref:System.Data.SqlDbType) jest reprezentowany jako wartość zmiennoprzecinkowa pojedynczej precyzji lub [`Single`](xref:System.Single), Typ wejściowy oczekiwany przez algorytmy ml.NET.</span><span class="sxs-lookup"><span data-stu-id="84369-146">The [`Real`](xref:System.Data.SqlDbType) type is represented as a single-precision floating-point value or [`Single`](xref:System.Single), the input type expected by ML.NET algorithms.</span></span> <span data-ttu-id="84369-147">W tym przykładzie kolumna `NumBed` jest liczbą całkowitą w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="84369-147">In this sample, the `NumBed` column is an integer in the database.</span></span> <span data-ttu-id="84369-148">Przy użyciu wbudowanej funkcji `CAST` jest ona konwertowana na [`Real`](xref:System.Data.SqlDbType).</span><span class="sxs-lookup"><span data-stu-id="84369-148">Using the `CAST` built-in function, it's converted to [`Real`](xref:System.Data.SqlDbType).</span></span> <span data-ttu-id="84369-149">Ponieważ właściwość `Price` jest już typu [`Real`](xref:System.Data.SqlDbType) jest załadowana jako.</span><span class="sxs-lookup"><span data-stu-id="84369-149">Because the `Price` property is already of type [`Real`](xref:System.Data.SqlDbType) it is loaded as is.</span></span>

<span data-ttu-id="84369-150">Użyj metody `Load`, aby załadować dane do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="84369-150">Use the `Load` method to load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a><span data-ttu-id="84369-151">Ładowanie danych z innych źródeł</span><span class="sxs-lookup"><span data-stu-id="84369-151">Load data from other sources</span></span>

<span data-ttu-id="84369-152">Oprócz ładowania danych przechowywanych w plikach, ML.NET obsługuje ładowanie danych ze źródeł, które obejmują, ale nie są ograniczone do:</span><span class="sxs-lookup"><span data-stu-id="84369-152">In addition to loading data stored in files, ML.NET supports loading data from sources that include but are not limited to:</span></span>

- <span data-ttu-id="84369-153">Kolekcje w pamięci</span><span class="sxs-lookup"><span data-stu-id="84369-153">In-memory collections</span></span>
- <span data-ttu-id="84369-154">JSON/XML</span><span class="sxs-lookup"><span data-stu-id="84369-154">JSON/XML</span></span>

<span data-ttu-id="84369-155">Należy pamiętać, że podczas pracy ze źródłami przesyłania strumieniowego ML.NET oczekuje, że dane wejściowe mają być w postaci kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="84369-155">Note that when working with streaming sources, ML.NET expects input to be in the form of an in-memory collection.</span></span> <span data-ttu-id="84369-156">W związku z tym podczas pracy ze źródłami, takimi jak JSON/XML, pamiętaj, aby sformatować dane w kolekcji w pamięci.</span><span class="sxs-lookup"><span data-stu-id="84369-156">Therefore, when working with sources like JSON/XML, make sure to format the data into an in-memory collection.</span></span>

<span data-ttu-id="84369-157">Nadana została następująca kolekcja w pamięci:</span><span class="sxs-lookup"><span data-stu-id="84369-157">Given the following in-memory collection:</span></span>

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

<span data-ttu-id="84369-158">Załaduj kolekcję znajdującą się w pamięci do [`IDataView`](xref:Microsoft.ML.IDataView) za pomocą metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :</span><span class="sxs-lookup"><span data-stu-id="84369-158">Load the in-memory collection into an [`IDataView`](xref:Microsoft.ML.IDataView) with the [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) method:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84369-159">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) zakłada, że [`IEnumerable`](xref:System.Collections.IEnumerable) ładowany z jest bezpieczny wątkowo.</span><span class="sxs-lookup"><span data-stu-id="84369-159">[`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) assumes that the [`IEnumerable`](xref:System.Collections.IEnumerable) it loads from is thread-safe.</span></span>

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a><span data-ttu-id="84369-160">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="84369-160">Next steps</span></span>

<span data-ttu-id="84369-161">Jeśli używasz konstruktora modelu do uczenia modelu uczenia maszynowego, zobacz [ładowanie danych szkoleniowych do konstruktora modeli](load-data-model-builder.md).</span><span class="sxs-lookup"><span data-stu-id="84369-161">If you're using Model Builder to train the machine learning model, see [Load training data into Model Builder](load-data-model-builder.md).</span></span>
