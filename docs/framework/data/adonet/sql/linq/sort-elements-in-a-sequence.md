---
title: Sortowanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: f6f112a63dd976a1d6ae91f2fafd6678a9f40846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945087"
---
# <a name="sort-elements-in-a-sequence"></a>Sortowanie elementów w sekwencji
Użyj operatora <xref:System.Linq.Enumerable.OrderBy%2A> , aby posortować sekwencję według jednego lub kilku kluczy.  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Program jest przeznaczony do obsługi porządkowania według prostych typów pierwotnych, `string`takich `int`jak,, i tak dalej. Nie obsługuje porządkowania złożonych klas wielowartościowych, takich jak typy anonimowe. Nie obsługuje `byte` również typów danych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sortuje `Employees` według daty zatrudnienia.  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `where` do sortowania `Orders` danych wysłanych `London` przez fracht.  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sortuje `Products` według ceny jednostkowej od najwyższego do najniższego.  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa mieszanki `OrderBy` do sortowania `Customers` według miejscowości, a następnie według nazwy kontaktu.  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład sortuje zamówienia od `EmployeeID 1` przez `ShipCountry`, a następnie według najwyższego do najniższego frachtu.  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład łączy <xref:System.Linq.Enumerable.OrderBy%2A>operatory, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.GroupBy%2A> i, aby znaleźć, żemająnajwyższącenęjednostkowąwkażdejkategorii,anastępniesortujewedługidentyfikatorakategoriiGrupujwedług.`Products`  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 W przypadku uruchomienia poprzedniego zapytania względem przykładowej bazy danych Northwind wyniki będą wyglądać następująco:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Zobacz także

- [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
