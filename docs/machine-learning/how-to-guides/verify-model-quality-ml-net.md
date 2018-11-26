---
title: Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET
description: Dowiedz się, jak można obliczyć metryki, aby ocenić i sprawdzić jakość modelu za pomocą platformy ML.NET uczenia maszynowego
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 6fd4dfab6104b4398918e42ed70584b04169a8c1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297675"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="8dec1-103">Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="8dec1-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

<span data-ttu-id="8dec1-104">Jak oceny jakości po uczenie modelu?</span><span class="sxs-lookup"><span data-stu-id="8dec1-104">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="8dec1-105">Każde zadanie uczenia maszyny udostępnia metryki dla oceny jakości.</span><span class="sxs-lookup"><span data-stu-id="8dec1-105">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="8dec1-106">Odpowiednie 'context' zadania umożliwia ocenę modelu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8dec1-106">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```