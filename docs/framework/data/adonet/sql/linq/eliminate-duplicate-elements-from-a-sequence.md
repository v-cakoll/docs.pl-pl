---
title: Eliminowanie zduplikowane elementy z sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 3dbb5be65823b456e5b573f7cbbad8d172022425
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357303"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Eliminowanie zduplikowane elementy z sekwencji
Użyj <xref:System.Linq.Queryable.Distinct%2A> operatora, aby wyeliminować zduplikowane elementy z sekwencji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Distinct%2A> do wybierania sekwencji miast unikatowy, które mają klientów.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
