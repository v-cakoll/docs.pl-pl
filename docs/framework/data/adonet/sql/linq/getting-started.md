---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 3bff4e9f268e9eac84c244cb58eed8b4384e717d
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634696"
---
# <a name="getting-started"></a>Wprowadzenie
Za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]można używać technologii LINQ do uzyskiwania dostępu do baz danych SQL tak samo jak w przypadku dostępu do kolekcji w pamięci.  
  
 Na przykład obiekt `nw` w poniższym kodzie jest tworzony w celu reprezentowania bazy danych `Northwind`, tabela `Customers` jest docelowa, wiersze są filtrowane pod kątem `Customers` z `London`, a do pobrania jest wybierany ciąg dla `CompanyName`.  
  
 Po wykonaniu pętli jest pobierana Kolekcja wartości `CompanyName`.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).  
  
 Na koniec dowiesz się, jak rozpocząć pracę nad własnym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to SQL](index.md)
- [Wprowadzenie do LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
