---
title: Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET
description: Dowiedz się, jak do nauczenia modelu, używając krzyżowa Weryfikacja za pomocą platformy ML.NET mają większy poziom dokładności przewidywania modelu uczenia maszynowego
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 41b99415d736b6583a8d43434c031e677e6f3ac8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145965"
---
# <a name="train-a-machine-learning-model-using-cross-validation---mlnet"></a>Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET

[Krzyżowa Weryfikacja](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) jest przydatną techniką, w przypadku aplikacji uczenia Maszynowego. On pomaga oszacować wariancję jakość modelu z jeden przebieg do innego i również eliminuje potrzebę wyodrębnić oddzielne testów, zestawu do oceny.

Strukturze ML.NET automatycznie stosuje cechowania poprawnie (tak długo, jak wszystkie przetwarzania wstępnego znajduje się w potoku jednym uczenia), a następnie użyć koncepcji "stratyfikacji column", aby upewnić się, nie rozdzielania powiązane przykłady.

Poniżej przedstawiono przykład szkolenia dla zestawu danych Iris przy użyciu losowego 90/10 train-test podziału i 5-fold krzyżowego sprawdzania poprawności:

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
