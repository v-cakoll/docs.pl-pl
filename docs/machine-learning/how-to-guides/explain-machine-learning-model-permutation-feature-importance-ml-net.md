---
title: Interpretowanie modeli ML.NET z funkcją permutacji
description: Zrozumienie znaczenia funkcji modeli ze znaczeniem funkcji permutacji w ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: c1163a41cd2feb0e8785ae9d4c6a71dfbedf3f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092619"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>Interpretowanie prognoz modelu przy użyciu ważnego funkcji permutacji

Korzystając ze znaczenia funkcji permutacji (PFI), dowiedz się, jak interpretować ML.NET prognoz modelu uczenia maszynowego. PFI daje względny wkład każdej funkcji sprawia, że do przewidywania.

Modele uczenia maszynowego są często traktowane jako czarne pola, które przyjmują dane wejściowe i generują dane wyjściowe. Pośrednie kroki lub interakcje między funkcjami, które wpływają na dane wyjściowe są rzadko rozumiane. Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego życia, takich jak opieka zdrowotna, niezwykle ważne jest zrozumienie, dlaczego model uczenia maszynowego podejmuje decyzje. Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, pracownicy służby zdrowia potrzebują sposobu, aby przyjrzeć się czynnikom, które przeszły do tworzenia tej diagnozy. Zapewnienie właściwej diagnozy może mieć duże znaczenie dla tego, czy pacjent ma szybki powrót do zdrowia, czy nie. W związku z tym im wyższy poziom explainability w modelu, tym większe zaufanie pracowników służby zdrowia musi zaakceptować lub odrzucić decyzje podjęte przez model.

Do wyjaśnienia modeli stosuje się różne techniki, z których jednym jest PFI. PFI to technika stosowana do wyjaśniania modeli klasyfikacji i regresji, która jest inspirowana [papierem *Losowych Lasów* Breimana](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (patrz sekcja 10). Na wysokim poziomie, sposób, w jaki to działa jest przez losowo tasowanie danych jedną funkcję na raz dla całego zestawu danych i obliczania, jak bardzo metryka wydajności odsetek zmniejsza. Im większa zmiana, tym ważniejsza jest ta funkcja.

Ponadto, podkreślając najważniejsze funkcje, konstruktorzy modeli mogą skupić się na użyciu podzbioru bardziej znaczących funkcji, które mogą potencjalnie skrócić hałas i czas szkolenia.

## <a name="load-the-data"></a>Ładowanie danych

Funkcje w zestawie danych używane w tym przykładzie znajdują się w kolumnach 1-12. Celem jest przewidzenie `Price`.

| Kolumna | Funkcja | Opis
| --- | --- | --- |
| 1 | PrzestępczośćRate | Wskaźnik przestępczości na mieszkańca
| 2 | Strefy mieszkalne | Strefy mieszkalne w mieście
| 3 | Strefy handlowe | Strefy niemieszkalne w mieście
| 4 | BliskoWoda | Bliskość zbiornika wodnego
| 5 | ToxicWasteLevels | Poziomy toksyczności (PPM)
| 6 | Średnia liczba pokoi | Średnia liczba pokoi w domu
| 7 | Strona domowa | Wiek domu
| 8 | BusinessCenterOdległość | Odległość do najbliższej dzielnicy biznesowej
| 9 | Dostęp do autostrady | Bliskość autostrad
| 10 | Stawka podatkowa | Stawka podatku od nieruchomości
| 11 | Legitymacja nauczyciela dla uczniów | Stosunek uczniów do nauczycieli
| 12 | PercentPopulationBelowPoverty (PercentPopulationBelowPoverty) | Odsetek ludności żyjącej poniżej ubóstwa
| 13 | Price | Cena domu

Poniżej przedstawiono przykład zestawu danych:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Dane w tym przykładzie mogą być modelowane przez klasę, jak `HousingPriceData` i załadowany do [`IDataView`](xref:Microsoft.ML.IDataView).

```csharp
class HousingPriceData
{
    [LoadColumn(0)]
    public float CrimeRate { get; set; }

    [LoadColumn(1)]
    public float ResidentialZones { get; set; }

    [LoadColumn(2)]
    public float CommercialZones { get; set; }

    [LoadColumn(3)]
    public float NearWater { get; set; }

    [LoadColumn(4)]
    public float ToxicWasteLevels { get; set; }

    [LoadColumn(5)]
    public float AverageRoomNumber { get; set; }

    [LoadColumn(6)]
    public float HomeAge { get; set; }

    [LoadColumn(7)]
    public float BusinessCenterDistance { get; set; }

    [LoadColumn(8)]
    public float HighwayAccess { get; set; }

    [LoadColumn(9)]
    public float TaxRate { get; set; }

    [LoadColumn(10)]
    public float StudentTeacherRatio { get; set; }

    [LoadColumn(11)]
    public float PercentPopulationBelowPoverty { get; set; }

    [LoadColumn(12)]
    [ColumnName("Label")]
    public float Price { get; set; }
}
```

## <a name="train-the-model"></a>Uczenie modelu

Poniższy przykład kodu ilustruje proces szkolenia modelu regresji liniowej do przewidywania cen domów.

```csharp
// 1. Get the column name of input features.
string[] featureColumnNames =
    data.Schema
        .Select(column => column.Name)
        .Where(columnName => columnName != "Label").ToArray();

// 2. Define estimator with data pre-processing steps
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", featureColumnNames)
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// 3. Create transformer using the data pre-processing estimator
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// 4. Pre-process the training data
IDataView preprocessedTrainData = dataPrepTransformer.Transform(data);

// 5. Define Stochastic Dual Coordinate Ascent machine learning estimator
var sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// 6. Train machine learning model
var sdcaModel = sdcaEstimator.Fit(preprocessedTrainData);
```

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Objaśnienie modelu za pomocą znaczenia funkcji permutacji (PFI)

W ML.NET [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) użyj metody dla danego zadania.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Wynik korzystania [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) z zestawu danych szkolenia [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) jest obiektów. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)zawiera statystyki podsumowujące, takie jak średnie [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) i odchylenie standardowe dla wielu `permutationCount` obserwacji równe liczbie permutacji określonej przez parametr.

Znaczenie lub w tym przypadku bezwzględny spadek średniej metryki [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) r-kwadrat obliczonej przez można następnie zamówić od najważniejszego do najmniej ważnego.

```csharp
// Order features by importance
var featureImportanceMetrics =
    permutationFeatureImportance
        .Select((metric, index) => new { index, metric.RSquared })
        .OrderByDescending(myFeatures => Math.Abs(myFeatures.RSquared.Mean));

Console.WriteLine("Feature\tPFI");

foreach (var feature in featureImportanceMetrics)
{
    Console.WriteLine($"{featureColumnNames[feature.index],-20}|\t{feature.RSquared.Mean:F6}");
}
```

Drukowanie wartości dla każdego `featureImportanceMetrics` z obiektów w będzie generować dane wyjściowe podobne do poniższych. Należy pamiętać, że należy oczekiwać, aby zobaczyć różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.

| Funkcja | Zmień na R-Kwadrat |
|:--|:--:|
Dostęp do autostrady       |   -0.042731
Legitymacja nauczyciela dla uczniów |   -0.012730
BusinessCenterOdległość| -0.010491
Stawka podatkowa             |   -0.008545
Średnia liczba pokoi   |   -0.003949
PrzestępczośćRate           |   -0.003665
Strefy handlowe     |   0.002749
Strona domowa             |   -0.002426
Strefy mieszkalne    |   -0.002319
BliskoWoda           |   0.000203
PercentPopulationLivingBelowPoverty|    0.000031
ToxicWasteLevels    |   -0.000019

Patrząc na pięć najważniejszych cech tego zbioru danych, na cenę domu prognozowanego przez ten model ma wpływ bliskość autostrad, stosunek nauczycieli uczniów do szkół w okolicy, bliskość głównych ośrodków zatrudnienia, stawka podatku od nieruchomości i średnia liczba pokoi w domu.
