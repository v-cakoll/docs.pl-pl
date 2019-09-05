---
title: 'Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 38a8ddfe4366fefccd0a874a2ad7a20424ef8fac
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249474"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="f5373-102">Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="f5373-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="f5373-103">Właściwości nawigacji we [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] właściwościach skrótu są używane do lokalizowania jednostek na końcu skojarzenia.</span><span class="sxs-lookup"><span data-stu-id="f5373-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="f5373-104">Właściwości nawigacji umożliwiają użytkownikowi nawigowanie z jednej jednostki do innej lub z jednej jednostki do powiązanych jednostek za pośrednictwem zestawu skojarzeń.</span><span class="sxs-lookup"><span data-stu-id="f5373-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="f5373-105">Ten temat zawiera przykłady w składni wyrażenia zapytania dotyczące sposobu nawigowania po relacjach przy użyciu właściwości nawigacji w LINQ to Entities zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="f5373-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="f5373-106">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f5373-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f5373-107">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="f5373-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="f5373-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5373-108">Example</span></span>  
 <span data-ttu-id="f5373-109">W poniższym przykładzie zastosowano <xref:System.Linq.Queryable.Select%2A> metodę, aby pobrać wszystkie identyfikatory kontaktów i sumę łącznej liczby należnych dla każdego kontaktu, którego nazwisko to "Zhou".</span><span class="sxs-lookup"><span data-stu-id="f5373-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="f5373-110">Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="f5373-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="f5373-111">`Sum` Metoda używawłaściwościnawigacji,abyzsumowaćsumęzewszystkich`Contact.SalesOrderHeader` zamówień dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f5373-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="f5373-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5373-112">Example</span></span>  
 <span data-ttu-id="f5373-113">Poniższy przykład pobiera wszystkie zamówienia kontaktów, których nazwisko to "Zhou".</span><span class="sxs-lookup"><span data-stu-id="f5373-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="f5373-114">Właściwość nawigacji służy do pobierania `SalesOrderHeader` kolekcji obiektów dla każdego kontaktu. `Contact.SalesOrderHeader`</span><span class="sxs-lookup"><span data-stu-id="f5373-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="f5373-115">Nazwa i zamówienia kontaktu są zwracane w typie anonimowym.</span><span class="sxs-lookup"><span data-stu-id="f5373-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="f5373-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5373-116">Example</span></span>  
 <span data-ttu-id="f5373-117">W poniższym przykładzie zastosowano `SalesOrderHeader.Address` `Address` właściwości `SalesOrderHeader.Contact` i nawigacji, aby uzyskać kolekcję obiektów `Contact` i skojarzonych z nimi kolejności.</span><span class="sxs-lookup"><span data-stu-id="f5373-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="f5373-118">Nazwisko osoby kontaktowej, adres ulicy, numer zamówienia sprzedaży oraz suma należna za każde zamówienie do miasta Seattle są zwracane w typie anonimowym.</span><span class="sxs-lookup"><span data-stu-id="f5373-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="f5373-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5373-119">Example</span></span>  
 <span data-ttu-id="f5373-120">W poniższym przykładzie użyto `Where` metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie `order.SalesOrderDetail` użyć właściwości nawigacji, aby uzyskać szczegółowe informacje dotyczące poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="f5373-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="f5373-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5373-121">See also</span></span>

- [<span data-ttu-id="f5373-122">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f5373-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
