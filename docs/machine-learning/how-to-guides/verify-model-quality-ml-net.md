---
title: Oblicz metryki, aby oszacować jakość modelu uczenia maszynowego
description: Dowiedz się, jak obliczyć metryki w celu oszacowania i sprawdzenia jakości modelu uczenia maszynowego za pomocą ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: 529003913b166c966e131b006800f944096605b7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855566"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Oblicz metryki, aby oszacować jakość modelu uczenia maszynowego 

> [!NOTE]
> Ten temat dotyczy ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .

Ta procedura i powiązana próbka są obecnie używane w programie **ml.NET w wersji 0,10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium programu dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)w witrynie GitHub.

Jak przeprowadzić ocenę jakości po nauczeniu modelu? Każde zadanie uczenia maszynowego udostępnia metryki na potrzeby oceny jakości.

Aby oszacować model, można użyć odpowiedniego kontekstu zadania, tak jak w poniższym przykładzie:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
