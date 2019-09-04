---
title: 'Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: c749a7bb1575ee52418f0953ff8216bf4221b674
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250148"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach
Właściwości nawigacji we [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] właściwościach skrótu są używane do lokalizowania jednostek na końcu skojarzenia. Właściwości nawigacji umożliwiają użytkownikowi nawigowanie z jednej jednostki do innej lub z jednej jednostki do powiązanych jednostek za pośrednictwem zestawu skojarzeń. Ten temat zawiera przykłady w składni zapytania opartej na metodzie, w jaki sposób nawigować po relacjach za pomocą właściwości nawigacji w zapytaniach LINQ to Entities.  
  
 Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład w składni zapytania opartej na metodzie używa <xref:System.Linq.Queryable.SelectMany%2A> metody, aby uzyskać wszystkie zamówienia kontaktów, których nazwisko to "Zhou". Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład w składni zapytania opartej na metodzie używa <xref:System.Linq.Queryable.Select%2A> metody, aby uzyskać wszystkie identyfikatory kontaktów i sumę łącznej liczby należnych dla każdego kontaktu, którego nazwisko to "Zhou". Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader` `Sum` Metoda używawłaściwościnawigacji,abyzsumowaćsumęzewszystkich`Contact.SalesOrderHeader` zamówień dla każdego kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład w składni zapytania opartej na metodzie pobiera wszystkie zamówienia kontaktów, których nazwisko to "Zhou". Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader` Nazwa i zamówienia kontaktu są zwracane w typie anonimowym.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano `SalesOrderHeader.Address` właściwości `SalesOrderHeader.Contact` nawigacji i w `Address` celu uzyskania kolekcji i `Contact` obiektów skojarzonych z poszczególnymi kolejnością. Nazwisko osoby kontaktowej, adres ulicy, numer zamówienia sprzedaży oraz suma należna za każde zamówienie do miasta Seattle są zwracane w typie anonimowym.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Where` metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie `order.SalesOrderDetail` użyć właściwości nawigacji, aby uzyskać szczegółowe informacje dotyczące poszczególnych zamówień.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Zobacz także

- [Relacje, właściwości nawigacji i klucze obce](/ef/ef6/fundamentals/relationships)
- [Zapytania w składniku LINQ to Entities](queries-in-linq-to-entities.md)
