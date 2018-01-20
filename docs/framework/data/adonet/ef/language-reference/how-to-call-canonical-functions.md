---
title: "Porady: wywoływać funkcje kanoniczny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 97ad63ea2aeb5ef1ef1acd1988254e995dbc63e0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="b1b12-102">Porady: wywoływać funkcje kanoniczny</span><span class="sxs-lookup"><span data-stu-id="b1b12-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="b1b12-103"><xref:System.Data.Objects.EntityFunctions> Klasa zawiera metody, które udostępniają kanonicznej funkcji do użycia w składniku LINQ do jednostek zapytań.</span><span class="sxs-lookup"><span data-stu-id="b1b12-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="b1b12-104">Aby uzyskać informacje na temat funkcji kanonicznej Zobacz [kanonicznej funkcji](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="b1b12-104">For information about canonical functions, see [Canonical Functions](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b1b12-105"><xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> i <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> metod w <xref:System.Data.Objects.EntityFunctions> klasy nie mają funkcji kanonicznej odpowiedniki.</span><span class="sxs-lookup"><span data-stu-id="b1b12-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="b1b12-106">Canonical funkcje, których wykonywanie obliczeń na zestaw wartości i zwraca pojedynczą wartość (znanej także jako kanonicznej funkcji agregujących) może być wywoływany bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="b1b12-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="b1b12-107">Inne funkcje canonical można wywołać tylko w ramach zapytania składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b1b12-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="b1b12-108">Aby wywołać funkcję agregującą bezpośrednio, należy podać <xref:System.Data.Objects.ObjectQuery%601> funkcji.</span><span class="sxs-lookup"><span data-stu-id="b1b12-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="b1b12-109">Aby uzyskać więcej informacji zobacz drugi przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="b1b12-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="b1b12-110">Niektóre funkcje canonical można wywołać za pomocą wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) metod w składniku LINQ do jednostek zapytań.</span><span class="sxs-lookup"><span data-stu-id="b1b12-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="b1b12-111">Aby uzyskać listę metodach CLR, które mapują kanonicznej funkcji, zobacz [metodę CLR mapowania funkcji kanonicznej](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="b1b12-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](../../../../../../docs/framework/data/adonet/ef/language-reference/clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1b12-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1b12-112">Example</span></span>  
 <span data-ttu-id="b1b12-113">W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="b1b12-113">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="b1b12-114">Przykład wykonuje zapytania składnika LINQ to Entities używającej <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metodę, aby zwrócić wszystkie produkty, dla której to różnica między `SellEndDate` i `SellStartDate` jest mniejsza niż 365 dni:</span><span class="sxs-lookup"><span data-stu-id="b1b12-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="b1b12-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1b12-115">Example</span></span>  
 <span data-ttu-id="b1b12-116">W poniższym przykładzie użyto [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span><span class="sxs-lookup"><span data-stu-id="b1b12-116">The following example uses the [AdventureWorks Sales Model](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span> <span data-ttu-id="b1b12-117">Przykład wywołuje agregacji <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> metody bezpośrednio do Zwróć odchylenie standardowe `SalesOrderHeader` sum częściowych.</span><span class="sxs-lookup"><span data-stu-id="b1b12-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="b1b12-118">Należy pamiętać, że <xref:System.Data.Objects.ObjectQuery%601> została przekazana do funkcji, co umożliwia można wywołać bez części zapytania składnika LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="b1b12-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b1b12-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1b12-119">See Also</span></span>  
 [<span data-ttu-id="b1b12-120">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b1b12-120">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="b1b12-121">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b1b12-121">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
