---
title: 'Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: 5ad601330a1f271b3221ae744928bdbad6c4fd7f
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539761"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="5b688-102">Przykłady składni wyrażeń zapytania: Nawigowanie po relacjach</span><span class="sxs-lookup"><span data-stu-id="5b688-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="5b688-103">Właściwości nawigacji w [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] właściwości skrótów używana do lokalizowania jednostek na końcach asocjacji.</span><span class="sxs-lookup"><span data-stu-id="5b688-103">Navigation properties in the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="5b688-104">Właściwości nawigacji umożliwia użytkownikowi przechodzić z jednej jednostki do innego lub z jednej jednostki do powiązanych jednostek poprzez skojarzenie zestawu.</span><span class="sxs-lookup"><span data-stu-id="5b688-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="5b688-105">Ten temat zawiera przykłady składni wyrażeń zapytania na nawigowanie po relacjach za pomocą właściwości nawigacji w składniku LINQ do zapytań jednostki.</span><span class="sxs-lookup"><span data-stu-id="5b688-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="5b688-106">Model sprzedaży AdventureWorks, używany w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="5b688-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5b688-107">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="5b688-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="5b688-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b688-108">Example</span></span>  
 <span data-ttu-id="5b688-109">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metodę, aby uzyskać cała komunikacja identyfikatorów i Suma całkowita termin każdego skontaktuj się z pomocą o nazwisku "Zhou".</span><span class="sxs-lookup"><span data-stu-id="5b688-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="5b688-110">`Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5b688-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="5b688-111">`Sum` Metoda używa `Contact.SalesOrderHeader` właściwość nawigacji, aby zsumować Suma ukończenia wszystkich zamówień dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5b688-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="5b688-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b688-112">Example</span></span>  
 <span data-ttu-id="5b688-113">Poniższy przykład pobiera wszystkie zamówienia, kontaktów, których nazwisko jest "Zhou".</span><span class="sxs-lookup"><span data-stu-id="5b688-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="5b688-114">`Contact.SalesOrderHeader` Właściwość nawigacji służy do uzyskiwania kolekcję `SalesOrderHeader` obiektów dla każdego kontaktu.</span><span class="sxs-lookup"><span data-stu-id="5b688-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="5b688-115">Nazwa kontaktu i zamówienia są zwracane w typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="5b688-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="5b688-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b688-116">Example</span></span>  
 <span data-ttu-id="5b688-117">W poniższym przykładzie użyto `SalesOrderHeader.Address` i `SalesOrderHeader.Contact` właściwości nawigacji pobieranie kolekcji z `Address` i `Contact` obiekty skojarzone z każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="5b688-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="5b688-118">Nazwisko kontaktu ulicy, zamówienia sprzedaży, liczby i łączna liczba termin dla każdego zamówienia na Miasto Seattle są zwracane w typu anonimowego.</span><span class="sxs-lookup"><span data-stu-id="5b688-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="5b688-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b688-119">Example</span></span>  
 <span data-ttu-id="5b688-120">W poniższym przykładzie użyto `Where` metodę, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegóły dotyczące każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="5b688-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="5b688-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b688-121">See also</span></span>

- [<span data-ttu-id="5b688-122">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="5b688-122">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
