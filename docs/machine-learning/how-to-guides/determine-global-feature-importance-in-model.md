---
title: Ustalenia funkcji znaczenie modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
description: Zrozumieć znaczenie funkcji modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 4b93e085dbb99e7f6f5a0a839b863aad1c69c7ba
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155460"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a><span data-ttu-id="c1e1b-103">Ustalenia funkcji znaczenie modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="c1e1b-103">Determine the feature importance of models with Permutation Feature Importance in ML.NET</span></span>

<span data-ttu-id="c1e1b-104">Podczas tworzenia modeli uczenia maszynowego, często nie jest wystarczająco, aby po prostu prognozowania.</span><span class="sxs-lookup"><span data-stu-id="c1e1b-104">When creating machine learning models, it is often not enough to simply make predictions.</span></span> <span data-ttu-id="c1e1b-105">Często deweloperom, osobom podejmującym decyzje i te wpływ modele uczenia maszynowego trzeba wiedzieć, jak modele uczenia maszynowego podejmowanie decyzji i funkcji, które przyczyniają się do ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="c1e1b-105">Often, machine learning developers, decision makers, and those affected by the models need to understand how machine learning models make decisions and which features contribute to their performance.</span></span> <span data-ttu-id="c1e1b-106">`Permutation Feature Importance` (PFI) jest narzędziem explainability modelu, która jest używana wewnętrznie w firmie Microsoft pomagające deweloperom learning maszyny lepiej zrozumieć znaczenie funkcji modeli.</span><span class="sxs-lookup"><span data-stu-id="c1e1b-106">`Permutation Feature Importance` (PFI) is a model explainability tool that is used internally at Microsoft to help machine learning developers better understand the feature importance of models.</span></span>

<span data-ttu-id="c1e1b-107">PFI to technika, aby określić **znaczenie globalnych funkcji** uczonego modelu uczenia maszynowego, motywowane Breiman w [papier "Random lasów", sekcji 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span><span class="sxs-lookup"><span data-stu-id="c1e1b-107">PFI is a technique to determine **global feature importance** in a trained machine learning model, motivated by Breiman in the ["Random Forests" paper, section 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf).</span></span> <span data-ttu-id="c1e1b-108">PFI mierzy znaczenie funkcji, zadając pytania, "jaki wpływ na podstawie modelu byłyby Jeśli wartości dla funkcji powoduje ustawiono losową \* wartość?".</span><span class="sxs-lookup"><span data-stu-id="c1e1b-108">PFI measures feature importance by asking the question, "What would the effect on the model be if the values for a feature were set to a random\* value?".</span></span> <span data-ttu-id="c1e1b-109">Zaletą metody PFI jest niezależny od modelu — działa z dowolnego modelu, które może przyjąć — i w dowolnym zestawie danych, a nie tylko zestaw treningowy można użyć do obliczenia znaczenie funkcji.</span><span class="sxs-lookup"><span data-stu-id="c1e1b-109">The advantage of the PFI method is that it is model agnostic — it works with any model that can be evaluated — and it can use any dataset, not just the training set, to compute feature importance.</span></span> <span data-ttu-id="c1e1b-110">Umożliwia PFI, takich jak więc tworzyć importances funkcji, takich jak ten wykres:</span><span class="sxs-lookup"><span data-stu-id="c1e1b-110">You can use PFI like so to produce feature importances like this graph:</span></span>

![Wykres znaczenie funkcji permutacji](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model, data);
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
                .ToArray();
 
// Write out the feature names and their importance to the model's R-squared value
for (int i = 0; i < featureNames.Length; i++)
  Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].rSquared:G4}");
```

<span data-ttu-id="c1e1b-112">Przykład za pomocą PFI do analizowania znaczenie funkcji modelu, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).</span><span class="sxs-lookup"><span data-stu-id="c1e1b-112">For a sample using PFI to analyze the feature importance of a model, see [the dotnet/machinelearning GitHub repository](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance.cs).</span></span>

<span data-ttu-id="c1e1b-113">/ \* Dobrze, nie losowe dokładnie, ale cieniowania w zestawie przykłady.</span><span class="sxs-lookup"><span data-stu-id="c1e1b-113">/\* Well, not random exactly, but permuted across the set of examples.</span></span>
