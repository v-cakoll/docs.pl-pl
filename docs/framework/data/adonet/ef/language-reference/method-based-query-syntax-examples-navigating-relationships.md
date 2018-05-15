---
title: 'Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 6435cf097b2fab880271d2c79ac8bb1afaf9cb6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="1408c-102">Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="1408c-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="1408c-103">Właściwości nawigacji w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] są używane do lokalizowania jednostek na końcu skojarzenia właściwości skrótu.</span><span class="sxs-lookup"><span data-stu-id="1408c-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="1408c-104">Właściwości nawigacji zezwolić użytkownikowi na przechodzenie z jednego obiektu do innego, albo z jednego obiektu do powiązanych jednostek przez skojarzenie ustawiona.</span><span class="sxs-lookup"><span data-stu-id="1408c-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="1408c-105">W tym temacie przedstawiono przykłady w składni zapytania oparte na metodzie nawigowanie po relacjach za pośrednictwem właściwości nawigacji w [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] zapytania.</span><span class="sxs-lookup"><span data-stu-id="1408c-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="1408c-106">Model sprzedaży AdventureWorks używany w tym przykładzie jest tworzony z kontaktu, adres produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="1408c-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1408c-107">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1408c-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="1408c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1408c-108">Example</span></span>  
 <span data-ttu-id="1408c-109">Poniższy przykład używa składni zapytania oparte na metodzie <xref:System.Linq.Queryable.SelectMany%2A> metodę, aby pobrać wszystkie zamówienia kontaktów, których nazwisko jest "Zhou".</span><span class="sxs-lookup"><span data-stu-id="1408c-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="1408c-110">`Contact.SalesOrderHeader` Właściwość nawigacji jest używany do pobierania kolekcję `SalesOrderHeader` obiektów dla każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="1408c-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="1408c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1408c-111">Example</span></span>  
 <span data-ttu-id="1408c-112">W poniższym przykładzie w składni zapytania oparte na metodzie <xref:System.Linq.Queryable.Select%2A> metody do pobrania wszystkich kontaktów identyfikatorów i sumy całkowitej ukończenia każdego skontaktuj się z których nazwisko jest "Zhou".</span><span class="sxs-lookup"><span data-stu-id="1408c-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="1408c-113">`Contact.SalesOrderHeader` Właściwość nawigacji jest używany do pobierania kolekcję `SalesOrderHeader` obiektów dla każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="1408c-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="1408c-114">`Sum` Używa metody `Contact.SalesOrderHeader` właściwości nawigacji do zsumowania łączną liczbę wszystkich zleceń dla każdego kontakt z powodu.</span><span class="sxs-lookup"><span data-stu-id="1408c-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="1408c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="1408c-115">Example</span></span>  
 <span data-ttu-id="1408c-116">Poniższy przykład w składni zapytania oparte na metodzie pobiera wszystkie zamówienia kontaktów, których nazwisko jest "Zhou".</span><span class="sxs-lookup"><span data-stu-id="1408c-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="1408c-117">`Contact.SalesOrderHeader` Właściwość nawigacji jest używany do pobierania kolekcję `SalesOrderHeader` obiektów dla każdego kontakt.</span><span class="sxs-lookup"><span data-stu-id="1408c-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="1408c-118">Nazwa kontaktu i zamówienia są zwracane w obrębie typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1408c-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="1408c-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="1408c-119">Example</span></span>  
 <span data-ttu-id="1408c-120">W poniższym przykładzie użyto `SalesOrderHeader.Address` i `SalesOrderHeader.Contact` właściwości nawigacji, aby uzyskać kolekcję `Address` i `Contact` obiekty skojarzone z każdym kolejności.</span><span class="sxs-lookup"><span data-stu-id="1408c-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="1408c-121">Nazwisko osoby kontaktowej ulicę, zamówienia sprzedaży, liczby i całkowitej termin dla każdego celu Miasto Seattle są zwracane w obrębie typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="1408c-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="1408c-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="1408c-122">Example</span></span>  
 <span data-ttu-id="1408c-123">W poniższym przykładzie użyto `Where` metody do znalezienia zlecenia, które zostały dokonane po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegółowe informacje dla każdego zlecenia.</span><span class="sxs-lookup"><span data-stu-id="1408c-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="1408c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1408c-124">See Also</span></span>  
 [<span data-ttu-id="1408c-125">Właściwości nawigacji</span><span class="sxs-lookup"><span data-stu-id="1408c-125">Navigation Properties</span></span>](http://msdn.microsoft.com/library/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
 [<span data-ttu-id="1408c-126">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="1408c-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
