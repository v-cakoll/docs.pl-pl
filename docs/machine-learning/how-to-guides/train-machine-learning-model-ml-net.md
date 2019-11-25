---
title: Trenowanie i ocenianie modelu
description: Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Model uczenia maszynowego identyfikuje wzorce w danych szkoleniowych, aby tworzyć prognozy przy użyciu nowych danych.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 0e0f43225b9bf243c31b3095817bdcbdb3123012
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976760"
---
# <a name="train-and-evaluate-a-model"></a>Trenowanie i ocenianie modelu

Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Chociaż ten przykład pociąga za sobą model regresji, pojęcia są stosowane w większości innych algorytmów.

## <a name="split-data-for-training-and-testing"></a>Dzielenie danych do szkolenia i testowania

Celem modelu uczenia maszynowego jest zidentyfikowanie wzorców w ramach danych szkoleniowych. Wzorce te służą do wprowadzania prognoz przy użyciu nowych danych.

Dane można modelować według klasy, takiej jak `HousingData`.

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

Nadano następujące dane, które są ładowane do [`IDataView`](xref:Microsoft.ML.IDataView).

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

Użyj metody [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) , aby podzielić dane na zestawy uczenia i testowe. Wynik będzie obiektem [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) , który zawiera dwa [`IDataView`](xref:Microsoft.ML.IDataView) elementy członkowskie, jeden dla zestawu pociąg i drugi dla zestawu testowego. Wartość procentowa podziału danych jest określana przez parametr `testFraction`. Poniższy fragment kodu zawiera 20% oryginalnych danych dla zestawu testów.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Przygotowywanie danych

Przed szkoleniem modelu uczenia maszynowego należy wstępnie przetworzyć dane. Więcej informacji na temat przygotowywania danych można znaleźć w [artykule](prepare-data-ml-net.md) dotyczącym przygotowania danych, jak również [`transforms page`](../resources/transforms.md).

Algorytmy ML.NET mają ograniczenia dotyczące typów kolumn wejściowych. Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.

### <a name="working-with-expected-column-types"></a>Praca z oczekiwanymi typami kolumn

Algorytmy uczenia maszynowego w ML.NET oczekują wektora zmiennoprzecinkowego o znanym rozmiarze jako dane wejściowe. Zastosuj atrybut [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do przetworzenia razem (tj. pikseli obrazów).

Jeśli dane nie są wszystkie liczbowe i chcesz zastosować różne przekształcenia danych osobno dla każdej z kolumn, użyj metody [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) po przetworzeniu wszystkich kolumn w celu połączenia wszystkich pojedynczych kolumn w jeden wektor funkcji, który jest wyprowadzany do nowej kolumny.

Poniższy fragment kodu łączy `Size` i `HistoricalPrices` kolumny w jeden wektor funkcji, który jest wyprowadzany do nowej kolumny o nazwie `Features`. Ponieważ istnieje różnica w skali, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest stosowana do kolumny `Features` do normalizacji danych.

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

Algorytmy ML.NET używają domyślnych nazw kolumn, gdy nie są określone. Wszystkie Instruktorzy mają parametr o nazwie `featureColumnName` dla danych wejściowych algorytmu i gdy ma to zastosowanie, ma także parametr dla oczekiwanej wartości o nazwie `labelColumnName`. Domyślnie te wartości są odpowiednio `Features` i `Label`.

Przy użyciu metody [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) podczas wstępnego przetwarzania, aby utworzyć nową kolumnę o nazwie `Features`, nie trzeba określać nazwy kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonym `IDataView`. Kolumna etykieta jest `CurrentPrice`, ale ponieważ atrybut [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) jest używany w modelu danych, ml.NET zmienia nazwę kolumny `CurrentPrice` na `Label`, co eliminuje konieczność podania parametru `labelColumnName` do algorytmu uczenia maszynowego szacowania.

Jeśli nie chcesz używać domyślnych nazw kolumn, Przekaż nazwy funkcji i etykiety kolumn jako parametry podczas definiowania algorytmu uczenia maszynowego szacowania, jak pokazano w kolejnym fragmencie kodu:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Uczenie modelu uczenia maszynowego

Gdy dane są wstępnie przetwarzane, użyj metody [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) , aby nauczyć model uczenia maszynowego z algorytmem regresji [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) .

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Wyodrębnij parametry modelu

Po przeszkoleniu modelu Wyodrębnij [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) zdobyte w celu przeprowadzenia inspekcji lub ponownego szkolenia. [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) zapewnia odchylenia i informacje o rozmieszczonych współczynników lub wagi przeszkolonego modelu.

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Inne modele mają parametry, które są specyficzne dla swoich zadań. Na przykład, [procesor K-oznacza](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze na podstawie centroids, a [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) zawiera właściwość, która przechowuje te informacje centroids. Aby dowiedzieć się więcej, zapoznaj się z [dokumentacją interfejsu API`Microsoft.ML.Trainers`](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` w ich nazwie.

## <a name="evaluate-model-quality"></a>Oceń jakość modelu

Aby pomóc w wyborze modelu najlepszego przebiegu, ważne jest, aby oszacować jego wydajność na danych testowych. Użyj metody [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) , aby zmierzyć różne metryki dla przeszkolonego modelu.

> [!NOTE]
> Metoda `Evaluate` generuje różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane. Więcej informacji można znaleźć w [dokumentacji interfejsu API`Microsoft.ML.Data`](xref:Microsoft.ML.Data) i poszukać klas, które zawierają `Metrics` w ich nazwie.

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

1. Zestaw danych testowych jest wstępnie przetworzony przy użyciu wcześniej zdefiniowanych transformacji przygotowywania danych.
2. Przeszkolony model uczenia maszynowego służy do przewidywania danych testowych.
3. W metodzie `Evaluate` wartości w kolumnie `CurrentPrice` zestawu danych testowych są porównywane z kolumną `Score` nowych prognoz danych wyjściowych w celu obliczenia metryk modelu regresji, z których jeden jest przechowywany w zmiennej `rSquared`.

> [!NOTE]
> W tym małym przykładzie R-kwadrat jest liczbą spoza zakresu 0-1 z powodu ograniczonego rozmiaru danych. W rzeczywistym scenariuszu należy oczekiwać wyświetlenia wartości z zakresu od 0 do 1.
