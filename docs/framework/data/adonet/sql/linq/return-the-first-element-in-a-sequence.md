---
title: Zwracanie pierwszego elementu w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081841"
---
# <a name="return-the-first-element-in-a-sequence"></a>Zwracanie pierwszego elementu w sekwencji
Użyj <xref:System.Linq.Enumerable.First%2A> operatora, aby powrócić do pierwszego elementu w sekwencji. Wysyła zapytanie, które używają <xref:System.Linq.Enumerable.First%2A> są wykonywane natychmiast.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy kod wyszukuje pierwszy `Shipper` w tabeli:  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod umożliwia znalezienie jednej `Customer` zawierający `CustomerID` BONAP.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
