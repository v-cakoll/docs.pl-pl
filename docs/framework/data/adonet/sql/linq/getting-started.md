---
title: Wprowadzenie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: db8a557a-fef8-4f4f-bb91-8cff7250ee25
ms.openlocfilehash: 7ddecf910b5f76fdb5e75300118fa0a063269116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556405"
---
# <a name="getting-started"></a>Wprowadzenie
Za pomocą [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], możesz użyć [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] technologii SQL dostęp do bazy danych tak, jak dostęp do kolekcji w pamięci.  
  
 Na przykład `nw` obiekt w poniższym kodzie zostanie utworzony do reprezentowania `Northwind` bazy danych, `Customers` podlega tabeli, wiersze zostały przefiltrowane pod kątem `Customers` z `London`i ciąg `CompanyName` jest zaznaczone do pobrania.  
  
 Po wykonaniu pętli, pobieranie `CompanyName` wartości są pobierane.  
  
 [!code-csharp[DLinqGettingStarted#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqGettingStarted/cs/Program.cs#1)]
 [!code-vb[DLinqGettingStarted#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqGettingStarted/vb/Module1.vb#1)]  
  
## <a name="next-steps"></a>Następne kroki  
 Niektóre dodatkowe przykłady, w tym wstawiania i aktualizowania, można znaleźć [co użytkownik może zrobić za pomocą LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/what-you-can-do-with-linq-to-sql.md).  
  
 Następnie spróbuj wykonać niektóre wskazówki i samouczki ułatwiające praktyczne doświadczenie korzystania z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Zobacz [nauka przez przewodniki](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
 Ponadto Dowiedz się, jak rozpocząć pracę na własną rękę [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projektu, czytając [typowe etapy za pomocą LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md).  
  
## <a name="see-also"></a>Zobacz także
- [LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [Wprowadzenie do LINQ](https://msdn.microsoft.com/library/24dddf19-12a0-4707-a4bc-eba4fa7f219e)
- [Model obiektu LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
