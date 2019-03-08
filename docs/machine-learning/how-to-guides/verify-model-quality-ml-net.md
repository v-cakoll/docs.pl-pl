---
title: Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET
description: Dowiedz się, jak można obliczyć metryki, aby ocenić i sprawdzić jakość modelu za pomocą platformy ML.NET uczenia maszynowego
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: ad71f7da6981ac370e60725f88d3c70b1d5c5237
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679219"
---
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a><span data-ttu-id="21860-103">Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET</span><span class="sxs-lookup"><span data-stu-id="21860-103">Calculate metrics to evaluate machine learning model quality - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="21860-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="21860-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="21860-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="21860-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="21860-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="21860-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="21860-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span><span class="sxs-lookup"><span data-stu-id="21860-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="21860-108">Jak oceny jakości po uczenie modelu?</span><span class="sxs-lookup"><span data-stu-id="21860-108">How do you evaluate quality after you train the model?</span></span> <span data-ttu-id="21860-109">Każde zadanie uczenia maszyny udostępnia metryki dla oceny jakości.</span><span class="sxs-lookup"><span data-stu-id="21860-109">Each machine learning task exposes metrics for quality evaluation.</span></span>

<span data-ttu-id="21860-110">Odpowiednie 'context' zadania umożliwia ocenę modelu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="21860-110">You can use the corresponding 'context' of the task to evaluate the model, as in the following example:</span></span>

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```