---
title: Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego
description: Dowiedz się, jak wykorzystać model uczenia maszynowego przeszkolony i ocenione w aplikacjach za pomocą strukturze ML.NET
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: ff3f0a8856382d020129693bcf722f572fd87606
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53131571"
---
# <a name="operationalize-a-trained-machine-learning-model-in-apps---mlnet"></a>Operacjonalizowanie uczony model, w aplikacjach — strukturze ML.NET uczenia maszynowego

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
