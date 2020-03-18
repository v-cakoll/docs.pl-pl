---
title: Ładowanie danych z plików i innych źródeł
description: Dowiedz się, jak załadować dane do przetwarzania i szkolenia do ML.NET przy użyciu interfejsu API. Dane są przechowywane w plikach, bazach danych, Kolekcjach JSON, XML lub w pamięci.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74344753"
---
# <a name="load-data-from-files-and-other-sources"></a>Ładowanie danych z plików i innych źródeł

Dowiedz się, jak załadować dane do przetwarzania i szkolenia do ML.NET przy użyciu interfejsu API. Dane są pierwotnie przechowywane w plikach lub innych źródłach danych, takich jak bazy danych, JSON, XML lub w pamięci kolekcji.

Jeśli używasz Konstruktora modeli, zobacz [Ładowanie danych szkoleniowych do Konstruktora modeli](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Tworzenie modelu danych

ML.NET umożliwia definiowanie modeli danych za pomocą klas. Na przykład, biorąc pod uwagę następujące dane wejściowe:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Utwórz model danych reprezentujący poniższy fragment kodu:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Adnotowanie modelu danych za pomocą atrybutów kolumn

Atrybuty dają ML.NET więcej informacji na temat modelu danych i źródła danych.

Atrybut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) określa indeksy kolumn właściwości.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute)jest wymagane tylko podczas ładowania danych z pliku.

Załaduj kolumny jako:

- Poszczególne `Size` kolumny `CurrentPrices` jak `HousingData` i w klasie.
- Wiele kolumn naraz w postaci wektora, jak `HistoricalPrices` w `HousingData` klasie.

Jeśli masz właściwość wektorową, zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do właściwości w modelu danych. Ważne jest, aby pamiętać, że wszystkie elementy wektora muszą być tego samego typu. Utrzymywanie kolumn w separacji pozwala na łatwość i elastyczność inżynierii funkcji, ale dla bardzo dużej liczby kolumn, praca na poszczególnych kolumnach powoduje wpływ na szybkość treningu.

ML.NET działa za pomocą nazw kolumn. Jeśli chcesz zmienić nazwę kolumny na inną niż nazwa właściwości, [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) użyj tego atrybutu. Podczas tworzenia obiektów w pamięci nadal tworzysz obiekty przy użyciu nazwy właściwości. Jednak w przypadku przetwarzania danych i tworzenia modeli uczenia maszynowego ML.NET [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) zastępuje i odwołuje się do właściwości z wartością podaną w atrybucie.

## <a name="load-data-from-a-single-file"></a>Ładowanie danych z pojedynczego pliku

Aby załadować dane z [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) pliku należy użyć metody wraz z modelem danych dla danych, które mają być załadowane. Ponieważ `separatorChar` parametr jest domyślnie rozdzielany przez kartę, w razie potrzeby zmień go dla pliku danych. Jeśli plik ma nagłówek, `hasHeader` ustaw `true` parametr tak, aby ignorował pierwszy wiersz w pliku i zaczął ładować dane z drugiego wiersza.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Ładowanie danych z wielu plików

W przypadku, gdy dane są przechowywane w wielu plikach, tak długo, jak schemat danych jest taki sam, ML.NET umożliwia ładowanie danych z wielu plików, które znajdują się w tym samym katalogu lub wielu katalogach.

### <a name="load-from-files-in-a-single-directory"></a>Ładowanie z plików w jednym katalogu

Gdy wszystkie pliki danych znajdują się w tym samym [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) katalogu, należy użyć symboli wieloznacznych w metodzie.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Ładowanie z plików w wielu katalogach

Aby załadować dane z wielu [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) katalogów, [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)użyj metody, aby utworzyć plik . Następnie użyj [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) metody i określ poszczególne ścieżki plików (symboli wieloznacznych nie można używać).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Ładowanie danych z relacyjnej bazy danych

ML.NET obsługuje ładowanie danych z różnych relacyjnych [`System.Data`](xref:System.Data) baz danych obsługiwanych przez to SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, Progress, IBM DB2 i wiele innych.

> [!NOTE]
> Aby `DatabaseLoader`użyć , odwołać się do [pakietu System.Data.SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) NuGet.

Biorąc pod uwagę bazę `House` danych o nazwie tabeli i następujący schemat:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Dane mogą być modelowane przez `HouseData`klasę, taką jak .

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Następnie, wewnątrz aplikacji, utwórz plik `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Zdefiniuj parametry połączenia, a także polecenie SQL, `DatabaseSource` które mają być wykonywane w bazie danych i utwórz wystąpienie. W tym przykładzie użyto bazy danych programu SQL Server localdb ze ścieżką pliku. Jednak DatabaseLoader obsługuje wszelkie inne prawidłowe parametry połączenia dla baz danych lokalnych i w chmurze.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Dane liczbowe, które [`Real`](xref:System.Data.SqlDbType) nie są typu, muszą zostać przekonwertowane na . [`Real`](xref:System.Data.SqlDbType) Typ [`Real`](xref:System.Data.SqlDbType) jest reprezentowany jako pojedyncza wartość zmiennoprzecinkowa lub [`Single`](xref:System.Single)typ wejściowy oczekiwany przez ML.NET algorytmów. W tym przykładzie `NumBed` kolumna jest liczbą całkowitą w bazie danych. Za `CAST` pomocą wbudowanej funkcji jest konwertowany [`Real`](xref:System.Data.SqlDbType)na . Ponieważ `Price` właściwość jest już [`Real`](xref:System.Data.SqlDbType) typu jest ładowany jak jest.

Użyj `Load` metody, aby załadować [`IDataView`](xref:Microsoft.ML.IDataView)dane do pliku .

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Ładowanie danych z innych źródeł

Oprócz ładowania danych przechowywanych w plikach, ML.NET obsługuje ładowanie danych ze źródeł, które obejmują, ale nie są ograniczone do:

- Kolekcje w pamięci
- JSON/XML

Należy zauważyć, że podczas pracy ze źródłami przesyłania strumieniowego ML.NET oczekuje, że dane wejściowe będą w formie kolekcji w pamięci. W związku z tym podczas pracy ze źródłami, takimi jak JSON/XML, upewnij się, że dane są sformatowany w kolekcji w pamięci.

Biorąc pod uwagę następującą kolekcję w pamięci:

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

Załaduj kolekcję [`IDataView`](xref:Microsoft.ML.IDataView) w [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) pamięci do metody:

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*)zakłada, że [`IEnumerable`](xref:System.Collections.IEnumerable) ładuje się z jest bezpieczny dla wątków.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Następne kroki

- Aby wyczyścić lub w inny sposób przetworzyć dane, zobacz [Przygotowywanie danych do tworzenia modelu](prepare-data-ml-net.md).
- Gdy wszystko będzie gotowe do utworzenia modelu, zobacz [Pociąg i oceń model](train-machine-learning-model-ml-net.md).
