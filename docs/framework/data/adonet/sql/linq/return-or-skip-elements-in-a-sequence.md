---
title: Zwracanie lub pomijanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: 7c98681493738b4e94ed14417fa1437efb6c12ac
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003311"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="8fab4-102">Zwracanie lub pomijanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="8fab4-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="8fab4-103">Użyj operatora <xref:System.Linq.Queryable.Take%2A>, aby zwrócić daną liczbę elementów w sekwencji, a następnie pominąć resztę.</span><span class="sxs-lookup"><span data-stu-id="8fab4-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="8fab4-104">Użyj operatora <xref:System.Linq.Queryable.Skip%2A>, aby pominąć daną liczbę elementów w sekwencji, a następnie zwrócić resztę.</span><span class="sxs-lookup"><span data-stu-id="8fab4-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fab4-105"><xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są używane w zapytaniach do SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="8fab4-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="8fab4-106">Aby uzyskać więcej informacji, zobacz wpis "Pomiń i przejmowanie wyjątków w SQL Server 2000" w [temacie Rozwiązywanie problemów](troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="8fab4-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8fab4-107">tłumaczy <xref:System.Linq.Queryable.Skip%2A> za pomocą podzapytania z klauzulą SQL `NOT EXISTS`.</span><span class="sxs-lookup"><span data-stu-id="8fab4-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="8fab4-108">To tłumaczenie ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="8fab4-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="8fab4-109">Argument musi być zestawem.</span><span class="sxs-lookup"><span data-stu-id="8fab4-109">The argument must be a set.</span></span> <span data-ttu-id="8fab4-110">Zestawy wielozbiorowe nie są obsługiwane, nawet jeśli są uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="8fab4-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="8fab4-111">Wygenerowane zapytanie może być znacznie bardziej złożone niż zapytanie wygenerowane dla zapytania podstawowego, w którym zastosowano <xref:System.Linq.Queryable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fab4-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="8fab4-112">Taka złożoność może spowodować spadek wydajności lub nawet przekroczenie limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="8fab4-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fab4-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fab4-113">Example</span></span>  
 <span data-ttu-id="8fab4-114">Poniższy przykład używa `Take` w celu wybrania pięciu pierwszych `Employees` zatrudnienia.</span><span class="sxs-lookup"><span data-stu-id="8fab4-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="8fab4-115">Należy pamiętać, że kolekcja jest najpierw posortowana według `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="8fab4-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="8fab4-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fab4-116">Example</span></span>  
 <span data-ttu-id="8fab4-117">Poniższy przykład używa <xref:System.Linq.Queryable.Skip%2A>, aby zaznaczyć wszystko z wyjątkiem 10 najtańszych `Products`.</span><span class="sxs-lookup"><span data-stu-id="8fab4-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="8fab4-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="8fab4-118">Example</span></span>  
 <span data-ttu-id="8fab4-119">Poniższy przykład łączy metody <xref:System.Linq.Queryable.Skip%2A> i <xref:System.Linq.Queryable.Take%2A>, aby pominąć pierwsze 50 rekordów, a następnie zwrócić następny 10.</span><span class="sxs-lookup"><span data-stu-id="8fab4-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="8fab4-120">operacje <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są dobrze zdefiniowane tylko w odniesieniu do uporządkowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="8fab4-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="8fab4-121">Semantyka nieuporządkowanych zestawów lub zestawów wielozbiorówowych jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8fab4-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="8fab4-122">Ze względu na ograniczenia dotyczące porządkowania w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przenieść argument operatora <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> do wyniku operatora.</span><span class="sxs-lookup"><span data-stu-id="8fab4-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fab4-123">Tłumaczenie jest różne dla SQL Server 2000 i SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="8fab4-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="8fab4-124">Jeśli planujesz używać <xref:System.Linq.Queryable.Skip%2A> z kwerendą złożoną, użyj SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="8fab4-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="8fab4-125">Należy wziąć pod uwagę następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania dla SQL Server 2000:</span><span class="sxs-lookup"><span data-stu-id="8fab4-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="8fab4-126">przesuwa porządkowanie do końca kodu SQL w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8fab4-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```sql
SELECT TOP 1 [t0].[CustomerID], [t0].[CompanyName],  
FROM [Customers] AS [t0]  
WHERE (NOT (EXISTS(  
    SELECT NULL AS [EMPTY]  
    FROM (  
        SELECT TOP 1 [t1].[CustomerID]  
        FROM [Customers] AS [t1]  
        WHERE [t1].[City] = @p0  
        ORDER BY [t1].[CustomerID]  
        ) AS [t2]  
    WHERE [t0].[CustomerID] = [t2].[CustomerID]  
    ))) AND ([t0].[City] = @p1)  
ORDER BY [t0].[CustomerID]  
```  
  
 <span data-ttu-id="8fab4-127">Gdy <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są powiązane ze sobą, cała określona kolejność musi być spójna.</span><span class="sxs-lookup"><span data-stu-id="8fab4-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="8fab4-128">W przeciwnym razie wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="8fab4-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="8fab4-129">W przypadku nieujemnych, stałych argumentów całkowitych opartych na specyfikacji SQL należy prawidłowo zdefiniować obie <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A>.</span><span class="sxs-lookup"><span data-stu-id="8fab4-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fab4-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fab4-130">See also</span></span>

- [<span data-ttu-id="8fab4-131">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="8fab4-131">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="8fab4-132">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="8fab4-132">Standard Query Operator Translation</span></span>](standard-query-operator-translation.md)
