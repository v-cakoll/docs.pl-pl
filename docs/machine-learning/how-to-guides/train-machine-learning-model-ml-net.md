---
title: Trenowanie i ocenianie modelu
description: Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Model uczenia maszynowego identyfikuje wzorce w danych szkoleniowych, aby przewidywać przy użyciu nowych danych.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976760"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="2eaaa-104">Trenowanie i ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="2eaaa-104">Train and evaluate a model</span></span>

<span data-ttu-id="2eaaa-105">Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-105">Learn how to build machine learning models, collect metrics, and measure performance with ML.NET.</span></span> <span data-ttu-id="2eaaa-106">Mimo że ten przykład pociągów modelu regresji, pojęcia mają zastosowanie w większości innych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="2eaaa-107">Dzielenie danych na potrzeby szkoleń i testowania</span><span class="sxs-lookup"><span data-stu-id="2eaaa-107">Split data for training and testing</span></span>

<span data-ttu-id="2eaaa-108">Celem modelu uczenia maszynowego jest zidentyfikowanie wzorców w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="2eaaa-109">Te wzorce są używane do prognozowania przy użyciu nowych danych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="2eaaa-110">Dane mogą być modelowane przez `HousingData`klasę, taką jak .</span><span class="sxs-lookup"><span data-stu-id="2eaaa-110">The data can be modeled by a class like `HousingData`.</span></span>

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

<span data-ttu-id="2eaaa-111">Biorąc pod uwagę następujące dane, które są ładowane do pliku [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="2eaaa-111">Given the following data which is loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

<span data-ttu-id="2eaaa-112">Użyj [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metody, aby podzielić dane na zestawy pociągów i testów.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="2eaaa-113">Wynik będzie obiekt, [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) który [`IDataView`](xref:Microsoft.ML.IDataView) zawiera dwa elementy członkowskie, jeden dla zestawu pociągów, a drugi dla zestawu testowego.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="2eaaa-114">Procent podziału danych jest `testFraction` określana przez parametr.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="2eaaa-115">Poniższy fragment kodu zawiera 20 procent oryginalnych danych dla zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="2eaaa-116">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="2eaaa-116">Prepare the data</span></span>

<span data-ttu-id="2eaaa-117">Dane muszą być wstępnie przetworzone przed szkoleniem modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="2eaaa-118">Więcej informacji na temat przygotowania danych można znaleźć na [temat przygotowania danych do artykułu inspedycyjnego,](prepare-data-ml-net.md) a także . [`transforms page`](../resources/transforms.md)</span><span class="sxs-lookup"><span data-stu-id="2eaaa-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="2eaaa-119">ML.NET algorytmy mają ograniczenia dotyczące typów kolumn wejściowych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="2eaaa-120">Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="2eaaa-121">Praca z oczekiwanymi typami kolumn</span><span class="sxs-lookup"><span data-stu-id="2eaaa-121">Working with expected column types</span></span>

<span data-ttu-id="2eaaa-122">Algorytmy uczenia maszynowego w ML.NET oczekiwać wektor float o znanym rozmiarze jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="2eaaa-123">Zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do przetwarzania razem (tj. pikseli obrazu).</span><span class="sxs-lookup"><span data-stu-id="2eaaa-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span>

<span data-ttu-id="2eaaa-124">Jeśli dane nie są wszystkie liczbowe i chcesz zastosować różne przekształcenia danych [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) w każdej z kolumn indywidualnie, należy użyć metody po przetworzeniu wszystkich kolumn, aby połączyć wszystkie poszczególne kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span>

<span data-ttu-id="2eaaa-125">Poniższy fragment kodu łączy `Size` kolumny `HistoricalPrices` i kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny o nazwie `Features`.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="2eaaa-126">Ponieważ istnieje różnica w skalach, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest `Features` stosowany do kolumny do normalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="2eaaa-127">Praca z domyślnymi nazwami kolumn</span><span class="sxs-lookup"><span data-stu-id="2eaaa-127">Working with default column names</span></span>

<span data-ttu-id="2eaaa-128">ML.NET algorytmy używają domyślnych nazw kolumn, gdy nie określono żadnych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="2eaaa-129">Wszyscy trenerzy `featureColumnName` mają parametr wywoływany dla danych wejściowych algorytmu i w `labelColumnName`stosownych przypadkach mają również parametr dla oczekiwanej wartości o nazwie .</span><span class="sxs-lookup"><span data-stu-id="2eaaa-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="2eaaa-130">Domyślnie te `Features` wartości `Label` są i odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-130">By default those values are `Features` and `Label` respectively.</span></span>

<span data-ttu-id="2eaaa-131">Za pomocą [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody podczas przetwarzania wstępnego, `Features`aby utworzyć nową kolumnę o nazwie , nie ma potrzeby, aby określić nazwę `IDataView`kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonej .</span><span class="sxs-lookup"><span data-stu-id="2eaaa-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="2eaaa-132">Kolumna etykiety jest `CurrentPrice` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) , ale ponieważ atrybut jest używany `CurrentPrice` w `Label` modelu danych, ML.NET zmienia `labelColumnName` nazwę kolumny, do której usuwa potrzebę dostarczenia parametru do estymatora algorytmu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span>

<span data-ttu-id="2eaaa-133">Jeśli nie chcesz używać domyślnych nazw kolumn, przekaż nazwy kolumn funkcji i etykiet jako parametry podczas definiowania estymatora algorytmu uczenia maszynowego, jak pokazano w kolejnym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="2eaaa-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="2eaaa-134">Szkolenie modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="2eaaa-134">Train the machine learning model</span></span>

<span data-ttu-id="2eaaa-135">Po przetworzeniu danych jest wstępnie [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) przetworzone, należy użyć metody [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) do uczenia modelu uczenia maszynowego za pomocą algorytmu regresji.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="2eaaa-136">Wyodrębnianie parametrów modelu</span><span class="sxs-lookup"><span data-stu-id="2eaaa-136">Extract model parameters</span></span>

<span data-ttu-id="2eaaa-137">Po przeszkoloniu modelu [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) wyodrębnij wyuczone do kontroli lub ponownego przeszkolenia.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="2eaaa-138">Zapewniają [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) błędy i wyuczonych współczynników lub wagi przeszkolonego modelu.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span>

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="2eaaa-139">Inne modele mają parametry, które są specyficzne dla ich zadań.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="2eaaa-140">Na przykład [algorytm K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na podstawie centroidów i zawiera właściwość, która przechowuje te wyuczone centroidy.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="2eaaa-141">Aby dowiedzieć się więcej, odwiedź [ `Microsoft.ML.Trainers` dokumentację interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` ich nazwy.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span>

## <a name="evaluate-model-quality"></a><span data-ttu-id="2eaaa-142">Ocena jakości modelu</span><span class="sxs-lookup"><span data-stu-id="2eaaa-142">Evaluate model quality</span></span>

<span data-ttu-id="2eaaa-143">Aby ułatwić wybór modelu o najlepszej wydajności, należy ocenić jego wydajność na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="2eaaa-144">Użyj [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody, aby zmierzyć różne metryki dla uczonego modelu.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="2eaaa-145">Metoda `Evaluate` tworzy różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="2eaaa-146">Aby uzyskać więcej informacji, odwiedź [ `Microsoft.ML.Data` dokumentację interfejsu API](xref:Microsoft.ML.Data) i poszukaj klas, które zawierają `Metrics` w ich imieniu.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span>

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

<span data-ttu-id="2eaaa-147">W poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="2eaaa-147">In the previous code sample:</span></span>

1. <span data-ttu-id="2eaaa-148">Zestaw danych testowych jest wstępnie przetwarzany przy użyciu przekształceń przygotowania danych wcześniej zdefiniowanych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span>
2. <span data-ttu-id="2eaaa-149">Uczonego modelu uczenia maszynowego służy do prognozowania danych testowych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="2eaaa-150">W `Evaluate` metodzie wartości w `CurrentPrice` kolumnie zestawu danych testowych `Score` są porównywane z kolumną prognoz nowo wyjściowych w celu obliczenia metryk dla modelu regresji, z których jeden R-Kwadrat jest przechowywany w zmiennej. `rSquared`</span><span class="sxs-lookup"><span data-stu-id="2eaaa-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="2eaaa-151">W tym małym przykładzie R-Squared jest liczbą nie w zakresie 0-1 ze względu na ograniczony rozmiar danych.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="2eaaa-152">W scenariuszu rzeczywistym należy oczekiwać, aby zobaczyć wartość z wartością z wartością z wartością od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="2eaaa-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
