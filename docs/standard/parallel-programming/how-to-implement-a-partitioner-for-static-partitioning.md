---
title: 'Porady: implementowanie partycjonera dla partycjonowania statycznego'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 302d7d98d04e528d205edf38c3fa13bb3f2b2252
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863076"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a>Porady: implementowanie partycjonera dla partycjonowania statycznego
Poniższy przykład przedstawia sposób implementować proste niestandardowego partycjonera dla PLINQ, który wykonuje partycjonowania statycznego. Ponieważ partycjonera nie obsługuje partycji dynamicznych, nie jest może być używany przez <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Tego konkretnego partycjonera udostępniać przyspieszenie za pośrednictwem partycjonera zakresu domyślnego źródła danych, dla których każdy element wymaga zwiększa ilość czasu przetwarzania.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 Partycje w tym przykładzie są oparte na założeniu liniowy wzrost czas przetwarzania dla każdego elementu. W świecie rzeczywistym może być trudne do przewidzenia czas przetwarzania w ten sposób. Jeśli statycznego partycjonera korzystają z określonego źródła danych, można zoptymalizować partycjonowania formułę dla źródła, Dodaj logikę równoważenia obciążenia lub używanie fragmentów, partycjonowanie podejście, jak pokazano w [porady: Implementowanie partycji dynamicznych](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
## <a name="see-also"></a>Zobacz także

- [Niestandardowe partycjonery dla PLINQ i TPL](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
