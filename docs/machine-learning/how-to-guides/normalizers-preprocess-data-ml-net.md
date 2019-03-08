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
# <a name="preprocess-training-data-with-normalizers-to-use-in-data-processing---mlnet"></a>Przetwarzanie wstępne danych szkoleniowych z normalizers do użycia podczas przetwarzania danych — strukturze ML.NET

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Strukturze ML.NET udostępnia szereg [algorytmy parametryczne i parametrycznych](https://machinelearningmastery.com/parametric-and-nonparametric-machine-learning-algorithms/).

Ma ona **nie** jako ważne normalizer, które możesz wybrać, ponieważ jest **użyj** normalizer podczas szkolenia liniowy lub innych modeli parametrycznych.

Zawsze dołączaj normalizer bezpośrednio w strukturze ML.NET potok nauczania, więc go:

- jest tylko skonfigurowanych pod kątem na dane szkoleniowe, a nie na podstawie posiadanych danych testowych
- poprawnie jest stosowany do wszystkich nowych danych przychodzących, bez konieczności stosowania dodatkowych wstępne przetwarzanie w czasie prognozy.

Poniżej przedstawiono fragment kodu, który demonstruje normalizacji w potokach uczenia. Przyjęto założenie, zestawu danych Iris:

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
