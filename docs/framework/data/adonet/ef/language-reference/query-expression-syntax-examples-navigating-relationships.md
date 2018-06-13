---
title: 'Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: e4297400bd7e76ca6202748d8f14d478364c1275
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32765493"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a>Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach
Właściwości nawigacji w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są używane do lokalizowania jednostek na końcu skojarzenia właściwości skrótu. Właściwości nawigacji zezwolić użytkownikowi na przechodzenie z jednego obiektu do innego, albo z jednego obiektu do powiązanych jednostek przez skojarzenie ustawiona. W tym temacie przedstawiono przykłady w składni wyrażeń zapytania nawigowanie po relacjach za pośrednictwem właściwości nawigacji w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.  
  
 Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.  
  
 Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metody do pobrania wszystkich kontaktów identyfikatorów i sumy całkowitej ukończenia każdego skontaktuj się z których nazwisko jest "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji jest używany do pobierania kolekcję `SalesOrderHeader` obiektów dla każdego kontakt. `Sum` Używa metody `Contact.SalesOrderHeader` właściwości nawigacji do zsumowania łączną liczbę wszystkich zleceń dla każdego kontakt z powodu.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pobiera wszystkie zamówienia kontaktów, których nazwisko jest "Zhou". `Contact.SalesOrderHeader` Właściwość nawigacji jest używany do pobierania kolekcję `SalesOrderHeader` obiektów dla każdego kontakt. Nazwa kontaktu i zamówienia są zwracane w obrębie typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `SalesOrderHeader.Address` i `SalesOrderHeader.Contact` pobieranie właściwości nawigacji kolekcji z `Address` i `Contact` obiekty skojarzone z każdym kolejności. Nazwisko osoby kontaktowej ulicę, zamówienia sprzedaży, liczby i całkowitej termin dla każdego celu Miasto Seattle są zwracane w obrębie typu anonimowego.  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Where` metody do znalezienia zlecenia, które zostały dokonane po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegółowe informacje dla każdego zlecenia.  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zapytania w składniku LINQ to Entities](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
