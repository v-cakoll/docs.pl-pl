---
title: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
description: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 7899c0efb80af178ec4fa8623b0712eb9e438e43
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738893"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="2757a-103">Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="2757a-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

<span data-ttu-id="2757a-104">Podczas tworzenia modeli uczenia maszynowego, często nie jest wystarczająco, aby po prostu prognozowania.</span><span class="sxs-lookup"><span data-stu-id="2757a-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="2757a-105">Często deweloperom, osobom podejmującym decyzje i te wpływ modele uczenia maszynowego trzeba wiedzieć, jak modele uczenia maszynowego podejmowanie decyzji i funkcji, które przyczyniają się do ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="2757a-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="2757a-106">**Uogólnione modele dodatku (GAMs)** są używane wewnętrznie w firmie Microsoft explainability modelu pomagające deweloperom learning maszyny, tworzyć modele o dużej pojemności, które mogą być łatwo interpretowane przez innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="2757a-106">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="2757a-107">GAMs są klasy **interpretowanej modeli** będących modeli liniowych, warunki, w którym znajdują się funkcje nieliniowych, o nazwie "kształtu funkcji" jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2757a-107">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="2757a-108">Jako modeli liniowych są interpretowane łatwe, ale ponieważ modele dowiedzieć się więcej funkcji funkcji zamiast pojedynczego wagi, ich modelowania bardziej złożonych relacji niż prosty model liniowy.</span><span class="sxs-lookup"><span data-stu-id="2757a-108">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="2757a-109">Wynikowy predykcyjne GAM ma termin intercept, który reprezentuje średni prognozowania nad zestaw szkoleniowy i funkcje kształtu, reprezentującymi odchyleń od średniej prognozy.</span><span class="sxs-lookup"><span data-stu-id="2757a-109">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="2757a-110">Funkcje kształtów można kontrolowane przez oka, aby zobaczyć odpowiedź modelu różne wartości funkcji i wizualizowane takich jak poniższy wykres, który jest tworzony na końcu w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="2757a-110">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="2757a-111">Trainer GAM w strukturze ML.NET jest implementowany przy użyciu płytka gradientu wzmocnionego drzewa (na przykład drzewa pnie) aby dowiedzieć się więcej funkcji nonparametric kształt i jest oparta na metody opisanej w [zrozumiałą modele klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou, Caruana i Gehrke.</span><span class="sxs-lookup"><span data-stu-id="2757a-111">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

```csharp
// Train the Generalized Additive Model
var fitPipeline = pipeline.Fit(data);
var gamModel = fitPipeline.LastTransformer.Model;

// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
Console.WriteLine($"Average predicted cost: {intercept:0.00}");

// Get the feature names from the training set
var featureNames = data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Get the index of a variable from the training data
var myFeatureIndex = featureNames.ToList().FindIndex(str => str.Equals("MyFeature"));

// The shape functions represent the deviation from the average prediction as a function of the feature value
// It is represented by a discrete set of bins
// First, get the array of bin upper bounds from the model for this feature
var myFeatureBins = gamModel.GetFeatureBinUpperBounds(myFeatureIndex);
// Then get the array of bin weights; these are the effect size for each bin
var myFeatureWeights = gamModel.GetFeatureWeights(myFeatureIndex);

// Write out the shape function for the feature (see the following figure for what this looks like)
for (int i = 0; i < myFeatureBins.Length; i++)
{
    Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
}
```

![Uogólnionego modele dodatku kształtu funkcji wykresu](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="2757a-113">Przykład sposobu uczenia modelu GAM, zbadaj i interpretacji wyników, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="2757a-113">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>