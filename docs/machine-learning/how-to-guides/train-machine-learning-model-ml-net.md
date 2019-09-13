---
title: Trenowanie i ocenianie modelu
description: Dowiedz się, jak tworzyć modele uczenia maszynowego, zbierać metryki i mierzyć wydajność za pomocą ML.NET. Model uczenia maszynowego identyfikuje wzorce w danych szkoleniowych, aby tworzyć prognozy przy użyciu nowych danych.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: fc735f28bad91b9714d7e6bf2a9c7c620acacc4d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929347"
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

Użyj metody [`TrainTestSplit`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) , aby podzielić dane na zestawy uczenia i testowe. Wynik będzie [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiektem zawierającym dwa [`IDataView`](xref:Microsoft.ML.IDataView) elementy członkowskie, jeden dla zestawu pociąg i drugi dla zestawu testowego. Procent podziału danych jest określany przez `testFraction` parametr. Poniższy fragment kodu zawiera 20% oryginalnych danych dla zestawu testów.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Przygotowywanie danych

Przed szkoleniem modelu uczenia maszynowego należy wstępnie przetworzyć dane. Więcej informacji na temat przygotowywania danych można znaleźć w [artykule Przygotowywanie danych](prepare-data-ml-net.md) , jak również [`transforms page`](../resources/transforms.md).

Algorytmy ML.NET mają ograniczenia dotyczące typów kolumn wejściowych. Ponadto wartości domyślne są używane dla nazw kolumn wejściowych i wyjściowych, gdy nie określono żadnych wartości.

### <a name="working-with-expected-column-types"></a>Praca z oczekiwanymi typami kolumn

Algorytmy uczenia maszynowego w ML.NET oczekują wektora zmiennoprzecinkowego o znanym rozmiarze jako dane wejściowe. [`VectorType`](xref:Microsoft.ML.Data.VectorTypeAttribute) Zastosuj atrybut do modelu danych, gdy wszystkie dane są już w formacie liczbowym i są przeznaczone do przetwarzania razem (tj. pikseli obrazów). 

Jeśli dane nie są wszystkie liczbowe i chcesz zastosować różne przekształcenia danych osobno dla każdej z kolumn, użyj [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody po przetworzeniu wszystkich kolumn, aby połączyć wszystkie poszczególne kolumny w jeden wektor funkcji, który jest wyprowadzany do nowej kolumny. 

Poniższy fragment kodu łączy `Size` i `HistoricalPrices` kolumny w jeden wektor funkcji, który jest wyprowadzany do nowej kolumny o nazwie `Features`. Ponieważ istnieje różnica w skali, jest stosowana [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) `Features` do kolumny, aby znormalizować dane.

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

Algorytmy ML.NET używają domyślnych nazw kolumn, gdy nie są określone. Wszystkie Instruktorzy mają parametr wywoływany `featureColumnName` dla danych wejściowych algorytmu i gdy ma to zastosowanie, ma także parametr dla oczekiwanej `labelColumnName`wartości. Domyślnie te wartości są `Features` i `Label` odpowiednio. 

Korzystając z [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody podczas wstępnego przetwarzania, aby utworzyć nową kolumnę o nazwie `Features`, nie trzeba określać nazwy kolumny funkcji w parametrach algorytmu, ponieważ już istnieje w wstępnie przetworzonym `IDataView`czasie. `CurrentPrice`Kolumna Label ma wartość, ale `CurrentPrice` [`ColumnName`](xref:Microsoft.ML.Data.ColumnNameAttribute) ponieważ atrybut jest używany w modelu danych, ml.NET zmienia nazwę kolumny, `labelColumnName` na `Label` która eliminuje konieczność podania parametru do algorytmu uczenia maszynowego szacowania. 

Jeśli nie chcesz używać domyślnych nazw kolumn, Przekaż nazwy funkcji i etykiety kolumn jako parametry podczas definiowania algorytmu uczenia maszynowego szacowania, jak pokazano w kolejnym fragmencie kodu:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Uczenie modelu uczenia maszynowego

Gdy dane są wstępnie przetwarzane, użyj [`Fit`](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) metody do uczenia modelu uczenia maszynowego [`StochasticDualCoordinateAscent`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) z algorytmem regresji.

```csharp
// Define StochasticDualCoordinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Wyodrębnij parametry modelu

Po przeszkoleniu modelu Wyodrębnij zdobytą [`ModelParameters`](xref:Microsoft.ML.Trainers.ModelParametersBase%601) wiedzę na potrzeby inspekcji lub ponownego szkolenia. [`LinearRegressionModelParameters`](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Zapewnianie obciążenia i rozmieszczonych współczynników lub wag dla przeszkolonego modelu. 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Inne modele mają parametry, które są specyficzne dla swoich zadań. Na przykład, [procesor K-oznacza](xref:Microsoft.ML.Trainers.KMeansTrainer) umieszcza dane w klastrze na podstawie centroids i [`KMeansModelParameters`](xref:Microsoft.ML.Trainers.KMeansModelParameters) zawiera właściwość, która przechowuje te informacje centroids. Aby dowiedzieć się więcej, zapoznaj się z [ `Microsoft.ML.Trainers` dokumentacją interfejsu API](xref:Microsoft.ML.Trainers) i `ModelParameters` Wyszukaj klasy, które zawierają nazwę. 

## <a name="evaluate-model-quality"></a>Oceń jakość modelu

Aby pomóc w wyborze modelu najlepszego przebiegu, ważne jest, aby oszacować jego wydajność na danych testowych. [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) Użyj metody, aby zmierzyć różne metryki dla przeszkolonego modelu.

> [!NOTE]
> `Evaluate` Metoda generuje różne metryki w zależności od tego, które zadanie uczenia maszynowego zostało wykonane. Aby uzyskać więcej informacji, zapoznaj się z [ `Microsoft.ML.Data` dokumentacją interfejsu API](xref:Microsoft.ML.Data) i Wyszukaj `Metrics` klasy, które zawierają nazwę. 

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
3. W metodzie wartości `CurrentPrice` w kolumnie `Score` zestawu danych testowych są porównywane z kolumną nowych prognoz danych wyjściowych w celu obliczenia metryk modelu regresji, z których jeden jest przechowywany w `Evaluate` `rSquared` zmienna.

> [!NOTE]
> W tym małym przykładzie R-kwadrat jest liczbą spoza zakresu 0-1 z powodu ograniczonego rozmiaru danych. W rzeczywistym scenariuszu należy oczekiwać wyświetlenia wartości z zakresu od 0 do 1.
