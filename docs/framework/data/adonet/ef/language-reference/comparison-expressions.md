---
title: Wyrażenia porównania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: a37e7e3d0759cb3cf17d2b4cbd3dd2e4877ff6c9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125648"
---
# <a name="comparison-expressions"></a>Wyrażenia porównania
Wyrażenie porównania sprawdza, czy stałą wartość, wartość właściwości lub metody powodują jest równe, nie równe, większe niż lub mniejsze niż inną wartość. Jeśli w danym porównaniu jest nieprawidłowa dla [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], zostanie zgłoszony wyjątek. Wszystkie porównania niejawne i jawne, wymagają, że wszystkie składniki są porównywalne w źródle danych. Porównywanie wyrażeń są często stosowane w `Where` klauzule ograniczania wyników zapytania.  
  
 W składni wyrażenia zapytania poniższy kod przedstawia zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równa "SO43663":  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 W składni zapytania oparte na metodzie poniższy kod przedstawia zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równa "SO43663":  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 W składni wyrażenia zapytania poniższy kod przedstawia zapytanie, które zwraca informację o zamówieniu sprzedaży, w których daty jest równa 8 lipca 2001:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 W składni zapytania oparte na metodzie poniższy kod przedstawia zapytanie, które zwraca informację o zamówieniu sprzedaży, w których daty jest równa 8 lipca 2001:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Wyrażeń, które stałą są konwertowane na serwerze, a próba czy ocena lokalna jest wykonywane. W poniższym przykładzie użyto wyrażenia w `Where` klauzula, która zapewni stałą.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] nie obsługuje przy użyciu klasy użytkownika jako stała. Jednak odwołaniem do właściwości w klasie użytkownika jest uznawany za stałą, zostanie przekonwertowane na wyrażeniu stałym drzewa poleceń i wykonywane w źródle danych.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Metody, które zwracają wyrażenie stałe nie są obsługiwane. Poniższy przykład zawiera metody w `Where` klauzula, która zwraca wartość stałą. W tym przykładzie spowoduje zgłoszenie wyjątku w czasie wykonywania.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
