---
title: Zastosuj technicznego opracowywania funkcji do trenowania modelu dla danych podzielonych na kategorie — strukturze ML.NET
description: Dowiedz się, jak zastosować technicznego opracowywania funkcji Machine learning szkolenie modelu dla danych podzielonych na kategorie za pomocą platformy ML.NET
ms.date: 02/06/2018
ms.custom: mvc,how-to
ms.openlocfilehash: c24840ee89917d270bcbacbcf36905b4ee82a4aa
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092088"
---
# <a name="apply-feature-engineering-for-model-training-on-categorical-data---mlnet"></a><span data-ttu-id="0246b-103">Zastosuj technicznego opracowywania funkcji do trenowania modelu dla danych podzielonych na kategorie — strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="0246b-103">Apply feature engineering for model training on categorical data - ML.NET</span></span>

<span data-ttu-id="0246b-104">Należy przekonwertować żadnych danych innych niż float do `float` typy danych, ponieważ wszystkie strukturze ML.NET `learners` oczekiwane funkcje jak `float vector`.</span><span class="sxs-lookup"><span data-stu-id="0246b-104">You need to convert any non float data to `float` data types since all ML.NET `learners` expect features as a `float vector`.</span></span>

<span data-ttu-id="0246b-105">Jeśli zestaw danych zawiera `categorical` dane (na przykład "enum"), strukturze ML.NET oferuje kilka sposobów podczas konwertowania go do funkcji:</span><span class="sxs-lookup"><span data-stu-id="0246b-105">If the dataset contains `categorical` data (for example, 'enum'), ML.NET offers several ways of converting it to features:</span></span>

- <span data-ttu-id="0246b-106">Jeden gorącego magazynu lokalnie kodowania</span><span class="sxs-lookup"><span data-stu-id="0246b-106">One-hot encoding</span></span>
- <span data-ttu-id="0246b-107">Bazujących na skrótach hot jeden kodowania</span><span class="sxs-lookup"><span data-stu-id="0246b-107">Hash-based one-hot encoding</span></span>
- <span data-ttu-id="0246b-108">Kodowanie binarne (indeks kategorii konwersji do nieco sekwencji i używania usługi bits jako funkcje)</span><span class="sxs-lookup"><span data-stu-id="0246b-108">Binary encoding (convert category index into a bit sequence and use bits as features)</span></span>

<span data-ttu-id="0246b-109">Element `one-hot encoding` może być niepotrzebne, jeśli niektóre kategorie są bardzo wysokiej kardynalności (wiele różnych wartości z małą ustawione najczęściej występujących.</span><span class="sxs-lookup"><span data-stu-id="0246b-109">A `one-hot encoding` can be wasteful if some categories are very high-cardinality (lots of different values, with a small set commonly occurring.</span></span> <span data-ttu-id="0246b-110">W takim przypadku Zmniejsz liczbę miejsc do kodowania za pomocą na podstawie liczby funkcji wyboru cech.</span><span class="sxs-lookup"><span data-stu-id="0246b-110">In that case, reduce the number of slots to encode with count-based feature selection.</span></span>

<span data-ttu-id="0246b-111">Uwzględnij podzielonych na kategorie cechowania bezpośrednio w potok nauczania strukturze ML.NET, aby upewnić się, że przekształcenie podzielonych na kategorie:</span><span class="sxs-lookup"><span data-stu-id="0246b-111">Include categorical featurization directly in the ML.NET learning pipeline to ensure that the categorical transformation:</span></span>

- <span data-ttu-id="0246b-112">jest tylko "uczony" na dane szkoleniowe, a nie na podstawie posiadanych danych testowych</span><span class="sxs-lookup"><span data-stu-id="0246b-112">is only 'trained' on the training data, and not on your test data,</span></span>
- <span data-ttu-id="0246b-113">poprawnie są stosowane do nowych danych przychodzących, bez dodatkowych wstępne przetwarzanie w czasie prognozy.</span><span class="sxs-lookup"><span data-stu-id="0246b-113">is correctly applied to new incoming data, without extra pre-processing at prediction time.</span></span>

<span data-ttu-id="0246b-114">W poniższym przykładzie pokazano podzielonych na kategorie obsługę [zestawu danych spisu treści dla dorosłych](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span><span class="sxs-lookup"><span data-stu-id="0246b-114">The following example illustrates categorical handling for the [adult census dataset](https://github.com/dotnet/machinelearning/blob/master/test/data/adult.tiny.with-schema.txt):</span></span>

```console
Label   Workclass   education   marital-status  occupation  relationship    ethnicity   sex native-country-region   age fnlwgt  education-num   capital-gain    capital-loss    hours-per-week
0   Private 11th    Never-married   Machine-op-inspct   Own-child   Black   Male    United-States   25  226802  7   0   0   40
0   Private HS-grad Married-civ-spouse  Farming-fishing Husband White   Male    United-States   38  89814   9   0   0   50
1   Local-gov   Assoc-acdm  Married-civ-spouse  Protective-serv Husband White   Male    United-States   28  336951  12  0   0   40
1   Private Some-college    Married-civ-spouse  Machine-op-inspct   Husband Black   Male    United-States   44  160323  10  7688    0   40
```

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging, 
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Define the reader: specify the data columns and where to find them in the text file.
var reader = mlContext.Data.CreateTextLoader(new[] 
    {
        new TextLoader.Column("Label", DataKind.BL, 0),
        // We will load all the categorical features into one vector column of size 8.
        new TextLoader.Column("CategoricalFeatures", DataKind.TX, 1, 8),
        // Similarly, load all numerical features into one vector of size 6.
        new TextLoader.Column("NumericalFeatures", DataKind.R4, 9, 14),
        // Let's also separately load the 'Workclass' column.
        new TextLoader.Column("Workclass", DataKind.TX, 1),
    },
    hasHeader: true
);

// Read the data.
var data = reader.Read(dataPath);

// Inspect the first 10 records of the categorical columns to check that they are correctly read.
var catColumns = data.GetColumn<string[]>(mlContext, "CategoricalFeatures").Take(10).ToArray();

// Build several alternative featurization pipelines.
var pipeline =
    // Convert each categorical feature into one-hot encoding independently.
    mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalOneHot")
        // Convert all categorical features into indices, and build a 'word bag' of these.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("CategoricalFeatures", "CategoricalBag",OneHotEncodingTransformer.OutputKind.Bag))
        // One-hot encode the workclass column, then drop all the categories that have fewer than 10 instances in the train set.
        .Append(mlContext.Transforms.Categorical.OneHotEncoding("Workclass", "WorkclassOneHot"))
        .Append(mlContext.Transforms.FeatureSelection.SelectFeaturesBasedOnCount("WorkclassOneHot", "WorkclassOneHotTrimmed", count: 10));

// Let's train our pipeline, and then apply it to the same data.
var transformedData = pipeline.Fit(data).Transform(data);

// Inspect some columns of the resulting dataset.
var categoricalBags = transformedData.GetColumn<float[]>(mlContext, "CategoricalBag").Take(10).ToArray();
var workclasses = transformedData.GetColumn<float[]>(mlContext, "WorkclassOneHotTrimmed").Take(10).ToArray();

// Of course, if we want to train the model, we will need to compose a single float vector of all the features.
// Here's how we could do this:

var fullLearningPipeline = pipeline
    // Concatenate two of the 3 categorical pipelines, and the numeric features.
    .Append(mlContext.Transforms.Concatenate("Features", "NumericalFeatures", "CategoricalBag", "WorkclassOneHotTrimmed"))
    // Cache data in memory so that the following trainer will be able to access training examples without
    // reading them from disk multiple times.
    .AppendCacheCheckpoint(mlContext)
    // Now we're ready to train. We chose our FastTree trainer for this classification task.
    .Append(mlContext.BinaryClassification.Trainers.FastTree(numTrees: 50));

// Train the model.
var model = fullLearningPipeline.Fit(data);
```
