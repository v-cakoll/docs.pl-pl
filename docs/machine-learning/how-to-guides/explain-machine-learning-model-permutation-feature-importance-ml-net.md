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
# <a name="interpret-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="88ab6-103">Interpretowanie prognoz modelu przy użyciu ważności funkcji permutacji</span><span class="sxs-lookup"><span data-stu-id="88ab6-103">Interpret model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="88ab6-104">Korzystając z ważności funkcji permutacji (PFI), Dowiedz się, jak interpretować przewidywania modelu ML.NET Machine Learning.</span><span class="sxs-lookup"><span data-stu-id="88ab6-104">Using Permutation Feature Importance (PFI), learn how to interpret ML.NET machine learning model predictions.</span></span> <span data-ttu-id="88ab6-105">PFI daje względny wkład każda funkcja do prognozowania.</span><span class="sxs-lookup"><span data-stu-id="88ab6-105">PFI gives the relative contribution each feature makes to a prediction.</span></span>

<span data-ttu-id="88ab6-106">Modele uczenia maszynowego często są traktowane jako nieprzezroczyste pola, które pobierają dane wejściowe i generują dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="88ab6-106">Machine learning models are often thought of as opaque boxes that take inputs and generate an output.</span></span> <span data-ttu-id="88ab6-107">Pośrednie kroki lub interakcje między funkcjami, które mają wpływ na dane wyjściowe są rzadko zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="88ab6-107">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="88ab6-108">Ponieważ uczenie maszynowe jest wprowadzane do większej liczby aspektów codziennego okresu istnienia, takiego jak opieka zdrowotna, ma największe znaczenie, aby zrozumieć, dlaczego model uczenia maszynowego podejmuje podejmowane decyzje.</span><span class="sxs-lookup"><span data-stu-id="88ab6-108">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="88ab6-109">Na przykład jeśli diagnozy są dokonywane przez model uczenia maszynowego, specjaliści ds. opieki zdrowotnej muszą zapoznać się ze wskaźnikami, które zapoznają się w celu rozwiązania tego problemu.</span><span class="sxs-lookup"><span data-stu-id="88ab6-109">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="88ab6-110">Zapewnienie właściwej diagnostyki może być świetnym rozwiązaniem w zakresie tego, czy pacjent ma szybkie odzyskiwanie, czy nie.</span><span class="sxs-lookup"><span data-stu-id="88ab6-110">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="88ab6-111">W związku z tym wyższy poziom wyjaśnień w modelu, pracownicy służby zdrowia większego zaufania muszą zaakceptować lub odrzucić decyzje podjęte przez model.</span><span class="sxs-lookup"><span data-stu-id="88ab6-111">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="88ab6-112">Różne techniki są używane do wyjaśnienia modeli, z których jeden jest PFI.</span><span class="sxs-lookup"><span data-stu-id="88ab6-112">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="88ab6-113">PFI jest techniką używaną do wyjaśnienia modeli klasyfikacji i regresji, które są [sponsorowane przez papier *losowy lasów* Breiman](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (patrz sekcja 10).</span><span class="sxs-lookup"><span data-stu-id="88ab6-113">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf) (see section 10).</span></span> <span data-ttu-id="88ab6-114">Na wysokim poziomie, w jaki działa, jest to spowodowane losowo Shuffling danych jedną funkcją w danym czasie dla całego zestawu danych i obliczaniem, ile metryki wydajności zmniejsza się odsetki.</span><span class="sxs-lookup"><span data-stu-id="88ab6-114">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="88ab6-115">Im większa zmiana, tym bardziej ważna jest funkcja.</span><span class="sxs-lookup"><span data-stu-id="88ab6-115">The larger the change, the more important that feature is.</span></span>

<span data-ttu-id="88ab6-116">Ponadto poprzez wyróżnienie najważniejszych funkcji konstruktory modeli mogą skupić się na użyciu podzestawu bardziej znaczących funkcji, które mogą potencjalnie zmniejszyć liczbę szumów i czas uczenia.</span><span class="sxs-lookup"><span data-stu-id="88ab6-116">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="88ab6-117">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="88ab6-117">Load the data</span></span>

<span data-ttu-id="88ab6-118">Funkcje w zestawie danych, które są używane na potrzeby tego przykładu, znajdują się w kolumnach 1-12.</span><span class="sxs-lookup"><span data-stu-id="88ab6-118">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="88ab6-119">Celem jest przewidywanie `Price` .</span><span class="sxs-lookup"><span data-stu-id="88ab6-119">The goal is to predict `Price`.</span></span>

| <span data-ttu-id="88ab6-120">Kolumna</span><span class="sxs-lookup"><span data-stu-id="88ab6-120">Column</span></span> | <span data-ttu-id="88ab6-121">Cecha</span><span class="sxs-lookup"><span data-stu-id="88ab6-121">Feature</span></span> | <span data-ttu-id="88ab6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="88ab6-122">Description</span></span>
| --- | --- | --- |
| <span data-ttu-id="88ab6-123">1</span><span class="sxs-lookup"><span data-stu-id="88ab6-123">1</span></span> | <span data-ttu-id="88ab6-124">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="88ab6-124">CrimeRate</span></span> | <span data-ttu-id="88ab6-125">Wskaźnik przestępczości na mieszkańca</span><span class="sxs-lookup"><span data-stu-id="88ab6-125">Per capita crime rate</span></span>
| <span data-ttu-id="88ab6-126">2</span><span class="sxs-lookup"><span data-stu-id="88ab6-126">2</span></span> | <span data-ttu-id="88ab6-127">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="88ab6-127">ResidentialZones</span></span> | <span data-ttu-id="88ab6-128">Strefy mieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="88ab6-128">Residential zones in town</span></span>
| <span data-ttu-id="88ab6-129">3</span><span class="sxs-lookup"><span data-stu-id="88ab6-129">3</span></span> | <span data-ttu-id="88ab6-130">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="88ab6-130">CommercialZones</span></span> | <span data-ttu-id="88ab6-131">Strefy niemieszkalne w mieście</span><span class="sxs-lookup"><span data-stu-id="88ab6-131">Non-residential zones in town</span></span>
| <span data-ttu-id="88ab6-132">4</span><span class="sxs-lookup"><span data-stu-id="88ab6-132">4</span></span> | <span data-ttu-id="88ab6-133">NearWater</span><span class="sxs-lookup"><span data-stu-id="88ab6-133">NearWater</span></span> | <span data-ttu-id="88ab6-134">Bliskość wody</span><span class="sxs-lookup"><span data-stu-id="88ab6-134">Proximity to body of water</span></span>
| <span data-ttu-id="88ab6-135">5</span><span class="sxs-lookup"><span data-stu-id="88ab6-135">5</span></span> | <span data-ttu-id="88ab6-136">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="88ab6-136">ToxicWasteLevels</span></span> | <span data-ttu-id="88ab6-137">Poziomy toksyczności (PPM)</span><span class="sxs-lookup"><span data-stu-id="88ab6-137">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="88ab6-138">6</span><span class="sxs-lookup"><span data-stu-id="88ab6-138">6</span></span> | <span data-ttu-id="88ab6-139">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="88ab6-139">AverageRoomNumber</span></span> | <span data-ttu-id="88ab6-140">Średnia liczba pokojów w domu</span><span class="sxs-lookup"><span data-stu-id="88ab6-140">Average number of rooms in house</span></span>
| <span data-ttu-id="88ab6-141">7</span><span class="sxs-lookup"><span data-stu-id="88ab6-141">7</span></span> | <span data-ttu-id="88ab6-142">Strona główna</span><span class="sxs-lookup"><span data-stu-id="88ab6-142">HomeAge</span></span> | <span data-ttu-id="88ab6-143">Wiek domu</span><span class="sxs-lookup"><span data-stu-id="88ab6-143">Age of home</span></span>
| <span data-ttu-id="88ab6-144">8</span><span class="sxs-lookup"><span data-stu-id="88ab6-144">8</span></span> | <span data-ttu-id="88ab6-145">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="88ab6-145">BusinessCenterDistance</span></span> | <span data-ttu-id="88ab6-146">Odległość z najbliższym okręgiem biznesowym</span><span class="sxs-lookup"><span data-stu-id="88ab6-146">Distance to nearest business district</span></span>
| <span data-ttu-id="88ab6-147">9</span><span class="sxs-lookup"><span data-stu-id="88ab6-147">9</span></span> | <span data-ttu-id="88ab6-148">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="88ab6-148">HighwayAccess</span></span> | <span data-ttu-id="88ab6-149">Bliskość autostrad</span><span class="sxs-lookup"><span data-stu-id="88ab6-149">Proximity to highways</span></span>
| <span data-ttu-id="88ab6-150">10</span><span class="sxs-lookup"><span data-stu-id="88ab6-150">10</span></span> | <span data-ttu-id="88ab6-151">TaxRate</span><span class="sxs-lookup"><span data-stu-id="88ab6-151">TaxRate</span></span> | <span data-ttu-id="88ab6-152">Stawka podatku własności</span><span class="sxs-lookup"><span data-stu-id="88ab6-152">Property tax rate</span></span>
| <span data-ttu-id="88ab6-153">11</span><span class="sxs-lookup"><span data-stu-id="88ab6-153">11</span></span> | <span data-ttu-id="88ab6-154">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="88ab6-154">StudentTeacherRatio</span></span> | <span data-ttu-id="88ab6-155">Stosunek uczniów do nauczycieli</span><span class="sxs-lookup"><span data-stu-id="88ab6-155">Ratio of students to teachers</span></span>
| <span data-ttu-id="88ab6-156">12</span><span class="sxs-lookup"><span data-stu-id="88ab6-156">12</span></span> | <span data-ttu-id="88ab6-157">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="88ab6-157">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="88ab6-158">Procent populacji zamieszkania poniżej ubóstwa</span><span class="sxs-lookup"><span data-stu-id="88ab6-158">Percent of population living below poverty</span></span>
| <span data-ttu-id="88ab6-159">13</span><span class="sxs-lookup"><span data-stu-id="88ab6-159">13</span></span> | <span data-ttu-id="88ab6-160">Cena</span><span class="sxs-lookup"><span data-stu-id="88ab6-160">Price</span></span> | <span data-ttu-id="88ab6-161">Cena domu</span><span class="sxs-lookup"><span data-stu-id="88ab6-161">Price of the home</span></span>

<span data-ttu-id="88ab6-162">Poniżej przedstawiono przykład zestawu danych:</span><span class="sxs-lookup"><span data-stu-id="88ab6-162">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="88ab6-163">Dane w tym przykładzie można modelować według klasy, takiej jak `HousingPriceData` i załadowanej do [`IDataView`](xref:Microsoft.ML.IDataView) .</span><span class="sxs-lookup"><span data-stu-id="88ab6-163">The data in this sample can be modeled by a class like `HousingPriceData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

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

## <a name="train-the-model"></a><span data-ttu-id="88ab6-164">Szkolenie modelu</span><span class="sxs-lookup"><span data-stu-id="88ab6-164">Train the model</span></span>

<span data-ttu-id="88ab6-165">Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej w celu przewidywania cen dla domu.</span><span class="sxs-lookup"><span data-stu-id="88ab6-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="88ab6-166">Wyjaśnij model z ważnością funkcji permutacji (PFI)</span><span class="sxs-lookup"><span data-stu-id="88ab6-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="88ab6-167">W ML.NET Użyj [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metody dla odpowiedniego zadania.</span><span class="sxs-lookup"><span data-stu-id="88ab6-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance =
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="88ab6-168">Wynik użycia [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) w zestawie danych szkoleniowych jest [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) obiektem.</span><span class="sxs-lookup"><span data-stu-id="88ab6-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="88ab6-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics)zapewnia statystykę podsumowania, na przykład odchylenie średnie i standardowe dla wielu obserwacji [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) równych liczbie permutacji określonych przez `permutationCount` parametr.</span><span class="sxs-lookup"><span data-stu-id="88ab6-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="88ab6-170">Istotność, czyli w tym przypadku średni spadek średniej wartości R-kwadratowej obliczony przez [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) może następnie być uporządkowany od najważniejszych do najmniej istotnych.</span><span class="sxs-lookup"><span data-stu-id="88ab6-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>

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

<span data-ttu-id="88ab6-171">Drukowanie wartości dla każdej z funkcji w programie `featureImportanceMetrics` spowoduje wygenerowanie danych wyjściowych podobnych do poniższych.</span><span class="sxs-lookup"><span data-stu-id="88ab6-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="88ab6-172">Należy pamiętać, że powinny być widoczne różne wyniki, ponieważ te wartości różnią się w zależności od danych, które są podane.</span><span class="sxs-lookup"><span data-stu-id="88ab6-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>

| <span data-ttu-id="88ab6-173">Cecha</span><span class="sxs-lookup"><span data-stu-id="88ab6-173">Feature</span></span> | <span data-ttu-id="88ab6-174">Zmień na R-kwadratowy</span><span class="sxs-lookup"><span data-stu-id="88ab6-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="88ab6-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="88ab6-175">HighwayAccess</span></span>       |   <span data-ttu-id="88ab6-176">-0,042731</span><span class="sxs-lookup"><span data-stu-id="88ab6-176">-0.042731</span></span>
<span data-ttu-id="88ab6-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="88ab6-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="88ab6-178">-0,012730</span><span class="sxs-lookup"><span data-stu-id="88ab6-178">-0.012730</span></span>
<span data-ttu-id="88ab6-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="88ab6-179">BusinessCenterDistance</span></span>| <span data-ttu-id="88ab6-180">-0,010491</span><span class="sxs-lookup"><span data-stu-id="88ab6-180">-0.010491</span></span>
<span data-ttu-id="88ab6-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="88ab6-181">TaxRate</span></span>             |   <span data-ttu-id="88ab6-182">-0,008545</span><span class="sxs-lookup"><span data-stu-id="88ab6-182">-0.008545</span></span>
<span data-ttu-id="88ab6-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="88ab6-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="88ab6-184">-0,003949</span><span class="sxs-lookup"><span data-stu-id="88ab6-184">-0.003949</span></span>
<span data-ttu-id="88ab6-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="88ab6-185">CrimeRate</span></span>           |   <span data-ttu-id="88ab6-186">-0,003665</span><span class="sxs-lookup"><span data-stu-id="88ab6-186">-0.003665</span></span>
<span data-ttu-id="88ab6-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="88ab6-187">CommercialZones</span></span>     |   <span data-ttu-id="88ab6-188">0,002749</span><span class="sxs-lookup"><span data-stu-id="88ab6-188">0.002749</span></span>
<span data-ttu-id="88ab6-189">Strona główna</span><span class="sxs-lookup"><span data-stu-id="88ab6-189">HomeAge</span></span>             |   <span data-ttu-id="88ab6-190">-0,002426</span><span class="sxs-lookup"><span data-stu-id="88ab6-190">-0.002426</span></span>
<span data-ttu-id="88ab6-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="88ab6-191">ResidentialZones</span></span>    |   <span data-ttu-id="88ab6-192">-0,002319</span><span class="sxs-lookup"><span data-stu-id="88ab6-192">-0.002319</span></span>
<span data-ttu-id="88ab6-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="88ab6-193">NearWater</span></span>           |   <span data-ttu-id="88ab6-194">0,000203</span><span class="sxs-lookup"><span data-stu-id="88ab6-194">0.000203</span></span>
<span data-ttu-id="88ab6-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="88ab6-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="88ab6-196">0,000031</span><span class="sxs-lookup"><span data-stu-id="88ab6-196">0.000031</span></span>
<span data-ttu-id="88ab6-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="88ab6-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="88ab6-198">-0,000019</span><span class="sxs-lookup"><span data-stu-id="88ab6-198">-0.000019</span></span>

<span data-ttu-id="88ab6-199">Biorąc pod uwagę pięć najważniejszych funkcji dla tego zestawu danych, Cena domu przewidywana przez ten model jest zależna od bliskości autostrad, liczby szkół uczniów w terenie, bliskości głównych centrów zatrudnienia, stawki podatku własności i średniej liczby pokojów w domu.</span><span class="sxs-lookup"><span data-stu-id="88ab6-199">Taking a look at the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
