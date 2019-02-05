---
title: Ustalenia funkcji znaczenie modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
description: Zrozumieć znaczenie funkcji modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET
ms.date: 02/01/2019
ms.custom: mvc,how-to
ms.openlocfilehash: a61e5dbbd544aa7df56291db9207343cb6f03e6e
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738815"
---
# <a name="determine-the-feature-importance-of-models-with-permutation-feature-importance-in-mlnet"></a>Ustalenia funkcji znaczenie modeli za pomocą permutacji funkcji znaczenie w strukturze ML.NET

Podczas tworzenia modeli uczenia maszynowego, często nie jest wystarczająco, aby po prostu prognozowania. Często deweloperom, osobom podejmującym decyzje i te wpływ modele uczenia maszynowego trzeba wiedzieć, jak modele uczenia maszynowego podejmowanie decyzji i funkcji, które przyczyniają się do ich wydajność. `Permutation Feature Importance` (PFI) jest narzędziem explainability modelu, która jest używana wewnętrznie w firmie Microsoft pomagające deweloperom learning maszyny lepiej zrozumieć znaczenie funkcji modeli.

PFI to technika, aby określić **znaczenie globalnych funkcji** uczonego modelu uczenia maszynowego, motywowane Breiman w [papier "Random lasów", sekcji 10](https://www.stat.berkeley.edu/~breiman/randomforest2001.pdf). PFI mierzy znaczenie funkcji, zadając pytania, "jaki wpływ na podstawie modelu byłyby Jeśli wartości dla funkcji powoduje ustawiono losową * wartość?". Zaletą metody PFI jest niezależny od modelu — działa z dowolnego modelu, które może przyjąć — i w dowolnym zestawie danych, a nie tylko zestaw treningowy można użyć do obliczenia znaczenie funkcji. Umożliwia PFI, takich jak więc tworzyć importances funkcji, takich jak ten wykres:

![Wykres znaczenie funkcji permutacji](./media/determine-global-feature-importance-in-model/pfi-graph.png)

```csharp
// Compute the feature importance using PFI
var permutationMetrics = mlContext.Regression.PermutationFeatureImportance(model.LastTransformer, model.Transform(data), "MedianHomeValue");

// Get the feature names from the training set
var featureNames =
    data.Schema.AsEnumerable()
    .Select(column => column.Name) // Get the column names
    .Where(name => name != "MedianHomeValue") // Drop the Label
    .ToArray();

// Write out the feature names and their importance to the model's Mean R-squared value
for (int i = 0; i < featureNames.Length;i++)
{
    Console.WriteLine($"{featureNames[i]}\t{permutationMetrics[i].RSquared.Mean:G4}");
}
```

Przykład za pomocą PFI do analizowania znaczenie funkcji modelu, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/samples/Microsoft.ML.Samples/Dynamic/PermutationFeatureImportance).

/ * Dobrze, nie losowe dokładnie, ale cieniowania w zestawie przykłady.
