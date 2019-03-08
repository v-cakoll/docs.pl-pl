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
# <a name="calculate-metrics-to-evaluate-machine-learning-model-quality---mlnet"></a>Oblicz metrykę do oceny usługi machine learning model jakość — strukturze ML.NET

> [!NOTE]
> W tym temacie odnosi się do strukturze ML.NET, która jest obecnie dostępna w wersji zapoznawczej, a materiał może ulec zmianie. Aby uzyskać więcej informacji, odwiedź stronę [wprowadzenie strukturze ML.NET](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).

Obecnie używasz w tym przykładzie porad i pokrewnych **strukturze ML.NET wersji 0.10**. Aby uzyskać więcej informacji, zobacz informacje o wersji w [repozytorium GitHub dotnet/machinelearning](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).

Jak oceny jakości po uczenie modelu? Każde zadanie uczenia maszyny udostępnia metryki dla oceny jakości.

Odpowiednie 'context' zadania umożliwia ocenę modelu, jak w poniższym przykładzie:

```csharp
// Read the test dataset.
var testData = reader.Read(testDataPath);
// Calculate metrics of the model on the test data.
var metrics = mlContext.Regression.Evaluate(model.Transform(testData), label: "Target");
```