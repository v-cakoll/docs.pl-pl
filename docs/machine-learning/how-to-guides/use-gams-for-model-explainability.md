---
title: Interpretowanie modeli ML.NET z ogólnymi modelami addytywne
description: Korzystaj z uogólnionych modeli i funkcji kształtu do interpretowania modeli w ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092476"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a><span data-ttu-id="ee2f4-103">Korzystaj z uogólnionych modeli i funkcji kształtu do interpretowania modeli w ML.NET</span><span class="sxs-lookup"><span data-stu-id="ee2f4-103">Use Generalized Additive Models and shape functions for model interpretability in ML.NET</span></span>

<span data-ttu-id="ee2f4-104">Podczas tworzenia modeli uczenia maszynowego często nie wystarczy, aby robić przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="ee2f4-105">Często deweloperzy uczenia maszynowego, osoby podejmujące decyzje i te, których dotyczą modele, muszą zrozumieć, jak modele uczenia maszynowego podejmują decyzje i jakie funkcje przyczyniają się do ich wydajności.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="ee2f4-106">**Ogólne modele addytywne (GAMs)** są używane wewnętrznie w firmie Microsoft w celu interpretowania modeli, aby ułatwić deweloperom uczenia maszynowego tworzenie modeli o wysokiej wydajności, które mogą być łatwo interpretowane przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model interpretability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="ee2f4-107">GAMs jest klasą **interpretowanych modeli** , które są modelami liniowymi, gdzie warunki są funkcjami nieliniowymi, nazywanymi "funkcjami kształtu" jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="ee2f4-108">Modele liniowe są łatwo interpretowane, ale ponieważ modele poznają funkcje funkcji zamiast pojedynczej wagi, mogą modelować bardziej złożone relacje niż prosty model liniowy.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="ee2f4-109">Wynikająca przewidywalność mapie gam ma termin przechwycenia reprezentujący średnią prognozę dla zestawu szkoleniowego i funkcje kształtu, które reprezentują odchylenia od średniej przewidywania.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="ee2f4-110">Funkcje kształtu mogą być sprawdzane przez oczy, aby zobaczyć odpowiedź modelu do różnych wartości funkcji i wizualizować jak Poniższy wykres, który jest tworzony na końcu przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="ee2f4-111">MAPIE gam Trainer w ML.NET jest zaimplementowana przy użyciu wzorów podwyższania poziomu gradientu (na przykład drzewa Stumps), aby poznać funkcje kształtu nieparametrycznego i opiera się na metodzie opisanej w [odniesieniu do modelu klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) przez Lou, Caruana i Gehrke.</span><span class="sxs-lookup"><span data-stu-id="ee2f4-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the column names from the training set
var columnNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = columnNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetBinEffects(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Wykres funkcji kształtów ogólnych modeli addytywne](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="ee2f4-113">Aby zapoznać się z przykładem sposobu uczenia modelu mapie gam i sprawdzenia i interpretacji wyników, zobacz [repozytorium dotnet/machinelearning w witrynie GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="ee2f4-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
