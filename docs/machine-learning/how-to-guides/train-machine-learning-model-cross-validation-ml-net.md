---
title: Uczenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej
description: Dowiedz się, jak tworzyć bardziej niezawodne modele uczenia maszynowego w programie ML.NET przy użyciu krzyżowego sprawdzania poprawności. Wzajemne sprawdzanie poprawności to technika szkoleń i oceny modelu, która dzieli dane na kilka partycji i pociąga za siebie wiele algorytmów na tych partycjach.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: f29103d0cf59cdec10a641b05ce359bf95c01ccd
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169055"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Uczenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej

Dowiedz się, jak korzystać z krzyżowego sprawdzania poprawności do uczenia bardziej niezawodnych modeli uczenia maszynowego w ML.NET. 

Wzajemne sprawdzanie poprawności to technika szkoleń i oceny modelu, która dzieli dane na kilka partycji i pociąga za siebie wiele algorytmów na tych partycjach. Ta technika podnosi niezawodność modelu przez wyprowadzenie danych z procesu szkolenia. Oprócz poprawy wydajności niewidocznych obserwacji w środowiskach z ograniczonymi danymi może być skutecznym narzędziem dla modeli szkoleniowych z mniejszym zestawem danych.

## <a name="the-data-and-data-model"></a>Dane i model danych

Dane z pliku o następującym formacie:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Dane można modelować według klasy, takiej jak `HousingData` i załadowanej [`IDataView`](xref:Microsoft.ML.IDataView)do.

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

## <a name="prepare-the-data"></a>Przygotowywanie danych

Wstępnie przetwórz dane przed użyciem ich do kompilowania modelu uczenia maszynowego. W tym przykładzie `Size` kolumny i `HistoricalPrices` są łączone w jeden wektor funkcji, który jest wyprowadzany do [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) nowej kolumny o nazwie `Features` przy użyciu metody. Oprócz pobierania danych do formatu oczekiwanego przez algorytmy ML.NET, łączenie kolumn optymalizuje kolejne operacje w potoku przez zastosowanie operacji raz dla połączonej kolumny zamiast każdej oddzielnej kolumny. 

Gdy kolumny są łączone w [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) jeden wektor, są stosowane `Features` do kolumny do pobrania `Size` i `HistoricalPrices` w tym samym zakresie między 0-1. 

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

## <a name="train-model-with-cross-validation"></a>Uczenie modelu z krzyżowego sprawdzania poprawności

Gdy dane zostaną wstępnie przetworzone, czas na nauczenie modelu. Najpierw wybierz algorytm najbardziej zbliżony do zadania uczenia maszynowego, które ma zostać wykonane. Ponieważ przewidywana wartość jest wartością liczbową, to zadanie jest regresją. Jednym z algorytmów regresji implementowanych przez ml.NET [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) jest algorytm. Aby przeprowadzić uczenie modelu z wykorzystaniem krzyżowego sprawdzania [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) poprawności, użyj metody. 

> [!NOTE]
> Chociaż ten przykład używa modelu regresji liniowej, CrossValidate ma zastosowanie do wszystkich innych zadań uczenia maszynowego w ML.NET, z wyjątkiem wykrywania anomalii.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)wykonuje następujące operacje:

1. Dzieli dane na liczbę partycji równą wartości określonej w `numberOfFolds` parametrze. Wynikiem każdej partycji jest [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) obiekt.
1. Model jest przeszkolony na każdej partycji przy użyciu określonego algorytmu uczenia maszynowego szacowania w zestawie danych szkoleniowych.
1. Wydajność poszczególnych modeli jest oceniana przy użyciu [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) metody w zestawie danych testowych. 
1. Model wraz z metrykami są zwracane dla każdego z modeli.

Wynik przechowywany w programie `cvResults` jest [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekcją obiektów. Ten obiekt obejmuje przeszkolony model, a także metryki, które są zarówno dostępne [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) , [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) jak i właściwości. W tym przykładzie `Model` właściwość jest typu [`ITransformer`](xref:Microsoft.ML.ITransformer) , a `Metrics` właściwość jest typu [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics). 

## <a name="evaluate-the-model"></a>Oceń model

Metryki dla różnych przeszkolonych modeli są dostępne za `Metrics` pomocą właściwości indywidualnego [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektu. W takim przypadku uzyskuje się dostęp do [metryki R-kwadrat](https://en.wikipedia.org/wiki/Coefficient_of_determination) i są one przechowywane `rSquared`w zmiennej. 

```csharp
IEnumerable<double> rSquared = 
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

Jeśli sprawdzisz zawartość `rSquared` zmiennej, dane wyjściowe powinny mieć pięć wartości z zakresu od 0-1, gdzie najlepiej do 1. Korzystając z metryk, takich jak R-Square, wybierz modele z największej do najgorszego wykonania. Następnie wybierz najwyższy model, aby dokonać prognoz lub wykonać dodatkowe operacje w programie.

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
