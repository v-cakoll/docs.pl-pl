---
title: Przetwarzanie wstępne danych szkoleniowych z normalizers do użycia podczas przetwarzania danych — strukturze ML.NET
description: Dowiedz się, jak używać normalizers można wstępnie przetworzyć dane szkoleniowe do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 2d18f7c19a51fd929ac6efb7f600cb1ac2733de8
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676606"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="50338-103">Przetwarzanie wstępne danych szkoleniowych z normalizers do użycia podczas przetwarzania danych — strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="50338-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="50338-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="50338-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="50338-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="50338-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="50338-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="50338-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="50338-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="50338-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="50338-108">Strukturze ML.NET udostępnia szereg [algorytmy parametryczne i parametrycznych](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span><span class="sxs-lookup"><span data-stu-id="50338-108">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="50338-109">Ma ona **nie** jako ważne normalizer, które możesz wybrać, ponieważ jest **użyj** normalizer podczas szkolenia liniowy lub innych modeli parametrycznych.</span><span class="sxs-lookup"><span data-stu-id="50338-109">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="50338-110">Zawsze dołączaj normalizer bezpośrednio w strukturze ML.NET potok nauczania, więc go:</span><span class="sxs-lookup"><span data-stu-id="50338-110">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="50338-111">jest tylko skonfigurowanych pod kątem na dane szkoleniowe, a nie na podstawie posiadanych danych testowych</span><span class="sxs-lookup"><span data-stu-id="50338-111">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="50338-112">poprawnie jest stosowany do wszystkich nowych danych przychodzących, bez konieczności stosowania dodatkowych wstępne przetwarzanie w czasie prognozy.</span><span class="sxs-lookup"><span data-stu-id="50338-112">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="50338-113">Poniżej przedstawiono fragment kodu, który demonstruje normalizacji w potokach uczenia.</span><span class="sxs-lookup"><span data-stu-id="50338-113">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="50338-114">Przyjęto założenie, zestawu danych Iris:</span><span class="sxs-lookup"><span data-stu-id="50338-114">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("Features",DataKind.R4,0,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has comma.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);

// Read the training data.
var trainData = reader.Read(dataPath);

// Apply all kinds of standard ML.NET normalization to the raw features.
var pipeline =
    mlContext.Transforms.Normalize(
            new NormalizingEstimator.MinMaxColumn(inputColumnName:"Features", outputColumnName:"MinMaxNormalized", fixZero: true),
            new NormalizingEstimator.MeanVarColumn(inputColumnName: "Features", outputColumnName: "MeanVarNormalized", fixZero: true),
            new NormalizingEstimator.BinningColumn(inputColumnName: "Features", outputColumnName: "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
