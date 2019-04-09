---
title: 'Przykłady składni wyrażeń zapytania: Filtrowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: eb1680ba8ca2fab5511dc20c94ad997ef04974fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134553"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="f5dfe-102">Przykłady składni wyrażeń zapytania: Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="f5dfe-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="f5dfe-103">Przykłady w tym temacie prezentują sposób użycia `Where` i `Where…Contains` metod do wykonywania zapytań [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) przy użyciu składni wyrażeń zapytania.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples) using query expression syntax.</span></span> <span data-ttu-id="f5dfe-104">Zapamiętaj, gdzie...</span><span class="sxs-lookup"><span data-stu-id="f5dfe-104">Note, Where…</span></span>`Contains` <span data-ttu-id="f5dfe-105">Nie można użyć jako części [skompilowany zapytania](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="f5dfe-105">cannot be used as a part of a [compiled query](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="f5dfe-106">Model sprzedaży AdventureWorks używanego w tych przykładach składa się z kontaktu, adres, produktu, SalesOrderHeader i szczegóły zamówienia sprzedaży tabele w przykładowej bazy danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="f5dfe-107">Przykłady w tym temacie należy użyć następującego `using` / `Imports` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="f5dfe-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="f5dfe-108">Gdzie</span><span class="sxs-lookup"><span data-stu-id="f5dfe-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5dfe-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-109">Example</span></span>  
 <span data-ttu-id="f5dfe-110">Poniższy przykład zwraca wszystkie zamówienia online.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="f5dfe-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-111">Example</span></span>  
 <span data-ttu-id="f5dfe-112">Poniższy przykład zwraca zamówienia, w których wielkość zamówienia jest większa niż 2 i mniej niż 6.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="f5dfe-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-113">Example</span></span>  
 <span data-ttu-id="f5dfe-114">Poniższy przykład zwraca wszystkie produkty kolor czerwony.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="f5dfe-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-115">Example</span></span>  
 <span data-ttu-id="f5dfe-116">W poniższym przykładzie użyto `Where` metodę, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie używa `order.SalesOrderDetail` właściwość nawigacji, aby uzyskać szczegóły dotyczące każdego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="f5dfe-117">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="f5dfe-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5dfe-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-118">Example</span></span>  
 <span data-ttu-id="f5dfe-119">W poniższym przykładzie użyto tablicy jako część `Where…Contains` klauzulę, aby znaleźć wszystkie produkty, które mają `ProductModelID` odpowiadającej wartości w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
>  <span data-ttu-id="f5dfe-120">Predykat w ramach `Where…Contains` klauzuli, można użyć <xref:System.Array>, <xref:System.Collections.Generic.List%601>, lub kolekcji dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="f5dfe-121">Można również zadeklarować i zainicjować kolekcję w zapytaniu składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="f5dfe-122">Zobacz przykład dalej, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f5dfe-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5dfe-123">Example</span></span>  
 <span data-ttu-id="f5dfe-124">Poniższy przykład deklaruje i inicjuje tablic w `Where…Contains` klauzulę, aby znaleźć wszystkie produkty, które mają `ProductModelID` lub `Size` pasujących wartości w tablicach.</span><span class="sxs-lookup"><span data-stu-id="f5dfe-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f5dfe-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5dfe-125">See also</span></span>

- [<span data-ttu-id="f5dfe-126">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="f5dfe-126">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
