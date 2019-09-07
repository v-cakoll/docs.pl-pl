---
title: 'Instrukcje: Wywoływanie funkcji Canonical'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b3d84873-7403-4957-8e20-b4ae39f50214
ms.openlocfilehash: a1c550b35142cffceeaf08f7d9ff049c766307e0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397566"
---
# <a name="how-to-call-canonical-functions"></a><span data-ttu-id="e2794-102">Instrukcje: Wywoływanie funkcji Canonical</span><span class="sxs-lookup"><span data-stu-id="e2794-102">How to: Call Canonical Functions</span></span>
<span data-ttu-id="e2794-103"><xref:System.Data.Objects.EntityFunctions> Klasa zawiera metody, które uwidaczniają funkcje kanoniczne do użycia w zapytaniach LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e2794-103">The <xref:System.Data.Objects.EntityFunctions> class contains methods that expose canonical functions to use in LINQ to Entities queries.</span></span> <span data-ttu-id="e2794-104">Aby uzyskać informacje o funkcjach kanonicznych, zobacz [funkcje kanoniczne](canonical-functions.md).</span><span class="sxs-lookup"><span data-stu-id="e2794-104">For information about canonical functions, see [Canonical Functions](canonical-functions.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2794-105">Metody <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> i <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> w<xref:System.Data.Objects.EntityFunctions> klasie nie mają odpowiedników funkcji kanonicznych.</span><span class="sxs-lookup"><span data-stu-id="e2794-105">The <xref:System.Data.Objects.EntityFunctions.AsUnicode%2A> and <xref:System.Data.Objects.EntityFunctions.AsNonUnicode%2A> methods in the <xref:System.Data.Objects.EntityFunctions> class do not have canonical function equivalents.</span></span>  
  
 <span data-ttu-id="e2794-106">Funkcje kanoniczne, które wykonują obliczenia na zestawie wartości i zwracają pojedynczą wartość (znaną również jako zagregowane funkcje kanoniczne), mogą być wywoływane bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e2794-106">Canonical functions that perform a calculation on a set of values and return a single value (also known as aggregate canonical functions) can be directly invoked.</span></span> <span data-ttu-id="e2794-107">Inne funkcje kanoniczne można wywołać tylko jako część zapytania LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e2794-107">Other canonical functions can only be called as part of a LINQ to Entities query.</span></span> <span data-ttu-id="e2794-108">Aby wywołać funkcję agregującą bezpośrednio, należy przekazać <xref:System.Data.Objects.ObjectQuery%601> do funkcji.</span><span class="sxs-lookup"><span data-stu-id="e2794-108">To call an aggregate function directly, you must pass an <xref:System.Data.Objects.ObjectQuery%601> to the function.</span></span> <span data-ttu-id="e2794-109">Aby uzyskać więcej informacji, zobacz drugi przykład poniżej.</span><span class="sxs-lookup"><span data-stu-id="e2794-109">For more information, see the second example below.</span></span>  
  
 <span data-ttu-id="e2794-110">Niektóre funkcje kanoniczne można wywołać przy użyciu metod środowiska uruchomieniowego języka wspólnego (CLR) w LINQ to Entities zapytaniach.</span><span class="sxs-lookup"><span data-stu-id="e2794-110">You can call some canonical functions by using common language runtime (CLR) methods in LINQ to Entities queries.</span></span> <span data-ttu-id="e2794-111">Aby zapoznać się z listą metod CLR, które mapują na funkcje kanoniczne, zobacz [Mapowanie funkcji CLR na funkcję kanoniczną](clr-method-to-canonical-function-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="e2794-111">For a list of CLR methods that map to canonical functions, see [CLR Method to Canonical Function Mapping](clr-method-to-canonical-function-mapping.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2794-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2794-112">Example</span></span>  
 <span data-ttu-id="e2794-113">W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="e2794-113">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="e2794-114">Przykład wykonuje kwerendę LINQ to Entities, która używa <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> metody, aby zwrócić wszystkie produkty, dla których różnica między `SellEndDate` i `SellStartDate` jest mniejsza niż 365 dni:</span><span class="sxs-lookup"><span data-stu-id="e2794-114">The example executes a LINQ to Entities query that uses the <xref:System.Data.Objects.EntityFunctions.DiffDays%2A> method to return all products for which the difference between `SellEndDate` and `SellStartDate` is less than 365 days:</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#1)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e2794-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2794-115">Example</span></span>  
 <span data-ttu-id="e2794-116">W poniższym przykładzie jest stosowany [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span><span class="sxs-lookup"><span data-stu-id="e2794-116">The following example uses the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks).</span></span> <span data-ttu-id="e2794-117">Przykład wywołuje metodę Aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> bezpośrednio, aby zwracała odchylenie `SalesOrderHeader` standardowe sum częściowych.</span><span class="sxs-lookup"><span data-stu-id="e2794-117">The example calls the aggregate <xref:System.Data.Objects.EntityFunctions.StandardDeviation%2A> method directly to return the standard deviation of `SalesOrderHeader` subtotals.</span></span> <span data-ttu-id="e2794-118">Należy zauważyć, <xref:System.Data.Objects.ObjectQuery%601> że do funkcji jest przenoszona funkcja, która umożliwia jej wywoływanie bez części zapytania LINQ to Entities.</span><span class="sxs-lookup"><span data-stu-id="e2794-118">Note that an <xref:System.Data.Objects.ObjectQuery%601> is passed to the function, which allows it to be called without being part of a LINQ to Entities query.</span></span>  
  
 [!code-csharp[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e canonicalandstorefunctions/cs/program.cs#2)]
 [!code-vb[DP L2E CanonicalAndStoreFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e canonicalandstorefunctions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e2794-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e2794-119">See also</span></span>

- [<span data-ttu-id="e2794-120">Wywoływanie funkcji w zapytaniach składnika LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e2794-120">Calling Functions in LINQ to Entities Queries</span></span>](calling-functions-in-linq-to-entities-queries.md)
- [<span data-ttu-id="e2794-121">Zapytania w składniku LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="e2794-121">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
