---
title: Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego
description: Dowiedz się, jak wykorzystać model uczenia maszynowego przeszkolony i ocenione w aplikacjach za pomocą strukturze ML.NET
ms.date: 03/05/2019
ms.custom: mvc,how-to
ms.openlocfilehash: be6906c939b82d00067babaeebe809dae3de413a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650430"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium dotnet/machinelearning github](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)

Gdy metryk modelu wygląda dobrze, nadszedł czas na operacjonalizowanie modelu. `model` Obiekt utworzony mogą być używane, utrwalona i ponownie użyte w różnych środowiskach, zastosowanie te same czynności, które "poznaniu" podczas szkolenia.

Aby zapisać w pliku modelu i załadować go ponownie (potencjalnie w innym kontekście), skorzystaj z następującego przykładu:

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
