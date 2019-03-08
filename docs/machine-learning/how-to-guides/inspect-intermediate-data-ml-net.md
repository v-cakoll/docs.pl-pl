---
title: Sprawdź wartości danych pośrednich podczas przetwarzania potokowego w strukturze ML.NET
description: Dowiedz się, jak przeprowadzać inspekcję wartości rzeczywiste dane pośrednie podczas strukturze ML.NET usługi machine learning przetwarzania potokowego w programie
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 3d20f153be7b502fb5a542a942245546412efde2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57678647"
---
# <a name="inspect-intermediate-data-values-during-mlnet-pipeline-processing"></a><span data-ttu-id="39fc5-103">Sprawdź wartości danych pośrednich podczas przetwarzania potokowego w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="39fc5-103">Inspect intermediate data values during ML.NET pipeline processing</span></span>

> [!NOTE]
> <span data-ttu-id="39fc5-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="39fc5-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="39fc5-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="39fc5-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="39fc5-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="39fc5-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="39fc5-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="39fc5-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="39fc5-108">Podczas eksperymentu można obserwować i Zweryfikuj wyniki przetwarzania danych w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="39fc5-108">During the experiment, you may want to observe and validate the data processing results at a given point.</span></span> <span data-ttu-id="39fc5-109">To nie jest proste, ponieważ operacje strukturze ML.NET są powolne, konstruowanie obiektów, które są zapowiedzi i danych.</span><span class="sxs-lookup"><span data-stu-id="39fc5-109">This isn't easy since ML.NET operations are lazy, constructing objects that are 'promises' of data.</span></span>

<span data-ttu-id="39fc5-110">`GetColumn<T>` — Metoda rozszerzenia umożliwia sprawdzanie danych pośrednich.</span><span class="sxs-lookup"><span data-stu-id="39fc5-110">The `GetColumn<T>` extension method lets you inspect the intermediate data.</span></span> <span data-ttu-id="39fc5-111">Zwraca zawartość jedna kolumna danych jako `IEnumerable`.</span><span class="sxs-lookup"><span data-stu-id="39fc5-111">It returns the contents of one data column as an `IEnumerable`.</span></span>

<span data-ttu-id="39fc5-112">Poniższy przykład pokazuje, jak używać `GetColumn<T>` — metoda rozszerzenia:</span><span class="sxs-lookup"><span data-stu-id="39fc5-112">The following example shows how to use the `GetColumn<T>` extension method:</span></span>

<span data-ttu-id="39fc5-113">[Przykładowy plik](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="39fc5-113">[Example file](https://github.com/dotnet/machinelearning/tree/master/test/data/adult.tiny.with-schema.txt):</span></span>
```
Label   Workclass   education   marital-status
0   Private 11th    Never-married
0   Private HS-grad Married-civ-spouse
1   Local-gov   Assoc-acdm  Married-civ-spouse
1   Private Some-college    Married-civ-spouse

```

<span data-ttu-id="39fc5-114">Nasze klasa jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="39fc5-114">Our class is defined as follows:</span></span>

```csharp
public class InspectedRow
{
    [LoadColumn(0)]
    public bool IsOver50K { get; set; }
    [LoadColumn(1)]
    public string WorkClass { get; set; }
    [LoadColumn(2)]
    public string Education { get; set; }
    [LoadColumn(3)]
    public string MaritalStatus { get; set; }
}
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Read the data into a data view.
var data = mlContext.Data.ReadFromTextFile<InspectedRow>(dataPath, hasHeader: true);

// Start creating our processing pipeline. For now, let's just concatenate all the text columns
// together into one.
var pipeline = mlContext.Transforms.Concatenate("AllFeatures", "WorkClass", "Education", "MaritalStatus");

// Fit our data pipeline and transform data with it.
var transformedData = pipeline.Fit(data).Transform(data);

// Extract the 'AllFeatures' column.
// This will give the entire dataset: make sure to only take several row
// in case the dataset is huge. The is similar to the static API, except
// you have to specify the column name and type.
var featureColumns =
    transformedData
        .GetColumn<string[]>(mlContext, "AllFeatures")
        .Take(20)
        .ToArray();
```
