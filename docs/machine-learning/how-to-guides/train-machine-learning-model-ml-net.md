---
title: Trenowanie i ocenianie modelu
description: Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Model uczenia maszynowego identyfikuje wzorce w danych szkoleniowych, aby prognozowania przy użyciu nowych danych.
ms.date: 03/31/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 51499f2c0ece615a99740bd9b27f99d4b5ed1d01
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523858"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="4d9f0-104">Trenowanie i ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="4d9f0-104">Train and evaluate a model</span></span>

<span data-ttu-id="4d9f0-105">Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="4d9f0-106">Mimo że w tym przykładzie trenuje model regresji, pojęcia mają zastosowanie w większości innych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="4d9f0-107">Dzielenie danych do treningów i testów</span><span class="sxs-lookup"><span data-stu-id="4d9f0-107">Split data for training and testing</span></span>

<span data-ttu-id="4d9f0-108">Celem modelu uczenia maszynowego jest zidentyfikowanie wzorców w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="4d9f0-109">Te wzorce są używane do prognoz przy użyciu nowych danych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="4d9f0-110">Dane mogą być modelowane przez `HousingData`klasę, taką jak .</span><span class="sxs-lookup"><span data-stu-id="4d9f0-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="4d9f0-111">Biorąc pod uwagę następujące dane, które są ładowane do . [`IDataView`](xref:Microsoft.ML.IDataView)</span><span class="sxs-lookup"><span data-stu-id="4d9f0-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
HousingData[] housingData = new HousingData[]
{
    new HousingData
    {
        Size = 600f,
        HistoricalPrices = new float[] { 100000f ,125000f ,122000f },
        CurrentPrice = 170000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 200000f, 250000f, 230000f },
        CurrentPrice = 225000f
    },
    new HousingData
    {
        Size = 1000f,
        HistoricalPrices = new float[] { 126000f, 130000f, 200000f },
        CurrentPrice = 195000f
    },
    new HousingData
    {
        Size = 850f,
        HistoricalPrices = new float[] { 150000f,175000f,210000f },
        CurrentPrice = 205000f
    },
    new HousingData
    {
        Size = 900f,
        HistoricalPrices = new float[] { 155000f, 190000f, 220000f },
        CurrentPrice = 210000f
    },
    new HousingData
    {
        Size = 550f,
        HistoricalPrices = new float[] { 99000f, 98000f, 130000f },
        CurrentPrice = 180000f
    }
};
```

<span data-ttu-id="4d9f0-112">Użyj [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metody, aby podzielić dane na zestawy pociągów i testów.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the data into train and test sets.</span></span> <span data-ttu-id="4d9f0-113">Wynikiem będzie obiekt, [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) który [`IDataView`](xref:Microsoft.ML.IDataView) zawiera dwa elementy członkowskie, jeden dla zestawu pociągów, a drugi dla zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="4d9f0-114">Procent podziału danych jest `testFraction` określany przez parametr.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="4d9f0-115">Poniższy fragment kodu wytrzymuje 20 procent oryginalnych danych dla zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="4d9f0-116">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="4d9f0-116">Prepare the data</span></span>

<span data-ttu-id="4d9f0-117">Dane muszą być wstępnie przetworzone przed szkoleniem modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="4d9f0-118">Więcej informacji na temat przygotowania danych można znaleźć na stronie [`transforms page`](../resources/transforms.md)do [przygotowywania danych,](prepare-data-ml-net.md) a także na stronie .</span><span class="sxs-lookup"><span data-stu-id="4d9f0-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="4d9f0-119">ML.NET algorytmy mają ograniczenia dotyczące typów kolumn wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="4d9f0-120">Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="4d9f0-121">Praca z oczekiwanymi typami kolumn</span><span class="sxs-lookup"><span data-stu-id="4d9f0-121">Working with expected column types</span></span>

<span data-ttu-id="4d9f0-122">Algorytmy uczenia maszynowego w ML.NET oczekiwać wektora float o znanym rozmiarze jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="4d9f0-123">Zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do wspólnego przetwarzania (tj. pikseli obrazu).</span><span class="sxs-lookup"><span data-stu-id="4d9f0-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="4d9f0-124">Jeśli dane nie są wszystkie numeryczne i chcesz zastosować różne przekształcenia danych [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) w każdej kolumnie indywidualnie, użyj metody po przetworzeniu wszystkich kolumn, aby połączyć wszystkie poszczególne kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="4d9f0-125">Poniższy fragment kodu łączy `Size` kolumny `HistoricalPrices` i kolumny w jeden wektor operacji, który `Features`jest wyprowadzany do nowej kolumny o nazwie .</span><span class="sxs-lookup"><span data-stu-id="4d9f0-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="4d9f0-126">Ponieważ istnieje różnica w skalach, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) jest `Features` stosowany do kolumny do normalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) is applied to the `Features` column to normalize the data.</span></span>

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply transforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a><span data-ttu-id="4d9f0-127">Praca z domyślnymi nazwami kolumn</span><span class="sxs-lookup"><span data-stu-id="4d9f0-127">Working with default column names</span></span>

<span data-ttu-id="4d9f0-128">ML.NET algorytmy używają domyślnych nazw kolumn, gdy nie są określone.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="4d9f0-129">Wszyscy trenerzy mają `featureColumnName` parametr wywoływany dla danych wejściowych algorytmu i w stosownych przypadkach mają również parametr dla oczekiwanej wartości o nazwie `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="4d9f0-130">Domyślnie te `Features` wartości `Label` są i odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="4d9f0-131">Za pomocą [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody podczas przetwarzania wstępnego, `Features`aby utworzyć nową kolumnę o nazwie , nie ma potrzeby, aby określić nazwę `IDataView`kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonych .</span><span class="sxs-lookup"><span data-stu-id="4d9f0-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="4d9f0-132">Kolumna etykiety `CurrentPrice`jest , [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ale ponieważ atrybut jest używany w modelu `CurrentPrice` danych, `Label` ML.NET zmienia nazwę kolumny, do której usuwa konieczność dostarczenia parametru `labelColumnName` do estymatora algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="4d9f0-133">Jeśli nie chcesz używać domyślnych nazw kolumn, przekaż nazwy kolumn funkcji i etykiet jako parametry podczas definiowania estymatora algorytmu uczenia maszynowego, jak pokazano w kolejnym urywek:</span><span class="sxs-lookup"><span data-stu-id="4d9f0-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a><span data-ttu-id="4d9f0-134">Buforowanie danych</span><span class="sxs-lookup"><span data-stu-id="4d9f0-134">Caching data</span></span>

<span data-ttu-id="4d9f0-135">Domyślnie podczas przetwarzania danych jest leniwie ładowany lub przesyłany strumieniowo, co oznacza, że trenerzy mogą ładować dane z dysku i iterować nad nim wiele razy podczas treningu.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-135">By default, when data is processed, it is lazily loaded or streamed which means that trainers may load the data from disk and iterate over it multiple times during training.</span></span> <span data-ttu-id="4d9f0-136">W związku z tym buforowanie jest zalecane dla zestawów danych, które pasują do pamięci, aby zmniejszyć liczbę razy dane są ładowane z dysku.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-136">Therefore, caching is recommended for datasets that fit into memory to reduce the number of times data is loaded from disk.</span></span> <span data-ttu-id="4d9f0-137">Buforowanie odbywa się w [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ramach [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)za pomocą .</span><span class="sxs-lookup"><span data-stu-id="4d9f0-137">Caching is done as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) by using [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A).</span></span>

<span data-ttu-id="4d9f0-138">Zaleca się stosowanie [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) przed trenerów w przygotowaniu.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-138">It's recommended to use [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before any trainers in the pipeline.</span></span>

<span data-ttu-id="4d9f0-139">Korzystając z [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)poniższego , dodając [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) przed trenerem [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) buforuje wyniki poprzednich estymatorów do późniejszego wykorzystania przez trenera.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-139">Using the following [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601), adding [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) before the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) trainer caches the results of the previous estimators for later use by the trainer.</span></span>

```csharp
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
// 3. Cache prepared data
// 4. Use Sdca trainer to train the model
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"))
        .AppendCacheCheckpoint(mlContext);
        .Append(mlContext.Regression.Trainers.Sdca());
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="4d9f0-140">Szkolenie modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="4d9f0-140">Train the machine learning model</span></span>

<span data-ttu-id="4d9f0-141">Gdy dane są wstępnie przetwarzane, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) użyj metody do uczenia modelu [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) uczenia maszynowego za pomocą algorytmu regresji.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-141">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="4d9f0-142">Wyodrębnianie parametrów modelu</span><span class="sxs-lookup"><span data-stu-id="4d9f0-142">Extract model parameters</span></span>

<span data-ttu-id="4d9f0-143">Po przeszkoleniu modelu wyodrębnić wyuczonych [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) do kontroli lub przekwalifikowania.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-143">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or retraining.</span></span> <span data-ttu-id="4d9f0-144">Podać [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) stronniczość i wyuczone współczynniki lub obciążenia wyszkolonego modelu.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-144">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="4d9f0-145">Inne modele mają parametry, które są specyficzne dla ich zadań.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-145">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="4d9f0-146">Na przykład [algorytm K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na podstawie centroidów i zawiera właściwość, która przechowuje te nauczyły centroidów.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-146">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="4d9f0-147">Aby dowiedzieć się więcej, odwiedź [ `Microsoft.ML.Trainers` dokumentację interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` w ich nazwie.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-147">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="4d9f0-148">Ocena jakości modelu</span><span class="sxs-lookup"><span data-stu-id="4d9f0-148">Evaluate model quality</span></span>

<span data-ttu-id="4d9f0-149">Aby ułatwić wybór modelu o najwyższej wydajności, należy ocenić jego wydajność na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-149">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="4d9f0-150">Użyj [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metody, aby zmierzyć różne metryki dla przeszkolonego modelu.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-150">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9f0-151">Metoda `Evaluate` tworzy różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-151">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="4d9f0-152">Aby uzyskać więcej informacji, odwiedź [ `Microsoft.ML.Data` dokumentację](xref:Microsoft.ML.Data) `Metrics` interfejsu API i poszukaj klas, które zawierają w ich nazwie.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-152">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

```csharp
// Measure trained model performance
// Apply data prep transformer to test data
IDataView transformedTestData = dataPrepTransformer.Transform(testData);

// Use trained model to make inferences on test data
IDataView testDataPredictions = trainedModel.Transform(transformedTestData);

// Extract model metrics and get RSquared
RegressionMetrics trainedModelMetrics = mlContext.Regression.Evaluate(testDataPredictions);
double rSquared = trainedModelMetrics.RSquared;
```

<span data-ttu-id="4d9f0-153">W poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="4d9f0-153">In the previous code sample:</span></span>

1. <span data-ttu-id="4d9f0-154">Zestaw danych testowych jest wstępnie przetwarzany przy użyciu przekształceń przygotowania danych wcześniej zdefiniowanych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-154">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="4d9f0-155">Przeszkolony model uczenia maszynowego jest używany do przewidywania danych testowych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-155">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="4d9f0-156">W `Evaluate` metodzie wartości w `CurrentPrice` kolumnie zestawu danych testowych `Score` są porównywane z kolumną prognozy nowo danych wyjściowych, aby obliczyć metryki `rSquared` dla modelu regresji, z których jeden, R-Squared jest przechowywany w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-156">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="4d9f0-157">W tym małym przykładzie R-Squared jest liczbą nie w zakresie 0-1 ze względu na ograniczony rozmiar danych.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-157">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="4d9f0-158">W scenariuszu rzeczywistym należy oczekiwać, aby zobaczyć wartość między 0 i 1.</span><span class="sxs-lookup"><span data-stu-id="4d9f0-158">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
