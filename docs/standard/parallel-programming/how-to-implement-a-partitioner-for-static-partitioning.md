---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 94fbb681b20b9c920c20df2a9017f75a9aa9a6ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73091532"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Porady: implementowanie partycjonera dla partycjonowania statycznego
W poniższym przykładzie przedstawiono jeden sposób zaimplementowania prostego niestandardowego partycjonera dla PLINQ, który wykonuje partycjonowanie statyczne. Ponieważ partycjonowanie nie obsługuje partycji dynamicznych, nie <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>jest zużywalny z . Ten konkretny partycjonowanie może zapewnić przyspieszenie w domyślnym partycjonowanie zakresu dla źródeł danych, dla których każdy element wymaga coraz większą ilość czasu przetwarzania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Partycje w tym przykładzie są oparte na założeniu liniowego wydłużenia czasu przetwarzania dla każdego elementu. W świecie rzeczywistym może być trudno przewidzieć czasy przetwarzania w ten sposób. Jeśli używasz partycjonowania statycznego z określonym źródłem danych, można zoptymalizować formułę partycjonowania dla źródła, dodać logikę równoważenia obciążenia lub użyć podejścia partycjonowania fragmentu, jak pokazano w [jak: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Zobacz też

- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
