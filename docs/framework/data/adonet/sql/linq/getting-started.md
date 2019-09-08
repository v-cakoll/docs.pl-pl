---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: bd82b7e83149aaa53cf1b240cb79f8747bccba47
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793916"
---
# <a name="getting-started"></a>Wprowadzenie
Korzystając [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]z programu, można [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] uzyskać dostęp do baz danych SQL w taki sam sposób jak w przypadku uzyskania dostępu do kolekcji w pamięci.  
  
 Na przykład `nw` obiekt w poniższym kodzie jest tworzony, aby `Northwind` reprezentować bazę danych, `Customers` tabela `Customers` jest docelowa, wiersze są filtrowane z `London`, a ciąg dla `CompanyName` jest zaznaczony do pobrania.  
  
 Po wykonaniu pętli jest pobierana kolekcja `CompanyName` wartości.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]programu. Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).  
  
 Na koniec dowiesz się, jak rozpocząć pracę nad [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] własnym projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to SQL](index.md)
- [Wprowadzenie do LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
