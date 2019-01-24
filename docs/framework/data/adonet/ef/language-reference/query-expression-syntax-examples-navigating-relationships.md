---
title: 'Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: ed59a25421f8347c25f80573fa127debf61b4c36
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522248"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach
Właściwości nawigacji w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] właściwości skrótów używana do lokalizowania jednostek na końcach asocjacji. Właściwości nawigacji umożliwia użytkownikowi przechodzić z jednej jednostki do innego lub z jednej jednostki do powiązanych jednostek poprzez skojarzenie zestawu. Ten temat zawiera przykłady składni wyrażeń zapytania na nawigowanie po relacjach za pomocą właściwości nawigacji w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metodę, aby uzyskać cała komunikacja identyfikatorów i Suma całkowita termin każdego skontaktuj się z pomocą o nazwisku "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu. `Sum` Metoda używa `Contact.SalesOrderHeader` właściwość nawigacji, aby zsumować Suma ukończenia wszystkich zamówień dla każdego kontaktu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera wszystkie zamówienia, kontaktów, których nazwisko jest "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu. Nazwa kontaktu i zamówienia są zwracane w typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `SalesOrderHeader.Address` i `SalesOrderHeader.Contact` właściwości nawigacji pobieranie kolekcji z `Address` i `Contact` obiekty skojarzone z każdego zamówienia. Nazwisko kontaktu ulicy, zamówienia sprzedaży, liczby i łączna liczba termin dla każdego zamówienia na Miasto Seattle są zwracane w typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Where` metodę, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegóły dotyczące każdego zamówienia.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Zobacz także
- [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
