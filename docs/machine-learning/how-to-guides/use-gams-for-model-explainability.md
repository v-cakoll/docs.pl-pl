---
title: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
description: Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET
ms.date: 12/04/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 489aee34d0404293bc080b934636c01bdab92fe9
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155487"
---
# <a name="use-generalized-additive-models-and-shape-functions-for-model-explainability-in-mlnet"></a>Uogólnione modele dodatku i kształtu funkcji na użytek explainability model w strukturze ML.NET

Podczas tworzenia modeli uczenia maszynowego, często nie jest wystarczająco, aby po prostu prognozowania. Często deweloperom, osobom podejmującym decyzje i te wpływ modele uczenia maszynowego trzeba wiedzieć, jak modele uczenia maszynowego podejmowanie decyzji i funkcji, które przyczyniają się do ich wydajność. **Uogólnione modele dodatku (GAMs)** są używane wewnętrznie w firmie Microsoft explainability modelu pomagające deweloperom learning maszyny, tworzyć modele o dużej pojemności, które mogą być łatwo interpretowane przez innych użytkowników.

GAMs są klasy **interpretowanej modeli** będących modeli liniowych, warunki, w którym znajdują się funkcje nieliniowych, o nazwie "kształtu funkcji" jednej zmiennej. Jako modeli liniowych są interpretowane łatwe, ale ponieważ modele dowiedzieć się więcej funkcji funkcji zamiast pojedynczego wagi, ich modelowania bardziej złożonych relacji niż prosty model liniowy. Wynikowy predykcyjne GAM ma termin intercept, który reprezentuje średni prognozowania nad zestaw szkoleniowy i funkcje kształtu, reprezentującymi odchyleń od średniej prognozy. Funkcje kształtów można kontrolowane przez oka, aby zobaczyć odpowiedź modelu różne wartości funkcji i wizualizowane takich jak poniższy wykres, który jest tworzony na końcu w przykładzie kodu. Trainer GAM w strukturze ML.NET jest implementowany przy użyciu płytka gradientu wzmocnionego drzewa (na przykład drzewa pnie) aby dowiedzieć się więcej funkcji nonparametric kształt i jest oparta na metody opisanej w [zrozumiałą modele klasyfikacji i regresji](https://www.cs.cornell.edu/~yinlou/papers/lou-kdd12.pdf) Lou, Caruana i Gehrke.

```csharp
// Train the Generalized Additive Model
var gamTrainer = mlContext.Regression.Trainers.GeneralizedAdditiveModels()
var gamModel = gamTrainer.Fit(data);
 
// The intercept for Generalize Additive Models represent the average prediction for the training data
var intercept = gamModel.Intercept;
 
// Get the feature names from the training set
var featureNames = data.Schema.GetColumns()
                .Select(tuple => tuple.column.Name) // Get the column names
                .Where(name => name != labelName) // Drop the Label
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
  Console.WriteLine($"x < {myFeatureBins[i]:0.00} => {myFeatureWeights[i]:0.000}");
```

![Uogólnionego modele dodatku kształtu funkcji wykresu](./media/use-gams-for-model-explainability/gam-shape-function-graph.png)

Przykład sposobu uczenia modelu GAM, zbadaj i interpretacji wyników, zobacz [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/blob/master/docs/samples/Microsoft.ML.Samples/Dynamic/GeneralizedAdditiveModels.cs).