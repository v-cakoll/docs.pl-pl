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
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="8d5fd-103">Interpretowanie prognoz modelu przy użyciu ważnego funkcji permutacji</span><span class="sxs-lookup"><span data-stu-id="8d5fd-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="8d5fd-104">Korzystając ze znaczenia funkcji permutacji (PFI), dowiedz się, jak interpretować ML.NET prognoz modelu uczenia maszynowego.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="8d5fd-105">PFI daje względny wkład każdej funkcji sprawia, że do przewidywania.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="8d5fd-106">Modele uczenia maszynowego są często traktowane jako czarne pola, które przyjmują dane wejściowe i generują dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-106">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="8d5fd-107">Pośrednie kroki lub interakcje między funkcjami, które wpływają na dane wyjściowe są rzadko rozumiane.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="8d5fd-108">Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego życia, takich jak opieka zdrowotna, niezwykle ważne jest zrozumienie, dlaczego model uczenia maszynowego podejmuje decyzje.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="8d5fd-109">Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, pracownicy służby zdrowia potrzebują sposobu, aby przyjrzeć się czynnikom, które przeszły do tworzenia tej diagnozy.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="8d5fd-110">Zapewnienie właściwej diagnozy może mieć duże znaczenie dla tego, czy pacjent ma szybki powrót do zdrowia, czy nie.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="8d5fd-111">W związku z tym im wyższy poziom explainability w modelu, tym większe zaufanie pracowników służby zdrowia musi zaakceptować lub odrzucić decyzje podjęte przez model.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="8d5fd-112">Do wyjaśnienia modeli stosuje się różne techniki, z których jednym jest PFI.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="8d5fd-113">PFI to technika stosowana do wyjaśniania modeli klasyfikacji i regresji, która jest inspirowana [papierem *Losowych Lasów* Breimana](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (patrz sekcja 10).</span><span class="sxs-lookup"><span data-stu-id="8d5fd-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="8d5fd-114">Na wysokim poziomie, sposób, w jaki to działa jest przez losowo tasowanie danych jedną funkcję na raz dla całego zestawu danych i obliczania, jak bardzo metryka wydajności odsetek zmniejsza.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="8d5fd-115">Im większa zmiana, tym ważniejsza jest ta funkcja.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="8d5fd-116">Ponadto, podkreślając najważniejsze funkcje, konstruktorzy modeli mogą skupić się na użyciu podzbioru bardziej znaczących funkcji, które mogą potencjalnie skrócić hałas i czas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="8d5fd-117">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="8d5fd-117">Load the data</span></span>

<span data-ttu-id="8d5fd-118">Funkcje w zestawie danych używane w tym przykładzie znajdują się w kolumnach 1-12.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="8d5fd-119">Celem jest przewidzenie `Price`.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="8d5fd-120">Kolumna</span><span class="sxs-lookup"><span data-stu-id="8d5fd-120">Column</span></span> | <span data-ttu-id="8d5fd-121">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8d5fd-121">Feature</span></span> | <span data-ttu-id="8d5fd-122">Opis</span><span class="sxs-lookup"><span data-stu-id="8d5fd-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="8d5fd-123">1</span><span class="sxs-lookup"><span data-stu-id="8d5fd-123">1</span></span> | <span data-ttu-id="8d5fd-124">PrzestępczośćRate</span><span class="sxs-lookup"><span data-stu-id="8d5fd-124">CrimeRate</span></span> | <span data-ttu-id="8d5fd-125">Wskaźnik przestępczości na mieszkańca</span><span class="sxs-lookup"><span data-stu-id="8d5fd-125">Per capita crime rate</span></span>
| <span data-ttu-id="8d5fd-126">2</span><span class="sxs-lookup"><span data-stu-id="8d5fd-126">2</span></span> | <span data-ttu-id="8d5fd-127">Strefy mieszkalne</span><span class="sxs-lookup"><span data-stu-id="8d5fd-127">ResidentialZones</span></span> | <span data-ttu-id="8d5fd-128">Strefy mieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="8d5fd-128">Residential zones in town</span></span>
| <span data-ttu-id="8d5fd-129">3</span><span class="sxs-lookup"><span data-stu-id="8d5fd-129">3</span></span> | <span data-ttu-id="8d5fd-130">Strefy handlowe</span><span class="sxs-lookup"><span data-stu-id="8d5fd-130">CommercialZones</span></span> | <span data-ttu-id="8d5fd-131">Strefy niemieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="8d5fd-131">Non-residential zones in town</span></span>
| <span data-ttu-id="8d5fd-132">4</span><span class="sxs-lookup"><span data-stu-id="8d5fd-132">4</span></span> | <span data-ttu-id="8d5fd-133">BliskoWoda</span><span class="sxs-lookup"><span data-stu-id="8d5fd-133">NearWater</span></span> | <span data-ttu-id="8d5fd-134">Bliskość zbiornika wodnego</span><span class="sxs-lookup"><span data-stu-id="8d5fd-134">Proximity to body of water</span></span>
| <span data-ttu-id="8d5fd-135">5</span><span class="sxs-lookup"><span data-stu-id="8d5fd-135">5</span></span> | <span data-ttu-id="8d5fd-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="8d5fd-136">ToxicWasteLevels</span></span> | <span data-ttu-id="8d5fd-137">Poziomy toksyczności (PPM)</span><span class="sxs-lookup"><span data-stu-id="8d5fd-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="8d5fd-138">6</span><span class="sxs-lookup"><span data-stu-id="8d5fd-138">6</span></span> | <span data-ttu-id="8d5fd-139">Średnia liczba pokoi</span><span class="sxs-lookup"><span data-stu-id="8d5fd-139">AverageRoomNumber</span></span> | <span data-ttu-id="8d5fd-140">Średnia liczba pokoi w domu</span><span class="sxs-lookup"><span data-stu-id="8d5fd-140">Average number of rooms in house</span></span>
| <span data-ttu-id="8d5fd-141">7</span><span class="sxs-lookup"><span data-stu-id="8d5fd-141">7</span></span> | <span data-ttu-id="8d5fd-142">Strona domowa</span><span class="sxs-lookup"><span data-stu-id="8d5fd-142">HomeAge</span></span> | <span data-ttu-id="8d5fd-143">Wiek domu</span><span class="sxs-lookup"><span data-stu-id="8d5fd-143">Age of home</span></span>
| <span data-ttu-id="8d5fd-144">8</span><span class="sxs-lookup"><span data-stu-id="8d5fd-144">8</span></span> | <span data-ttu-id="8d5fd-145">BusinessCenterOdległość</span><span class="sxs-lookup"><span data-stu-id="8d5fd-145">BusinessCenterDistance</span></span> | <span data-ttu-id="8d5fd-146">Odległość do najbliższej dzielnicy biznesowej</span><span class="sxs-lookup"><span data-stu-id="8d5fd-146">Distance to nearest business district</span></span>
| <span data-ttu-id="8d5fd-147">9</span><span class="sxs-lookup"><span data-stu-id="8d5fd-147">9</span></span> | <span data-ttu-id="8d5fd-148">Dostęp do autostrady</span><span class="sxs-lookup"><span data-stu-id="8d5fd-148">HighwayAccess</span></span> | <span data-ttu-id="8d5fd-149">Bliskość autostrad</span><span class="sxs-lookup"><span data-stu-id="8d5fd-149">Proximity to highways</span></span>
| <span data-ttu-id="8d5fd-150">10</span><span class="sxs-lookup"><span data-stu-id="8d5fd-150">10</span></span> | <span data-ttu-id="8d5fd-151">Stawka podatkowa</span><span class="sxs-lookup"><span data-stu-id="8d5fd-151">TaxRate</span></span> | <span data-ttu-id="8d5fd-152">Stawka podatku od nieruchomości</span><span class="sxs-lookup"><span data-stu-id="8d5fd-152">Property tax rate</span></span>
| <span data-ttu-id="8d5fd-153">11</span><span class="sxs-lookup"><span data-stu-id="8d5fd-153">11</span></span> | <span data-ttu-id="8d5fd-154">Legitymacja nauczyciela dla uczniów</span><span class="sxs-lookup"><span data-stu-id="8d5fd-154">StudentTeacherRatio</span></span> | <span data-ttu-id="8d5fd-155">Stosunek uczniów do nauczycieli</span><span class="sxs-lookup"><span data-stu-id="8d5fd-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="8d5fd-156">12</span><span class="sxs-lookup"><span data-stu-id="8d5fd-156">12</span></span> | <span data-ttu-id="8d5fd-157">PercentPopulationBelowPoverty (PercentPopulationBelowPoverty)</span><span class="sxs-lookup"><span data-stu-id="8d5fd-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="8d5fd-158">Odsetek ludności żyjącej poniżej ubóstwa</span><span class="sxs-lookup"><span data-stu-id="8d5fd-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="8d5fd-159">13</span><span class="sxs-lookup"><span data-stu-id="8d5fd-159">13</span></span> | <span data-ttu-id="8d5fd-160">Price</span><span class="sxs-lookup"><span data-stu-id="8d5fd-160">Price</span></span> | <span data-ttu-id="8d5fd-161">Cena domu</span><span class="sxs-lookup"><span data-stu-id="8d5fd-161">Price of the home</span></span>

<span data-ttu-id="8d5fd-162">Poniżej przedstawiono przykład zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="8d5fd-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="8d5fd-163">Dane w tym przykładzie mogą być modelowane przez klasę, jak `HousingPriceData` i załadowany do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="8d5fd-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="8d5fd-164">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="8d5fd-164">Train the model</span></span>

<span data-ttu-id="8d5fd-165">Poniższy przykład kodu ilustruje proces szkolenia modelu regresji liniowej do przewidywania cen domów.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="8d5fd-166">Objaśnienie modelu za pomocą znaczenia funkcji permutacji (PFI)</span><span class="sxs-lookup"><span data-stu-id="8d5fd-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="8d5fd-167">W ML.NET [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) użyj metody dla danego zadania.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="8d5fd-168">Wynik korzystania [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) z zestawu danych szkolenia [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) jest obiektów.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="8d5fd-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)zawiera statystyki podsumowujące, takie jak średnie [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) i odchylenie standardowe dla wielu `permutationCount` obserwacji równe liczbie permutacji określonej przez parametr.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="8d5fd-170">Znaczenie lub w tym przypadku bezwzględny spadek średniej metryki [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) r-kwadrat obliczonej przez można następnie zamówić od najważniejszego do najmniej ważnego.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="8d5fd-171">Drukowanie wartości dla każdego `featureImportanceMetrics` z obiektów w będzie generować dane wyjściowe podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="8d5fd-172">Należy pamiętać, że należy oczekiwać, aby zobaczyć różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="8d5fd-173">Funkcja</span><span class="sxs-lookup"><span data-stu-id="8d5fd-173">Feature</span></span> | <span data-ttu-id="8d5fd-174">Zmień na R-Kwadrat</span><span class="sxs-lookup"><span data-stu-id="8d5fd-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="8d5fd-175">Dostęp do autostrady</span><span class="sxs-lookup"><span data-stu-id="8d5fd-175">HighwayAccess</span></span>       |   <span data-ttu-id="8d5fd-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="8d5fd-176">-0.042731</span></span>
<span data-ttu-id="8d5fd-177">Legitymacja nauczyciela dla uczniów</span><span class="sxs-lookup"><span data-stu-id="8d5fd-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="8d5fd-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="8d5fd-178">-0.012730</span></span>
<span data-ttu-id="8d5fd-179">BusinessCenterOdległość</span><span class="sxs-lookup"><span data-stu-id="8d5fd-179">BusinessCenterDistance</span></span>| <span data-ttu-id="8d5fd-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="8d5fd-180">-0.010491</span></span>
<span data-ttu-id="8d5fd-181">Stawka podatkowa</span><span class="sxs-lookup"><span data-stu-id="8d5fd-181">TaxRate</span></span>             |   <span data-ttu-id="8d5fd-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="8d5fd-182">-0.008545</span></span>
<span data-ttu-id="8d5fd-183">Średnia liczba pokoi</span><span class="sxs-lookup"><span data-stu-id="8d5fd-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="8d5fd-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="8d5fd-184">-0.003949</span></span>
<span data-ttu-id="8d5fd-185">PrzestępczośćRate</span><span class="sxs-lookup"><span data-stu-id="8d5fd-185">CrimeRate</span></span>           |   <span data-ttu-id="8d5fd-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="8d5fd-186">-0.003665</span></span>
<span data-ttu-id="8d5fd-187">Strefy handlowe</span><span class="sxs-lookup"><span data-stu-id="8d5fd-187">CommercialZones</span></span>     |   <span data-ttu-id="8d5fd-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="8d5fd-188">0.002749</span></span>
<span data-ttu-id="8d5fd-189">Strona domowa</span><span class="sxs-lookup"><span data-stu-id="8d5fd-189">HomeAge</span></span>             |   <span data-ttu-id="8d5fd-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="8d5fd-190">-0.002426</span></span>
<span data-ttu-id="8d5fd-191">Strefy mieszkalne</span><span class="sxs-lookup"><span data-stu-id="8d5fd-191">ResidentialZones</span></span>    |   <span data-ttu-id="8d5fd-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="8d5fd-192">-0.002319</span></span>
<span data-ttu-id="8d5fd-193">BliskoWoda</span><span class="sxs-lookup"><span data-stu-id="8d5fd-193">NearWater</span></span>           |   <span data-ttu-id="8d5fd-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="8d5fd-194">0.000203</span></span>
<span data-ttu-id="8d5fd-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="8d5fd-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="8d5fd-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="8d5fd-196">0.000031</span></span>
<span data-ttu-id="8d5fd-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="8d5fd-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="8d5fd-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="8d5fd-198">-0.000019</span></span>

<span data-ttu-id="8d5fd-199">Patrząc na pięć najważniejszych cech tego zbioru danych, na cenę domu prognozowanego przez ten model ma wpływ bliskość autostrad, stosunek nauczycieli uczniów do szkół w okolicy, bliskość głównych ośrodków zatrudnienia, stawka podatku od nieruchomości i średnia liczba pokoi w domu.</span><span class="sxs-lookup"><span data-stu-id="8d5fd-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
