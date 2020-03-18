---
title: Obliczanie metryk w celu oceny jakości modelu uczenia maszynowego
description: Dowiedz się, jak obliczyć metryki, aby ocenić i zweryfikować jakość modelu uczenia maszynowego za pomocą ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73975841"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a>Obliczanie metryk w celu oceny jakości modelu uczenia maszynowego

> [!NOTE]
> Ten temat odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)

Ten przykład i powiązane są obecnie przy użyciu **ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [reppo github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Jak oceniasz jakość po wytrenowaniu modelu? Każde zadanie uczenia maszynowego udostępnia metryki dla oceny jakości.

Można użyć odpowiedniego "kontekstu" zadania do oceny modelu, jak w poniższym przykładzie:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
