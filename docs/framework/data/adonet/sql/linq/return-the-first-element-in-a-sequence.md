---
title: Zwracanie pierwszego elementu w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792720"
---
# <a name="return-the-first-element-in-a-sequence"></a>Zwracanie pierwszego elementu w sekwencji
<xref:System.Linq.Enumerable.First%2A> Użyj operatora, aby zwrócić pierwszy element w sekwencji. Zapytania, które <xref:System.Linq.Enumerable.First%2A> używają są wykonywane od razu.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.  
  
## <a name="example"></a>Przykład  
 Poniższy kod umożliwia znalezienie pierwszego `Shipper` w tabeli:  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod umożliwia znalezienie pojedynczego `Customer` , który `CustomerID` ma BONAP.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind wyniki są `ID = BONAP, Contact = Laurence Lebihan`następujące.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](query-examples.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
