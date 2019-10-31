---
title: 'Porady: implementowanie partycji dynamicznych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
ms.openlocfilehash: 3970566b4e3f51ce538c328d4e69b20ec22ec09b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091422"
---
# <a name="how-to-implement-dynamic-partitions"></a>Porady: implementowanie partycji dynamicznych

Poniższy przykład pokazuje, jak zaimplementować niestandardowy <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType>, który implementuje partycjonowanie dynamiczne i może być używany z pewnych przeciążeń <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.  
  
## <a name="example"></a>Przykład

Za każdym razem, gdy partycja wywołuje <xref:System.Collections.IEnumerator.MoveNext%2A> w module wyliczającym, moduł wyliczający tworzy partycję z jednym elementem listy. W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>partycja jest wystąpieniem <xref:System.Threading.Tasks.Task>. Ponieważ żądania są wykonywane współbieżnie w wielu wątkach, jest synchronizowany dostęp do bieżącego indeksu.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Jest to przykład partycjonowania fragmentu, z każdym fragmentem składającym się z jednego elementu. Zapewniając więcej elementów naraz, można zmniejszyć rywalizację o blokadę i teoretycznie osiągnąć wyższą wydajność. Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia, aby zapewnić, że wszystkie wątki są zajęte, dopóki wszystkie zadania nie zostaną wykonane.  
  
## <a name="see-also"></a>Zobacz także

* [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Instrukcje: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
