---
title: 'Instrukcje: zapytanie o informacje'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: 3380b486da33a5dc083ed51f6705e666978df197
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634654"
---
# <a name="how-to-query-for-information"></a>Instrukcje: zapytanie o informacje
Zapytania w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] używają tej samej składni co zapytania w LINQ. Jedyną różnicą jest to, że obiekty, do których odwołują się zapytania [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] są mapowane na elementy w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tłumaczy zapytania zapisane w równoważne zapytania SQL i wysyła je do serwera w celu przetworzenia.  
  
 Niektóre funkcje zapytań LINQ mogą wymagać specjalnej uwagi w aplikacjach [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące zapytań](query-concepts.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie pyta o listę klientów z usługi Londyn. W tym przykładzie `Customers` jest tabelą w przykładowej bazie danych Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
