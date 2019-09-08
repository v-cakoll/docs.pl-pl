---
title: Odnajdywanie wartości maksymalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: ebef8cb373da4021fd68fd7ce38de8cb06eb81ec
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782171"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Odnajdywanie wartości maksymalnej w sekwencji numerycznej
Użyj operatora <xref:System.Linq.Enumerable.Max%2A> , aby znaleźć najwyższą wartość w sekwencji wartości liczbowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie najnowszej daty zatrudnienia dla każdego pracownika.  
  
 W przypadku uruchomienia tego zapytania względem przykładowej bazy danych Northwind dane wyjściowe to: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład znajduje najwięcej jednostek w magazynie dla każdego produktu.  
  
 W przypadku uruchomienia tego przykładu w przypadku przykładowej bazy danych Northwind dane wyjściowe `125`to:.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano wartość Max, `Products` aby znaleźć wartość, która ma najwyższą cenę jednostkową w każdej kategorii. Następnie dane wyjściowe wyświetlają wyniki według kategorii.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 W przypadku uruchomienia poprzedniego zapytania względem przykładowej bazy danych Northwind wyniki będą wyglądać następująco:  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a>Zobacz także

- [Zapytania zagregowane](aggregate-queries.md)
- [Pobieranie przykładowych baz danych](downloading-sample-databases.md)
