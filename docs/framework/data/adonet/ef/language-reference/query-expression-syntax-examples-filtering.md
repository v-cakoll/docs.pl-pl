---
title: 'Przykłady składni wyrażeń zapytania: Filtrowanie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 4ce4e28df3a09ddf718b000725afb0c9125bdd77
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397102"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="0685d-102">Przykłady składni wyrażeń zapytania: Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="0685d-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="0685d-103">W przykładach w tym temacie pokazano, `Where` jak za pomocą metod i `Where…Contains` zbadać [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) przy użyciu składni wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="0685d-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="0685d-104">Uwaga, gdzie...`Contains`</span><span class="sxs-lookup"><span data-stu-id="0685d-104">Note, Where…`Contains`</span></span> <span data-ttu-id="0685d-105">nie można użyć jako części [skompilowanego zapytania](compiled-queries-linq-to-entities.md).</span><span class="sxs-lookup"><span data-stu-id="0685d-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="0685d-106">Model sprzedaży AdventureWorks używany w tych przykładach jest tworzony na podstawie tabel Contact, Address, Product, SalesOrderHeader i SalesOrderDetail w przykładowej bazie danych AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0685d-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="0685d-107">Przykłady w tym temacie wykorzystują następujące `using` / `Imports` instrukcje:</span><span class="sxs-lookup"><span data-stu-id="0685d-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="0685d-108">Gdzie</span><span class="sxs-lookup"><span data-stu-id="0685d-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="0685d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-109">Example</span></span>  
 <span data-ttu-id="0685d-110">Poniższy przykład zwraca wszystkie zamówienia online.</span><span class="sxs-lookup"><span data-stu-id="0685d-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="0685d-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-111">Example</span></span>  
 <span data-ttu-id="0685d-112">Poniższy przykład zwraca zamówienia, w których ilość zamówienia jest większa niż 2 i mniejsza niż 6.</span><span class="sxs-lookup"><span data-stu-id="0685d-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="0685d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-113">Example</span></span>  
 <span data-ttu-id="0685d-114">Poniższy przykład zwraca wszystkie kolorowe produkty.</span><span class="sxs-lookup"><span data-stu-id="0685d-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="0685d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-115">Example</span></span>  
 <span data-ttu-id="0685d-116">W poniższym przykładzie użyto `Where` metody, aby znaleźć zamówienia, które zostały wprowadzone po 1 grudnia 2003, a następnie `order.SalesOrderDetail` użyć właściwości nawigacji, aby uzyskać szczegółowe informacje dotyczące poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="0685d-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="0685d-117">Gdzie... Wyświetlana</span><span class="sxs-lookup"><span data-stu-id="0685d-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="0685d-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-118">Example</span></span>  
 <span data-ttu-id="0685d-119">Poniższy przykład używa tablicy jako części `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które `ProductModelID` są zgodne z wartością w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0685d-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="0685d-120">Jako część predykatu w `Where…Contains` klauzuli, można <xref:System.Array>użyć, a <xref:System.Collections.Generic.List%601>lub kolekcji dowolnego typu, który implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejs.</span><span class="sxs-lookup"><span data-stu-id="0685d-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="0685d-121">Można również zadeklarować i zainicjować kolekcję w ramach zapytania LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="0685d-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="0685d-122">Aby uzyskać więcej informacji, zobacz następny przykład.</span><span class="sxs-lookup"><span data-stu-id="0685d-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0685d-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="0685d-123">Example</span></span>  
 <span data-ttu-id="0685d-124">Poniższy przykład deklaruje i inicjuje tablice w `Where…Contains` klauzuli, aby znaleźć wszystkie produkty, które `ProductModelID` mają lub `Size` które pasują do wartości w tablicach.</span><span class="sxs-lookup"><span data-stu-id="0685d-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0685d-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0685d-125">See also</span></span>

- [<span data-ttu-id="0685d-126">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0685d-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
