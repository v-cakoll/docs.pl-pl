---
title: 'Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: 0060f14319bb0dfbed597e59dfe44666c4cfbe84
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854443"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="ef7da-102">Przykłady składni zapytania oparte na metodzie: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="ef7da-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="ef7da-103">Właściwości nawigacji w Entity Framework są właściwościami skrótu używanymi do lokalizowania jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="ef7da-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="ef7da-104">Właściwości nawigacji umożliwiają użytkownikowi nawigowanie z jednej jednostki do innej lub z jednej jednostki do powiązanych jednostek za pośrednictwem zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="ef7da-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="ef7da-105">Ten temat zawiera przykłady w składni zapytania opartej na metodzie, w jaki sposób nawigować po relacjach za pomocą właściwości nawigacji w zapytaniach LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="ef7da-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="ef7da-106">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="ef7da-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="ef7da-107">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="ef7da-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="ef7da-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef7da-108">Example</span></span>  
 <span data-ttu-id="ef7da-109">Poniższy przykład w składni zapytania opartej na metodzie używa <xref:System.Linq.Queryable.SelectMany%2A> metody, aby uzyskać wszystkie zamówienia kontaktów, których nazwisko to "Zhou".</span><span class="sxs-lookup"><span data-stu-id="ef7da-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="ef7da-110">Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="ef7da-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="ef7da-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef7da-111">Example</span></span>  
 <span data-ttu-id="ef7da-112">Poniższy przykład w składni zapytania opartej na metodzie używa <xref:System.Linq.Queryable.Select%2A> metody, aby uzyskać wszystkie identyfikatory kontaktów i sumę łącznej liczby należnych dla każdego kontaktu, którego nazwisko to "Zhou".</span><span class="sxs-lookup"><span data-stu-id="ef7da-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="ef7da-113">Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="ef7da-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="ef7da-114">`Sum` Metoda używawłaściwościnawigacji,abyzsumowaćsumęzewszystkich`Contact.SalesOrderHeader` zamówień dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="ef7da-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="ef7da-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef7da-115">Example</span></span>  
 <span data-ttu-id="ef7da-116">Poniższy przykład w składni zapytania opartej na metodzie pobiera wszystkie zamówienia kontaktów, których nazwisko to "Zhou".</span><span class="sxs-lookup"><span data-stu-id="ef7da-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="ef7da-117">Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="ef7da-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="ef7da-118">Nazwa i zamówienia kontaktu są zwracane w typie anonimowym.</span><span class="sxs-lookup"><span data-stu-id="ef7da-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="ef7da-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef7da-119">Example</span></span>  
 <span data-ttu-id="ef7da-120">W poniższym przykładzie zastosowano `SalesOrderHeader.Address` właściwości `SalesOrderHeader.Contact` nawigacji i w `Address` celu uzyskania kolekcji i `Contact` obiektów skojarzonych z poszczególnymi kolejnością.</span><span class="sxs-lookup"><span data-stu-id="ef7da-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="ef7da-121">Nazwisko osoby kontaktowej, adres ulicy, numer zamówienia sprzedaży oraz suma należna za każde zamówienie do miasta Seattle są zwracane w typie anonimowym.</span><span class="sxs-lookup"><span data-stu-id="ef7da-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="ef7da-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef7da-122">Example</span></span>  
 <span data-ttu-id="ef7da-123">W poniższym przykładzie użyto `Where` metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie `order.SalesOrderDetail` użyć właściwości nawigacji, aby uzyskać szczegółowe informacje dotyczące poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="ef7da-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="ef7da-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef7da-124">See also</span></span>

- [<span data-ttu-id="ef7da-125">Relacje, właściwości nawigacji i klucze obce</span><span class="sxs-lookup"><span data-stu-id="ef7da-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="ef7da-126">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="ef7da-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
