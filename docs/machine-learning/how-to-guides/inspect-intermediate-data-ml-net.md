---
title: Sprawdź wartości danych pośrednich podczas przetwarzania potokowego w strukturze ML.NET
description: Dowiedz się, jak przeprowadzać inspekcję wartości rzeczywiste dane pośrednie podczas strukturze ML.NET usługi machine learning przetwarzania potokowego w programie
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: cd229c120f7599c9a304a84a1669947e613fc917
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671937"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="6752e-103">Sprawdź wartości danych pośrednich podczas przetwarzania potokowego w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="6752e-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

<span data-ttu-id="6752e-104">Podczas eksperymentu można obserwować i Zweryfikuj wyniki przetwarzania danych w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="6752e-104">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="6752e-105">To nie jest proste, ponieważ operacje strukturze ML.NET są powolne, konstruowanie obiektów, które są zapowiedzi i danych.</span><span class="sxs-lookup"><span data-stu-id="6752e-105">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="6752e-106">`GetColumn<T>` — Metoda rozszerzenia umożliwia sprawdzanie danych pośrednich.</span><span class="sxs-lookup"><span data-stu-id="6752e-106">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="6752e-107">Zwraca zawartość jedna kolumna danych jako `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="6752e-107">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="6752e-108">Poniższy przykład pokazuje, jak używać `GetColumn<T>` — metoda rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="6752e-108">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="6752e-109">[Przykładowy plik](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="6752e-109">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

<span data-ttu-id="6752e-110">Nasze klasa jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6752e-110">Our class is defined as follows:</span></span>

```csharp
private class InspectedRow
{
    public bool IsOver50K;
    public string Workclass;
    public string Education;
    public string MaritalStatus;
    public string[] AllFeatures;
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Create the reader: define the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // A boolean column depicting the 'label'.
        new TextLoader.Column("IsOver50K", DataKind.BL, 0),
        // Three text columns.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
        new TextLoader.Column("Education", DataKind.TX, 2),
        new TextLoader.Column("MaritalStatus", DataKind.TX, 3)
    },
    // First line of the file is a header, not a data row.
    HasHeader = true
});

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "Education", "MaritalStatus");

// Let's verify that the data has been read correctly. 
// First, we read the data file.
var data = reader.Read(dataPath);

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// 'transformedData' is a 'promise' of data. Let's actually read it.
var someRows = transformedData
    // Convert to an enumerable of user-defined type. 
    .AsEnumerable<InspectedRow>(mlContext, reuseRowObject: false)
    // Take a couple values as an array.
    .Take(4).ToArray();

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns = transformedData.GetColumn<string[]>(mlContext, "AllFeatures")
    .Take(20).ToArray();
```