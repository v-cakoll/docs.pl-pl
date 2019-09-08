---
title: Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 7de65579cb41641aded0b9a320fac59804959ff5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782233"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Określanie, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek
Operator <xref:System.Linq.Enumerable.All%2A> zwraca`true` , jeśli wszystkie elementy w sekwencji spełniają warunek.  
  
 Operator <xref:System.Linq.Queryable.Any%2A> zwraca`true` , jeśli którykolwiek element w sekwencji spełnia warunek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zwraca sekwencję klientów, którzy mają co najmniej jedno zamówienie. `Where` Klauzulama`true`wartość, Jeśli dana`Customer` wartość ma .`Order` / `where`  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod Visual Basic określa listę klientów, którzy nie przetworzyli zamówień, i gwarantuje, że dla każdego klienta na tej liście zostanie podana nazwa kontaktu.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Przykład  
 Poniższy C# przykład zwraca sekwencję klientów, których zamówienia zaczynają się `ShipCity` od znaku "C". Również uwzględniono w zwracaniu klientów, którzy nie mają zamówień. (Według projektu, <xref:System.Linq.Queryable.All%2A> operator zwraca `true` dla pustej sekwencji). Klienci bez zamówień są eliminowani w danych wyjściowych konsoli za pomocą `Count` operatora.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
