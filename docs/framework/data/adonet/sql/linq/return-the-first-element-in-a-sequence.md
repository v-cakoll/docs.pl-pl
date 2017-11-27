---
title: Zwraca pierwszy Element w sekwencji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cb43e75ae5cf55df87d00f44aa856d353dd25c0d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-the-first-element-in-a-sequence"></a>Zwraca pierwszy Element w sekwencji
Użyj <xref:System.Linq.Enumerable.First%2A> operatora, aby zwrócić pierwszego elementu w sekwencji. Wysyła zapytanie używające <xref:System.Linq.Enumerable.First%2A> są wykonywane natychmiast.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie obsługuje <xref:System.Linq.Enumerable.Last%2A> operatora.  
  
## <a name="example"></a>Przykład  
 Następujący kod znajduje pierwszy `Shipper` w tabeli:  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod umożliwia znalezienie pojedynczą `Customer` mający `CustomerID` BONAP.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, wyniki są `ID = BONAP, Contact = Laurence Lebihan`.  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
