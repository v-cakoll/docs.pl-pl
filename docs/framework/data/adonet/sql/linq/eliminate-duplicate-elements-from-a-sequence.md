---
title: Eliminowanie zduplikowanych elementów z sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 49138e9b130b1a2137b5e9e779875d6107972578
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032594"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Eliminowanie zduplikowanych elementów z sekwencji
Użyj <xref:System.Linq.Queryable.Distinct%2A> operatora w celu wyeliminowania zduplikowanych elementów z sekwencji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Distinct%2A> do wybierania sekwencji unikatowy miast, które miały klientów.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
