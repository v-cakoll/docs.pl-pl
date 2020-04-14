---
title: Interpretowanie modeli ML.NET za pomocą uogólnionych modeli dodatków
description: Użyj uogólnionych modeli dodatków i funkcji kształtu, aby interpretalnością modelu w ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 29eac7a609ada57283a7c5b55b935e30709930dd
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243131"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>Użyj uogólnionych modeli dodatków i funkcji kształtu, aby interpretalnością modelu w ML.NET

Podczas tworzenia modeli uczenia maszynowego często nie wystarczy po prostu przewidywać. Często deweloperzy uczenia maszynowego, decydenci i osoby, których dotyczą modele, muszą zrozumieć, w jaki sposób modele uczenia maszynowego podejmują decyzje i które funkcje przyczyniają się do ich wydajności. **Uogólnione modele dodatków (GAM)** są używane wewnętrznie w firmie Microsoft do interpretacji modelu, aby pomóc deweloperom uczenia maszynowego tworzyć modele o dużej pojemności, które mogą być łatwo interpretowane przez innych.

GAMs to klasa **modeli interpretowalnych,** które są modelami liniowymi, w których terminy są funkcjami nieliniowymi, zwanymi "funkcjami kształtu" pojedynczej zmiennej. Jako modele liniowe są one łatwo interpretowane, ale ponieważ modele uczą się funkcji funkcji zamiast pojedynczej wagi, mogą modelować bardziej złożone relacje niż prosty model liniowy. Wynikowy predictor GAM ma termin przechwytywania, który reprezentuje średnią przewidywanie w zestawie szkoleniowym i funkcji kształtu, które reprezentują odchylenie od przewidywania średniej. Funkcje kształtu mogą być sprawdzane przez oko, aby zobaczyć odpowiedź modelu na różne wartości operacji i wizualizowane, podobnie jak poniższy wykres, który jest tworzony na końcu przykładu kodu. Trener GAM w ML.NET jest implementowany przy użyciu płytkich gradientów wzmocnionych drzew (na przykład pniaki drzewa), aby nauczyć się nieparametrycznych funkcji kształtu i opiera się na metodzie opisanej w [Intelkwalifikowalne modele klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) przez Lou, Caruana i Gehrke.

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

![Wykres funkcji kształtu Uogólnione modele dodatków](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Na przykład sposobu trenowania modelu GAM i sprawdzania i interpretowania wyników można znaleźć w [przykładzie trenera klasyfikacji binarnej](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/Trainers/BinaryClassification/Gam.cs).
