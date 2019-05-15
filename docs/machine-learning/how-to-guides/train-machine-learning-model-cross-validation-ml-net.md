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
# <a name="train-and-evaluate-a-machine-learning-model-using-cross-validation"></a>Nauczanie i ocena model uczenia maszynowego przy użyciu krzyżowego sprawdzania poprawności

Dowiedz się, jak na potrzeby tworzenia bardziej niezawodnych modeli uczenia maszynowego w strukturze ML.NET krzyżowego sprawdzania poprawności. 

Krzyżowa Weryfikacja jest szkolenia i model oceny technika, która dzieli dane na wiele partycji, a następnie szkolenie modeli wielu algorytmów na te partycje. Ta technika zwiększa niezawodność modelu, zawierający dane z procesu uczenia. Oprócz poprawianie wydajności niewidzianych uwagi, w środowiskach ograniczonego danych może być skutecznym narzędziem do szkolenia modele z mniejszych zestawu danych.

## <a name="the-data-and-data-model"></a>Dane oraz model danych

Podane dane z pliku, ma następujący format:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Dane mogą być modelowane przez klasę, takie jak `HousingData`:

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

Załadowane dane w [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="prepare-the-data"></a>Przygotowywanie danych

Wstępne przetwarzanie danych przed ich użyciem do tworzenia modelu uczenia maszynowego. W tym przykładzie `Size` i `HistoricalPrices` kolumny są łączone w jednej funkcji wektor, który jest wyprowadzana do nową kolumnę o nazwie `Features` przy użyciu [ `Concatenate` ](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody. Oprócz pobierania danych do formatu oczekiwanego przez algorytmy strukturze ML.NET, złączenie kolumn optymalizuje kolejne operacje w potoku, stosując wykonać jeden raz dla połączonych kolumny zamiast wszystkich oddzielne kolumny. 

Po kolumny są łączone w pojedynczy wektor [ `NormalizeMinMax` ](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jest stosowany do `Features` kolumny, aby uzyskać `Size` i `HistoricalPrices` w tym samym zakresie 0 – 1. 

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

## <a name="train-model-with-cross-validation"></a>Szkolenie modelu za pomocą krzyżowego sprawdzania poprawności

Gdy dane zostały wstępnie przetworzone, nadszedł czas na szkolenie modelu. Najpierw należy wybrać algorytm, najlepiej pasującą za pomocą zadań do wykonania uczenia maszynowego. Ponieważ numerycznie ciągłe wartość jest wartością prognozowaną, zadanie jest regresji. Jeden z algorytmów regresji implementowany przez strukturze ML.NET jest [ `StochasticDualCoordinateAscentCoordinator` ](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorytmu. Do nauczenia modelu przy użyciu krzyżowego sprawdzania poprawności [ `CrossValidate` ](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody. 

> [!NOTE]
> Chociaż ten przykład używa modelu regresji liniowej, CrossValidate ma zastosowanie do wszystkich innych zadań w strukturze ML.NET, z wyjątkiem wykrywania anomalii uczenia maszynowego.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) wykonuje następujące operacje:

1. Dzieli dane na liczbę partycji jest równa wartości określonej w `numberOfFolds` parametru. Wynik każdej partycji jest [ `TrainTestData` ](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiektu.
1. Model jest uczony w każdej partycji przy użyciu określonego komputera uczenie algorytmu narzędzie do szacowania zestawów danych szkoleniowych.
1. Każdy model wydajności jest obliczane przy użyciu [ `Evaluate` ](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody testowego zestawu danych. 
1. Model wraz z jego metryki są zwracane dla wszystkich modeli.

Wynik przechowywany w `cvResults` to zbiór [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektów. Ten obiekt zawiera trenowanego modelu, a także metryk, które są zarówno dostępną formę [ `Model` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) i [ `Metrics` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) właściwości odpowiednio. W tym przykładzie `Model` właściwość jest typu [ `ITransformer` ](xref:Microsoft.ML.ITransformer) i `Metrics` właściwość jest typu [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="extract-metrics"></a>Wyodrębnij metryki

Metryki dla różnych modeli uczonego jest możliwy za pośrednictwem `Metrics` właściwości poszczególnych [ `CrossValidationResult` ](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektu. W tym przypadku [R-kwadrat metryki](https://en.wikipedia.org/wiki/Coefficient_of_determination) uzyskuje dostęp i przechowywane w zmiennej `rSquared`. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Jeśli możesz zbadać zawartość `rSquared` zmiennej, dane wyjściowe powinny być pięciu wartości z zakresu od 0 – 1, w przypadku, gdy bliżej 1 oznacza, że najlepiej.

## <a name="select-the-best-performing-model"></a>Wybierz najlepiej działający model

Metryki, takie jak R-kwadrat, wybierz opcję przy użyciu modeli z najlepiej najgorszy wykonywania. Następnie wybierz górny modelu do prognozowania lub wykonanie dodatkowych operacji za pomocą.

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
