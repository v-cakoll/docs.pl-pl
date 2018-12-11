---
title: Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET
description: Dowiedz się, jak można obliczyć metryki, aby ocenić i sprawdzić jakość modelu za pomocą platformy ML.NET uczenia maszynowego
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149526"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a>Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET

Jak oceny jakości po uczenie modelu? Każde zadanie uczenia maszyny udostępnia metryki dla oceny jakości.

Odpowiednie 'context' zadania umożliwia ocenę modelu, jak w poniższym przykładzie:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```