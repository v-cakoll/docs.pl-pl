---
title: 'Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 9f2dced10b9d5e8326dcfd25a105e44cfc68573c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499955"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a>Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach
Właściwości nawigacji w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] właściwości skrótów używana do lokalizowania jednostek na końcach asocjacji. Właściwości nawigacji umożliwia użytkownikowi przechodzić z jednej jednostki do innego lub z jednej jednostki do powiązanych jednostek poprzez skojarzenie zestawu. Ten temat zawiera przykłady składni zapytania oparte na metodzie na nawigowanie po relacjach za pomocą właściwości nawigacji w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa składni zapytania oparte na metodzie <xref:System.Linq.Queryable.SelectMany%2A> metodę, aby pobrać wszystkie zamówienia, kontaktów, których nazwisko jest "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przy użyciu składni zapytania oparte na metodzie <xref:System.Linq.Queryable.Select%2A> metodę, aby uzyskać cała komunikacja identyfikatorów i Suma całkowita termin każdego skontaktuj się z pomocą o nazwisku "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu. `Sum` Metoda używa `Contact.SalesOrderHeader` właściwość nawigacji, aby zsumować Suma ukończenia wszystkich zamówień dla każdego kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przy użyciu składni zapytania oparte na metodzie pobiera wszystkie zamówienia, kontaktów, których nazwisko jest "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu. Nazwa kontaktu i zamówienia są zwracane w typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `SalesOrderHeader.Address` i `SalesOrderHeader.Contact` właściwości nawigacji, aby uzyskać kolekcję `Address` i `Contact` obiekty skojarzone z każdego zamówienia. Nazwisko kontaktu ulicy, zamówienia sprzedaży, liczby i łączna liczba termin dla każdego zamówienia na Miasto Seattle są zwracane w typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Where` metodę, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegóły dotyczące każdego zamówienia.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Zobacz też  
 [Właściwości nawigacji](https://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
