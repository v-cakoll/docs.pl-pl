---
title: 'Przykłady składni wyrażeń zapytania: Rzut'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: 3e4b30c5d4d1cd5703ff6ec15a1c3fe32e41f42a
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55903736"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="542dd-102">Przykłady składni wyrażeń zapytania: Rzut</span><span class="sxs-lookup"><span data-stu-id="542dd-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="542dd-103">Przykłady w tym temacie prezentują sposób użycia `Select` metody i `From … From …` słów kluczowych, aby wysłać zapytanie [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="542dd-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="542dd-104">`From … From …` jest równoważne z kwerendy na podstawie `SelectMany` metody.</span><span class="sxs-lookup"><span data-stu-id="542dd-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="542dd-105">Model sprzedaży AdventureWorks używanego w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="542dd-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="542dd-106">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="542dd-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="542dd-107">Wybierz</span><span class="sxs-lookup"><span data-stu-id="542dd-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="542dd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-108">Example</span></span>  
 <span data-ttu-id="542dd-109">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> metodę, aby zwrócić wszystkie wiersze z `Product` tabelę i wyświetlić nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="542dd-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="542dd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-110">Example</span></span>  
 <span data-ttu-id="542dd-111">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Select%2A> celu zwrócenia sekwencji tylko nazwy produktu.</span><span class="sxs-lookup"><span data-stu-id="542dd-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="542dd-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-112">Example</span></span>  
 <span data-ttu-id="542dd-113">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Select%2A> metody do projektu `Product.Name` i `Product.ProductID` właściwości sekwencję typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="542dd-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="542dd-114">Od...</span><span class="sxs-lookup"><span data-stu-id="542dd-114">From …</span></span> <span data-ttu-id="542dd-115">Od...</span><span class="sxs-lookup"><span data-stu-id="542dd-115">From …</span></span> <span data-ttu-id="542dd-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="542dd-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="542dd-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-117">Example</span></span>  
 <span data-ttu-id="542dd-118">W poniższym przykładzie użyto `From … From …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby zaznaczyć wszystko porządkuje gdzie `TotalDue` jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="542dd-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="542dd-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-119">Example</span></span>  
 <span data-ttu-id="542dd-120">W poniższym przykładzie użyto `From … From …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby wybrać wszystkie zamówienia, w którym kolejność została wprowadzona w 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="542dd-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="542dd-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="542dd-121">Example</span></span>  
 <span data-ttu-id="542dd-122">W poniższym przykładzie użyto `From … From …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metoda) aby wybrać wszystkie zamówienia, w którym kolejność łączna liczba jest większa niż 10000.00 i używa `From` przypisania, aby uniknąć żądanie Suma dwa razy.</span><span class="sxs-lookup"><span data-stu-id="542dd-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="542dd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="542dd-123">See also</span></span>
- [<span data-ttu-id="542dd-124">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="542dd-124">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
