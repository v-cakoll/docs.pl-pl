---
title: 'Instrukcje: Obsługa kluczy złożonych w zapytaniach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: 2621ab4db207d1b868fbe3778c30c744201b0506
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033816"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Instrukcje: Obsługa kluczy złożonych w zapytaniach
Niektóre operatory może zająć tylko jeden argument. Jeśli argument musi zawierać więcej niż jedną kolumnę z bazy danych, należy utworzyć typ anonimowy do reprezentowania połączenie.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia zapytanie, które wywołuje `GroupBy` operatora, który może mieć tylko jedną `key` argumentu.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Przykład  
 Taka sama sytuacja dotyczy sprzężenia, jak w poniższym przykładzie:  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
