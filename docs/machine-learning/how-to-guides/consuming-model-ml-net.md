---
title: Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego
description: Dowiedz się, jak wykorzystać model uczenia maszynowego przeszkolony i ocenione w aplikacjach za pomocą strukturze ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675137"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a><span data-ttu-id="4d8fa-103">Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego</span><span class="sxs-lookup"><span data-stu-id="4d8fa-103">Operationalize a trained machine learning model in apps - ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="4d8fa-104">W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="4d8fa-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="4d8fa-105">Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span><span class="sxs-lookup"><span data-stu-id="4d8fa-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="4d8fa-106">Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**.</span><span class="sxs-lookup"><span data-stu-id="4d8fa-106">This how-to and related sample are currently using **ML.NET version 0.10**.</span></span> <span data-ttu-id="4d8fa-107">Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span><span class="sxs-lookup"><span data-stu-id="4d8fa-107">For more information, see the release notes at the [dotnet/machinelearning github repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="4d8fa-108">Gdy metryk modelu wygląda dobrze, nadszedł czas na operacjonalizowanie modelu.</span><span class="sxs-lookup"><span data-stu-id="4d8fa-108">When the model metrics look good to you, it's time to 'operationalize' the model.</span></span> <span data-ttu-id="4d8fa-109">`model` Obiekt utworzony mogą być używane, utrwalona i ponownie użyte w różnych środowiskach, zastosowanie te same czynności, które "poznaniu" podczas szkolenia.</span><span class="sxs-lookup"><span data-stu-id="4d8fa-109">The `model` object you built can be consumed, persisted, and reused in different environments, applying the same steps that it 'learned' during training.</span></span>

<span data-ttu-id="4d8fa-110">Aby zapisać w pliku modelu i załadować go ponownie (potencjalnie w innym kontekście), skorzystaj z następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="4d8fa-110">To save the model to a file, and reload it (potentially in a different context), use the following example:</span></span>

```csharp
using (var stream = File.Create(modelPath))
{
    // Saving and loading happens to 'dynamic' models.
    mlContext.Model.Save(model, stream);
}

// Potentially, the lines below can be in a different process altogether.

// When you load the model, it's a transformer.
ITransformer loadedModel;
using (var stream = File.OpenRead(modelPath))
    loadedModel = mlContext.Model.Load(stream);
```
