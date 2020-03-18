---
title: Szkolenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej
description: Dowiedz się, jak używać sprawdzania poprawności krzyżowej do tworzenia bardziej niezawodnych modeli uczenia maszynowego w ML.NET. Krzyżowa weryfikacja jest techniką oceny szkolenia i modelu, która dzieli dane na kilka partycji i szkoli wiele algorytmów na tych partycjach.
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976929"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a>Szkolenie modelu uczenia maszynowego przy użyciu weryfikacji krzyżowej

Dowiedz się, jak używać sprawdzania poprawności krzyżowej do uczenia bardziej niezawodnych modeli uczenia maszynowego w ML.NET.

Krzyżowa weryfikacja jest techniką oceny szkolenia i modelu, która dzieli dane na kilka partycji i szkoli wiele algorytmów na tych partycjach. Technika ta poprawia niezawodność modelu, przechowując dane z procesu szkolenia. Oprócz poprawy wydajności w niewidocznych obserwacjach, w środowiskach ograniczonych danymi może być skutecznym narzędziem do szkolenia modeli z mniejszym zestawem danych.

## <a name="the-data-and-data-model"></a>Model danych i danych

Dane z pliku, który ma następujący format:

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

Dane mogą być modelowane przez `HousingData` klasę, [`IDataView`](xref:Microsoft.ML.IDataView)jak i załadowany do .

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

Wstępnie przetwórz dane przed użyciem go do utworzenia modelu uczenia maszynowego. W tym przykładzie `Size` `HistoricalPrices` kolumny i kolumny są łączone w wektor pojedynczej operacji, który jest wyprowadzany do nowej kolumny o nazwie `Features` przy użyciu [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) metody. Oprócz uzyskania danych do formatu oczekiwanego przez algorytmy ML.NET, połączając kolumny optymalizuje kolejne operacje w potoku, stosując operację raz dla kolumny skonkretyzowanej zamiast każdej z oddzielnych kolumn.

Po połączeniu kolumn w jeden [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) wektor, `Features` jest stosowany `Size` `HistoricalPrices` do kolumny, aby uzyskać i w tym samym zakresie między 0-1.

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

## <a name="train-model-with-cross-validation"></a>Model pociągu z walidacją krzyża

Po przetworzeniu danych nadszedł czas, aby nabyć model. Najpierw wybierz algorytm, który najbardziej ściśle wyrównuje się z zadaniem uczenia maszynowego do wykonania. Ponieważ przewidywana wartość jest wartością liczbowo ciągłą, zadaniem jest regresja. Jednym z algorytmów regresji zaimplementowanych [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) przez ML.NET jest algorytm. Aby nabyć model z krzyżowego sprawdzania poprawności należy użyć [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) metody.

> [!NOTE]
> Mimo że w tym przykładzie używa modelu regresji liniowej, CrossValidate ma zastosowanie do wszystkich innych zadań uczenia maszynowego w ML.NET z wyjątkiem wykrywania anomalii.

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*)wykonuje następujące czynności:

1. Dzieli dane na liczbę partycji równą wartości określonej `numberOfFolds` w parametrze. Wynikiem każdej partycji [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) jest obiekt.
1. Model jest uznawiany na każdej partycji przy użyciu określonego estymatora algorytmu uczenia maszynowego w zestawie danych szkoleniowych.
1. Wydajność każdego modelu jest oceniana [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) przy użyciu metody na zestawie danych testowych.
1. Model wraz z jego metryki są zwracane dla każdego z modeli.

Wynik przechowywany `cvResults` w jest [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) kolekcją obiektów. Ten obiekt zawiera uczonego modelu, jak również [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) metryki, które są dostępne formie i [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) właściwości odpowiednio. W tym przykładzie `Model` właściwość jest [`ITransformer`](xref:Microsoft.ML.ITransformer) typu, a `Metrics` [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics)właściwość jest typu .

## <a name="evaluate-the-model"></a>Ocena modelu

Metryki dla różnych modeli przeszkolonych są dostępne za pośrednictwem `Metrics` właściwości poszczególnych [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) obiektów. W takim przypadku [metryka R-Kwadrat](https://en.wikipedia.org/wiki/Coefficient_of_determination) jest dostępna i `rSquared`przechowywana w zmiennej .

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

W przypadku sprawdzenia zawartości `rSquared` zmiennej, dane wyjściowe powinny być pięć wartości od 0-1, gdzie bliżej 1 oznacza najlepsze. Korzystając z metryk, takich jak R-Squared, wybierz modele od najlepszego do najgorszego. Następnie wybierz top model do prognozowania lub wykonać dodatkowe operacje z.

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
