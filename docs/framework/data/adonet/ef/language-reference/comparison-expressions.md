---
title: Wyrażenia porównania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec7637a9-01d5-4a95-8bb0-478311cd263b
ms.openlocfilehash: d0926bb1a0e35caa058f268f0a0c414e805a8674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251171"
---
# <a name="comparison-expressions"></a>Wyrażenia porównania
Wyrażenie porównania sprawdza, czy wartość stała, wartość właściwości lub wynik metody są równe, nie równe, większe niż lub mniejsze niż inna wartość. Jeśli określone porównanie nie jest prawidłowe dla LINQ to Entities, zostanie zgłoszony wyjątek. Wszystkie porównania, zarówno niejawne, jak i jawne, wymagają, aby wszystkie składniki były porównywalne w źródle danych. Wyrażenia porównania są często używane w `Where` klauzulach ograniczających wyniki zapytania.  
  
 Poniższy przykład w składni wyrażenia zapytania pokazuje zapytanie zwracające wyniki, w przypadku których numer zamówienia sprzedaży jest równy "SO43663":  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression)]  
  
 Poniższy przykład w składni zapytania opartej na metodzie pokazuje zapytanie, które zwraca wyniki, gdzie numer zamówienia sprzedaży jest równy "SO43663":  
  
 [!code-csharp[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#restrictionexpression_mq)]
 [!code-vb[DP L2E Conceptual Examples#RestrictionExpression_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#restrictionexpression_mq)]  
  
 Poniższy przykład w składni wyrażenia zapytania pokazuje zapytanie, które zwraca informacje o zamówieniach sprzedaży, gdzie Data wysyłki jest równa 8 lipca 2001:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison)]  
  
 Poniższy przykład w składni zapytania opartej na metodzie przedstawia zapytanie, które zwraca informacje o zamówieniach sprzedaży, gdzie Data wysyłki jest równa 8 lipca 2001:  
  
 [!code-csharp[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#datetimecomparison_mq)]
 [!code-vb[DP L2E Conceptual Examples#DateTimeComparison_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#datetimecomparison_mq)]  
  
 Wyrażenia, które zwracają stałą, są konwertowane na serwerze i nie ma konieczności przeprowadzania oceny lokalnej. Poniższy przykład używa wyrażenia w `Where` klauzuli, która zwraca stałą.  
  
 [!code-csharp[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#constantexpression)]
 [!code-vb[DP L2E Conceptual Examples#ConstantExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#constantexpression)]  
  
 LINQ to Entities nie obsługuje używania klasy użytkownika jako stałej. Jednak odwołanie do właściwości w klasie użytkownika jest uznawane za stałe i zostanie przekonwertowane na wyrażenie stałe drzewa poleceń i wykonane w źródle danych.  
  
 [!code-csharp[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myclass)]
 [!code-vb[DP L2E Conceptual Examples#MyClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myclass)]  
  
 [!code-csharp[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#propertyasconstant)]
 [!code-vb[DP L2E Conceptual Examples#PropertyAsConstant](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#propertyasconstant)]  
  
 Metody zwracające wyrażenie stałe nie są obsługiwane. Poniższy przykład zawiera metodę w `Where` klauzuli, która zwraca stałą. Ten przykład zgłosi wyjątek w czasie wykonywania.  
  
 [!code-csharp[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#methodasconstantfails)]
 [!code-vb[DP L2E Conceptual Examples#MethodAsConstantFails](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#methodasconstantfails)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia w zapytaniach składnika LINQ to Entities](expressions-in-linq-to-entities-queries.md)
