---
title: 'Instrukcje: Zapytanie dotyczące informacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e538d288-2070-40ca-9da6-4fbc68cd6ad0
ms.openlocfilehash: aedf89f1e570b34d31050fabb91842cefe351488
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59162845"
---
# <a name="how-to-query-for-information"></a>Instrukcje: Zapytanie dotyczące informacji
Zapytania w programie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] należy użyć tej samej składni jako zapytania w [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jedyną różnicą jest to, że obiekty do którego odwołuje się [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania są mapowane do elementów w bazie danych. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada zapytania, który zapisane na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia.  
  
 Niektóre funkcje [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] zapytania mogą potrzebować szczególną uwagę w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [kwestie dotyczące zapytań](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie pyta, czy lista klienci z Londynu. W tym przykładzie `Customers` jest tabela w bazie danych Northwind.  
  
 [!code-csharp[DLinqQuerying#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#1)]
 [!code-vb[DLinqQuerying#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Tworzenie modelu obiektu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
