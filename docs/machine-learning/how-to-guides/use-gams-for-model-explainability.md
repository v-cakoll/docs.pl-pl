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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-interpretability-in-mlnet"></a>Korzystaj z uogólnionych modeli i funkcji kształtu do interpretowania modeli w ML.NET

Podczas tworzenia modeli uczenia maszynowego często nie wystarczy, aby robić przewidywania. Często deweloperzy uczenia maszynowego, osoby podejmujące decyzje i te, których dotyczą modele, muszą zrozumieć, jak modele uczenia maszynowego podejmują decyzje i jakie funkcje przyczyniają się do ich wydajności. **Ogólne modele addytywne (GAMs)** są używane wewnętrznie w firmie Microsoft w celu interpretowania modeli, aby ułatwić deweloperom uczenia maszynowego tworzenie modeli o wysokiej wydajności, które mogą być łatwo interpretowane przez inne osoby.

GAMs jest klasą **interpretowanych modeli** , które są modelami liniowymi, gdzie warunki są funkcjami nieliniowymi, nazywanymi "funkcjami kształtu" jednej zmiennej. Modele liniowe są łatwo interpretowane, ale ponieważ modele poznają funkcje funkcji zamiast pojedynczej wagi, mogą modelować bardziej złożone relacje niż prosty model liniowy. Wynikająca przewidywalność mapie gam ma termin przechwycenia reprezentujący średnią prognozę dla zestawu szkoleniowego i funkcje kształtu, które reprezentują odchylenia od średniej przewidywania. Funkcje kształtu mogą być sprawdzane przez oczy, aby zobaczyć odpowiedź modelu do różnych wartości funkcji i wizualizować jak Poniższy wykres, który jest tworzony na końcu przykładu kodu. MAPIE gam Trainer w ML.NET jest zaimplementowana przy użyciu wzorów podwyższania poziomu gradientu (na przykład drzewa Stumps), aby poznać funkcje kształtu nieparametrycznego i opiera się na metodzie opisanej w [odniesieniu do modelu klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) przez Lou, Caruana i Gehrke.

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

Aby zapoznać się z przykładem sposobu uczenia modelu mapie gam i sprawdzenia i interpretacji wyników, zobacz [repozytorium dotnet/machinelearning w witrynie GitHub](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).
