---
title: Ładowanie danych z plików i innych źródeł
description: Dowiedz się, jak załadować dane do przetwarzania i szkolenia do ML.NET przy użyciu interfejsu API. Dane są przechowywane w kolekcjach plików, baz danych, JSON, XML lub w pamięci.
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to, title-hack-0625
ms.openlocfilehash: 83aaae2d2e75b3076841750bf5d505390a538bc0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344753"
---
# <a name="load-data-from-files-and-other-sources"></a>Ładowanie danych z plików i innych źródeł

Dowiedz się, jak załadować dane do przetwarzania i szkolenia do ML.NET przy użyciu interfejsu API. Dane są początkowo przechowywane w plikach lub w innych źródłach danych, takich jak bazy danych, JSON, XML lub kolekcje w pamięci.

Jeśli używasz konstruktora modelu, zobacz [ładowanie danych szkoleniowych do konstruktora modeli](load-data-model-builder.md).

## <a name="create-the-data-model"></a>Tworzenie modelu danych

ML.NET umożliwia definiowanie modeli danych za pośrednictwem klas. Na przykład uwzględniając następujące dane wejściowe:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
700, 100000, 3000000, 250000, 500000
1000, 600000, 400000, 650000, 700000
```

Utwórz model danych, który reprezentuje Poniższy fragment kodu:

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

### <a name="annotating-the-data-model-with-column-attributes"></a>Dodawanie adnotacji do modelu danych z atrybutami kolumn

Atrybuty dają ML.NET więcej informacji na temat modelu danych i źródła danych.

Atrybut [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) określa właściwości indeksów kolumn.

> [!IMPORTANT]
> [`LoadColumn`](xref:Microsoft.ML.Data.LoadColumnAttribute) jest wymagana tylko w przypadku ładowania danych z pliku.

Załaduj kolumny jako:

- Pojedyncze kolumny, takie jak `Size` i `CurrentPrices`, w klasie `HousingData`.
- Wiele kolumn w czasie w postaci wektora, tak jak `HistoricalPrices` w klasie `HousingData`.

Jeśli masz Właściwość Vector, zastosuj atrybut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) do właściwości w modelu danych. Należy pamiętać, że wszystkie elementy w wektorze muszą być tego samego typu. Przechowywanie oddzielonych kolumn umożliwia łatwe i elastyczne Inżynieria funkcji, ale w przypadku bardzo dużej liczby kolumn działanie w poszczególnych kolumnach powoduje wpływ na szybkość uczenia się.

ML.NET działa za poorednictwem nazw kolumn. Jeśli chcesz zmienić nazwę kolumny na inną niż nazwa właściwości, Użyj atrybutu [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) . Podczas tworzenia obiektów w pamięci, nadal można tworzyć obiekty przy użyciu nazwy właściwości. Jednak w przypadku przetwarzania danych i kompilowania modeli uczenia maszynowego ML.NET przesłania i odwołuje się do właściwości o wartości podanej w atrybucie [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) .

## <a name="load-data-from-a-single-file"></a>Ładowanie danych z jednego pliku

Aby załadować dane z pliku, użyj metody [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) wraz z modelem danych w celu załadowania danych. Ponieważ parametr `separatorChar` jest domyślnie rozdzielany tabulatorami, w razie potrzeby zmień go na plik danych. Jeśli plik ma nagłówek, ustaw parametr `hasHeader` na `true`, aby zignorować pierwszy wiersz w pliku i rozpocząć ładowanie danych z drugiego wiersza.

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("my-data-file.csv", separatorChar: ',', hasHeader: true);
```

## <a name="load-data-from-multiple-files"></a>Ładowanie danych z wielu plików

W przypadku, gdy dane są przechowywane w wielu plikach, pod warunkiem że schemat danych jest taki sam, ML.NET umożliwia ładowanie danych z wielu plików, które znajdują się w tym samym katalogu lub w wielu katalogach.

### <a name="load-from-files-in-a-single-directory"></a>Ładowanie z plików w jednym katalogu

Gdy wszystkie pliki danych znajdują się w tym samym katalogu, Użyj symboli wieloznacznych w metodzie [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile*) .

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

//Load Data File
IDataView data = mlContext.Data.LoadFromTextFile<HousingData>("Data/*", separatorChar: ',', hasHeader: true);
```

### <a name="load-from-files-in-multiple-directories"></a>Ładowanie z plików w wielu katalogach

Aby załadować dane z wielu katalogów, należy utworzyć [`TextLoader`](xref:Microsoft.ML.Data.TextLoader)za pomocą metody [`CreateTextLoader`](xref:Microsoft.ML.TextLoaderSaverCatalog.CreateTextLoader*) . Następnie użyj metody [`TextLoader.Load`](xref:Microsoft.ML.DataLoaderExtensions.Load*) i określ poszczególne ścieżki plików (nie można używać symboli wieloznacznych).

```csharp
//Create MLContext
MLContext mlContext = new MLContext();

// Create TextLoader
TextLoader textLoader = mlContext.Data.CreateTextLoader<HousingData>(separatorChar: ',', hasHeader: true);

// Load Data
IDataView data = textLoader.Load("DataFolder/SubFolder1/1.txt", "DataFolder/SubFolder2/1.txt");
```

## <a name="load-data-from-a-relational-database"></a>Ładowanie danych z relacyjnej bazy danych

ML.NET obsługuje ładowanie danych z różnych relacyjnych baz danych obsługiwanych przez [`System.Data`](xref:System.Data) , które obejmują SQL Server, Azure SQL Database, Oracle, SQLite, PostgreSQL, postęp, IBM DB2 i wiele innych.

> [!NOTE]
> Aby użyć `DatabaseLoader`, należy odwołać się do pakietu NuGet [System. Data. SqlClient](https://www.nuget.org/packages/System.Data.SqlClient) .

Nadana baza danych z tabelą o nazwie `House` i następującym schematem:

```SQL
CREATE TABLE [House] (
    [HouseId] INT NOT NULL IDENTITY,
    [Size] INT NOT NULL,
    [NumBed] INT NOT NULL,
    [Price] REAL NOT NULL
    CONSTRAINT [PK_House] PRIMARY KEY ([HouseId])
);
```

Dane można modelować według klasy, takiej jak `HouseData`.

```csharp
public class HouseData
{
    public float Size { get; set; }

    public float NumBed { get; set; }

    public float Price { get; set; }
}
```

Następnie w aplikacji Utwórz `DatabaseLoader`.

```csharp
MLContext mlContext = new MLContext();

DatabaseLoader loader = mlContext.Data.CreateDatabaseLoader<HouseData>();
```

Zdefiniuj parametry połączenia oraz polecenie SQL do wykonania w bazie danych i Utwórz wystąpienie `DatabaseSource`. Ten przykład używa bazy danych LocalDB SQL Server z ścieżką do pliku. DatabaseLoader jednak obsługuje inne prawidłowe parametry połączenia dla baz danych lokalnie i w chmurze.

```csharp
string connectionString = @"Data Source=(LocalDB)\MSSQLLocalDB;AttachDbFilename=<YOUR-DB-FILEPATH>;Database=<YOUR-DB-NAME>;Integrated Security=True;Connect Timeout=30";

string sqlCommand = "SELECT Size, CAST(NumBed as REAL) as NumBed, Price FROM House";

DatabaseSource dbSource = new DatabaseSource(SqlClientFactory.Instance, connectionString, sqlCommand);
```

Dane liczbowe, które nie są typu [`Real`](xref:System.Data.SqlDbType) , należy przekonwertować na [`Real`](xref:System.Data.SqlDbType). Typ [`Real`](xref:System.Data.SqlDbType) jest reprezentowany jako wartość zmiennoprzecinkowa pojedynczej precyzji lub [`Single`](xref:System.Single), Typ wejściowy oczekiwany przez algorytmy ml.NET. W tym przykładzie kolumna `NumBed` jest liczbą całkowitą w bazie danych. Przy użyciu wbudowanej funkcji `CAST` jest ona konwertowana na [`Real`](xref:System.Data.SqlDbType). Ponieważ właściwość `Price` jest już typu [`Real`](xref:System.Data.SqlDbType) jest załadowana jako.

Użyj metody `Load`, aby załadować dane do [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
IDataView data = loader.Load(dbSource);
```

## <a name="load-data-from-other-sources"></a>Ładowanie danych z innych źródeł

Oprócz ładowania danych przechowywanych w plikach, ML.NET obsługuje ładowanie danych ze źródeł, które obejmują, ale nie są ograniczone do:

- Kolekcje w pamięci
- JSON/XML

Należy pamiętać, że podczas pracy ze źródłami przesyłania strumieniowego ML.NET oczekuje, że dane wejściowe mają być w postaci kolekcji w pamięci. W związku z tym podczas pracy ze źródłami, takimi jak JSON/XML, pamiętaj, aby sformatować dane w kolekcji w pamięci.

Nadana została następująca kolekcja w pamięci:

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

Załaduj kolekcję znajdującą się w pamięci do [`IDataView`](xref:Microsoft.ML.IDataView) za pomocą metody [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) :

> [!IMPORTANT]
> [`LoadFromEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.LoadFromEnumerable*) zakłada, że [`IEnumerable`](xref:System.Collections.IEnumerable) ładowany z jest bezpieczny wątkowo.

```csharp
// Create MLContext
MLContext mlContext = new MLContext();

//Load Data
IDataView data = mlContext.Data.LoadFromEnumerable<HousingData>(inMemoryCollection);
```

## <a name="next-steps"></a>Następne kroki

- Aby czyścić lub w inny sposób przetwarzać dane, zobacz [Przygotowywanie danych do kompilowania modelu](prepare-data-ml-net.md).
- Gdy wszystko jest gotowe do skompilowania modelu, zobacz temat [uczenie i ocenianie modelu](train-machine-learning-model-ml-net.md).
