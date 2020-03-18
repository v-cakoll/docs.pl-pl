---
title: Szkolenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej
description: Dowiedz się, jak używać sprawdzania poprawności krzyżowej do tworzenia bardziej niezawodnych modeli uczenia maszynowego w ML.NET. Krzyżowa weryfikacja jest techniką oceny szkolenia i modelu, która dzieli dane na kilka partycji i szkoli wiele algorytmów na tych partycjach.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976929"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="6bb6f-104">Szkolenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej</span><span class="sxs-lookup"><span data-stu-id="6bb6f-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="6bb6f-105">Dowiedz się, jak używać sprawdzania poprawności krzyżowej do uczenia bardziej niezawodnych modeli uczenia maszynowego w ML.NET.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span>

<span data-ttu-id="6bb6f-106">Krzyżowa weryfikacja jest techniką oceny szkolenia i modelu, która dzieli dane na kilka partycji i szkoli wiele algorytmów na tych partycjach.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="6bb6f-107">Technika ta poprawia niezawodność modelu, przechowując dane z procesu szkolenia.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="6bb6f-108">Oprócz poprawy wydajności w niewidocznych obserwacjach, w środowiskach ograniczonych danymi może być skutecznym narzędziem do szkolenia modeli z mniejszym zestawem danych.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="6bb6f-109">Model danych i danych</span><span class="sxs-lookup"><span data-stu-id="6bb6f-109">The data and data model</span></span>

<span data-ttu-id="6bb6f-110">Dane z pliku, który ma następujący format:</span><span class="sxs-lookup"><span data-stu-id="6bb6f-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="6bb6f-111">Dane mogą być modelowane przez `HousingData` klasę, [`IDataView`](xref:Microsoft.ML.IDataView)jak i załadowany do .</span><span class="sxs-lookup"><span data-stu-id="6bb6f-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="prepare-the-data"></a><span data-ttu-id="6bb6f-112">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="6bb6f-112">Prepare the data</span></span>

<span data-ttu-id="6bb6f-113">Wstępnie przetwórz dane przed użyciem go do utworzenia modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="6bb6f-114">W tym przykładzie `Size` `HistoricalPrices` kolumny i kolumny są łączone w wektor pojedynczej operacji, który jest wyprowadzany do nowej kolumny o nazwie `Features` przy użyciu [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="6bb6f-115">Oprócz uzyskania danych do formatu oczekiwanego przez algorytmy ML.NET, połączając kolumny optymalizuje kolejne operacje w potoku, stosując operację raz dla kolumny skonkretyzowanej zamiast każdej z oddzielnych kolumn.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span>

<span data-ttu-id="6bb6f-116">Po połączeniu kolumn w jeden [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) wektor, `Features` jest stosowany `Size` `HistoricalPrices` do kolumny, aby uzyskać i w tym samym zakresie między 0-1.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span>

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

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="6bb6f-117">Model pociągu z walidacją krzyża</span><span class="sxs-lookup"><span data-stu-id="6bb6f-117">Train model with cross validation</span></span>

<span data-ttu-id="6bb6f-118">Po przetworzeniu danych nadszedł czas, aby nabyć model.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="6bb6f-119">Najpierw wybierz algorytm, który najbardziej ściśle wyrównuje się z zadaniem uczenia maszynowego do wykonania.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="6bb6f-120">Ponieważ przewidywana wartość jest wartością liczbowo ciągłą, zadaniem jest regresja.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="6bb6f-121">Jednym z algorytmów regresji zaimplementowanych [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) przez ML.NET jest algorytm.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="6bb6f-122">Aby nabyć model z krzyżowego sprawdzania poprawności należy użyć [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span>

> [!NOTE]
> <span data-ttu-id="6bb6f-123">Mimo że w tym przykładzie używa modelu regresji liniowej, CrossValidate ma zastosowanie do wszystkich innych zadań uczenia maszynowego w ML.NET z wyjątkiem wykrywania anomalii.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="6bb6f-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6bb6f-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="6bb6f-125">Dzieli dane na liczbę partycji równą wartości określonej `numberOfFolds` w parametrze.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="6bb6f-126">Wynikiem każdej partycji [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="6bb6f-127">Model jest uznawiany na każdej partycji przy użyciu określonego estymatora algorytmu uczenia maszynowego w zestawie danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="6bb6f-128">Wydajność każdego modelu jest oceniana [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) przy użyciu metody na zestawie danych testowych.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span>
1. <span data-ttu-id="6bb6f-129">Model wraz z jego metryki są zwracane dla każdego z modeli.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="6bb6f-130">Wynik przechowywany `cvResults` w jest [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekcją obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="6bb6f-131">Ten obiekt zawiera uczonego modelu, jak również [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) metryki, które są dostępne formie i [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) właściwości odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="6bb6f-132">W tym przykładzie `Model` właściwość jest [`ITransformer`](xref:Microsoft.ML.ITransformer) typu, a `Metrics` [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)właściwość jest typu .</span><span class="sxs-lookup"><span data-stu-id="6bb6f-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="6bb6f-133">Ocena modelu</span><span class="sxs-lookup"><span data-stu-id="6bb6f-133">Evaluate the model</span></span>

<span data-ttu-id="6bb6f-134">Metryki dla różnych modeli przeszkolonych są dostępne za pośrednictwem `Metrics` właściwości poszczególnych [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="6bb6f-135">W takim przypadku [metryka R-Kwadrat](https://en.wikipedia.org/wiki/Coefficient_of_determination) jest dostępna i `rSquared`przechowywana w zmiennej .</span><span class="sxs-lookup"><span data-stu-id="6bb6f-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span>

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="6bb6f-136">W przypadku sprawdzenia zawartości `rSquared` zmiennej, dane wyjściowe powinny być pięć wartości od 0-1, gdzie bliżej 1 oznacza najlepsze.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="6bb6f-137">Korzystając z metryk, takich jak R-Squared, wybierz modele od najlepszego do najgorszego.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="6bb6f-138">Następnie wybierz top model do prognozowania lub wykonać dodatkowe operacje z.</span><span class="sxs-lookup"><span data-stu-id="6bb6f-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

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
