---
title: Łączenie dwóch sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76767e7c-0607-4e1d-9ca2-a94f311f45eb
ms.openlocfilehash: c0a6dde667c4f858d8177dc80a726619f463f3a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354056"
---
# <a name="concatenate-two-sequences"></a>Łączenie dwóch sekwencji
Użyj <xref:System.Linq.Queryable.Concat%2A> operator do łączenia dwóch sekwencji.  
  
 <xref:System.Linq.Queryable.Concat%2A> Operator jest zdefiniowany dla uporządkowanych multisets gdzie zamówień odbiornika i argument są takie same.  
  
 Kolejność w programie SQL jest ostatnim krokiem przed wyniki są tworzone. Z tego powodu <xref:System.Linq.Queryable.Concat%2A> operator jest implementowane za pomocą `UNION ALL` i kolejność jej argumenty nie zostaną zachowane. Aby upewnić się, że porządkowania jest prawidłowa w wynikach, upewnij się, że jawnie kolejność wyników.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> do zwrócenia sekwencji wszystkich `Customer` i `Employee` numerem telefonu i faksu.  
  
 [!code-csharp[DLinqQueryExamples#39](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#39)]
 [!code-vb[DLinqQueryExamples#39](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#39)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie użyto <xref:System.Linq.Queryable.Concat%2A> do zwrócenia sekwencji wszystkich `Customer` i `Employee` nazwy i mapowania numeru telefonu.  
  
 [!code-csharp[DLinqQueryExamples#40](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#40)]
 [!code-vb[DLinqQueryExamples#40](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#40)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Translacja standardowego operatora zapytania](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
