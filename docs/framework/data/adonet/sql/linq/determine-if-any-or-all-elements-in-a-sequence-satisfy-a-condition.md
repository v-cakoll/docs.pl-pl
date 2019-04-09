---
title: Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128339"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
<xref:System.Linq.Enumerable.All%2A> Operator zwraca `true` Jeśli wszystkie elementy w sekwencji spełniają warunek.  
  
 <xref:System.Linq.Queryable.Any%2A> Operator zwraca `true` Jeśli dowolnego elementu w sekwencji spełniają warunek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jedno ustawienie kolejności. `Where` / `where` Daje w wyniku klauzuli `true` Jeśli danego `Customer` ma jakiekolwiek `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod w języku Visual Basic Określa listę klientów, którzy nie dokonali zamówień i gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Przykład  
 Następujące C# przykład zwraca sekwencję klientów, których zamówienia mają `ShipCity` rozpoczynające się od "C". Również powrót obejmuje klienci, którzy mają nie zamówienia. (Zgodnie z projektem <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji.) Klienci z brak zamówień są eliminowane w danych wyjściowych konsoli przy użyciu `Count` operatora.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
