---
title: Przetwarzanie wstępne danych szkoleniowych z normalizers do użycia podczas przetwarzania danych — strukturze ML.NET
description: Dowiedz się, jak używać normalizers można wstępnie przetworzyć dane szkoleniowe do użycia w modelu uczenia maszynowego, kompilowania, szkolenia i oceniania za pomocą platformy ML.NET
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 4311307f5410a96bb4a30fcedd88bc43afd25c12
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738581"
---
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a><span data-ttu-id="d207b-103">Przetwarzanie wstępne danych szkoleniowych z normalizers do użycia podczas przetwarzania danych — strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="d207b-103">Preprocess training data with normalizers to use in data processing - ML.NET</span></span>

<span data-ttu-id="d207b-104">Strukturze ML.NET udostępnia szereg [algorytmy parametryczne i parametrycznych](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span><span class="sxs-lookup"><span data-stu-id="d207b-104">ML.NET exposes a number of [parametric and non-parametric algorithms](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).</span></span>

<span data-ttu-id="d207b-105">Ma ona **nie** jako ważne normalizer, które możesz wybrać, ponieważ jest **użyj** normalizer podczas szkolenia liniowy lub innych modeli parametrycznych.</span><span class="sxs-lookup"><span data-stu-id="d207b-105">It's **not** as important which normalizer you choose as it is to **use** a normalizer when training linear or other parametric models.</span></span>

<span data-ttu-id="d207b-106">Zawsze dołączaj normalizer bezpośrednio w strukturze ML.NET potok nauczania, więc go:</span><span class="sxs-lookup"><span data-stu-id="d207b-106">Always include the normalizer directly in the ML.NET learning pipeline, so it:</span></span>

- <span data-ttu-id="d207b-107">jest tylko skonfigurowanych pod kątem na dane szkoleniowe, a nie na podstawie posiadanych danych testowych</span><span class="sxs-lookup"><span data-stu-id="d207b-107">is only trained on the training data, and not on your test data,</span></span>
- <span data-ttu-id="d207b-108">poprawnie jest stosowany do wszystkich nowych danych przychodzących, bez konieczności stosowania dodatkowych wstępne przetwarzanie w czasie prognozy.</span><span class="sxs-lookup"><span data-stu-id="d207b-108">is correctly applied to all the new incoming data, without the need for extra pre-processing at prediction time.</span></span>

<span data-ttu-id="d207b-109">Poniżej przedstawiono fragment kodu, który demonstruje normalizacji w potokach uczenia.</span><span class="sxs-lookup"><span data-stu-id="d207b-109">Here's a snippet of code that demonstrates normalization in learning pipelines.</span></span> <span data-ttu-id="d207b-110">Przyjęto założenie, zestawu danych Iris:</span><span class="sxs-lookup"><span data-stu-id="d207b-110">It assumes the Iris dataset:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextReader(
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
        new NormalizingEstimator.MinMaxColumn("Features", "MinMaxNormalized", fixZero: true),
        new NormalizingEstimator.MeanVarColumn("Features", "MeanVarNormalized", fixZero: true),
        new NormalizingEstimator.BinningColumn("Features", "BinNormalized", numBins: 256));

// Let's train our pipeline of normalizers, and then apply it to the same data.
var normalizedData = pipeline.Fit(trainData).Transform(trainData);

// Inspect one column of the resulting dataset.
var meanVarValues = normalizedData.GetColumn<float[]>(mlContext, "MeanVarNormalized").ToArray();
```
