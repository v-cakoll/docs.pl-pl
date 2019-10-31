---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091532"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Porady: implementowanie partycjonera dla partycjonowania statycznego
W poniższym przykładzie pokazano jeden ze sposobów implementacji prostego niestandardowego Partitioner dla PLINQ, który wykonuje statyczne partycjonowanie. Ponieważ partycja nie obsługuje partycji dynamicznych, nie można jej używać z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Ta konkretna partycja może dostarczyć przyspieszenie przez domyślną partycję zakresu dla źródeł danych, dla których każdy element wymaga wzrostu czasu przetwarzania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Partycje w tym przykładzie opierają się na założeniu liniowego wzrostu czasu przetwarzania dla każdego elementu. W świecie rzeczywistym może być trudne przewidywanie czasu przetwarzania w ten sposób. Jeśli używasz statycznej partycji z określonym źródłem danych, możesz zoptymalizować formułę partycjonowania dla źródła, dodać logikę równoważenia obciążenia lub użyć podejścia partycjonowania fragmentu, jak pokazano w [instrukcje: implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
