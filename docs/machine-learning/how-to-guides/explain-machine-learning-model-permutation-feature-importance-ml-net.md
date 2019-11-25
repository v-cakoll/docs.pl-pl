---
title: Wyjaśnij przewidywania modelu przy użyciu ważności funkcji permutacji
description: Zrozumienie znaczenia funkcji dla modeli o ważności funkcji permutacji w ML.NET
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 4bad8b0ed17a34ba290bf9c00d65cc3f000a2acf
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976687"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="635a0-103">Wyjaśnij przewidywania modelu przy użyciu ważności funkcji permutacji</span><span class="sxs-lookup"><span data-stu-id="635a0-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="635a0-104">Dowiedz się, jak wyjaśnić przewidywania modelu uczenia maszynowego ML.NET przez zrozumienie, jakie funkcje muszą być przewidywaniami przy użyciu funkcji permutacji (PFI).</span><span class="sxs-lookup"><span data-stu-id="635a0-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="635a0-105">Modele uczenia maszynowego często są uważane za czarne pola, które pobierają dane wyjściowe i generują wyjście.</span><span class="sxs-lookup"><span data-stu-id="635a0-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="635a0-106">Pośrednie kroki lub interakcje między funkcjami, które mają wpływ na dane wyjściowe są rzadko zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="635a0-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="635a0-107">Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego okresu istnienia, takiego jak opieka zdrowotna, ma największe znaczenie, aby zrozumieć, dlaczego model uczenia maszynowego podejmuje podejmowane decyzje.</span><span class="sxs-lookup"><span data-stu-id="635a0-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="635a0-108">Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, specjaliści ds. opieki zdrowotnej muszą zapoznać się ze wskaźnikami, które zapoznają się w celu rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="635a0-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="635a0-109">Zapewnienie właściwej diagnostyki może być świetnym rozwiązaniem w zakresie tego, czy pacjent ma szybkie odzyskiwanie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="635a0-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="635a0-110">W związku z tym wyższy poziom wyjaśnień w modelu, pracownicy służby zdrowia większego zaufania muszą zaakceptować lub odrzucić decyzje podjęte przez model.</span><span class="sxs-lookup"><span data-stu-id="635a0-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="635a0-111">Różne techniki są używane do wyjaśnienia modeli, z których jeden jest PFI.</span><span class="sxs-lookup"><span data-stu-id="635a0-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="635a0-112">PFI jest techniką używaną do wyjaśnienia modeli klasyfikacji i regresji, które są [sponsorowane przez papier *losowy lasów* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (patrz sekcja 10).</span><span class="sxs-lookup"><span data-stu-id="635a0-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="635a0-113">Na wysokim poziomie, w jaki działa, jest to spowodowane losowo Shuffling danych jedną funkcją w danym czasie dla całego zestawu danych i obliczaniem, ile metryki wydajności zmniejsza się odsetki.</span><span class="sxs-lookup"><span data-stu-id="635a0-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="635a0-114">Im większa zmiana, tym bardziej ważna jest funkcja.</span><span class="sxs-lookup"><span data-stu-id="635a0-114">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="635a0-115">Ponadto poprzez wyróżnienie najważniejszych funkcji konstruktory modeli mogą skupić się na użyciu podzestawu bardziej znaczących funkcji, które mogą potencjalnie zmniejszyć liczbę szumów i czas uczenia.</span><span class="sxs-lookup"><span data-stu-id="635a0-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="635a0-116">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="635a0-116">Load the data</span></span>

<span data-ttu-id="635a0-117">Funkcje w zestawie danych, które są używane na potrzeby tego przykładu, znajdują się w kolumnach 1-12.</span><span class="sxs-lookup"><span data-stu-id="635a0-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="635a0-118">Celem jest przewidywanie `Price`.</span><span class="sxs-lookup"><span data-stu-id="635a0-118">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="635a0-119">Kolumna</span><span class="sxs-lookup"><span data-stu-id="635a0-119">Column</span></span> | <span data-ttu-id="635a0-120">Funkcja</span><span class="sxs-lookup"><span data-stu-id="635a0-120">Feature</span></span> | <span data-ttu-id="635a0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="635a0-121">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="635a0-122">1</span><span class="sxs-lookup"><span data-stu-id="635a0-122">1</span></span> | <span data-ttu-id="635a0-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="635a0-123">CrimeRate</span></span> | <span data-ttu-id="635a0-124">Wskaźnik przestępczości na mieszkańca</span><span class="sxs-lookup"><span data-stu-id="635a0-124">Per capita crime rate</span></span>
| <span data-ttu-id="635a0-125">2</span><span class="sxs-lookup"><span data-stu-id="635a0-125">2</span></span> | <span data-ttu-id="635a0-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="635a0-126">ResidentialZones</span></span> | <span data-ttu-id="635a0-127">Strefy mieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="635a0-127">Residential zones in town</span></span>
| <span data-ttu-id="635a0-128">3</span><span class="sxs-lookup"><span data-stu-id="635a0-128">3</span></span> | <span data-ttu-id="635a0-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="635a0-129">CommercialZones</span></span> | <span data-ttu-id="635a0-130">Strefy niemieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="635a0-130">Non-residential zones in town</span></span>
| <span data-ttu-id="635a0-131">4</span><span class="sxs-lookup"><span data-stu-id="635a0-131">4</span></span> | <span data-ttu-id="635a0-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="635a0-132">NearWater</span></span> | <span data-ttu-id="635a0-133">Bliskość wody</span><span class="sxs-lookup"><span data-stu-id="635a0-133">Proximity to body of water</span></span>
| <span data-ttu-id="635a0-134">5</span><span class="sxs-lookup"><span data-stu-id="635a0-134">5</span></span> | <span data-ttu-id="635a0-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="635a0-135">ToxicWasteLevels</span></span> | <span data-ttu-id="635a0-136">Poziomy toksyczności (PPM)</span><span class="sxs-lookup"><span data-stu-id="635a0-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="635a0-137">6</span><span class="sxs-lookup"><span data-stu-id="635a0-137">6</span></span> | <span data-ttu-id="635a0-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="635a0-138">AverageRoomNumber</span></span> | <span data-ttu-id="635a0-139">Średnia liczba pokojów w domu</span><span class="sxs-lookup"><span data-stu-id="635a0-139">Average number of rooms in house</span></span>
| <span data-ttu-id="635a0-140">7</span><span class="sxs-lookup"><span data-stu-id="635a0-140">7</span></span> | <span data-ttu-id="635a0-141">Strona główna</span><span class="sxs-lookup"><span data-stu-id="635a0-141">HomeAge</span></span> | <span data-ttu-id="635a0-142">Wiek domu</span><span class="sxs-lookup"><span data-stu-id="635a0-142">Age of home</span></span>
| <span data-ttu-id="635a0-143">8</span><span class="sxs-lookup"><span data-stu-id="635a0-143">8</span></span> | <span data-ttu-id="635a0-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="635a0-144">BusinessCenterDistance</span></span> | <span data-ttu-id="635a0-145">Odległość z najbliższym okręgiem biznesowym</span><span class="sxs-lookup"><span data-stu-id="635a0-145">Distance to nearest business district</span></span>
| <span data-ttu-id="635a0-146">9</span><span class="sxs-lookup"><span data-stu-id="635a0-146">9</span></span> | <span data-ttu-id="635a0-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="635a0-147">HighwayAccess</span></span> | <span data-ttu-id="635a0-148">Bliskość autostrad</span><span class="sxs-lookup"><span data-stu-id="635a0-148">Proximity to highways</span></span>
| <span data-ttu-id="635a0-149">10</span><span class="sxs-lookup"><span data-stu-id="635a0-149">10</span></span> | <span data-ttu-id="635a0-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="635a0-150">TaxRate</span></span> | <span data-ttu-id="635a0-151">Stawka podatku własności</span><span class="sxs-lookup"><span data-stu-id="635a0-151">Property tax rate</span></span>
| <span data-ttu-id="635a0-152">11</span><span class="sxs-lookup"><span data-stu-id="635a0-152">11</span></span> | <span data-ttu-id="635a0-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="635a0-153">StudentTeacherRatio</span></span> | <span data-ttu-id="635a0-154">Stosunek uczniów do nauczycieli</span><span class="sxs-lookup"><span data-stu-id="635a0-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="635a0-155">12</span><span class="sxs-lookup"><span data-stu-id="635a0-155">12</span></span> | <span data-ttu-id="635a0-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="635a0-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="635a0-157">Procent populacji zamieszkania poniżej ubóstwa</span><span class="sxs-lookup"><span data-stu-id="635a0-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="635a0-158">13</span><span class="sxs-lookup"><span data-stu-id="635a0-158">13</span></span> | <span data-ttu-id="635a0-159">Koszt</span><span class="sxs-lookup"><span data-stu-id="635a0-159">Price</span></span> | <span data-ttu-id="635a0-160">Cena domu</span><span class="sxs-lookup"><span data-stu-id="635a0-160">Price of the home</span></span>

<span data-ttu-id="635a0-161">Poniżej przedstawiono przykład zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="635a0-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="635a0-162">Dane w tym przykładzie mogą być modelowane przez klasę, taką jak `HousingPriceData` i ładowane do [`IDataView`](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="635a0-162">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="635a0-163">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="635a0-163">Train the model</span></span>

<span data-ttu-id="635a0-164">Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej w celu przewidywania cen dla domu.</span><span class="sxs-lookup"><span data-stu-id="635a0-164">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="635a0-165">Wyjaśnij model z ważnością funkcji permutacji (PFI)</span><span class="sxs-lookup"><span data-stu-id="635a0-165">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="635a0-166">W ML.NET Użyj metody [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) dla odpowiedniego zadania.</span><span class="sxs-lookup"><span data-stu-id="635a0-166">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="635a0-167">Wynik używania [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) w zestawie danych szkoleniowych jest [`ImmutableArray`em](xref:System.Collections.Immutable.ImmutableArray) obiektów [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) .</span><span class="sxs-lookup"><span data-stu-id="635a0-167">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="635a0-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) zapewnia statystyki podsumowania, takie jak średnia i odchylenie standardowe dla wielu obserwacji [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) równe liczbie permutacji określonych przez `permutationCount` parametr.</span><span class="sxs-lookup"><span data-stu-id="635a0-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="635a0-169">Istotność, czyli w tym przypadku średni spadek średniej wartości R-kwadratowej obliczony przez [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) może być uporządkowany od najważniejszych do najmniej istotnych.</span><span class="sxs-lookup"><span data-stu-id="635a0-169">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="635a0-170">Drukowanie wartości dla każdej z funkcji w `featureImportanceMetrics` generuje dane wyjściowe podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="635a0-170">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="635a0-171">Należy pamiętać, że powinny być widoczne różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.</span><span class="sxs-lookup"><span data-stu-id="635a0-171">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="635a0-172">Funkcja</span><span class="sxs-lookup"><span data-stu-id="635a0-172">Feature</span></span> | <span data-ttu-id="635a0-173">Zmień na R-kwadratowy</span><span class="sxs-lookup"><span data-stu-id="635a0-173">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="635a0-174">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="635a0-174">HighwayAccess</span></span>       |   <span data-ttu-id="635a0-175">-0,042731</span><span class="sxs-lookup"><span data-stu-id="635a0-175">-0.042731</span></span>
<span data-ttu-id="635a0-176">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="635a0-176">StudentTeacherRatio</span></span> |   <span data-ttu-id="635a0-177">-0,012730</span><span class="sxs-lookup"><span data-stu-id="635a0-177">-0.012730</span></span>
<span data-ttu-id="635a0-178">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="635a0-178">BusinessCenterDistance</span></span>| <span data-ttu-id="635a0-179">-0,010491</span><span class="sxs-lookup"><span data-stu-id="635a0-179">-0.010491</span></span>
<span data-ttu-id="635a0-180">TaxRate</span><span class="sxs-lookup"><span data-stu-id="635a0-180">TaxRate</span></span>             |   <span data-ttu-id="635a0-181">-0,008545</span><span class="sxs-lookup"><span data-stu-id="635a0-181">-0.008545</span></span>
<span data-ttu-id="635a0-182">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="635a0-182">AverageRoomNumber</span></span>   |   <span data-ttu-id="635a0-183">-0,003949</span><span class="sxs-lookup"><span data-stu-id="635a0-183">-0.003949</span></span>
<span data-ttu-id="635a0-184">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="635a0-184">CrimeRate</span></span>           |   <span data-ttu-id="635a0-185">-0,003665</span><span class="sxs-lookup"><span data-stu-id="635a0-185">-0.003665</span></span>
<span data-ttu-id="635a0-186">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="635a0-186">CommercialZones</span></span>     |   <span data-ttu-id="635a0-187">0,002749</span><span class="sxs-lookup"><span data-stu-id="635a0-187">0.002749</span></span>
<span data-ttu-id="635a0-188">Strona główna</span><span class="sxs-lookup"><span data-stu-id="635a0-188">HomeAge</span></span>             |   <span data-ttu-id="635a0-189">-0,002426</span><span class="sxs-lookup"><span data-stu-id="635a0-189">-0.002426</span></span>
<span data-ttu-id="635a0-190">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="635a0-190">ResidentialZones</span></span>    |   <span data-ttu-id="635a0-191">-0,002319</span><span class="sxs-lookup"><span data-stu-id="635a0-191">-0.002319</span></span>
<span data-ttu-id="635a0-192">NearWater</span><span class="sxs-lookup"><span data-stu-id="635a0-192">NearWater</span></span>           |   <span data-ttu-id="635a0-193">0,000203</span><span class="sxs-lookup"><span data-stu-id="635a0-193">0.000203</span></span>
<span data-ttu-id="635a0-194">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="635a0-194">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="635a0-195">0,000031</span><span class="sxs-lookup"><span data-stu-id="635a0-195">0.000031</span></span>
<span data-ttu-id="635a0-196">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="635a0-196">ToxicWasteLevels</span></span>    |   <span data-ttu-id="635a0-197">-0,000019</span><span class="sxs-lookup"><span data-stu-id="635a0-197">-0.000019</span></span>

<span data-ttu-id="635a0-198">Zapoznaj się z pięcioma najważniejszymi funkcjami tego zestawu danych, Cena domu przewidywanego przez ten model ma wpływ na bliskość autostrad, współczynnika nauczycieli uczniów w terenie, bliskość głównych centrów zatrudnienia, stawka podatku własności i Średnia liczba pokojów w domu.</span><span class="sxs-lookup"><span data-stu-id="635a0-198">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
