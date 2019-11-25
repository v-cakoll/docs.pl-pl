---
title: Oblicz metryki, aby oszacować jakość modelu uczenia maszynowego
description: Dowiedz się, jak obliczyć metryki w celu oszacowania i sprawdzenia jakości modelu uczenia maszynowego za pomocą ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: d6409307cd283ae67d7546c4dc6e19e6089a0766
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975841"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="43880-103">Oblicz metryki, aby oszacować jakość modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="43880-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="43880-104">Ten temat dotyczy ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="43880-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="43880-105">Aby uzyskać więcej informacji, odwiedź stronę [ml.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) .</span><span class="sxs-lookup"><span data-stu-id="43880-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="43880-106">Ta procedura i powiązana próbka są obecnie używane w programie **ml.NET w wersji 0,10**.</span><span class="sxs-lookup"><span data-stu-id="43880-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="43880-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium programu dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="43880-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="43880-108">Jak przeprowadzić ocenę jakości po nauczeniu modelu?</span><span class="sxs-lookup"><span data-stu-id="43880-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="43880-109">Każde zadanie uczenia maszynowego udostępnia metryki na potrzeby oceny jakości.</span><span class="sxs-lookup"><span data-stu-id="43880-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="43880-110">Aby oszacować model, można użyć odpowiedniego kontekstu zadania, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="43880-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
