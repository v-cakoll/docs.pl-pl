---
title: Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET
description: Dowiedz się, jak do nauczenia modelu, używając krzyżowa Weryfikacja za pomocą platformy ML.NET mają większy poziom dokładności przewidywania modelu uczenia maszynowego
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 7191d8bdbb9375dff6ccc7acb0aacab3cbef56a2
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676541"
---
# <a name="train-a-machine-learning-model-using-cross-validation---mlnet"></a><span data-ttu-id="80263-103">Szkolenie modelu uczenia maszynowego, za pomocą krzyżowego sprawdzania poprawności - strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="80263-103">Train a machine learning model using cross-validation - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="80263-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="80263-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="80263-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="80263-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="80263-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="80263-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="80263-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="80263-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="80263-108">[Krzyżowa Weryfikacja](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) jest przydatną techniką, w przypadku aplikacji uczenia Maszynowego.</span><span class="sxs-lookup"><span data-stu-id="80263-108">[Cross-validation](https://en.wikipedia.org/wiki/Cross-validation_(statistics)) is a useful technique for ML applications.</span></span> <span data-ttu-id="80263-109">On pomaga oszacować wariancję jakość modelu z jeden przebieg do innego i również eliminuje potrzebę wyodrębnić oddzielne testów, zestawu do oceny.</span><span class="sxs-lookup"><span data-stu-id="80263-109">It helps estimate the variance of the model quality from one run to another and also eliminates the need to extract a separate test set for evaluation.</span></span>

<span data-ttu-id="80263-110">Strukturze ML.NET automatycznie stosuje cechowania poprawnie (tak długo, jak wszystkie przetwarzania wstępnego znajduje się w potoku jednym uczenia), a następnie użyć koncepcji "stratyfikacji column", aby upewnić się, nie rozdzielania powiązane przykłady.</span><span class="sxs-lookup"><span data-stu-id="80263-110">ML.NET automatically applies featurization correctly (as long as all of the preprocessing resides in one learning pipeline) then use the 'stratification column' concept to make sure that related examples don't get separated.</span></span>

<span data-ttu-id="80263-111">Poniżej przedstawiono przykład szkolenia dla zestawu danych Iris przy użyciu losowego 90/10 train-test podziału i 5-fold krzyżowego sprawdzania poprawności:</span><span class="sxs-lookup"><span data-stu-id="80263-111">Here's a training example on an Iris dataset using randomized 90/10 train-test split, and a 5-fold cross-validation:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// First, we define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(
    columns: new TextLoader.Column[]
    {
        // The four features of the Iris dataset will be grouped together as one Features column.
        new TextLoader.Column("SepalLength",DataKind.R4,0),
        new TextLoader.Column("SepalWidth",DataKind.R4,1),
        new TextLoader.Column("PetalLength",DataKind.R4,2),
        new TextLoader.Column("PetalWidth",DataKind.R4,3),
        // Label: kind of iris.
        new TextLoader.Column("Label",DataKind.TX,4)
    },
    // Default separator is tab, but the dataset has semicolon.
    separatorChar: ',',
    // First line of the file is a header, not a data row.
    hasHeader: true
);


// Read the data.
var data = reader.Read(dataPath);

// Build the training pipeline.
var dynamicPipeline =
    // Concatenate all the features together into one column 'Features'.
    mlContext.Transforms.Concatenate("Features", "SepalLength", "SepalWidth", "PetalLength", "PetalWidth")
    // Note that the label is text, so it needs to be converted to key.
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Label"), TransformerScope.TrainTest)
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
