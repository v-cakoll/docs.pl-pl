---
title: Interpretowanie modeli ML.NET za pomocą uogólnionych modeli dodatków
description: Użyj ogólnych modeli dodatków i funkcji kształtu dla interpretacji modelu w ML.NET
ms.date: 01/30/2020
ms.custom: mvc,how-to
ms.openlocfilehash: 6df19eff4fec98c5815a9f8f4d8e4e9a80cba6ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77092476"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>Użyj ogólnych modeli dodatków i funkcji kształtu dla interpretacji modelu w ML.NET

Podczas tworzenia modeli uczenia maszynowego często nie wystarczy po prostu tworzyć prognozy. Często deweloperzy uczenia maszynowego, decydenci i osoby, których dotyczą modele, muszą zrozumieć, w jaki sposób modele uczenia maszynowego podejmują decyzje i które funkcje przyczyniają się do ich wydajności. **Generalized Additive Models (GAMs)** są używane wewnętrznie w firmie Microsoft do interpretacji modelu, aby ułatwić deweloperom uczenia maszynowego tworzenie modeli o dużej pojemności, które mogą być łatwo interpretowane przez inne osoby.

GAMs są klasą **modeli podlegających interpretacji,** które są modelami liniowymi, w których terminy są funkcjami nieliniowymi, zwanymi "funkcjami kształtu" pojedynczej zmiennej. Jako modele liniowe są one łatwo interpretowane, ale ponieważ modele uczą się funkcji obiektów zamiast pojedynczej wagi, mogą modelować bardziej złożone relacje niż prosty model liniowy. Wynikowy predyktor GAM ma termin przechwytywania, który reprezentuje średnią prognozę w zestawie szkoleniowym i funkcje kształtu, które reprezentują odchylenie od średniej prognozy. Funkcje kształtu mogą być kontrolowane przez oko, aby zobaczyć odpowiedź modelu na różne wartości operacji i wizualizowane jak poniższy wykres, który jest tworzony na końcu przykładu kodu. Trener GAM w ML.NET jest implementowany przy użyciu płytkich gradientu wzmocnionych drzew (na przykład pniaki drzewa) do nauki funkcji kształtu nieparametrycznego i opiera się na metodzie opisanej w [Inteludowy modele klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) przez Lou, Caruana i Gehrke.

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

Aby uzyskać przykład o tym, jak nabyć model GAM i sprawdzić i zinterpretować wyniki, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
