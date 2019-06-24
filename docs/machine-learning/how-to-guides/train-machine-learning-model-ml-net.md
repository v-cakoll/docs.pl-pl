---
title: Trenowanie i ocenianie modelu
description: Informacje o sposobie tworzenia modeli uczenia maszynowego, wyodrębnić parametry nauczony i zmierzyć wydajność za pomocą platformy ML.NET. Mimo że w tym przykładzie szkolenie modeli model regresji, pojęcia mają zastosowanie w większości innych algorytmów.
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0612
ms.openlocfilehash: d93353a3503ba67bde5fb61dc88f45d26e2f4306
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307441"
---
# <a name="train-and-evaluate-a-model"></a><span data-ttu-id="ae81c-104">Trenowanie i ocenianie modelu</span><span class="sxs-lookup"><span data-stu-id="ae81c-104">Train and evaluate a model</span></span>

<span data-ttu-id="ae81c-105">Informacje o sposobie tworzenia modeli uczenia maszynowego, wyodrębnić parametry nauczony i zmierzyć wydajność za pomocą platformy ML.NET.</span><span class="sxs-lookup"><span data-stu-id="ae81c-105">Learn how to build machine learning models, extract learned parameters and measure performance with ML.NET.</span></span> <span data-ttu-id="ae81c-106">Mimo że w tym przykładzie szkolenie modeli model regresji, pojęcia mają zastosowanie w większości innych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="ae81c-106">Although this sample trains a regression model, the concepts are applicable throughout a majority of the other algorithms.</span></span>

## <a name="split-data-for-training-and-testing"></a><span data-ttu-id="ae81c-107">Podział danych na potrzeby szkolenia i testowania</span><span class="sxs-lookup"><span data-stu-id="ae81c-107">Split data for training and testing</span></span>

<span data-ttu-id="ae81c-108">Cel modelu uczenia maszynowego jest aby zidentyfikować wzorce w danych szkoleniowych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-108">The goal of a machine learning model is to identify patterns within training data.</span></span> <span data-ttu-id="ae81c-109">Te wzorce są używane do prognozowania przy użyciu nowych danych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-109">These patterns are used to make predictions using new data.</span></span>

<span data-ttu-id="ae81c-110">Biorąc pod uwagę następujące modelu danych:</span><span class="sxs-lookup"><span data-stu-id="ae81c-110">Given the following data model:</span></span>

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

<span data-ttu-id="ae81c-111">Załaduj dane do [ `IDataView` ](xref:Microsoft.ML.IDataView):</span><span class="sxs-lookup"><span data-stu-id="ae81c-111">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

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

<span data-ttu-id="ae81c-112">Użyj [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metodę, aby podzielić dane na szkolenie i testowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="ae81c-112">Use the [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) method to split the data into train and test sets.</span></span> <span data-ttu-id="ae81c-113">Wynik będzie [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiekt, który zawiera dwa [ `IDataView` ](xref:Microsoft.ML.IDataView) elementów członkowskich, po jednym dla zestawu szkolenie i drugą dla zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="ae81c-113">The result will be a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object which contains two [`IDataView`](xref:Microsoft.ML.IDataView) members, one for the train set and the other for the test set.</span></span> <span data-ttu-id="ae81c-114">Dane, Podziel wartość procentowa jest określana przez `testFraction` parametru.</span><span class="sxs-lookup"><span data-stu-id="ae81c-114">The data split percentage is determined by the `testFraction` parameter.</span></span> <span data-ttu-id="ae81c-115">Poniższy fragment kodu zawiera limit 20 procent oryginalne dane dla zestawu testów.</span><span class="sxs-lookup"><span data-stu-id="ae81c-115">The snippet below is holding out 20 percent of the original data for the test set.</span></span>

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a><span data-ttu-id="ae81c-116">Przygotowywanie danych</span><span class="sxs-lookup"><span data-stu-id="ae81c-116">Prepare the data</span></span>

<span data-ttu-id="ae81c-117">Dane muszą być wstępnie przetworzone przed szkolenie modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ae81c-117">The data needs to be pre-processed before training a machine learning model.</span></span> <span data-ttu-id="ae81c-118">Więcej informacji na temat przygotowywania danych można znaleźć na [instrukcje przeznaczonego do przygotowania danych](prepare-data-ml-net.md) , jak również [ `transforms page` ](../resources/transforms.md).</span><span class="sxs-lookup"><span data-stu-id="ae81c-118">More information on data preparation can be found on the [data prep how-to article](prepare-data-ml-net.md) as well as the [`transforms page`](../resources/transforms.md).</span></span>

<span data-ttu-id="ae81c-119">Algorytmy strukturze ML.NET ustawić ograniczenie zezwalające na typach kolumny wejściowej.</span><span class="sxs-lookup"><span data-stu-id="ae81c-119">ML.NET algorithms have constraints on input column types.</span></span> <span data-ttu-id="ae81c-120">Ponadto dla nazw kolumn wejściowych i wyjściowych są używane wartości domyślne, jeśli nie określono żadnych wartości.</span><span class="sxs-lookup"><span data-stu-id="ae81c-120">Additionally, default values are used for input and output column names when no values are specified.</span></span>

### <a name="working-with-expected-column-types"></a><span data-ttu-id="ae81c-121">Praca z typami oczekiwanej kolumny</span><span class="sxs-lookup"><span data-stu-id="ae81c-121">Working with expected column types</span></span>

<span data-ttu-id="ae81c-122">Algorytmów uczenia maszynowego w strukturze ML.NET oczekiwać wektor float rozmiar znane jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ae81c-122">The machine learning algorithms in ML.NET expect a float vector of known size as input.</span></span> <span data-ttu-id="ae81c-123">Zastosuj [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybutu do wspólnego modelu danych podczas wszystkich danych jest już w formacie numerycznym i jest przeznaczona do przetwarzania (tj. piksele obrazu).</span><span class="sxs-lookup"><span data-stu-id="ae81c-123">Apply the [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) attribute to your data model when all of the data is already in numerical format and is intended to be processed together (i.e. image pixels).</span></span> 

<span data-ttu-id="ae81c-124">Jeśli dane nie są wszystkie wartości liczbowych i chcesz zastosować przekształcenia danych różnych każdej z kolumn oddzielnie, należy użyć [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody po wszystkich kolumn zostały przetworzone, aby połączyć wszystkie poszczególne kolumny do wektora jednej funkcji, które znajdują się dane wyjściowe na nową kolumnę.</span><span class="sxs-lookup"><span data-stu-id="ae81c-124">If data is not all numerical and you want to apply different data transformations on each of the columns individually, use the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method after all of the columns have been processed to combine all of the individual columns into a single feature vector that is output to a new column.</span></span> 

<span data-ttu-id="ae81c-125">Poniższy fragment kodu łączy `Size` i `HistoricalPrices` kolumny wektor jednej funkcji, który jest wysyłany na nową kolumnę o nazwie `Features`.</span><span class="sxs-lookup"><span data-stu-id="ae81c-125">The following snippet combines the `Size` and `HistoricalPrices` columns into a single feature vector that is output to a new column called `Features`.</span></span> <span data-ttu-id="ae81c-126">Ponieważ ma różnicy w skali, [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest stosowany do `Features` kolumny do normalizacji danych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-126">Because there is a difference in scales, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to normalize the data.</span></span>

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

### <a name="working-with-default-column-names"></a><span data-ttu-id="ae81c-127">Praca z domyślne nazwy kolumn</span><span class="sxs-lookup"><span data-stu-id="ae81c-127">Working with default column names</span></span>

<span data-ttu-id="ae81c-128">Algorytmy strukturze ML.NET Użyj domyślne nazwy kolumn, gdy nie jest określona.</span><span class="sxs-lookup"><span data-stu-id="ae81c-128">ML.NET algorithms use default column names when none are specified.</span></span> <span data-ttu-id="ae81c-129">Wszystkie Instruktorzy ma parametr o nazwie `featureColumnName` dla danych wejściowych, algorytm i zastosowanie mają również parametr oczekiwana wartość o nazwie `labelColumnName`.</span><span class="sxs-lookup"><span data-stu-id="ae81c-129">All trainers have a parameter called `featureColumnName` for the inputs of the algorithm and when applicable they also have a parameter for the expected value called `labelColumnName`.</span></span> <span data-ttu-id="ae81c-130">Domyślnie te wartości są `Features` i `Label` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="ae81c-130">By default those values are `Features` and `Label` respectively.</span></span> 

<span data-ttu-id="ae81c-131">Za pomocą [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody podczas wstępnego przetwarzania, aby utworzyć nową kolumnę o nazwie `Features`, trzeba określić nazwę kolumny funkcji za pomocą parametrów algorytmu, ponieważ już istnieje w Wstępnie przetworzony `IDataView`.</span><span class="sxs-lookup"><span data-stu-id="ae81c-131">By using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method during pre-processing to create a new column called `Features`, there is no need to specify the feature column name in the parameters of the algorithm since it already exists in the pre-processed `IDataView`.</span></span> <span data-ttu-id="ae81c-132">Kolumna etykiety jest `CurrentPrice`, ale ponieważ [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut jest używany w modelu danych, zmienia nazwę strukturze ML.NET `CurrentPrice` kolumny `Label` który usuwa potrzebę zapewnienia `labelColumnName` parametr do szacowania Algorytm uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="ae81c-132">The label column is `CurrentPrice`, but since the [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute is used in the data model, ML.NET renames the `CurrentPrice` column to `Label` which removes the need to provide the `labelColumnName` parameter to the machine learning algorithm estimator.</span></span> 

<span data-ttu-id="ae81c-133">Jeśli nie chcesz używać domyślne nazwy kolumn, przekazywane nazwy funkcji i etykiet kolumn jako parametry podczas definiowania algorytm narzędzie do szacowania, jak pokazano przez kolejne fragment uczenia maszynowego:</span><span class="sxs-lookup"><span data-stu-id="ae81c-133">If you don't want to use the default column names, pass in the names of the feature and label columns as parameters when defining the machine learning algorithm estimator as demonstrated by the subsequent snippet:</span></span>

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a><span data-ttu-id="ae81c-134">Szkolenie modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="ae81c-134">Train the machine learning model</span></span>

<span data-ttu-id="ae81c-135">Gdy dane są wstępnie przetworzone, użyć [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) metody do nauczenia modelu uczenia maszynowego przy użyciu [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorytmu regresji.</span><span class="sxs-lookup"><span data-stu-id="ae81c-135">Once the data is pre-processed, use the [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) method to train the machine learning model with the [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) regression algorithm.</span></span>

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a><span data-ttu-id="ae81c-136">Wyodrębnianie parametrów modelu</span><span class="sxs-lookup"><span data-stu-id="ae81c-136">Extract model parameters</span></span>

<span data-ttu-id="ae81c-137">Po model jest uczony, Wyodrębnij nauczony [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase%601) kontroli lub ponownego szkolenia.</span><span class="sxs-lookup"><span data-stu-id="ae81c-137">After the model has been trained, extract the learned [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) for inspection or re-training.</span></span> <span data-ttu-id="ae81c-138">[ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Obciążenia i nauczony lub wagi trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ae81c-138">The [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) provide the bias and learned coefficients or weights of the trained model.</span></span> 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> <span data-ttu-id="ae81c-139">Inne modele zawierają parametry, które są specyficzne dla ich zadań.</span><span class="sxs-lookup"><span data-stu-id="ae81c-139">Other models have parameters that are specific to their tasks.</span></span> <span data-ttu-id="ae81c-140">Na przykład [algorytm K-średnich](xref:Microsoft.ML.Trainers.KMeansTrainer) polega na spakowaniu danych w klastrze, w oparciu o centroids i [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) zawiera właściwość, która przechowuje te nauczony centroids.</span><span class="sxs-lookup"><span data-stu-id="ae81c-140">For example, the [K-Means algorithm](xref:Microsoft.ML.Trainers.KMeansTrainer) puts data into cluster based on centroids and the [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) contains a property that stores these learned centroids.</span></span> <span data-ttu-id="ae81c-141">Aby dowiedzieć się więcej, odwiedź stronę [ `Microsoft.ML.Trainers` dokumentacji interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` w ich imieniu.</span><span class="sxs-lookup"><span data-stu-id="ae81c-141">To learn more, visit the [`Microsoft.ML.Trainers` API Documentation](xref:Microsoft.ML.Trainers) and look for classes that contain `ModelParameters` in their name.</span></span> 

## <a name="evaluate-model-quality"></a><span data-ttu-id="ae81c-142">Oceń jakość modelu</span><span class="sxs-lookup"><span data-stu-id="ae81c-142">Evaluate model quality</span></span>

<span data-ttu-id="ae81c-143">Aby ułatwić, wybierz opcję najlepiej działający model, istotne jest ocena jej wydajności na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-143">To help choose the best performing model, it is essential to evaluate its performance on test data.</span></span> <span data-ttu-id="ae81c-144">Użyj [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metod w celu mierzenia różne metryki dla trenowanego modelu.</span><span class="sxs-lookup"><span data-stu-id="ae81c-144">Use the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method, to measure various metrics for the trained model.</span></span>

> [!NOTE]
> <span data-ttu-id="ae81c-145">`Evaluate` Generuje różne metryki, w zależności od tego, którego urządzenia zostało wykonane zadanie uczenia.</span><span class="sxs-lookup"><span data-stu-id="ae81c-145">The `Evaluate` method produces different metrics depending on which machine learning task was performed.</span></span> <span data-ttu-id="ae81c-146">Aby uzyskać więcej informacji, odwiedź stronę [ `Microsoft.ML.Data` dokumentacji interfejsu API](xref:Microsoft.ML.Data) i poszukaj klas, które zawierają `Metrics` w ich imieniu.</span><span class="sxs-lookup"><span data-stu-id="ae81c-146">For more details, visit the [`Microsoft.ML.Data` API Documentation](xref:Microsoft.ML.Data) and look for classes that contain `Metrics` in their name.</span></span> 

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

<span data-ttu-id="ae81c-147">W poprzednim przykładzie kodu:</span><span class="sxs-lookup"><span data-stu-id="ae81c-147">In the previous code sample:</span></span>  
1. <span data-ttu-id="ae81c-148">Wstępnie testowego zestawu danych jest przetwarzany, za pomocą przekształcenia przygotowania danych, wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="ae81c-148">Test data set is pre-processed using the data preparation transforms previously defined.</span></span> 
2. <span data-ttu-id="ae81c-149">Model uczenia maszynowego uczonego jest używany do tworzenia prognoz na danych testowych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-149">The trained machine learning model is used to make predictions on the test data.</span></span>
3. <span data-ttu-id="ae81c-150">W `Evaluate` metody, wartości w `CurrentPrice` kolumny zestawu danych testowych są porównywane `Score` kolumny wyjściowe nowo modelu prognozy można obliczyć metryki dotyczące regresji, jednym z nich, R-kwadrat jest przechowywany w `rSquared` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ae81c-150">In the `Evaluate` method, the values in the `CurrentPrice` column of the test data set are compared against the `Score` column of the newly output predictions to calculate the metrics for the regression model, one of which, R-Squared is stored in the `rSquared` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="ae81c-151">W tym przykładzie małych R-kwadrat jest liczbą nie jest w zakresie 0 – 1, ze względu na ograniczone rozmiaru danych.</span><span class="sxs-lookup"><span data-stu-id="ae81c-151">In this small example, the R-Squared is a number not in the range of 0-1 because of the limited size of the data.</span></span> <span data-ttu-id="ae81c-152">W rzeczywistych scenariuszy należy się spodziewać się wartość z zakresu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="ae81c-152">In a real-world scenario, you should expect to see a value between 0 and 1.</span></span>
