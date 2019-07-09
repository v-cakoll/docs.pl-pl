---
title: Zwracanie lub pomijanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
ms.openlocfilehash: e0f2c6300f8dccb8cc316527af9c75f6a40ff2df
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661895"
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="3d023-102">Zwracanie lub pomijanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="3d023-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="3d023-103">Użyj <xref:System.Linq.Queryable.Take%2A> operatora zwracają danej liczby elementów w sekwencji, a następnie pominąć resztę.</span><span class="sxs-lookup"><span data-stu-id="3d023-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="3d023-104">Użyj <xref:System.Linq.Queryable.Skip%2A> operator, aby pominąć danej liczby elementów w sekwencji, a następnie wróć resztę.</span><span class="sxs-lookup"><span data-stu-id="3d023-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d023-105"><xref:System.Linq.Enumerable.Take%2A> i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="3d023-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="3d023-106">Aby uzyskać więcej informacji, zobacz wpis "Pomiń i Pobierz wyjątki w programie SQL Server 2000 do niego dostępu" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3d023-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d023-107">wykonuje translację <xref:System.Linq.Queryable.Skip%2A> przy użyciu podzapytania SQL `NOT EXISTS` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3d023-107">translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="3d023-108">Tłumaczenie ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="3d023-108">This translation has the following limitations:</span></span>  
  
- <span data-ttu-id="3d023-109">Argument musi być ustawiony.</span><span class="sxs-lookup"><span data-stu-id="3d023-109">The argument must be a set.</span></span> <span data-ttu-id="3d023-110">Multisets nie są obsługiwane, nawet wtedy, gdy określona.</span><span class="sxs-lookup"><span data-stu-id="3d023-110">Multisets are not supported, even if ordered.</span></span>  
  
- <span data-ttu-id="3d023-111">Wygenerowane zapytanie może być znacznie bardziej skomplikowane niż zapytanie wygenerowane dla podstawowego zapytania, na którym <xref:System.Linq.Queryable.Skip%2A> jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="3d023-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="3d023-112">Taki poziom złożoności może spowodować spadek wydajności lub nawet limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="3d023-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d023-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d023-113">Example</span></span>  
 <span data-ttu-id="3d023-114">W poniższym przykładzie użyto `Take` zaznacz pierwsze pięć `Employees` zatrudnienia.</span><span class="sxs-lookup"><span data-stu-id="3d023-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="3d023-115">Należy zauważyć, że kolekcja jest najpierw posortowane według `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="3d023-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="3d023-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d023-116">Example</span></span>  
 <span data-ttu-id="3d023-117">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Skip%2A> zaznacz wszystkie regiony z wyjątkiem 10 najbardziej kosztowne `Products`.</span><span class="sxs-lookup"><span data-stu-id="3d023-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="3d023-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="3d023-118">Example</span></span>  
 <span data-ttu-id="3d023-119">Poniższy przykład łączy <xref:System.Linq.Queryable.Skip%2A> i <xref:System.Linq.Queryable.Take%2A> metody w celu pominięcia 50 pierwszych rekordów, a następnie wróć dalej 10.</span><span class="sxs-lookup"><span data-stu-id="3d023-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="3d023-120"><xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> operacje są dobrze zdefiniowane wyłącznie w odniesieniu do uporządkowanej zestawów.</span><span class="sxs-lookup"><span data-stu-id="3d023-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="3d023-121">Semantyka nieuporządkowane zestawy lub multisets jest niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3d023-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="3d023-122">Ze względu na ograniczenia w kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] spróbuje przenieść porządkowanie argument <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> operatora wynik operatora.</span><span class="sxs-lookup"><span data-stu-id="3d023-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d023-123">Tłumaczenie jest inny dla programu SQL Server 2000 i SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="3d023-123">Translation is different for SQL Server 2000 and SQL Server 2005.</span></span> <span data-ttu-id="3d023-124">Jeśli planujesz używać <xref:System.Linq.Queryable.Skip%2A> z zapytaniem o dowolnej złożoności, użyj programu SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="3d023-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use SQL Server 2005.</span></span>  
  
 <span data-ttu-id="3d023-125">Należy wziąć pod uwagę następujące [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania dla programu SQL Server 2000:</span><span class="sxs-lookup"><span data-stu-id="3d023-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for SQL Server 2000:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3d023-126">Przenosi, to porządkowanie-to-end w języku SQL w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3d023-126">moves the ordering to the end in the SQL code, as follows:</span></span>  
  
```  
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
  
 <span data-ttu-id="3d023-127">Gdy <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są połączone, wszystkie określonej kolejności, muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="3d023-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="3d023-128">W przeciwnym wypadku wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3d023-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="3d023-129">Do nieujemnej wartości, stałe argumentów całkowitych na podstawie SQL specyfikacji, zarówno <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są dobrze zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="3d023-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d023-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d023-130">See also</span></span>

- [<span data-ttu-id="3d023-131">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="3d023-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="3d023-132">Translacja standardowego operatora zapytania</span><span class="sxs-lookup"><span data-stu-id="3d023-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
