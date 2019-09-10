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
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>Korzystaj z uogólnionych modeli i funkcji kształtu do wyjaśnienia modelu w ML.NET

> [!NOTE]
> Ten temat dotyczy ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Ta procedura i powiązana próbka są obecnie używane w programie **ml.NET w wersji 0,10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium programu dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)w witrynie GitHub.

Podczas tworzenia modeli uczenia maszynowego często nie wystarczy, aby robić przewidywania. Często deweloperzy uczenia maszynowego, osoby podejmujące decyzje i te, których dotyczą modele, muszą zrozumieć, jak modele uczenia maszynowego podejmują decyzje i jakie funkcje przyczyniają się do ich wydajności. **Ogólne modele addytywne (GAMs)** są używane wewnętrznie w firmie Microsoft w celu uzyskania wyjaśnień, aby ułatwić deweloperom uczenia maszynowego tworzenie modeli o wysokiej wydajności, które mogą być łatwo interpretowane przez inne osoby.

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
