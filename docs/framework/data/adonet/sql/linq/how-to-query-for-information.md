---
title: 'Instrukcje: Zapytanie dotyczące informacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: ed32bbe7d27357cbed7d77dd235b698a65c0e29e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793536"
---
# <a name="how-to-query-for-information"></a>Instrukcje: Zapytanie dotyczące informacji
Zapytania w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programie używają tej samej składni co zapytania [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]w. Jedyną różnicą jest to, że obiekty, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] do których odwołują się zapytania, są mapowane na elementy w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQC#()](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zapytania zapisane w równoważne zapytania SQL i wysyła je do serwera w celu przetworzenia.  
  
 Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytań mogą wymagać specjalnej uwagi w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacjach. Aby uzyskać więcej informacji, zobacz [pojęcia dotyczące zapytań](query-concepts.md).  
  
## <a name="example"></a>Przykład  
 Poniższe zapytanie pyta o listę klientów z usługi Londyn. W tym przykładzie `Customers` jest to tabela w przykładowej bazie danych Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie modelu obiektu](creating-the-object-model.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
- [Wykonywanie zapytania w bazie danych](querying-the-database.md)
