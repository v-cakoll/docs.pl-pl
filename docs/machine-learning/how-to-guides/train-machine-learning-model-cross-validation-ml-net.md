---
title: Nauczanie i ocena model uczenia maszynowego przy użyciu krzyżowego sprawdzania poprawności
description: Dowiedz się, jak nauczanie i ocena model uczenia maszynowego przy użyciu krzyżowego sprawdzania poprawności
ms.date: 05/03/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: a06711ca83ea545adc7292cf6d8173f006fdb94d
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557834"
---
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="3dce9-103">Nauczanie i ocena model uczenia maszynowego przy użyciu krzyżowego sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="3dce9-103">Train and evaluate a machine learning model using cross validation</span></span>

<span data-ttu-id="3dce9-104">Dowiedz się, jak na potrzeby tworzenia bardziej niezawodnych modeli uczenia maszynowego w strukturze ML.NET krzyżowego sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="3dce9-104">Learn how to use cross validation to build more robust machine learning models in ML.NET.</span></span> 

<span data-ttu-id="3dce9-105">Krzyżowa Weryfikacja jest szkolenia i model oceny technika, która dzieli dane na wiele partycji, a następnie szkolenie modeli wielu algorytmów na te partycje.</span><span class="sxs-lookup"><span data-stu-id="3dce9-105">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="3dce9-106">Ta technika zwiększa niezawodność modelu, zawierający dane z procesu uczenia.</span><span class="sxs-lookup"><span data-stu-id="3dce9-106">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="3dce9-107">Oprócz poprawianie wydajności niewidzianych uwagi, w środowiskach ograniczonego danych może być skutecznym narzędziem do szkolenia modele z mniejszych zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="3dce9-107">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="3dce9-108">Dane oraz model danych</span><span class="sxs-lookup"><span data-stu-id="3dce9-108">The data and data model</span></span>

<span data-ttu-id="3dce9-109">Podane dane z pliku, ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="3dce9-109">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="3dce9-110">Dane mogą być modelowane przez klasę, takie jak `HousingData`:</span><span class="sxs-lookup"><span data-stu-id="3dce9-110">The data can be modeled by a class like `HousingData`:</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }
 
    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

<span data-ttu-id="3dce9-111">Załadowane dane w [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="3dce9-111">Load the data in into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="3dce9-112">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="3dce9-112">Prepare the data</span></span>

<span data-ttu-id="3dce9-113">Wstępne przetwarzanie danych przed ich użyciem do tworzenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="3dce9-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="3dce9-114">W tym przykładzie `Size` i `HistoricalPrices` kolumny są łączone w jednej funkcji wektor, który jest wyprowadzana do nową kolumnę o nazwie `Features` przy użyciu [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody.</span><span class="sxs-lookup"><span data-stu-id="3dce9-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="3dce9-115">Oprócz pobierania danych do formatu oczekiwanego przez algorytmy strukturze ML.NET, złączenie kolumn optymalizuje kolejne operacje w potoku, stosując wykonać jeden raz dla połączonych kolumny zamiast wszystkich oddzielne kolumny.</span><span class="sxs-lookup"><span data-stu-id="3dce9-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span> 

<span data-ttu-id="3dce9-116">Po kolumny są łączone w pojedynczy wektor [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest stosowany do `Features` kolumny, aby uzyskać `Size` i `HistoricalPrices` w tym samym zakresie 0 – 1.</span><span class="sxs-lookup"><span data-stu-id="3dce9-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span> 

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator = 
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="3dce9-117">Szkolenie modelu za pomocą krzyżowego sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="3dce9-117">Train model with cross validation</span></span>

<span data-ttu-id="3dce9-118">Gdy dane zostały wstępnie przetworzone, nadszedł czas na szkolenie modelu.</span><span class="sxs-lookup"><span data-stu-id="3dce9-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="3dce9-119">Najpierw należy wybrać algorytm, najlepiej pasującą za pomocą zadań do wykonania uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="3dce9-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="3dce9-120">Ponieważ numerycznie ciągłe wartość jest wartością prognozowaną, zadanie jest regresji.</span><span class="sxs-lookup"><span data-stu-id="3dce9-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="3dce9-121">Jeden z algorytmów regresji implementowany przez strukturze ML.NET jest [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorytmu.</span><span class="sxs-lookup"><span data-stu-id="3dce9-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="3dce9-122">Do nauczenia modelu przy użyciu krzyżowego sprawdzania poprawności [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody.</span><span class="sxs-lookup"><span data-stu-id="3dce9-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span> 

> [!NOTE]
> <span data-ttu-id="3dce9-123">Chociaż ten przykład używa modelu regresji liniowej, CrossValidate ma zastosowanie do wszystkich innych zadań w strukturze ML.NET, z wyjątkiem wykrywania anomalii uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="3dce9-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="3dce9-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) wykonuje następujące operacje:</span><span class="sxs-lookup"><span data-stu-id="3dce9-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="3dce9-125">Dzieli dane na liczbę partycji jest równa wartości określonej w `numberOfFolds` parametru.</span><span class="sxs-lookup"><span data-stu-id="3dce9-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="3dce9-126">Wynik każdej partycji jest [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiektu.</span><span class="sxs-lookup"><span data-stu-id="3dce9-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="3dce9-127">Model jest uczony w każdej partycji przy użyciu określonego komputera uczenie algorytmu narzędzie do szacowania zestawów danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="3dce9-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="3dce9-128">Każdy model wydajności jest obliczane przy użyciu [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody testowego zestawu danych.</span><span class="sxs-lookup"><span data-stu-id="3dce9-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span> 
1. <span data-ttu-id="3dce9-129">Model wraz z jego metryki są zwracane dla wszystkich modeli.</span><span class="sxs-lookup"><span data-stu-id="3dce9-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="3dce9-130">Wynik przechowywany w `cvResults` to zbiór [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektów.</span><span class="sxs-lookup"><span data-stu-id="3dce9-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="3dce9-131">Ten obiekt zawiera trenowanego modelu, a także metryk, które są zarówno dostępną formę [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) i [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) właściwości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="3dce9-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="3dce9-132">W tym przykładzie `Model` właściwość jest typu [ `ITransformer` ](xref:Microsoft.ML.ITransformer) i `Metrics` właściwość jest typu [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics).</span><span class="sxs-lookup"><span data-stu-id="3dce9-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span> 

## <a name="extract-metrics"></a><span data-ttu-id="3dce9-133">Wyodrębnij metryki</span><span class="sxs-lookup"><span data-stu-id="3dce9-133">Extract metrics</span></span>

<span data-ttu-id="3dce9-134">Metryki dla różnych modeli uczonego jest możliwy za pośrednictwem `Metrics` właściwości poszczególnych [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektu.</span><span class="sxs-lookup"><span data-stu-id="3dce9-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="3dce9-135">W tym przypadku [R-kwadrat metryki](https://en.wikipedia.org/wiki/Coefficient_of_determination) uzyskuje dostęp i przechowywane w zmiennej `rSquared`.</span><span class="sxs-lookup"><span data-stu-id="3dce9-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span> 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="3dce9-136">Jeśli możesz zbadać zawartość `rSquared` zmiennej, dane wyjściowe powinny być pięciu wartości z zakresu od 0 – 1, w przypadku, gdy bliżej 1 oznacza, że najlepiej.</span><span class="sxs-lookup"><span data-stu-id="3dce9-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span>

## <a name="select-the-best-performing-model"></a><span data-ttu-id="3dce9-137">Wybierz najlepiej działający model</span><span class="sxs-lookup"><span data-stu-id="3dce9-137">Select the best performing model</span></span>

<span data-ttu-id="3dce9-138">Metryki, takie jak R-kwadrat, wybierz opcję przy użyciu modeli z najlepiej najgorszy wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3dce9-138">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="3dce9-139">Następnie wybierz górny modelu do prognozowania lub wykonanie dodatkowych operacji za pomocą.</span><span class="sxs-lookup"><span data-stu-id="3dce9-139">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
