---
title: 'Porady: implementowanie partycji dynamicznych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1e5dc93997918e0f7da29fa1f94c434a556f19f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>Porady: implementowanie partycji dynamicznych
Poniższy przykład przedstawia sposób zaimplementowania niestandardowego <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> który implementuje dynamiczne partycjonowanie i mogą być używane z niektórych przeciążenia <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.  
  
## <a name="example"></a>Przykład  
 Zawsze wywołuje partycji <xref:System.Collections.IEnumerator.MoveNext%2A> przez moduł wyliczający modułu wyliczającego zapewnia partycji z listy jeden element. W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>, partycja jest <xref:System.Threading.Tasks.Task> wystąpienia. Ponieważ żądania są wykonywane jednocześnie na wielu wątków, dostęp do bieżącego indeksu jest zsynchronizowany.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 To jest przykład fragmentu partycjonowania z każdego fragmentu składające się z jednego elementu. Zapewniając więcej elementów jednocześnie, można zmniejszyć konfliktu za pośrednictwem blokady i teoretycznie osiągnąć większą wydajność. W pewnym momencie większych fragmentów mogą jednak wymagać dodatkową logikę równoważenia obciążenia, aby zachować wszystkie wątki zajęty, dopóki wszystkie praca jest wykonywana.  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Porady: Implementowanie Partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
