---
title: Wyjaśnij przewidywania modelu przy użyciu ważności funkcji permutacji
description: Zrozumienie znaczenia funkcji dla modeli o ważności funkcji permutacji w ML.NET
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 9617582c79b2278e3a68e7acf84568247b81eca1
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167656"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="f019f-103">Wyjaśnij przewidywania modelu przy użyciu ważności funkcji permutacji</span><span class="sxs-lookup"><span data-stu-id="f019f-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="f019f-104">Dowiedz się, jak wyjaśnić przewidywania modelu uczenia maszynowego ML.NET przez zrozumienie, jakie funkcje muszą być przewidywaniami przy użyciu funkcji permutacji (PFI).</span><span class="sxs-lookup"><span data-stu-id="f019f-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="f019f-105">Modele uczenia maszynowego często są uważane za czarne pola, które pobierają dane wyjściowe i generują wyjście.</span><span class="sxs-lookup"><span data-stu-id="f019f-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="f019f-106">Pośrednie kroki lub interakcje między funkcjami, które mają wpływ na dane wyjściowe są rzadko zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="f019f-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="f019f-107">Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego okresu istnienia, takiego jak opieka zdrowotna, ma największe znaczenie, aby zrozumieć, dlaczego model uczenia maszynowego podejmuje podejmowane decyzje.</span><span class="sxs-lookup"><span data-stu-id="f019f-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="f019f-108">Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, specjaliści ds. opieki zdrowotnej muszą zapoznać się ze wskaźnikami, które zapoznają się w celu rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="f019f-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="f019f-109">Zapewnienie właściwej diagnostyki może być świetnym rozwiązaniem w zakresie tego, czy pacjent ma szybkie odzyskiwanie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="f019f-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="f019f-110">W związku z tym wyższy poziom wyjaśnień w modelu, pracownicy służby zdrowia większego zaufania muszą zaakceptować lub odrzucić decyzje podjęte przez model.</span><span class="sxs-lookup"><span data-stu-id="f019f-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="f019f-111">Różne techniki są używane do wyjaśnienia modeli, z których jeden jest PFI.</span><span class="sxs-lookup"><span data-stu-id="f019f-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="f019f-112">PFI jest techniką używaną do wyjaśnienia modeli klasyfikacji i regresji, które są sponsorowane przez [papier *losowy lasów* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(patrz sekcja 10).</span><span class="sxs-lookup"><span data-stu-id="f019f-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="f019f-113">Na wysokim poziomie, w jaki działa, jest to spowodowane losowo Shuffling danych jedną funkcją w danym czasie dla całego zestawu danych i obliczaniem, ile metryki wydajności zmniejsza się odsetki.</span><span class="sxs-lookup"><span data-stu-id="f019f-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="f019f-114">Im większa zmiana, tym bardziej ważna jest funkcja.</span><span class="sxs-lookup"><span data-stu-id="f019f-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="f019f-115">Ponadto poprzez wyróżnienie najważniejszych funkcji konstruktory modeli mogą skupić się na użyciu podzestawu bardziej znaczących funkcji, które mogą potencjalnie zmniejszyć liczbę szumów i czas uczenia.</span><span class="sxs-lookup"><span data-stu-id="f019f-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="f019f-116">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="f019f-116">Load the data</span></span>

<span data-ttu-id="f019f-117">Funkcje w zestawie danych, które są używane na potrzeby tego przykładu, znajdują się w kolumnach 1-12.</span><span class="sxs-lookup"><span data-stu-id="f019f-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="f019f-118">Celem jest przewidywanie `Price`.</span><span class="sxs-lookup"><span data-stu-id="f019f-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="f019f-119">Kolumna</span><span class="sxs-lookup"><span data-stu-id="f019f-119">Column</span></span> | <span data-ttu-id="f019f-120">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f019f-120">Feature</span></span> | <span data-ttu-id="f019f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="f019f-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="f019f-122">1</span><span class="sxs-lookup"><span data-stu-id="f019f-122">1</span></span> | <span data-ttu-id="f019f-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="f019f-123">CrimeRate</span></span> | <span data-ttu-id="f019f-124">Wskaźnik przestępczości na mieszkańca</span><span class="sxs-lookup"><span data-stu-id="f019f-124">Per capita crime rate</span></span>
| <span data-ttu-id="f019f-125">2</span><span class="sxs-lookup"><span data-stu-id="f019f-125">2</span></span> | <span data-ttu-id="f019f-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="f019f-126">ResidentialZones</span></span> | <span data-ttu-id="f019f-127">Strefy mieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="f019f-127">Residential zones in town</span></span>
| <span data-ttu-id="f019f-128">3</span><span class="sxs-lookup"><span data-stu-id="f019f-128">3</span></span> | <span data-ttu-id="f019f-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="f019f-129">CommercialZones</span></span> | <span data-ttu-id="f019f-130">Strefy niemieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="f019f-130">Non-residential zones in town</span></span>
| <span data-ttu-id="f019f-131">4</span><span class="sxs-lookup"><span data-stu-id="f019f-131">4</span></span> | <span data-ttu-id="f019f-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="f019f-132">NearWater</span></span> | <span data-ttu-id="f019f-133">Bliskość wody</span><span class="sxs-lookup"><span data-stu-id="f019f-133">Proximity to body of water</span></span>
| <span data-ttu-id="f019f-134">5</span><span class="sxs-lookup"><span data-stu-id="f019f-134">5</span></span> | <span data-ttu-id="f019f-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="f019f-135">ToxicWasteLevels</span></span> | <span data-ttu-id="f019f-136">Poziomy toksyczności (PPM)</span><span class="sxs-lookup"><span data-stu-id="f019f-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="f019f-137">6</span><span class="sxs-lookup"><span data-stu-id="f019f-137">6</span></span> | <span data-ttu-id="f019f-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="f019f-138">AverageRoomNumber</span></span> | <span data-ttu-id="f019f-139">Średnia liczba pokojów w domu</span><span class="sxs-lookup"><span data-stu-id="f019f-139">Average number of rooms in house</span></span>
| <span data-ttu-id="f019f-140">7</span><span class="sxs-lookup"><span data-stu-id="f019f-140">7</span></span> | <span data-ttu-id="f019f-141">Strona główna</span><span class="sxs-lookup"><span data-stu-id="f019f-141">HomeAge</span></span> | <span data-ttu-id="f019f-142">Wiek domu</span><span class="sxs-lookup"><span data-stu-id="f019f-142">Age of home</span></span>
| <span data-ttu-id="f019f-143">8</span><span class="sxs-lookup"><span data-stu-id="f019f-143">8</span></span> | <span data-ttu-id="f019f-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="f019f-144">BusinessCenterDistance</span></span> | <span data-ttu-id="f019f-145">Odległość z najbliższym okręgiem biznesowym</span><span class="sxs-lookup"><span data-stu-id="f019f-145">Distance to nearest business district</span></span>
| <span data-ttu-id="f019f-146">9</span><span class="sxs-lookup"><span data-stu-id="f019f-146">9</span></span> | <span data-ttu-id="f019f-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="f019f-147">HighwayAccess</span></span> | <span data-ttu-id="f019f-148">Bliskość autostrad</span><span class="sxs-lookup"><span data-stu-id="f019f-148">Proximity to highways</span></span>
| <span data-ttu-id="f019f-149">10</span><span class="sxs-lookup"><span data-stu-id="f019f-149">10</span></span> | <span data-ttu-id="f019f-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="f019f-150">TaxRate</span></span> | <span data-ttu-id="f019f-151">Stawka podatku własności</span><span class="sxs-lookup"><span data-stu-id="f019f-151">Property tax rate</span></span>
| <span data-ttu-id="f019f-152">11</span><span class="sxs-lookup"><span data-stu-id="f019f-152">11</span></span> | <span data-ttu-id="f019f-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="f019f-153">StudentTeacherRatio</span></span> | <span data-ttu-id="f019f-154">Stosunek uczniów do nauczycieli</span><span class="sxs-lookup"><span data-stu-id="f019f-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="f019f-155">12</span><span class="sxs-lookup"><span data-stu-id="f019f-155">12</span></span> | <span data-ttu-id="f019f-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="f019f-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="f019f-157">Procent populacji zamieszkania poniżej ubóstwa</span><span class="sxs-lookup"><span data-stu-id="f019f-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="f019f-158">13</span><span class="sxs-lookup"><span data-stu-id="f019f-158">13</span></span> | <span data-ttu-id="f019f-159">Cena</span><span class="sxs-lookup"><span data-stu-id="f019f-159">Price</span></span> | <span data-ttu-id="f019f-160">Cena domu</span><span class="sxs-lookup"><span data-stu-id="f019f-160">Price of the home</span></span>

<span data-ttu-id="f019f-161">Poniżej przedstawiono przykład zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="f019f-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="f019f-162">Dane w tym przykładzie można modelować według klasy, takiej jak `HousingPriceData` i załadowanej [`IDataView`](xref:Microsoft.ML.IDataView)do.</span><span class="sxs-lookup"><span data-stu-id="f019f-162">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="f019f-163">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="f019f-163">Train the model</span></span>

<span data-ttu-id="f019f-164">Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej w celu przewidywania cen dla domu.</span><span class="sxs-lookup"><span data-stu-id="f019f-164">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="f019f-165">Wyjaśnij model z ważnością funkcji permutacji (PFI)</span><span class="sxs-lookup"><span data-stu-id="f019f-165">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="f019f-166">W ml.NET Użyj [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metody dla odpowiedniego zadania.</span><span class="sxs-lookup"><span data-stu-id="f019f-166">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="f019f-167">Wynik użycia [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) w zestawie danych szkoleniowych [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) jest [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) obiektem.</span><span class="sxs-lookup"><span data-stu-id="f019f-167">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="f019f-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)zapewnia statystykę podsumowania, na przykład odchylenie średnie i standardowe dla [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) wielu obserwacji równych liczbie permutacji określonych `permutationCount` przez parametr.</span><span class="sxs-lookup"><span data-stu-id="f019f-168">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="f019f-169">Istotność, czyli w tym przypadku średni spadek średniej wartości R-kwadratowej obliczony przez [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) może następnie być uporządkowany od najważniejszych do najmniej istotnych.</span><span class="sxs-lookup"><span data-stu-id="f019f-169">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="f019f-170">Drukowanie wartości dla każdej z funkcji w programie `featureImportanceMetrics` spowoduje wygenerowanie danych wyjściowych podobnych do poniższych.</span><span class="sxs-lookup"><span data-stu-id="f019f-170">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="f019f-171">Należy pamiętać, że powinny być widoczne różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.</span><span class="sxs-lookup"><span data-stu-id="f019f-171">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="f019f-172">Funkcja</span><span class="sxs-lookup"><span data-stu-id="f019f-172">Feature</span></span> | <span data-ttu-id="f019f-173">Zmień na R-kwadratowy</span><span class="sxs-lookup"><span data-stu-id="f019f-173">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="f019f-174">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="f019f-174">HighwayAccess</span></span>       |   <span data-ttu-id="f019f-175">-0,042731</span><span class="sxs-lookup"><span data-stu-id="f019f-175">-0.042731</span></span>
<span data-ttu-id="f019f-176">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="f019f-176">StudentTeacherRatio</span></span> |   <span data-ttu-id="f019f-177">-0,012730</span><span class="sxs-lookup"><span data-stu-id="f019f-177">-0.012730</span></span>
<span data-ttu-id="f019f-178">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="f019f-178">BusinessCenterDistance</span></span>| <span data-ttu-id="f019f-179">-0.010491</span><span class="sxs-lookup"><span data-stu-id="f019f-179">-0.010491</span></span>
<span data-ttu-id="f019f-180">TaxRate</span><span class="sxs-lookup"><span data-stu-id="f019f-180">TaxRate</span></span>             |   <span data-ttu-id="f019f-181">-0.008545</span><span class="sxs-lookup"><span data-stu-id="f019f-181">-0.008545</span></span>
<span data-ttu-id="f019f-182">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="f019f-182">AverageRoomNumber</span></span>   |   <span data-ttu-id="f019f-183">-0,003949</span><span class="sxs-lookup"><span data-stu-id="f019f-183">-0.003949</span></span>
<span data-ttu-id="f019f-184">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="f019f-184">CrimeRate</span></span>           |   <span data-ttu-id="f019f-185">-0,003665</span><span class="sxs-lookup"><span data-stu-id="f019f-185">-0.003665</span></span>
<span data-ttu-id="f019f-186">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="f019f-186">CommercialZones</span></span>     |   <span data-ttu-id="f019f-187">0,002749</span><span class="sxs-lookup"><span data-stu-id="f019f-187">0.002749</span></span>
<span data-ttu-id="f019f-188">Strona główna</span><span class="sxs-lookup"><span data-stu-id="f019f-188">HomeAge</span></span>             |   <span data-ttu-id="f019f-189">-0,002426</span><span class="sxs-lookup"><span data-stu-id="f019f-189">-0.002426</span></span>
<span data-ttu-id="f019f-190">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="f019f-190">ResidentialZones</span></span>    |   <span data-ttu-id="f019f-191">-0,002319</span><span class="sxs-lookup"><span data-stu-id="f019f-191">-0.002319</span></span>
<span data-ttu-id="f019f-192">NearWater</span><span class="sxs-lookup"><span data-stu-id="f019f-192">NearWater</span></span>           |   <span data-ttu-id="f019f-193">0,000203</span><span class="sxs-lookup"><span data-stu-id="f019f-193">0.000203</span></span>
<span data-ttu-id="f019f-194">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="f019f-194">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="f019f-195">0,000031</span><span class="sxs-lookup"><span data-stu-id="f019f-195">0.000031</span></span>
<span data-ttu-id="f019f-196">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="f019f-196">ToxicWasteLevels</span></span>    |   <span data-ttu-id="f019f-197">-0,000019</span><span class="sxs-lookup"><span data-stu-id="f019f-197">-0.000019</span></span>

<span data-ttu-id="f019f-198">Zapoznaj się z pięcioma najważniejszymi funkcjami tego zestawu danych, Cena domu przewidywanego przez ten model ma wpływ na bliskość autostrad, współczynnika nauczycieli uczniów w terenie, bliskość głównych centrów zatrudnienia, stawka podatku własności i Średnia liczba pokojów w domu.</span><span class="sxs-lookup"><span data-stu-id="f019f-198">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
