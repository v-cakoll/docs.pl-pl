---
title: Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET
description: Dowiedz się, jak do nauczenia modelu, używając krzyżowa Weryfikacja za pomocą platformy ML.NET mają większy poziom dokładności przewidywania modelu uczenia maszynowego
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 41b99415d736b6583a8d43434c031e677e6f3ac8
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297678"
---
# <a name="train-a-machine-learning-model-using-cross-validation---mlnet"></a><span data-ttu-id="f52bc-103">Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="f52bc-103">Train a machine learning model using cross-validation - ML.NET</span></span>

<span data-ttu-id="f52bc-104">[Krzyżowa Weryfikacja](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) jest przydatną techniką, w przypadku aplikacji uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="f52bc-104">[Cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) is a useful technique for ML applications.</span></span> <span data-ttu-id="f52bc-105">On pomaga oszacować wariancję jakość modelu z jeden przebieg do innego i również eliminuje potrzebę wyodrębnić oddzielne testów, zestawu do oceny.</span><span class="sxs-lookup"><span data-stu-id="f52bc-105">It helps estimate the variance of the model quality from one run to another and also eliminates the need to extract a separate test set for evaluation.</span></span>

<span data-ttu-id="f52bc-106">Strukturze ML.NET automatycznie stosuje cechowania poprawnie (tak długo, jak wszystkie przetwarzania wstępnego znajduje się w potoku jednym uczenia), a następnie użyć koncepcji "stratyfikacji column", aby upewnić się, nie rozdzielania powiązane przykłady.</span><span class="sxs-lookup"><span data-stu-id="f52bc-106">ML.NET automatically applies featurization correctly (as long as all of the preprocessing resides in one learning pipeline) then use the 'stratification column' concept to make sure that related examples don't get separated.</span></span>

<span data-ttu-id="f52bc-107">Poniżej przedstawiono przykład szkolenia dla zestawu danych Iris przy użyciu losowego 90/10 train-test podziału i 5-fold krzyżowego sprawdzania poprawności:</span><span class="sxs-lookup"><span data-stu-id="f52bc-107">Here's a training example on an Iris dataset using randomized 90/10 train-test split, and a 5-fold cross-validation:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.TextReader(new TextLoader.Arguments
{
    Column = new[] {
        // We read the first 11 values as a single float vector.
        new TextLoader.Column("SepalLength", DataKind.R4, 0),
        new TextLoader.Column("SepalWidth", DataKind.R4, 1),
        new TextLoader.Column("PetalLength", DataKind.R4, 2),
        new TextLoader.Column("PetalWidth", DataKind.R4, 3),
        // Label: kind of iris.
        new TextLoader.Column("Label", DataKind.TX, 4),
    },
    Separator = ","
});

// Read the data.
var data = reader.Read(dataPath);

// Build the training pipeline.
var dynamicPipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Categorical.MapValueToKey("Label"), TransformerScope.TrainTest)
    // Use the multi-class SDCA model to predict the label using features.
    .Append(mlContext.MulticlassClassification.Trainers.StochasticDualCoordinateAscent());

// Split the data 90:10 into train and test sets, train and evaluate.
var (trainData, testData) = mlContext.MulticlassClassification.TrainTestSplit(data, testFraction: 0.1);

// Train the model.
var model = dynamicPipeline.Fit(trainData);
// Compute quality metrics on the test set.
var metrics = mlContext.MulticlassClassification.Evaluate(model.Transform(testData));
Console.WriteLine(metrics.AccuracyMicro);

// Now run the 5-fold cross-validation experiment, using the same pipeline.
var cvResults = mlContext.MulticlassClassification.CrossValidate(data, dynamicPipeline, numFolds: 5);

// The results object is an array of 5 elements. For each of the 5 folds, we have metrics, model and scored test data.
// Let's compute the average micro-accuracy.
var microAccuracies = cvResults.Select(r => r.metrics.AccuracyMicro);
Console.WriteLine(microAccuracies.Average());
```
