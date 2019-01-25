---
title: Łączenie dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: 831905ca5a712bcb80d5bab1aef61a81d2ade1b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734287"
---
# <a name="concatenate-two-sequences"></a>Łączenie dwóch sekwencji
Użyj <xref:System.Linq.Queryable.Concat%2A> operatora łączenie dwóch sekwencji.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operator jest zdefiniowany dla uporządkowane multisets, gdzie zamówienia odbiornika i argument są takie same.  
  
 Kolejność w języku SQL jest to ostatni krok, zanim wyniki są tworzone. Z tego powodu <xref:System.Linq.Queryable.Concat%2A> operator jest implementowany przy użyciu `UNION ALL` i nie pozwala zachować kolejność argumentów. Aby upewnić się, że szeregowania jest poprawny w wynikach, upewnij się, że jawne kolejność wyników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> celu zwrócenia sekwencji wszystkich `Customer` i `Employee` numery telefonu i faksu.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> celu zwrócenia sekwencji wszystkich `Customer` i `Employee` nazwy i mapowania numeru telefonu.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Zobacz także
- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
