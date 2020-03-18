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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality"></a><span data-ttu-id="72942-103">Obliczanie metryk w celu oceny jakości modelu uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="72942-103">Calculate metrics to evaluate machine learning model quality</span></span>

> [!NOTE]
> <span data-ttu-id="72942-104">Ten temat odnosi się do ML.NET, który jest obecnie w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="72942-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="72942-105">Aby uzyskać więcej informacji, odwiedź stronę [ML.NET.](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet)</span><span class="sxs-lookup"><span data-stu-id="72942-105">For more information, visit the [ML.NET](https://dotnet.microsoft.com/apps/machinelearning-ai/ml-dotnet) page.</span></span>

<span data-ttu-id="72942-106">Ten przykład i powiązane są obecnie przy użyciu **ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="72942-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="72942-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [reppo github dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="72942-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="72942-108">Jak oceniasz jakość po wytrenowaniu modelu?</span><span class="sxs-lookup"><span data-stu-id="72942-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="72942-109">Każde zadanie uczenia maszynowego udostępnia metryki dla oceny jakości.</span><span class="sxs-lookup"><span data-stu-id="72942-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="72942-110">Można użyć odpowiedniego "kontekstu" zadania do oceny modelu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="72942-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```
