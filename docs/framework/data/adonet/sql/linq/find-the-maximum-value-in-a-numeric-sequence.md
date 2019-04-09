---
title: Odnajdywanie wartości maksymalnej w sekwencji numerycznej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70d7c058-0280-4815-a008-6f290093591a
ms.openlocfilehash: b7a2588b9e5082915dff4d371adff2ad3d232d74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122762"
---
# <a name="find-the-maximum-value-in-a-numeric-sequence"></a>Odnajdywanie wartości maksymalnej w sekwencji numerycznej
Użyj <xref:System.Linq.Enumerable.Max%2A> operator, aby znaleźć największą wartość w sekwencji wartości liczbowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie Najpóźniejsza data zatrudnienia dla każdego pracownika.  
  
 Po uruchomieniu tego zapytania względem przykładowej bazy danych Northwind, dane wyjściowe to: `11/15/1994 12:00:00 AM`.  
  
 [!code-csharp[DLinqQueryExamples#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#6)]
 [!code-vb[DLinqQueryExamples#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#6)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia znalezienie większość jednostek w magazynie dla każdego produktu.  
  
 Po uruchomieniu tego przykładu w bazie danych Northwind przykładowe dane wyjściowe to: `125`.  
  
 [!code-csharp[DLinqQueryExamples#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#7)]
 [!code-vb[DLinqQueryExamples#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#7)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto Max można znaleźć `Products` mają najwyższą cena jednostkowa w każdej kategorii. Dane wyjściowe następnie wyświetla wyniki według kategorii.  
  
 [!code-csharp[DLinqQueryExamples#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#8)]
 [!code-vb[DLinqQueryExamples#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#8)]  
  
 Jeśli uruchamiasz poprzednie zapytanie względem przykładowej bazy danych Northwind, wyniki będą wyglądać w następujący sposób:  
  
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

- [Zapytania zagregowane](../../../../../../docs/framework/data/adonet/sql/linq/aggregate-queries.md)
- [Pobieranie przykładowych baz danych](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
