---
title: Zwracanie sumy zbiorów dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8b8bd3cb-86d4-4a3b-9906-61f68726dd1f
ms.openlocfilehash: 1b981d3002cf4a23897ce98927aebe96086f8a4a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781231"
---
# <a name="return-the-set-union-of-two-sequences"></a>Zwracanie sumy zbiorów dwóch sekwencji
<xref:System.Linq.Queryable.Union%2A> Użyj operatora, aby zwrócić zestaw zbiorów dwóch sekwencji.  
  
## <a name="example"></a>Przykład  
 Ten przykład używa <xref:System.Linq.Queryable.Union%2A> do zwracania sekwencji wszystkich krajów/regionów, w których `Customers` jest albo lub `Employees`.  
  
 [!code-csharp[DLinqQueryExamples#43](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#43)]
 [!code-vb[DLinqQueryExamples#43](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#43)]  
  
 W programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]operatorjestzdefiniowany dla wielozbiorów jako nieuporządkowane łączenie wielozestawów (w efekcie w wyniku [`UNION ALL`](https://docs.microsoft.com/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-2017) klauzuli w języku SQL). <xref:System.Linq.Queryable.Union%2A>

Aby uzyskać więcej informacji i przykładów, <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>Zobacz.
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
- [Translacja standardowego operatora zapytania](standard-query-operator-translation.md)
