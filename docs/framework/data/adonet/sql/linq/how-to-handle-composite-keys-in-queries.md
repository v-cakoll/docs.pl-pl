---
title: 'Porady: Obsługa klucze złożone w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 26c281445b84d3b3f85980de6ae4076411bb4fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354242"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Porady: Obsługa klucze złożone w zapytaniach
Operatory niektóre możliwe jest tylko jeden argument. Argument musi zawierać więcej niż jedną kolumnę z bazy danych, należy utworzyć typu anonimowego do reprezentowania połączenie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono kwerendę, która wywołuje `GroupBy` operatora, który można wykonać tylko jedną `key` argumentu.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Ta sama sytuacja dotyczy sprzężenia, jak w poniższym przykładzie:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
