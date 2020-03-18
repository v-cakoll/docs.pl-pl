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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091422"
---
# <a name="how-to-implement-dynamic-partitions"></a>Porady: implementowanie partycji dynamicznych

W poniższym przykładzie pokazano, jak zaimplementować niestandardowe, <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> który implementuje partycjonowanie dynamiczne i może służyć z niektórych przeciążeń <xref:System.Threading.Tasks.Parallel.ForEach%2A> i z PLINQ.  
  
## <a name="example"></a>Przykład

Za każdym razem <xref:System.Collections.IEnumerator.MoveNext%2A> partycji wywołuje wyliczacza, wyliczacz udostępnia partycji z jednym elementem listy. W przypadku PLINQ <xref:System.Threading.Tasks.Parallel.ForEach%2A>i , partycja jest wystąpieniem. <xref:System.Threading.Tasks.Task> Ponieważ żądania są dzieje się jednocześnie na wielu wątków, dostęp do bieżącego indeksu jest synchronizowany.  

[!code-csharp[TPL_Partitioners#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner02.cs#OrderableListPartitioner)]
[!code-vb[TPL_Partitioners#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/dynamicpartitioner.vb#04)]  

Jest to przykład partycjonowania fragmentu, z każdym fragmentem składającym się z jednego elementu. Dostarczając więcej elementów naraz, można zmniejszyć rywalizację o blokadę i teoretycznie osiągnąć szybszą wydajność. Jednak w pewnym momencie większe fragmenty mogą wymagać dodatkowej logiki równoważenia obciążenia, aby wszystkie wątki były zajęte, dopóki nie zostanie wykonana cała praca.  
  
## <a name="see-also"></a>Zobacz też

* [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
* [Porady: implementowanie partycjonera dla partycjonowania statycznego](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
