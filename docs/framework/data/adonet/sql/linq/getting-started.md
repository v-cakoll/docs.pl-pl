---
title: Wprowadzenie
description: W tym przykładowym kodzie Rozpocznij korzystanie z LINQ to SQL, aby używać technologii LINQ do uzyskiwania dostępu do baz danych SQL tak samo jak w przypadku dostępu do kolekcji w pamięci.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: a46c42e917bdab0d32ee594bbcd604ee9e3d26bc
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286420"
---
# <a name="getting-started"></a>Wprowadzenie
Korzystając z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , można uzyskać dostęp do baz danych SQL przy użyciu technologii LINQ tak samo jak w przypadku dostępu do kolekcji w pamięci.  
  
 Na przykład `nw` obiekt w poniższym kodzie jest tworzony, aby reprezentować `Northwind` bazę danych, `Customers` tabela jest docelowa, wiersze są filtrowane dla `Customers` z `London` , a ciąg dla `CompanyName` jest wybierany do pobrania.  
  
 Po wykonaniu pętli `CompanyName` jest pobierana Kolekcja wartości.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Aby zapoznać się z dodatkowymi przykładami, w tym wstawianiem i aktualizowaniem, zobacz [co możesz zrobić z LINQ to SQL](what-you-can-do-with-linq-to-sql.md).  
  
 Następnie Wypróbuj niektóre instruktaże i samouczki, aby korzystać z programu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Zobacz [uczenie się według przewodników](learning-by-walkthroughs.md).  
  
 Na koniec dowiesz się, jak rozpocząć pracę nad własnym [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektem, odczytując [typowe kroki dotyczące korzystania z LINQ to SQL](typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to SQL](index.md)
- [Wprowadzenie do LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/index.md)
- [Wprowadzenie do LINQ (Visual Basic)](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)
- [Model obiektu LINQ to SQL](the-linq-to-sql-object-model.md)
