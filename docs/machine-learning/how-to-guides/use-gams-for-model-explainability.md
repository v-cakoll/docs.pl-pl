---
title: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
description: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: f7b8b9a3daabb16f59c901911a1f6950ce864fff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689794"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="dde4f-103">Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="dde4f-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="dde4f-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="dde4f-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="dde4f-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="dde4f-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="dde4f-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="dde4f-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="dde4f-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="dde4f-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="dde4f-108">Podczas tworzenia modeli uczenia maszynowego, często nie jest wystarczająco, aby po prostu prognozowania.</span><span class="sxs-lookup"><span data-stu-id="dde4f-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="dde4f-109">Często deweloperom, osobom podejmującym decyzje i te wpływ modele uczenia maszynowego trzeba wiedzieć, jak modele uczenia maszynowego podejmowanie decyzji i funkcji, które przyczyniają się do ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="dde4f-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="dde4f-110">**Uogólnione modele dodatku (GAMs)** są używane wewnętrznie w firmie Microsoft explainability modelu pomagające deweloperom learning maszyny, tworzyć modele o dużej pojemności, które mogą być łatwo interpretowane przez innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="dde4f-110">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="dde4f-111">GAMs są klasy **interpretowanej modeli** będących modeli liniowych, warunki, w którym znajdują się funkcje nieliniowych, o nazwie "kształtu funkcji" jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="dde4f-111">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="dde4f-112">Jako modeli liniowych są interpretowane łatwe, ale ponieważ modele dowiedzieć się więcej funkcji funkcji zamiast pojedynczego wagi, ich modelowania bardziej złożonych relacji niż prosty model liniowy.</span><span class="sxs-lookup"><span data-stu-id="dde4f-112">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="dde4f-113">Wynikowy predykcyjne GAM ma termin intercept, który reprezentuje średni prognozowania nad zestaw szkoleniowy i funkcje kształtu, reprezentującymi odchyleń od średniej prognozy.</span><span class="sxs-lookup"><span data-stu-id="dde4f-113">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="dde4f-114">Funkcje kształtów można kontrolowane przez oka, aby zobaczyć odpowiedź modelu różne wartości funkcji i wizualizowane takich jak poniższy wykres, który jest tworzony na końcu w przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="dde4f-114">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="dde4f-115">Trainer GAM w strukturze ML.NET jest implementowany przy użyciu płytka gradientu wzmocnionego drzewa (na przykład drzewa pnie) aby dowiedzieć się więcej funkcji nonparametric kształt i jest oparta na metody opisanej w [zrozumiałą modele klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou, Caruana i Gehrke.</span><span class="sxs-lookup"><span data-stu-id="dde4f-115">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

![Uogólnionego modele dodatku kształtu funkcji wykresu](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

<span data-ttu-id="dde4f-117">Przykład sposobu uczenia modelu GAM, zbadaj i interpretacji wyników, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="dde4f-117">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
