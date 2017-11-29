---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b28ff0bb8436fefc4956918889435e258ae98b12
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Porady: implementowanie partycjonera dla partycjonowania statycznego
Poniższy przykład przedstawia sposób Implementowanie prostego niestandardowych partycjonera dla PLINQ, który wykonuje partycjonowania statycznego. Ponieważ obiekt partitioner nie obsługuje dynamicznej partycji, nie jest dostępne z <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Ten moduł partycjonowania w szczególności może zawierać przyspieszenie przez obiekt partitioner domyślny zakres dla źródeł danych, dla których każdy element wymaga zwiększa ilość czasu przetwarzania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Partycje w tym przykładzie są oparte na założeniu liniowy wzrost czasu przetwarzania dla każdego elementu. W świecie rzeczywistym może być trudna do przewidzenia, czas przetwarzania w ten sposób. Jeśli używasz statycznego partycjonera z określonego źródła danych, można zoptymalizować partycjonowania formuła źródła, Dodaj logikę równoważenia obciążenia lub użyj fragmentu partycjonowania podejście, jak pokazano w [porady: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Niestandardowe Partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
