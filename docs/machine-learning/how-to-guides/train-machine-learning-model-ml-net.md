---
title: Trenowanie i ocenianie modelu
description: Informacje o sposobie tworzenia modeli uczenia maszynowego, wyodrębnić parametry nauczony i zmierzyć wydajność za pomocą platformy ML.NET. Mimo że w tym przykładzie szkolenie modeli model regresji, pojęcia mają zastosowanie w większości innych algorytmów.
ms.date: 06/11/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to, title-hack-0612
ms.openlocfilehash: b7799d19f5ad51ce509cc6872d9053cad1158552
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025596"
---
# <a name="train-and-evaluate-a-model"></a>Trenowanie i ocenianie modelu

Informacje o sposobie tworzenia modeli uczenia maszynowego, wyodrębnić parametry nauczony i zmierzyć wydajność za pomocą platformy ML.NET. Mimo że w tym przykładzie szkolenie modeli model regresji, pojęcia mają zastosowanie w większości innych algorytmów.

## <a name="split-data-for-training-and-testing"></a>Podział danych na potrzeby szkolenia i testowania

Cel modelu uczenia maszynowego jest aby zidentyfikować wzorce w danych szkoleniowych. Te wzorce są używane do prognozowania przy użyciu nowych danych.

Biorąc pod uwagę następujące modelu danych:

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

Załaduj dane do [ `IDataView` ](xref:Microsoft.ML.IDataView):

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

Użyj [ `TrainTestSplit` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit*) metodę, aby podzielić dane na szkolenie i testowanie zestawów. Wynik będzie [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiekt, który zawiera dwa [ `IDataView` ](xref:Microsoft.ML.IDataView) elementów członkowskich, po jednym dla zestawu szkolenie i drugą dla zestawu testów. Dane, Podziel wartość procentowa jest określana przez `testFraction` parametru. Poniższy fragment kodu zawiera limit 20 procent oryginalne dane dla zestawu testów.

```csharp
DataOperationsCatalog.TrainTestData dataSplit = mlContext.Data.TrainTestSplit(data, testFraction: 0.2);
IDataView trainData = dataSplit.TrainSet;
IDataView testData = dataSplit.TestSet;
```

## <a name="prepare-the-data"></a>Przygotowywanie danych

Dane muszą być wstępnie przetworzone przed szkolenie modelu uczenia maszynowego. Więcej informacji na temat przygotowywania danych można znaleźć na [instrukcje przeznaczonego do przygotowania danych](prepare-data-ml-net.md) , jak również [ `transforms page` ](../resources/transforms.md).

Algorytmy strukturze ML.NET ustawić ograniczenie zezwalające na typach kolumny wejściowej. Ponadto dla nazw kolumn wejściowych i wyjściowych są używane wartości domyślne, jeśli nie określono żadnych wartości.

### <a name="working-with-expected-column-types"></a>Praca z typami oczekiwanej kolumny

Algorytmów uczenia maszynowego w strukturze ML.NET oczekiwać wektor float rozmiar znane jako dane wejściowe. Zastosuj [ `VectorType` ](xref:Microsoft.ML.Data.VectorTypeAttribute) atrybutu do wspólnego modelu danych podczas wszystkich danych jest już w formacie numerycznym i jest przeznaczona do przetwarzania (tj. piksele obrazu). 

Jeśli dane nie są wszystkie wartości liczbowych i chcesz zastosować przekształcenia danych różnych każdej z kolumn oddzielnie, należy użyć [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody po wszystkich kolumn zostały przetworzone, aby połączyć wszystkie poszczególne kolumny do wektora jednej funkcji, które znajdują się dane wyjściowe na nową kolumnę. 

Poniższy fragment kodu łączy `Size` i `HistoricalPrices` kolumny wektor jednej funkcji, który jest wysyłany na nową kolumnę o nazwie `Features`. Ponieważ ma różnicy w skali, [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest stosowany do `Features` kolumny do normalizacji danych.

```csharp
// Define Data Prep Estimator
// 1. Concatenate Size and Historical into a single feature vector output to a new column called Features
// 2. Normalize Features vector
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", "Size", "HistoricalPrices")
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(trainData);

// Apply tranforms to training data
IDataView transformedTrainingData = dataPrepTransformer.Transform(trainData);
```

### <a name="working-with-default-column-names"></a>Praca z domyślne nazwy kolumn

Algorytmy strukturze ML.NET Użyj domyślne nazwy kolumn, gdy nie jest określona. Wszystkie Instruktorzy ma parametr o nazwie `featureColumnName` dla danych wejściowych, algorytm i zastosowanie mają również parametr oczekiwana wartość o nazwie `labelColumnName`. Domyślnie te wartości są `Features` i `Label` odpowiednio. 

Za pomocą [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody podczas wstępnego przetwarzania, aby utworzyć nową kolumnę o nazwie `Features`, trzeba określić nazwę kolumny funkcji za pomocą parametrów algorytmu, ponieważ już istnieje w Wstępnie przetworzony `IDataView`. Kolumna etykiety jest `CurrentPrice`, ale ponieważ [ `ColumnName` ](xref:Microsoft.ML.Data.ColumnNameAttribute) atrybut jest używany w modelu danych, zmienia nazwę strukturze ML.NET `CurrentPrice` kolumny `Label` który usuwa potrzebę zapewnienia `labelColumnName` parametr do szacowania Algorytm uczenia maszynowego. 

Jeśli nie chcesz używać domyślne nazwy kolumn, przekazywane nazwy funkcji i etykiet kolumn jako parametry podczas definiowania algorytm narzędzie do szacowania, jak pokazano przez kolejne fragment uczenia maszynowego:

```csharp
var UserDefinedColumnSdcaEstimator = mlContext.Regression.Trainers.Sdca(labelColumnName: "MyLabelColumnName", featureColumnName: "MyFeatureColumnName");
```

## <a name="train-the-machine-learning-model"></a>Szkolenie modelu uczenia maszynowego

Gdy dane są wstępnie przetworzone, użyć [ `Fit` ](xref:Microsoft.ML.Trainers.TrainerEstimatorBase`2.Fit*) metody do nauczenia modelu uczenia maszynowego przy użyciu [ `StochasticDualCoordinateAscent` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorytmu regresji.

```csharp
// Define StochasticDualCoodrinateAscent regression algorithm estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Build machine learning model
var trainedModel = sdcaEstimator.Fit(transformedTrainingData);
```

## <a name="extract-model-parameters"></a>Wyodrębnianie parametrów modelu

Po model jest uczony, Wyodrębnij nauczony [ `ModelParameters` ](xref:Microsoft.ML.Trainers.ModelParametersBase%601) kontroli lub ponownego szkolenia. [ `LinearRegressionModelParameters` ](xref:Microsoft.ML.Trainers.LinearRegressionModelParameters) Obciążenia i nauczony lub wagi trenowanego modelu. 

```csharp
var trainedModelParameters = trainedModel.Model as LinearRegressionModelParameters;
```

> [!NOTE]
> Inne modele zawierają parametry, które są specyficzne dla ich zadań. Na przykład [algorytm K-średnich](xref:Microsoft.ML.Trainers.KMeansTrainer) polega na spakowaniu danych w klastrze, w oparciu o centroids i [ `KMeansModelParameters` ](xref:Microsoft.ML.Trainers.KMeansModelParameters) zawiera właściwość, która przechowuje te nauczony centroids. Aby dowiedzieć się więcej, odwiedź stronę [ `Microsoft.ML.Trainers` dokumentacji interfejsu API](xref:Microsoft.ML.Trainers) i poszukaj klas, które zawierają `ModelParameters` w ich imieniu. 

## <a name="evaluate-model-quality"></a>Oceń jakość modelu

Aby ułatwić, wybierz opcję najlepiej działający model, istotne jest ocena jej wydajności na danych testowych. Użyj [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metod w celu mierzenia różne metryki dla trenowanego modelu.

> [!NOTE]
> `Evaluate` Metoda generuje różne metryki, w zależności od tego, w jakim komputerze został zadania uczenia zostało wykonane. Aby uzyskać więcej informacji, odwiedź stronę [ `Microsoft.ML.Data` dokumentacji interfejsu API](xref:Microsoft.ML.Data) i poszukaj klas, które zawierają `Metrics` w ich imieniu. 

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
1. Wstępnie testowego zestawu danych jest przetwarzany, za pomocą przekształcenia przygotowania danych, wcześniej zdefiniowany. 
2. Model uczenia maszynowego uczonego jest używany do tworzenia prognoz na danych testowych.
3. W `Evaluate` metody, wartości w `CurrentPrice` kolumny zestawu danych testowych są porównywane `Score` kolumny wyjściowe nowo modelu prognozy można obliczyć metryki dotyczące regresji, jednym z nich, R-kwadrat jest przechowywany w `rSquared` zmiennej.

> [!NOTE]
> W tym przykładzie małych R-kwadrat jest liczbą nie jest w zakresie 0 – 1, ze względu na ograniczone rozmiaru danych. W rzeczywistych scenariuszy należy się spodziewać się wartość z zakresu od 0 do 1.
