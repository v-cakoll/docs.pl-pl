---
title: Korzystaj z uogólnionych modeli i funkcji kształtu do celów objaśniających model
description: Korzystaj z uogólnionych modeli i funkcji kształtu do wyjaśnienia modelu w ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: c58cf823007196c35da093fab7423c1e40ba1158
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855602"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a><span data-ttu-id="41058-103">Korzystaj z uogólnionych modeli i funkcji kształtu do wyjaśnienia modelu w ML.NET</span><span class="sxs-lookup"><span data-stu-id="41058-103">Use Generalized Additive Models and shape functions for model explainability in ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="41058-104">Ten temat dotyczy ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="41058-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="41058-105">Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="41058-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="41058-106">Ta procedura i powiązana próbka są obecnie używane w programie **ml.NET w wersji 0,10**.</span><span class="sxs-lookup"><span data-stu-id="41058-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="41058-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium programu dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="41058-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="41058-108">Podczas tworzenia modeli uczenia maszynowego często nie wystarczy, aby robić przewidywania.</span><span class="sxs-lookup"><span data-stu-id="41058-108">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="41058-109">Często deweloperzy uczenia maszynowego, osoby podejmujące decyzje i te, których dotyczą modele, muszą zrozumieć, jak modele uczenia maszynowego podejmują decyzje i jakie funkcje przyczyniają się do ich wydajności.</span><span class="sxs-lookup"><span data-stu-id="41058-109">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="41058-110">**Ogólne modele addytywne (GAMs)** są używane wewnętrznie w firmie Microsoft w celu uzyskania wyjaśnień, aby ułatwić deweloperom uczenia maszynowego tworzenie modeli o wysokiej wydajności, które mogą być łatwo interpretowane przez inne osoby.</span><span class="sxs-lookup"><span data-stu-id="41058-110">**Generalized Additive Models (GAMs)** are used internally at Microsoft for model explainability to help machine learning developers create high-capacity models that can be easily interpreted by others.</span></span>

<span data-ttu-id="41058-111">GAMs jest klasą **interpretowanych modeli** , które są modelami liniowymi, gdzie warunki są funkcjami nieliniowymi, nazywanymi "funkcjami kształtu" jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="41058-111">GAMs are a class of **interpretable models** that are linear models where the terms are nonlinear functions, called "shape functions" of a single variable.</span></span> <span data-ttu-id="41058-112">Modele liniowe są łatwo interpretowane, ale ponieważ modele poznają funkcje funkcji zamiast pojedynczej wagi, mogą modelować bardziej złożone relacje niż prosty model liniowy.</span><span class="sxs-lookup"><span data-stu-id="41058-112">As linear models, they are easily interpreted but because the models learn functions of features instead of a single weight, they can model more complex relationships than a simple linear model.</span></span> <span data-ttu-id="41058-113">Wynikająca przewidywalność mapie gam ma termin przechwycenia reprezentujący średnią prognozę dla zestawu szkoleniowego i funkcje kształtu, które reprezentują odchylenia od średniej przewidywania.</span><span class="sxs-lookup"><span data-stu-id="41058-113">The resulting GAM predictor has an intercept term that represents the average prediction over the training set, and shape functions that represent the deviation from the average prediction.</span></span> <span data-ttu-id="41058-114">Funkcje kształtu mogą być sprawdzane przez oczy, aby zobaczyć odpowiedź modelu do różnych wartości funkcji i wizualizować jak Poniższy wykres, który jest tworzony na końcu przykładu kodu.</span><span class="sxs-lookup"><span data-stu-id="41058-114">The shape functions can be inspected by eye to see the response of the model to different values of a feature, and visualized like the following graph that is created at the end of the code example.</span></span> <span data-ttu-id="41058-115">MAPIE gam Trainer w ML.NET jest zaimplementowana przy użyciu wzorów podwyższania poziomu gradientu (na przykład drzewa Stumps), aby poznać funkcje kształtu nieparametrycznego i opiera się na metodzie opisanej w [odniesieniu do modelu klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) przez Lou, Caruana i Gehrke.</span><span class="sxs-lookup"><span data-stu-id="41058-115">The GAM trainer in ML.NET is implemented using shallow gradient boosted trees (for example tree stumps) to learn nonparametric shape functions, and is based on the method described in [Intelligible Models for Classification and Regression](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) by Lou, Caruana, and Gehrke.</span></span>

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

<span data-ttu-id="41058-117">Aby zapoznać się z przykładem sposobu uczenia modelu mapie gam i sprawdzenia i interpretacji wyników, zobacz [repozytorium dotnet/machinelearning w witrynie GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span><span class="sxs-lookup"><span data-stu-id="41058-117">For a sample of how to train a GAM model and inspect and interpret the results, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).</span></span>
