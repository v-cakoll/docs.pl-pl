---
title: Wyjaśniono, określane są przewidywania modelu przy użyciu permutacji funkcji znaczenie
description: Zrozumieć znaczenie funkcji modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 1037a1f1c21ef2c9b9a87a070a7d2003c1e76eb4
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307369"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a>Wyjaśniono, określane są przewidywania modelu przy użyciu permutacji funkcji znaczenie

Dowiedz się, jak wyjaśniono w strukturze ML.NET usługi machine learning określane są przewidywania modelu zrozumienie, jakie funkcje wkład prognozy przy użyciu znaczenie funkcji permutacji (PFI).

Modele uczenia maszynowego są często uważane za czarne pola, które pobrać dane wejściowe i generować dane wyjściowe. Kroki pośrednie lub interakcji między funkcje, które mają wpływ na dane wyjściowe rzadko są zrozumiałe. Ponieważ usługi machine learning zostanie wprowadzona inne aspekty codzienności, takich jak opieka zdrowotna, jest priorytetowe znaczenie, aby zrozumieć, dlaczego usługi machine learning model sprawia, że decyzje robi. Na przykład jeśli diagnozować zostaną wprowadzone przez model usługi machine learning, profesjonalistów z branży opieki zdrowotnej muszą mieć możliwość przejrzenia czynniki, które pojawiły się w tworzenie tego diagnozować. Podając odpowiednie Diagnostyka może spowodować, że doskonałe różnica od tego, czy pacjent ma szybkiego odzyskiwania, czy nie. Im wyższy poziom explainability w modelu większą pewnością specjalistów opieki zdrowotnej więc o zaakceptowanie lub odrzucenie decyzje przez model.

Różnych technik przetwarzania są używane do wyjaśnienia modeli, z których jedna jest PFI. PFI to technika używana do wyjaśnienia modeli klasyfikacji i regresji, które są INSPIROWANE przez [firmy Breiman *lasów Random* dokument](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(patrz sekcja 10). Na wysokim poziomie jak działa polega na losowo rekonfiguracja danych jedną funkcję na raz dla całego zestawu danych i obliczanie, zmniejsza ilość Metryka wydajności zainteresowania. Im więcej zmian, niezwykle ważne jest tej funkcji. 

Ponadto przez wyróżnienie najważniejszych funkcji, konstruktorzy modelu skupić się na za pomocą podzestawu bardziej zrozumiały funkcje, które potencjalnie może zmniejszyć hałasu i czasu szkoleń.

## <a name="load-the-data"></a>Ładowanie danych

Funkcje zestawu danych używanego w tym przykładzie są w kolumnach 1 – 12. Celem jest przewidzieć `Price`. 

| Kolumna | Funkcja | Opis 
| --- | --- | --- |
| 1 | CrimeRate | Stawki na mieszkańca przestępstw.
| 2 | ResidentialZones | Rezydentna stref miejskiej
| 3 | CommercialZones | Rezydentna spoza strefy w miejscowości
| 4 | NearWater | Bliskość treści limitu górnego
| 5 | ToxicWasteLevels | Poziomy toksyczności (PPM)
| 6 | AverageRoomNumber | Średnia liczba pokojach w domu
| 7 | HomeAge | Wiek głównej
| 8 | BusinessCenterDistance | Odległość do najbliższej district biznesowych
| 9 | HighwayAccess | Bliskość autostrady
| 10 | TaxRate | Stawka podatku właściwości
| 11 | StudentTeacherRatio | Współczynnik uczniów i nauczycieli
| 12 | PercentPopulationBelowPoverty | Procent populacji życia poniżej ubóstwa
| 13 | Cena | Cena miejsce, w którym

Poniżej przedstawiono przykładowy zestaw danych:

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

Dane w tym przykładzie można modelować przez klasę, takie jak `HousingPriceData`:

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

Załaduj dane do [ `IDataView` ](xref:Microsoft.ML.IDataView).

## <a name="train-the-model"></a>Uczenie modelu

Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej do prognozowania cen domu.

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a>Wyjaśniono modelu przy użyciu znaczenie funkcji permutacji (PFI)

Używane w strukturze ML.NET [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metoda odpowiedniego zadania.

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

Wynik za pomocą [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na zestaw danych szkoleniowych [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) z [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) obiektów. [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) zapewnia wiele uwagi na statystyki zbiorcze, takie jak średnia i odchylenie standardowe [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) liczbą permutacji określony przez `permutationCount` parametru.

Ważność, lub w tym przypadku bezwzględne spadek R-kwadrat metryki obliczana na podstawie [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) następnie może zostać określona od najważniejszych do najmniej ważne.  

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

Drukowanie wartości dla każdej funkcji `featureImportanceMetrics` wygeneruje dane wyjściowe podobne do poniższych. Należy pamiętać, który powinien powinna się pojawić różne wyniki, ponieważ różnią się te wartości na podstawie danych, które posiadają.  

| Funkcja | Zmiany do R-kwadrat |
|:--|:--:|
HighwayAccess       |   -0.042731
StudentTeacherRatio |   -0.012730
BusinessCenterDistance| -0.010491
TaxRate             |   -0.008545
AverageRoomNumber   |   -0.003949
CrimeRate           |   -0.003665
CommercialZones     |   0.002749
HomeAge             |   -0.002426
ResidentialZones    |   -0.002319
NearWater           |   0.000203
PercentPopulationLivingBelowPoverty|    0.000031
ToxicWasteLevels    |   -0.000019

Biorąc przyjrzeć się pięć najważniejszych funkcji dla tego zestawu danych, cena domu prognozowane przez ten model ma wpływ swoją bliskość autostrady, stosunek nauczyciel uczniów szkół w obszarze, odległości między elementami pracy główne centra stawka podatku właściwości i Średnia liczba pokojach w domu.
