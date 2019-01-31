---
title: Ładowanie danych z wieloma kolumnami z pliku CSV, machine learning przetwarzania - strukturze ML.NET
description: Dowiedz się, jak można załadować danych z wieloma kolumnami z pliku CSV do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 01/29/2019
ms.custom: mvc,how-to
ms.openlocfilehash: a06d7edfb4746a39377116b15903b68f8723cb02
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479714"
---
# <a name="load-data-with-many-columns-from-a-csv-file-for-machine-learning-processing---mlnet"></a><span data-ttu-id="6e285-103">Ładowanie danych z wieloma kolumnami z pliku CSV, machine learning przetwarzania - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="6e285-103">Load data with many columns from a CSV file for machine learning processing - ML.NET</span></span>

<span data-ttu-id="6e285-104">`TextLoader` Służy do ładowania danych z plików tekstowych.</span><span class="sxs-lookup"><span data-stu-id="6e285-104">`TextLoader` is used to load data from text files.</span></span> <span data-ttu-id="6e285-105">Należy określić kolumny danych, ich typy i ich lokalizacji w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="6e285-105">You need to specify the data columns, their types, and their location in the text file.</span></span>

<span data-ttu-id="6e285-106">Jeśli plik wejściowy zawiera wiele kolumn, tego samego typu i zawsze używane razem, przeczytaj je jako *kolumny wektor*.</span><span class="sxs-lookup"><span data-stu-id="6e285-106">When the input file contains many columns of the same type and always used together, read them as a *vector column*.</span></span> <span data-ttu-id="6e285-107">Ta strategia wyniki w schemacie Wyczyść dane i eliminuje koszty wydajności niepotrzebne, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6e285-107">This strategy results in a clean data schema and avoids unnecessary performance costs, as shown in the following example:</span></span>

<span data-ttu-id="6e285-108">[Przykładowy plik](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span><span class="sxs-lookup"><span data-stu-id="6e285-108">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/generated_regression_dataset.csv):</span></span>

```console
-2.75;0.77;-0.61;0.14;1.39;0.38;-0.53;-0.50;-2.13;-0.39;0.46;140.66
-0.61;-0.37;-0.12;0.55;-1.00;0.84;-0.02;1.30;-0.24;-0.50;-2.12;148.12
-0.85;-0.91;1.81;0.02;-0.78;-1.41;-1.09;-0.65;0.90;-0.37;-0.22;402.20
0.28;1.05;-0.24;0.30;-0.99;0.19;0.32;-0.95;-1.19;-0.63;0.75;443.51
```

<span data-ttu-id="6e285-109">Odczytywanie tego pliku przy użyciu `TextLoader`:</span><span class="sxs-lookup"><span data-stu-id="6e285-109">Reading this file using `TextLoader`:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
    columns: new TextLoader.Column[]
    {
    // We read the first 10 values as a single float vector.
        new TextLoader.Column("FeatureVector",DataKind.R4,0,9),
        // Separately, read the target variable.
        new TextLoader.Column("Target",DataKind.R4,10)
    },
    // Default separator is tab, but we need a semicolon.
    separatorChar: ';',
    hasHeader: true
);

// Now read the file (remember though, readers are lazy, so the actual reading will happen when the data is accessed).
var data = reader.Read(dataPath);
```    