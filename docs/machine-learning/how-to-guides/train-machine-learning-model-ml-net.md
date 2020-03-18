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
# <a name="train-and-evaluate-a-model"></a>Trenowanie i ocenianie modelu

Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Mimo że ten przykład pociągów modelu regresji, pojęcia mają zastosowanie w większości innych algorytmów.

## <a name="split-data-for-training-and-testing"></a>Dzielenie danych na potrzeby szkoleń i testowania

Celem modelu uczenia maszynowego jest zidentyfikowanie wzorców w danych szkoleniowych. Te wzorce są używane do prognozowania przy użyciu nowych danych.

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

Biorąc pod uwagę następujące dane, które są ładowane do pliku [`IDataView`](xref:Microsoft.ML.IDataView).

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

Użyj [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metody, aby podzielić dane na zestawy pociągów i testów. Wynik będzie obiekt, [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) który [`IDataView`](xref:Microsoft.ML.IDataView) zawiera dwa elementy członkowskie, jeden dla zestawu pociągów, a drugi dla zestawu testowego. Procent podziału danych jest `testFraction` określana przez parametr. Poniższy fragment kodu zawiera 20 procent oryginalnych danych dla zestawu testów.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Przygotowywanie danych

Dane muszą być wstępnie przetworzone przed szkoleniem modelu uczenia maszynowego. Więcej informacji na temat przygotowania danych można znaleźć na [temat przygotowania danych do artykułu inspedycyjnego,](prepare-data-ml-net.md) a także . [`transforms page`](../resources/transforms.md)

ML.NET algorytmy mają ograniczenia dotyczące typów kolumn wejściowych. Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.

### <a name="working-with-expected-column-types"></a>Praca z oczekiwanymi typami kolumn

Algorytmy uczenia maszynowego w ML.NET oczekiwać wektor float o znanym rozmiarze jako dane wejściowe. Zastosuj [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybut do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do przetwarzania razem (tj. pikseli obrazu).

Jeśli dane nie są wszystkie liczbowe i chcesz zastosować różne przekształcenia danych [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) w każdej z kolumn indywidualnie, należy użyć metody po przetworzeniu wszystkich kolumn, aby połączyć wszystkie poszczególne kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny.

Poniższy fragment kodu łączy `Size` kolumny `HistoricalPrices` i kolumny w jeden wektor operacji, który jest wyprowadzany do nowej kolumny o nazwie `Features`. Ponieważ istnieje różnica w skalach, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest `Features` stosowany do kolumny do normalizacji danych.

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

ML.NET algorytmy używają domyślnych nazw kolumn, gdy nie określono żadnych. Wszyscy trenerzy `featureColumnName` mają parametr wywoływany dla danych wejściowych algorytmu i w `labelColumnName`stosownych przypadkach mają również parametr dla oczekiwanej wartości o nazwie . Domyślnie te `Features` wartości `Label` są i odpowiednio.

Za pomocą [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody podczas przetwarzania wstępnego, `Features`aby utworzyć nową kolumnę o nazwie , nie ma potrzeby, aby określić nazwę `IDataView`kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonej . Kolumna etykiety jest `CurrentPrice` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) , ale ponieważ atrybut jest używany `CurrentPrice` w `Label` modelu danych, ML.NET zmienia `labelColumnName` nazwę kolumny, do której usuwa potrzebę dostarczenia parametru do estymatora algorytmu uczenia maszynowego.

Jeśli nie chcesz używać domyślnych nazw kolumn, przekaż nazwy kolumn funkcji i etykiet jako parametry podczas definiowania estymatora algorytmu uczenia maszynowego, jak pokazano w kolejnym fragmencie kodu:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Szkolenie modelu uczenia maszynowego

Po przetworzeniu danych jest wstępnie [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) przetworzone, należy użyć metody [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) do uczenia modelu uczenia maszynowego za pomocą algorytmu regresji.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Wyodrębnianie parametrów modelu

Po przeszkoloniu modelu [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) wyodrębnij wyuczone do kontroli lub ponownego przeszkolenia. Zapewniają [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) błędy i wyuczonych współczynników lub wagi przeszkolonego modelu.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Inne modele mają parametry, które są specyficzne dla ich zadań. Na przykład [algorytm K-Means](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) na podstawie centroidów i zawiera właściwość, która przechowuje te wyuczone centroidy. Aby dowiedzieć się więcej, odwiedź [ `Microsoft.ML.Trainers` dokumentację interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` ich nazwy.

## <a name="evaluate-model-quality"></a>Ocena jakości modelu

Aby ułatwić wybór modelu o najlepszej wydajności, należy ocenić jego wydajność na danych testowych. Użyj [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody, aby zmierzyć różne metryki dla uczonego modelu.

> [!NOTE]
> Metoda `Evaluate` tworzy różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane. Aby uzyskać więcej informacji, odwiedź [ `Microsoft.ML.Data` dokumentację interfejsu API](xref:Microsoft.ML.Data) i poszukaj klas, które zawierają `Metrics` w ich imieniu.

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
2. Uczonego modelu uczenia maszynowego służy do prognozowania danych testowych.
3. W `Evaluate` metodzie wartości w `CurrentPrice` kolumnie zestawu danych testowych `Score` są porównywane z kolumną prognoz nowo wyjściowych w celu obliczenia metryk dla modelu regresji, z których jeden R-Kwadrat jest przechowywany w zmiennej. `rSquared`

> [!NOTE]
> W tym małym przykładzie R-Squared jest liczbą nie w zakresie 0-1 ze względu na ograniczony rozmiar danych. W scenariuszu rzeczywistym należy oczekiwać, aby zobaczyć wartość z wartością z wartością z wartością od 0 do 1.
