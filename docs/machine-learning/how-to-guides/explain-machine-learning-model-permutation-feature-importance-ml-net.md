---
title: Wyjaśniono, określane są przewidywania modelu przy użyciu permutacji funkcji znaczenie
description: Zrozumieć znaczenie funkcji modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
ms.date: 05/02/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to
ms.openlocfilehash: 51ef4b55b1518381881e57d83fd43f8ec7f786c6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645065"
---
# <a name="explain-model-predictions-using-permutation-feature-importance"></a><span data-ttu-id="6c4c3-103">Wyjaśniono, określane są przewidywania modelu przy użyciu permutacji funkcji znaczenie</span><span class="sxs-lookup"><span data-stu-id="6c4c3-103">Explain model predictions using Permutation Feature Importance</span></span>

<span data-ttu-id="6c4c3-104">Dowiedz się, jak wyjaśniono w strukturze ML.NET usługi machine learning określane są przewidywania modelu zrozumienie, jakie funkcje wkład prognozy przy użyciu znaczenie funkcji permutacji (PFI).</span><span class="sxs-lookup"><span data-stu-id="6c4c3-104">Learn how to explain ML.NET machine learning model predictions by understanding the contribution features have to predictions using Permutation Feature Importance (PFI).</span></span>

<span data-ttu-id="6c4c3-105">Modele uczenia maszynowego są często uważane za czarne pola, które pobrać dane wejściowe i generować dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-105">Machine learning models are often thought of as black boxes that take inputs and generate an output.</span></span> <span data-ttu-id="6c4c3-106">Kroki pośrednie lub interakcji między funkcje, które mają wpływ na dane wyjściowe rzadko są zrozumiałe.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-106">The intermediate steps or interactions among the features that influence the output are rarely understood.</span></span> <span data-ttu-id="6c4c3-107">Ponieważ usługi machine learning zostanie wprowadzona inne aspekty codzienności, takich jak opieka zdrowotna, jest priorytetowe znaczenie, aby zrozumieć, dlaczego usługi machine learning model sprawia, że decyzje robi.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-107">As machine learning is introduced into more aspects of everyday life such as healthcare, it's of utmost importance to understand why a machine learning model makes the decisions it does.</span></span> <span data-ttu-id="6c4c3-108">Na przykład jeśli diagnozować zostaną wprowadzone przez model usługi machine learning, profesjonalistów z branży opieki zdrowotnej muszą mieć możliwość przejrzenia czynniki, które pojawiły się w tworzenie tego diagnozować.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-108">For example, if diagnoses are made by a machine learning model, healthcare professionals need a way to look into the factors that went into making that diagnoses.</span></span> <span data-ttu-id="6c4c3-109">Podając odpowiednie Diagnostyka może spowodować, że doskonałe różnica od tego, czy pacjent ma szybkiego odzyskiwania, czy nie.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-109">Providing the right diagnosis could make a great difference on whether a patient has a speedy recovery or not.</span></span> <span data-ttu-id="6c4c3-110">Im wyższy poziom explainability w modelu większą pewnością specjalistów opieki zdrowotnej więc o zaakceptowanie lub odrzucenie decyzje przez model.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-110">Therefore the higher the level of explainability in a model, the greater confidence healthcare professionals have to accept or reject the decisions made by the model.</span></span>

<span data-ttu-id="6c4c3-111">Różnych technik przetwarzania są używane do wyjaśnienia modeli, z których jedna jest PFI.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-111">Various techniques are used to explain models, one of which is PFI.</span></span> <span data-ttu-id="6c4c3-112">PFI to technika używana do wyjaśnienia modeli klasyfikacji i regresji, które są INSPIROWANE przez [firmy Breiman *lasów Random* dokument](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(patrz sekcja 10).</span><span class="sxs-lookup"><span data-stu-id="6c4c3-112">PFI is a technique used to explain classification and regression models that is inspired by [Breiman's *Random Forests* paper](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf)(see section 10).</span></span> <span data-ttu-id="6c4c3-113">Na wysokim poziomie jak działa polega na losowo rekonfiguracja danych jedną funkcję na raz dla całego zestawu danych i obliczanie, zmniejsza ilość Metryka wydajności zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-113">At a high level, the way it works is by randomly shuffling data one feature at a time for the entire dataset and calculating how much the performance metric of interest decreases.</span></span> <span data-ttu-id="6c4c3-114">Im więcej zmian, niezwykle ważne jest tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-114">The larger the change, the more important that feature is.</span></span> 

<span data-ttu-id="6c4c3-115">Ponadto przez wyróżnienie najważniejszych funkcji, konstruktorzy modelu skupić się na za pomocą podzestawu bardziej zrozumiały funkcje, które potencjalnie może zmniejszyć hałasu i czasu szkoleń.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-115">Additionally, by highlighting the most important features, model builders can focus on using a subset of more meaningful features which can potentially reduce noise and training time.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6c4c3-116">Ładowanie danych</span><span class="sxs-lookup"><span data-stu-id="6c4c3-116">Load the data</span></span>

<span data-ttu-id="6c4c3-117">Funkcje zestawu danych używanego w tym przykładzie są w kolumnach 1 – 12.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-117">The features in the dataset being used for this sample are in columns 1-12.</span></span> <span data-ttu-id="6c4c3-118">Celem jest przewidzieć `Price`.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-118">The goal is to predict `Price`.</span></span> 

| <span data-ttu-id="6c4c3-119">Kolumna</span><span class="sxs-lookup"><span data-stu-id="6c4c3-119">Column</span></span> | <span data-ttu-id="6c4c3-120">Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c4c3-120">Feature</span></span> | <span data-ttu-id="6c4c3-121">Opis</span><span class="sxs-lookup"><span data-stu-id="6c4c3-121">Description</span></span> 
| --- | --- | --- |
| <span data-ttu-id="6c4c3-122">1</span><span class="sxs-lookup"><span data-stu-id="6c4c3-122">1</span></span> | <span data-ttu-id="6c4c3-123">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="6c4c3-123">CrimeRate</span></span> | <span data-ttu-id="6c4c3-124">Stawki na mieszkańca przestępstw.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-124">Per capita crime rate</span></span>
| <span data-ttu-id="6c4c3-125">2</span><span class="sxs-lookup"><span data-stu-id="6c4c3-125">2</span></span> | <span data-ttu-id="6c4c3-126">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="6c4c3-126">ResidentialZones</span></span> | <span data-ttu-id="6c4c3-127">Rezydentna stref miejskiej</span><span class="sxs-lookup"><span data-stu-id="6c4c3-127">Residential zones in town</span></span>
| <span data-ttu-id="6c4c3-128">3</span><span class="sxs-lookup"><span data-stu-id="6c4c3-128">3</span></span> | <span data-ttu-id="6c4c3-129">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="6c4c3-129">CommercialZones</span></span> | <span data-ttu-id="6c4c3-130">Rezydentna spoza strefy w miejscowości</span><span class="sxs-lookup"><span data-stu-id="6c4c3-130">Non-residential zones in town</span></span>
| <span data-ttu-id="6c4c3-131">4</span><span class="sxs-lookup"><span data-stu-id="6c4c3-131">4</span></span> | <span data-ttu-id="6c4c3-132">NearWater</span><span class="sxs-lookup"><span data-stu-id="6c4c3-132">NearWater</span></span> | <span data-ttu-id="6c4c3-133">Bliskość treści limitu górnego</span><span class="sxs-lookup"><span data-stu-id="6c4c3-133">Proximity to body of water</span></span>
| <span data-ttu-id="6c4c3-134">5</span><span class="sxs-lookup"><span data-stu-id="6c4c3-134">5</span></span> | <span data-ttu-id="6c4c3-135">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="6c4c3-135">ToxicWasteLevels</span></span> | <span data-ttu-id="6c4c3-136">Poziomy toksyczności (PPM)</span><span class="sxs-lookup"><span data-stu-id="6c4c3-136">Toxicity levels (PPM)</span></span>
| <span data-ttu-id="6c4c3-137">6</span><span class="sxs-lookup"><span data-stu-id="6c4c3-137">6</span></span> | <span data-ttu-id="6c4c3-138">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="6c4c3-138">AverageRoomNumber</span></span> | <span data-ttu-id="6c4c3-139">Średnia liczba pokojach w domu</span><span class="sxs-lookup"><span data-stu-id="6c4c3-139">Average number of rooms in house</span></span>
| <span data-ttu-id="6c4c3-140">7</span><span class="sxs-lookup"><span data-stu-id="6c4c3-140">7</span></span> | <span data-ttu-id="6c4c3-141">HomeAge</span><span class="sxs-lookup"><span data-stu-id="6c4c3-141">HomeAge</span></span> | <span data-ttu-id="6c4c3-142">Wiek głównej</span><span class="sxs-lookup"><span data-stu-id="6c4c3-142">Age of home</span></span>
| <span data-ttu-id="6c4c3-143">8</span><span class="sxs-lookup"><span data-stu-id="6c4c3-143">8</span></span> | <span data-ttu-id="6c4c3-144">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="6c4c3-144">BusinessCenterDistance</span></span> | <span data-ttu-id="6c4c3-145">Odległość do najbliższej district biznesowych</span><span class="sxs-lookup"><span data-stu-id="6c4c3-145">Distance to nearest business district</span></span>
| <span data-ttu-id="6c4c3-146">9</span><span class="sxs-lookup"><span data-stu-id="6c4c3-146">9</span></span> | <span data-ttu-id="6c4c3-147">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="6c4c3-147">HighwayAccess</span></span> | <span data-ttu-id="6c4c3-148">Bliskość autostrady</span><span class="sxs-lookup"><span data-stu-id="6c4c3-148">Proximity to highways</span></span>
| <span data-ttu-id="6c4c3-149">10</span><span class="sxs-lookup"><span data-stu-id="6c4c3-149">10</span></span> | <span data-ttu-id="6c4c3-150">TaxRate</span><span class="sxs-lookup"><span data-stu-id="6c4c3-150">TaxRate</span></span> | <span data-ttu-id="6c4c3-151">Stawka podatku właściwości</span><span class="sxs-lookup"><span data-stu-id="6c4c3-151">Property tax rate</span></span>
| <span data-ttu-id="6c4c3-152">11</span><span class="sxs-lookup"><span data-stu-id="6c4c3-152">11</span></span> | <span data-ttu-id="6c4c3-153">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="6c4c3-153">StudentTeacherRatio</span></span> | <span data-ttu-id="6c4c3-154">Współczynnik uczniów i nauczycieli</span><span class="sxs-lookup"><span data-stu-id="6c4c3-154">Ratio of students to teachers</span></span>
| <span data-ttu-id="6c4c3-155">12</span><span class="sxs-lookup"><span data-stu-id="6c4c3-155">12</span></span> | <span data-ttu-id="6c4c3-156">PercentPopulationBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="6c4c3-156">PercentPopulationBelowPoverty</span></span> | <span data-ttu-id="6c4c3-157">Procent populacji życia poniżej ubóstwa</span><span class="sxs-lookup"><span data-stu-id="6c4c3-157">Percent of population living below poverty</span></span>
| <span data-ttu-id="6c4c3-158">13</span><span class="sxs-lookup"><span data-stu-id="6c4c3-158">13</span></span> | <span data-ttu-id="6c4c3-159">Cena</span><span class="sxs-lookup"><span data-stu-id="6c4c3-159">Price</span></span> | <span data-ttu-id="6c4c3-160">Cena miejsce, w którym</span><span class="sxs-lookup"><span data-stu-id="6c4c3-160">Price of the home</span></span>

<span data-ttu-id="6c4c3-161">Poniżej przedstawiono przykładowy zestaw danych:</span><span class="sxs-lookup"><span data-stu-id="6c4c3-161">A sample of the dataset is shown below:</span></span>

```text
1,24,13,1,0.59,3,96,11,23,608,14,13,32
4,80,18,1,0.37,5,14,7,4,346,19,13,41
2,98,16,1,0.25,10,5,1,8,689,13,36,12
```

<span data-ttu-id="6c4c3-162">Dane w tym przykładzie można modelować przez klasę, takie jak `HousingPriceData`:</span><span class="sxs-lookup"><span data-stu-id="6c4c3-162">The data in this sample can be modeled by a class like `HousingPriceData`:</span></span>

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

<span data-ttu-id="6c4c3-163">Załaduj dane do [ `IDataView` ](xref:Microsoft.ML.IDataView).</span><span class="sxs-lookup"><span data-stu-id="6c4c3-163">Load the data into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

## <a name="train-the-model"></a><span data-ttu-id="6c4c3-164">Uczenie modelu</span><span class="sxs-lookup"><span data-stu-id="6c4c3-164">Train the model</span></span>

<span data-ttu-id="6c4c3-165">Poniższy przykład kodu ilustruje proces uczenia modelu regresji liniowej do prognozowania cen domu.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-165">The code sample below illustrates the process of training a linear regression model to predict house prices.</span></span>

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

## <a name="explain-the-model-with-permutation-feature-importance-pfi"></a><span data-ttu-id="6c4c3-166">Wyjaśniono modelu przy użyciu znaczenie funkcji permutacji (PFI)</span><span class="sxs-lookup"><span data-stu-id="6c4c3-166">Explain the model with Permutation Feature Importance (PFI)</span></span>

<span data-ttu-id="6c4c3-167">Używane w strukturze ML.NET [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) metoda odpowiedniego zadania.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-167">In ML.NET use the [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) method for your respective task.</span></span>

```csharp
ImmutableArray<RegressionMetricsStatistics> permutationFeatureImportance = 
    mlContext
        .Regression
        .PermutationFeatureImportance(sdcaModel, preprocessedTrainData, permutationCount:3);
```

<span data-ttu-id="6c4c3-168">Wynik za pomocą [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) na zestaw danych szkoleniowych [ `ImmutableArray` ](xref:System.Collections.Immutable.ImmutableArray) z [ `RegressionMetricsStatistics` ](xref:Microsoft.ML.Data.RegressionMetricsStatistics) obiektów.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-168">The result of using [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) on the training dataset is an [`ImmutableArray`](xref:System.Collections.Immutable.ImmutableArray) of [`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) objects.</span></span> <span data-ttu-id="6c4c3-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) zapewnia wiele uwagi na statystyki zbiorcze, takie jak średnia i odchylenie standardowe [ `RegressionMetrics` ](xref:Microsoft.ML.Data.RegressionMetrics) liczbą permutacji określony przez `permutationCount` parametru.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-169">[`RegressionMetricsStatistics`](xref:Microsoft.ML.Data.RegressionMetricsStatistics) provides summary statistics like mean and standard deviation for multiple observations of [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) equal to the number of permutations specified by the `permutationCount` parameter.</span></span>

<span data-ttu-id="6c4c3-170">Ważność, lub w tym przypadku bezwzględne spadek R-kwadrat metryki obliczana na podstawie [ `PermutationFeatureImportance` ](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) następnie może zostać określona od najważniejszych do najmniej ważne.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-170">The importance, or in this case, the absolute average decrease in R-squared metric calculated by [`PermutationFeatureImportance`](xref:Microsoft.ML.PermutationFeatureImportanceExtensions) can then be ordered from most important to least important.</span></span>  

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

<span data-ttu-id="6c4c3-171">Drukowanie wartości dla każdej funkcji `featureImportanceMetrics` wygeneruje dane wyjściowe podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-171">Printing the values for each of the features in `featureImportanceMetrics` would generate output similar to that below.</span></span> <span data-ttu-id="6c4c3-172">Należy pamiętać, który powinien powinna się pojawić różne wyniki, ponieważ różnią się te wartości na podstawie danych, które posiadają.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-172">Keep in mind that you should expect to see different results because these values vary based on the data that they are given.</span></span>  

| <span data-ttu-id="6c4c3-173">Funkcja</span><span class="sxs-lookup"><span data-stu-id="6c4c3-173">Feature</span></span> | <span data-ttu-id="6c4c3-174">Zmiany do R-kwadrat</span><span class="sxs-lookup"><span data-stu-id="6c4c3-174">Change to R-Squared</span></span> |
|:--|:--:|
<span data-ttu-id="6c4c3-175">HighwayAccess</span><span class="sxs-lookup"><span data-stu-id="6c4c3-175">HighwayAccess</span></span>       |   <span data-ttu-id="6c4c3-176">-0.042731</span><span class="sxs-lookup"><span data-stu-id="6c4c3-176">-0.042731</span></span>
<span data-ttu-id="6c4c3-177">StudentTeacherRatio</span><span class="sxs-lookup"><span data-stu-id="6c4c3-177">StudentTeacherRatio</span></span> |   <span data-ttu-id="6c4c3-178">-0.012730</span><span class="sxs-lookup"><span data-stu-id="6c4c3-178">-0.012730</span></span>
<span data-ttu-id="6c4c3-179">BusinessCenterDistance</span><span class="sxs-lookup"><span data-stu-id="6c4c3-179">BusinessCenterDistance</span></span>| <span data-ttu-id="6c4c3-180">-0.010491</span><span class="sxs-lookup"><span data-stu-id="6c4c3-180">-0.010491</span></span>
<span data-ttu-id="6c4c3-181">TaxRate</span><span class="sxs-lookup"><span data-stu-id="6c4c3-181">TaxRate</span></span>             |   <span data-ttu-id="6c4c3-182">-0.008545</span><span class="sxs-lookup"><span data-stu-id="6c4c3-182">-0.008545</span></span>
<span data-ttu-id="6c4c3-183">AverageRoomNumber</span><span class="sxs-lookup"><span data-stu-id="6c4c3-183">AverageRoomNumber</span></span>   |   <span data-ttu-id="6c4c3-184">-0.003949</span><span class="sxs-lookup"><span data-stu-id="6c4c3-184">-0.003949</span></span>
<span data-ttu-id="6c4c3-185">CrimeRate</span><span class="sxs-lookup"><span data-stu-id="6c4c3-185">CrimeRate</span></span>           |   <span data-ttu-id="6c4c3-186">-0.003665</span><span class="sxs-lookup"><span data-stu-id="6c4c3-186">-0.003665</span></span>
<span data-ttu-id="6c4c3-187">CommercialZones</span><span class="sxs-lookup"><span data-stu-id="6c4c3-187">CommercialZones</span></span>     |   <span data-ttu-id="6c4c3-188">0.002749</span><span class="sxs-lookup"><span data-stu-id="6c4c3-188">0.002749</span></span>
<span data-ttu-id="6c4c3-189">HomeAge</span><span class="sxs-lookup"><span data-stu-id="6c4c3-189">HomeAge</span></span>             |   <span data-ttu-id="6c4c3-190">-0.002426</span><span class="sxs-lookup"><span data-stu-id="6c4c3-190">-0.002426</span></span>
<span data-ttu-id="6c4c3-191">ResidentialZones</span><span class="sxs-lookup"><span data-stu-id="6c4c3-191">ResidentialZones</span></span>    |   <span data-ttu-id="6c4c3-192">-0.002319</span><span class="sxs-lookup"><span data-stu-id="6c4c3-192">-0.002319</span></span>
<span data-ttu-id="6c4c3-193">NearWater</span><span class="sxs-lookup"><span data-stu-id="6c4c3-193">NearWater</span></span>           |   <span data-ttu-id="6c4c3-194">0.000203</span><span class="sxs-lookup"><span data-stu-id="6c4c3-194">0.000203</span></span>
<span data-ttu-id="6c4c3-195">PercentPopulationLivingBelowPoverty</span><span class="sxs-lookup"><span data-stu-id="6c4c3-195">PercentPopulationLivingBelowPoverty</span></span>|    <span data-ttu-id="6c4c3-196">0.000031</span><span class="sxs-lookup"><span data-stu-id="6c4c3-196">0.000031</span></span>
<span data-ttu-id="6c4c3-197">ToxicWasteLevels</span><span class="sxs-lookup"><span data-stu-id="6c4c3-197">ToxicWasteLevels</span></span>    |   <span data-ttu-id="6c4c3-198">-0.000019</span><span class="sxs-lookup"><span data-stu-id="6c4c3-198">-0.000019</span></span>

<span data-ttu-id="6c4c3-199">Przeglądając pięć najważniejszych funkcji dla tego zestawu danych, a cena domu prognozowane przez ten model ma wpływ swoją bliskość autostrady, stosunek nauczyciel uczniów szkół w obszarze, odległości między elementami pracy główne centra stawka podatku właściwości i Średnia liczba pokojach w domu.</span><span class="sxs-lookup"><span data-stu-id="6c4c3-199">Taking a look at the the five most important features for this dataset, the price of a house predicted by this model is influenced by its proximity to highways, student teacher ratio of schools in the area, proximity to major employment centers, property tax rate and average number of rooms in the home.</span></span>
