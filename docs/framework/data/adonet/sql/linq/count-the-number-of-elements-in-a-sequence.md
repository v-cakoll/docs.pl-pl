---
title: "Liczba liczba elementów w sekwencji"
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
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 060dec47169adccee10477e1c01d7afb02ab0973
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Liczba liczba elementów w sekwencji
Użyj <xref:System.Linq.Enumerable.Count%2A> operatora, aby określić liczbę elementów w sekwencji.  
  
 Wykonywanie tej kwerendy względem przykładowej bazy danych Northwind generuje dane wyjściowe z `91`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zlicza `Customers` w bazie danych.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zlicza produkty w bazie danych, które nie zostały anulowane.  
  
 Uruchomione w tym przykładzie przed przykładowej bazy danych Northwind generuje dane wyjściowe z `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)  
 [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
