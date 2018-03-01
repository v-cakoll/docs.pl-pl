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
helpviewer_keywords:
- tasks, how to create a dynamic partitioner
ms.assetid: c875ad12-a161-43e6-ad1c-3d6927c536a7
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9b08c387c9b10a9d6fa8728a7fce87a7894a37fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-implement-dynamic-partitions"></a>Porady: implementowanie partycji dynamicznych
Poniższy przykład przedstawia sposób zaimplementowania niestandardowego <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> który implementuje dynamiczne partycjonowanie i mogą być używane z niektórych przeciążenia <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.  
  
## <a name="example"></a>Przykład  
 Zawsze wywołuje partycji <xref:System.Collections.IEnumerator.MoveNext%2A> przez moduł wyliczający modułu wyliczającego zapewnia partycji z listy jeden element. W przypadku PLINQ i <xref:System.Threading.Tasks.Parallel.ForEach%2A>, partycja jest <xref:System.Threading.Tasks.Task> wystąpienia. Ponieważ żądania są wykonywane jednocześnie na wielu wątków, dostęp do bieżącego indeksu jest zsynchronizowany.  
  
 [!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#04)]
 [!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  
  
 To jest przykład fragmentu partycjonowania z każdego fragmentu składające się z jednego elementu. Zapewniając więcej elementów jednocześnie, można zmniejszyć konfliktu za pośrednictwem blokady i teoretycznie osiągnąć większą wydajność. W pewnym momencie większych fragmentów mogą jednak wymagać dodatkową logikę równoważenia obciążenia, aby zachować wszystkie wątki zajęty, dopóki wszystkie praca jest wykonywana.  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Instrukcje: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
