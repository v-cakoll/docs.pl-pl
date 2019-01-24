---
title: Zwracanie zestawu różnic między dwoma sekwencjami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 282ec36a2ad489e77db9fb5b338d3189c3001f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609034"
---
# <a name="return-the-set-difference-between-two-sequences"></a>Zwracanie zestawu różnic między dwoma sekwencjami
Użyj <xref:System.Linq.Queryable.Except%2A> operator ma być zwracanie zestawu różnic między dwoma sekwencjami.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Except%2A> w celu zwrócenia sekwencji wszystkie kraje, w którym `Customers` aktywna, ale w przypadku którego nie `Employees` na żywo.  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Except%2A> działa dobrze zdefiniowane tylko na zestawach. Semantyka dla multisets jest niezdefiniowane.  
  
## <a name="see-also"></a>Zobacz także
- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
