---
title: Interpretowanie modeli ML.NET z ważnością funkcji permutacji
description: Zrozumienie znaczenia funkcji dla modeli o ważności funkcji permutacji w ML.NET
ms.date: 01/30/2020
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: ed0d6736f1f2e988d96a397cad77a7fc743489da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174234"
---
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a>Interpretowanie prognoz modelu przy użyciu ważności funkcji permutacji

Korzystając z ważności funkcji permutacji (PFI), Dowiedz się, jak interpretować przewidywania modelu ML.NET Machine Learning. PFI daje względny wkład każda funkcja do prognozowania.

Modele uczenia maszynowego często są traktowane jako nieprzezroczyste pola, które pobierają dane wejściowe i generują dane wyjściowe. Pośrednie kroki lub interakcje między funkcjami, które mają wpływ na dane wyjściowe są rzadko zrozumiałe. Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego okresu istnienia, takiego jak opieka zdrowotna, ma największe znaczenie, aby zrozumieć, dlaczego model uczenia maszynowego podejmuje podejmowane decyzje. Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, specjaliści ds. opieki zdrowotnej muszą zapoznać się ze wskaźnikami, które zapoznają się w celu rozwiązania tego problemu. Zapewnienie właściwej diagnostyki może być świetnym rozwiązaniem w zakresie tego, czy pacjent ma szybkie odzyskiwanie, czy nie. W związku z tym wyższy poziom wyjaśnień w modelu, pracownicy służby zdrowia większego zaufania muszą zaakceptować lub odrzucić decyzje podjęte przez model.

Różne techniki są używane do wyjaśnienia modeli, z których jeden jest PFI. PFI jest techniką używaną do wyjaśnienia modeli klasyfikacji i regresji, które są [sponsorowane przez papier *losowy lasów* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (patrz sekcja 10). Na wysokim poziomie, w jaki działa, jest to spowodowane losowo Shuffling danych jedną funkcją w danym czasie dla całego zestawu danych i obliczaniem, ile metryki wydajności zmniejsza się odsetki. Im większa zmiana, tym bardziej ważna jest funkcja.

Ponadto poprzez wyróżnienie najważniejszych funkcji konstruktory modeli mogą skupić się na użyciu podzestawu bardziej znaczących funkcji, które mogą potencjalnie zmniejszyć liczbę szumów i czas uczenia.

## <a name="load-the-data"></a>Ładowanie danych

Funkcje w zestawie danych, które są używane na potrzeby tego przykładu, znajdują się w kolumnach 1-12. Celem jest przewidywanie `Price` .

| Kolumna | Cecha | Opis
| --- | --- | --- |
| 1 | CrimeRate | Wskaźnik przestępczości na mieszkańca
| 2 | ResidentialZones | Strefy mieszkalne w mieście
| 3 | CommercialZones | Strefy niemieszkalne w mieście
| 4 | NearWater | Bliskość wody
| 5 | ToxicWasteLevels | Poziomy toksyczności (PPM)
| 6 | AverageRoomNumber | Średnia liczba pokojów w domu
| 7 | Strona główna | Wiek domu
| 8 | BusinessCenterDistance | Odległość z najbliższym okręgiem biznesowym
| 9 | HighwayAccess | Bliskość autostrad
| 10 | TaxRate | Stawka podatku własności
| 11 | StudentTeacherRatio | Stosunek uczniów do nauczycieli
| 12 | PercentPopulationBelowPoverty | Procent populacji zamieszkania poniżej ubóstwa
| 13 | Cena | Cena domu

Poniżej przedstawiono przykład zestawu danych:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Dane w tym przykładzie można modelować według klasy, takiej jak `HousingPriceData` i załadowanej do [`IDataView`](xref:Microsoft.ML.IDataView) .

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

## <a name="train-the-model"></a>Szkolenie modelu

Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej w celu przewidywania cen dla domu.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Wyjaśnij model z ważnością funkcji permutacji (PFI)

W ML.NET Użyj [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metody dla odpowiedniego zadania.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Wynik użycia [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) w zestawie danych szkoleniowych jest [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) obiektem. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)zapewnia statystykę podsumowania, na przykład odchylenie średnie i standardowe dla wielu obserwacji [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) równych liczbie permutacji określonych przez `permutationCount` parametr.

Istotność, czyli w tym przypadku średni spadek średniej wartości R-kwadratowej obliczony przez [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) może następnie być uporządkowany od najważniejszych do najmniej istotnych.

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

Drukowanie wartości dla każdej z funkcji w programie `featureImportanceMetrics` spowoduje wygenerowanie danych wyjściowych podobnych do poniższych. Należy pamiętać, że powinny być widoczne różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.

| Cecha | Zmień na R-kwadratowy |
|:--|:--:|
HighwayAccess       |   -0,042731
StudentTeacherRatio |   -0,012730
BusinessCenterDistance| -0,010491
TaxRate             |   -0,008545
AverageRoomNumber   |   -0,003949
CrimeRate           |   -0,003665
CommercialZones     |   0,002749
Strona główna             |   -0,002426
ResidentialZones    |   -0,002319
NearWater           |   0,000203
PercentPopulationLivingBelowPoverty|    0,000031
ToxicWasteLevels    |   -0,000019

Biorąc pod uwagę pięć najważniejszych funkcji dla tego zestawu danych, Cena domu przewidywana przez ten model jest zależna od bliskości autostrad, liczby szkół uczniów w terenie, bliskości głównych centrów zatrudnienia, stawki podatku własności i średniej liczby pokojów w domu.
