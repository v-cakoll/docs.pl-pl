---
title: Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: cd910b35f82f816158cb686a283e44e3b8b6b33b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359975"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Określić, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
<xref:System.Linq.Enumerable.All%2A> Operator zwraca `true` , gdy wszystkie elementy w sekwencji spełniają warunek.  
  
 <xref:System.Linq.Queryable.Any%2A> Operator zwraca `true` Jeśli dowolny element w sekwencji spełnia warunek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jednego zamówienia. `Where` / `where` Daje w wyniku klauzuli `true` Jeśli dany `Customer` ma jakiekolwiek `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod Visual Basic Określa listę klientów, którzy nie dokonali zamówienia i zapewnia, że dla każdego klienta na tej liście podano nazwę kontaktu.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie C# zwraca sekwencję klientów, których zamówień `ShipCity` rozpoczynające się od "C". Również zwracany obejmuje klientów, którzy mają żadnych zleceń. (Zgodnie z projektem <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji.) Klienci z żadnych zamówień są eliminowane w danych wyjściowych konsoli przy użyciu `Count` operatora.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
