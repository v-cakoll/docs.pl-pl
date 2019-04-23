---
title: Licznik liczby elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccbe5d54-c9eb-4b14-b0ab-f628483c5f99
ms.openlocfilehash: b39b0a1487c9f250e32b13330f2f70b7e3c7c877
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59209531"
---
# <a name="count-the-number-of-elements-in-a-sequence"></a>Licznik liczby elementów w sekwencji
Użyj <xref:System.Linq.Enumerable.Count%2A> operator, aby określić liczbę elementów w sekwencji.  
  
 Uruchomienie tego zapytania względem przykładowej bazy danych Northwind generuje dane wyjściowe `91`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zlicza `Customers` w bazie danych.  
  
 [!code-csharp[DLinqQueryExamples#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#4)]
 [!code-vb[DLinqQueryExamples#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zlicza produkty w bazie danych, które nie zostały wycofane.  
  
 Działających w tym przykładzie w odniesieniu do przykładowej bazy danych Northwind generuje dane wyjściowe `69`.  
  
 [!code-csharp[DLinqQueryExamples#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#5)]
 [!code-vb[DLinqQueryExamples#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
