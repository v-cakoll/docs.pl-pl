---
title: 'Przykłady składni wyrażeń zapytania: Rzut'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 079926c5-e6b5-4fb9-b4cf-9c63886dd626
ms.openlocfilehash: b5139cc310689eb05833ead8d35c03d02eb2fc58
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398418"
---
# <a name="query-expression-syntax-examples-projection"></a><span data-ttu-id="dca87-102">Przykłady składni wyrażeń zapytania: Rzut</span><span class="sxs-lookup"><span data-stu-id="dca87-102">Query Expression Syntax Examples: Projection</span></span>
<span data-ttu-id="dca87-103">W przykładach w tym temacie pokazano, jak za `Select` pomocą metody `From … From …` i słów kluczowych zbadać [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="dca87-103">The examples in this topic demonstrate how to use the `Select` method and the `From … From …` keywords to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="dca87-104">`From … From …`jest odpowiednikiem `SelectMany` metody w oparciu o zapytanie.</span><span class="sxs-lookup"><span data-stu-id="dca87-104">`From … From …` is the query based equivalent of the `SelectMany` method.</span></span> <span data-ttu-id="dca87-105">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dca87-105">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="dca87-106">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="dca87-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="select"></a><span data-ttu-id="dca87-107">Wybierz</span><span class="sxs-lookup"><span data-stu-id="dca87-107">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="dca87-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-108">Example</span></span>  
 <span data-ttu-id="dca87-109">W poniższym przykładzie zastosowano <xref:System.Linq.Enumerable.Select%2A> metodę, aby zwrócić wszystkie wiersze `Product` z tabeli i wyświetlić nazwy produktów.</span><span class="sxs-lookup"><span data-stu-id="dca87-109">The following example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP L2E Examples#SelectSimple1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="dca87-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-110">Example</span></span>  
 <span data-ttu-id="dca87-111">Poniższy przykład używa <xref:System.Linq.Enumerable.Select%2A> do zwracania sekwencji tylko nazw produktów.</span><span class="sxs-lookup"><span data-stu-id="dca87-111">The following example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP L2E Examples#SelectSimple2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectsimple2)]  
  
### <a name="example"></a><span data-ttu-id="dca87-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-112">Example</span></span>  
 <span data-ttu-id="dca87-113">W poniższym przykładzie zastosowano <xref:System.Linq.Queryable.Select%2A> metodę w celu `Product.Name` zaprojektowania właściwości i `Product.ProductID` w sekwencji typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="dca87-113">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to project the `Product.Name` and `Product.ProductID` properties into a sequence of anonymous types.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectanonymoustypes)]
 [!code-vb[DP L2E Examples#SelectAnonymousTypes](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectanonymoustypes)]  
  
## <a name="from--from--selectmany"></a><span data-ttu-id="dca87-114">Z...</span><span class="sxs-lookup"><span data-stu-id="dca87-114">From …</span></span> <span data-ttu-id="dca87-115">Z...</span><span class="sxs-lookup"><span data-stu-id="dca87-115">From …</span></span> <span data-ttu-id="dca87-116">(SelectMany)</span><span class="sxs-lookup"><span data-stu-id="dca87-116">(SelectMany)</span></span>  
  
### <a name="example"></a><span data-ttu-id="dca87-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-117">Example</span></span>  
 <span data-ttu-id="dca87-118">Poniższy przykład używa `From … From …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody), aby wybrać wszystkie zamówienia, których `TotalDue` wartość jest mniejsza niż 500,00.</span><span class="sxs-lookup"><span data-stu-id="dca87-118">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="dca87-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-119">Example</span></span>  
 <span data-ttu-id="dca87-120">W poniższym przykładzie użyto `From … From …` (równoważnej <xref:System.Linq.Enumerable.SelectMany%2A> metodzie), aby wybrać wszystkie zamówienia, w których zamówienie zostało wykonane w dniu 1 października 2002 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="dca87-120">The following example uses `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP L2E Examples#SelectManyCompoundFrom2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="dca87-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="dca87-121">Example</span></span>  
 <span data-ttu-id="dca87-122">W poniższym przykładzie zastosowano `From … From …` (odpowiednik <xref:System.Linq.Enumerable.SelectMany%2A> metody), aby wybrać wszystkie zamówienia, w których suma zamówienia jest większa niż 10000,00, i używa `From` przypisania, aby uniknąć podania łącznej liczby dwa razy.</span><span class="sxs-lookup"><span data-stu-id="dca87-122">The following example uses a `From … From …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP L2E Examples#SelectManyFromAssignment](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="dca87-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dca87-123">See also</span></span>

- [<span data-ttu-id="dca87-124">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="dca87-124">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
