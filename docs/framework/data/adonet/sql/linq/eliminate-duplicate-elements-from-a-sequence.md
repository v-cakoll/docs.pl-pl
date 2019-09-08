---
title: Eliminowanie zduplikowanych elementów z sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 9b8e19ac76869c33d01a59ee3aad104a7ddbb8f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782210"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Eliminowanie zduplikowanych elementów z sekwencji
Użyj operatora <xref:System.Linq.Queryable.Distinct%2A> , aby wyeliminować zduplikowane elementy z sekwencji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa <xref:System.Linq.Queryable.Distinct%2A> do wybierania sekwencji unikatowych miast, którzy mają klientów.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
