---
title: Zwracanie zestawu części wspólnych dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 07f48ab7ef1095ba80b1a955a4bd1ea602a75aa8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62033426"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>Zwracanie zestawu części wspólnych dwóch sekwencji
Użyj <xref:System.Linq.Queryable.Intersect%2A> operator, aby zwrócić zestawu części wspólnych dwóch sekwencji.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Intersect%2A> w celu zwrócenia sekwencji wszystkie kraje, w których obie `Customers` i `Employees` na żywo.  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 W [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Linq.Queryable.Intersect%2A> działa dobrze zdefiniowane tylko na zestawach. Semantyka dla multisets jest niezdefiniowane.  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
