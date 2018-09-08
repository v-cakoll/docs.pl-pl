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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b2d46264113cb4c961f6c4b971b5986bdd9eb6a7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180975"
---
# <a name="how-to-implement-dynamic-partitions"></a>Porady: implementowanie partycji dynamicznych
Poniższy przykład pokazuje, jak zaimplementować niestandardowy <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> które implementuje dynamiczne partycjonowanie i mogą być używane z niektórych przeciążenia <xref:System.Threading.Tasks.Parallel.ForEach%2A> z PLINQ.  
  
## <a name="example"></a>Przykład  
 Zawsze wywołuje partycji <xref:System.Collections.IEnumerator.MoveNext%2A> przez moduł wyliczający modułu wyliczającego zapewnia partycji z listy jeden element. W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>, partycja jest <xref:System.Threading.Tasks.Task> wystąpienia. Ponieważ żądania są wykonywane równolegle w wielu wątkach, dostęp do bieżącego indeksu są synchronizowane.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 Jest to przykład fragmentów, partycjonowanie, z każdym fragmentem składający się z jednym elementem. Przez zapewnienie im więcej elementów w danym momencie, może zmniejszyć rywalizację na blokadę, a teoretycznie osiągnąć zwiększyć wydajność. Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia Aby zachować wszystkie wątki zajęty, aż wszystkie zadania są wykonywane.  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
- [Instrukcje: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
