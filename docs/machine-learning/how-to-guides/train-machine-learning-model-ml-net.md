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
# <a name="train-and-evaluate-a-model"></a>Trenowanie i ocenianie modelu

Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Mimo że w tym przykładzie trenuje model regresji, pojęcia mają zastosowanie w większości innych algorytmów.

## <a name="split-data-for-training-and-testing"></a>Dzielenie danych do treningów i testów

Celem modelu uczenia maszynowego jest zidentyfikowanie wzorców w danych szkoleniowych. Te wzorce są używane do prognoz przy użyciu nowych danych.

Dane mogą być modelowane przez `HousingData`klasę, taką jak .

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

Biorąc pod uwagę następujące dane, które są ładowane do . [`IDataView`](xref:Microsoft.ML.IDataView)

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

Użyj [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) metody, aby podzielić dane na zestawy pociągów i testów. Wynikiem będzie obiekt, [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) który [`IDataView`](xref:Microsoft.ML.IDataView) zawiera dwa elementy członkowskie, jeden dla zestawu pociągów, a drugi dla zestawu testów. Procent podziału danych jest `testFraction` określany przez parametr. Poniższy fragment kodu wytrzymuje 20 procent oryginalnych danych dla zestawu testów.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Przygotowywanie danych

Dane muszą być wstępnie przetworzone przed szkoleniem modelu uczenia maszynowego. Więcej informacji na temat przygotowania danych można znaleźć na stronie [`transforms page`](../resources/transforms.md)do [przygotowywania danych,](prepare-data-ml-net.md) a także na stronie .

ML.NET algorytmy mają ograniczenia dotyczące typów kolumn wejściowych. Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.

### <a name="working-with-expected-column-types"></a>Praca z oczekiwanymi typami kolumn

Algorytmy uczenia maszynowego w ML.NET oczekiwać wektora float o znanym rozmiarze jako dane wejściowe. Zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do wspólnego przetwarzania (tj. pikseli obrazu).

Jeśli dane nie są wszystkie numeryczne i chcesz zastosować różne przekształcenia danych [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) w każdej kolumnie indywidualnie, użyj metody po przetworzeniu wszystkich kolumn, aby połączyć wszystkie poszczególne kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny.

Poniższy fragment kodu łączy `Size` kolumny `HistoricalPrices` i kolumny w jeden wektor operacji, który `Features`jest wyprowadzany do nowej kolumny o nazwie . Ponieważ istnieje różnica w skalach, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) jest `Features` stosowany do kolumny do normalizacji danych.

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

### <a name="working-with-default-column-names"></a>Praca z domyślnymi nazwami kolumn

ML.NET algorytmy używają domyślnych nazw kolumn, gdy nie są określone. Wszyscy trenerzy mają `featureColumnName` parametr wywoływany dla danych wejściowych algorytmu i w stosownych przypadkach mają również parametr dla oczekiwanej wartości o nazwie `labelColumnName`. Domyślnie te `Features` wartości `Label` są i odpowiednio.

Za pomocą [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) metody podczas przetwarzania wstępnego, `Features`aby utworzyć nową kolumnę o nazwie , nie ma potrzeby, aby określić nazwę `IDataView`kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonych . Kolumna etykiety `CurrentPrice`jest , [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ale ponieważ atrybut jest używany w modelu `CurrentPrice` danych, `Label` ML.NET zmienia nazwę kolumny, do której usuwa konieczność dostarczenia parametru `labelColumnName` do estymatora algorytmu uczenia maszynowego.

Jeśli nie chcesz używać domyślnych nazw kolumn, przekaż nazwy kolumn funkcji i etykiet jako parametry podczas definiowania estymatora algorytmu uczenia maszynowego, jak pokazano w kolejnym urywek:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="caching-data"></a>Buforowanie danych

Domyślnie podczas przetwarzania danych jest leniwie ładowany lub przesyłany strumieniowo, co oznacza, że trenerzy mogą ładować dane z dysku i iterować nad nim wiele razy podczas treningu. W związku z tym buforowanie jest zalecane dla zestawów danych, które pasują do pamięci, aby zmniejszyć liczbę razy dane są ładowane z dysku. Buforowanie odbywa się w [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) ramach [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A)za pomocą .

Zaleca się stosowanie [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) przed trenerów w przygotowaniu.

Korzystając z [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601)poniższego , dodając [`AppendCacheCheckpoint`](xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A) przed trenerem [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) buforuje wyniki poprzednich estymatorów do późniejszego wykorzystania przez trenera.

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

## <a name="train-the-machine-learning-model"></a>Szkolenie modelu uczenia maszynowego

Gdy dane są wstępnie przetwarzane, [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase%602.Fit%2A) użyj metody do uczenia modelu [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) uczenia maszynowego za pomocą algorytmu regresji.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Wyodrębnianie parametrów modelu

Po przeszkoleniu modelu wyodrębnić wyuczonych [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) do kontroli lub przekwalifikowania. Podać [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) stronniczość i wyuczone współczynniki lub obciążenia wyszkolonego modelu.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Inne modele mają parametry, które są specyficzne dla ich zadań. Na przykład [algorytm K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na podstawie centroidów i zawiera właściwość, która przechowuje te nauczyły centroidów. Aby dowiedzieć się więcej, odwiedź [ `Microsoft.ML.Trainers` dokumentację interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` w ich nazwie.

## <a name="evaluate-model-quality"></a>Ocena jakości modelu

Aby ułatwić wybór modelu o najwyższej wydajności, należy ocenić jego wydajność na danych testowych. Użyj [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) metody, aby zmierzyć różne metryki dla przeszkolonego modelu.

> [!NOTE]
> Metoda `Evaluate` tworzy różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane. Aby uzyskać więcej informacji, odwiedź [ `Microsoft.ML.Data` dokumentację](xref:Microsoft.ML.Data) `Metrics` interfejsu API i poszukaj klas, które zawierają w ich nazwie.

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

W poprzednim przykładzie kodu:

1. Zestaw danych testowych jest wstępnie przetwarzany przy użyciu przekształceń przygotowania danych wcześniej zdefiniowanych.
2. Przeszkolony model uczenia maszynowego jest używany do przewidywania danych testowych.
3. W `Evaluate` metodzie wartości w `CurrentPrice` kolumnie zestawu danych testowych `Score` są porównywane z kolumną prognozy nowo danych wyjściowych, aby obliczyć metryki `rSquared` dla modelu regresji, z których jeden, R-Squared jest przechowywany w zmiennej.

> [!NOTE]
> W tym małym przykładzie R-Squared jest liczbą nie w zakresie 0-1 ze względu na ograniczony rozmiar danych. W scenariuszu rzeczywistym należy oczekiwać, aby zobaczyć wartość między 0 i 1.
