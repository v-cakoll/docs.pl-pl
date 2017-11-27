---
title: "Zwracanym lub Pomiń elementy w sekwencji"
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
ms.assetid: 81a31acd-e0f1-4bca-9a12-fa1ad5752374
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f8fed70e5eafb096ae2e7b2da882e1e4f6c8ed63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-or-skip-elements-in-a-sequence"></a><span data-ttu-id="7cc41-102">Zwracanym lub Pomiń elementy w sekwencji</span><span class="sxs-lookup"><span data-stu-id="7cc41-102">Return Or Skip Elements in a Sequence</span></span>
<span data-ttu-id="7cc41-103">Użyj <xref:System.Linq.Queryable.Take%2A> operatora w celu uzyskania danej liczby elementów w sekwencji, a następnie pominąć resztę.</span><span class="sxs-lookup"><span data-stu-id="7cc41-103">Use the <xref:System.Linq.Queryable.Take%2A> operator to return a given number of elements in a sequence and then skip over the remainder.</span></span>  
  
 <span data-ttu-id="7cc41-104">Użyj <xref:System.Linq.Queryable.Skip%2A> operatora, aby pominąć danej liczby elementów w sekwencji, a następnie wróć resztę.</span><span class="sxs-lookup"><span data-stu-id="7cc41-104">Use the <xref:System.Linq.Queryable.Skip%2A> operator to skip over a given number of elements in a sequence and then return the remainder.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cc41-105"><xref:System.Linq.Enumerable.Take%2A>i <xref:System.Linq.Enumerable.Skip%2A> mają pewne ograniczenia, gdy są one używane w kwerendach do programu SQL Server 2000.</span><span class="sxs-lookup"><span data-stu-id="7cc41-105"><xref:System.Linq.Enumerable.Take%2A> and <xref:System.Linq.Enumerable.Skip%2A> have certain limitations when they are used in queries against SQL Server 2000.</span></span> <span data-ttu-id="7cc41-106">Aby uzyskać więcej informacji, zobacz wpis "Pomiń i podjąć wyjątków w programie SQL Server 2000" w [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="7cc41-106">For more information, see the "Skip and Take Exceptions in SQL Server 2000" entry in [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7cc41-107">wykonuje translację <xref:System.Linq.Queryable.Skip%2A> za pomocą podzapytania SQL `NOT EXISTS` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7cc41-107"> translates <xref:System.Linq.Queryable.Skip%2A> by using a subquery with the SQL `NOT EXISTS` clause.</span></span> <span data-ttu-id="7cc41-108">Tłumaczenie ma następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="7cc41-108">This translation has the following limitations:</span></span>  
  
-   <span data-ttu-id="7cc41-109">Argument musi być ustawiony.</span><span class="sxs-lookup"><span data-stu-id="7cc41-109">The argument must be a set.</span></span> <span data-ttu-id="7cc41-110">Multisets nie są obsługiwane, nawet jeśli uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="7cc41-110">Multisets are not supported, even if ordered.</span></span>  
  
-   <span data-ttu-id="7cc41-111">Wygenerowane zapytanie może być znacznie bardziej skomplikowane niż zapytania wygenerowany dla zapytania bazowego, na którym <xref:System.Linq.Queryable.Skip%2A> została zastosowana.</span><span class="sxs-lookup"><span data-stu-id="7cc41-111">The generated query can be much more complex than the query generated for the base query on which <xref:System.Linq.Queryable.Skip%2A> is applied.</span></span> <span data-ttu-id="7cc41-112">Taki poziom złożoności może spowodować spadek wydajności lub nawet limitu czasu.</span><span class="sxs-lookup"><span data-stu-id="7cc41-112">This complexity can cause decrease in performance or even a time-out.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cc41-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cc41-113">Example</span></span>  
 <span data-ttu-id="7cc41-114">W poniższym przykładzie użyto `Take` Wybierz pierwsze pięć `Employees` dzierżawione.</span><span class="sxs-lookup"><span data-stu-id="7cc41-114">The following example uses `Take` to select the first five `Employees` hired.</span></span> <span data-ttu-id="7cc41-115">Należy pamiętać, że kolekcja jest najpierw posortowane według `HireDate`.</span><span class="sxs-lookup"><span data-stu-id="7cc41-115">Note that the collection is first sorted by `HireDate`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#16](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#16)]
 [!code-vb[DLinqQueryExamples#16](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="7cc41-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cc41-116">Example</span></span>  
 <span data-ttu-id="7cc41-117">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Skip%2A> aby wybrać wszystkie z wyjątkiem 10 najdroższych `Products`.</span><span class="sxs-lookup"><span data-stu-id="7cc41-117">The following example uses <xref:System.Linq.Queryable.Skip%2A> to select all except the 10 most expensive `Products`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#17](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#17)]
 [!code-vb[DLinqQueryExamples#17](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#17)]  
  
## <a name="example"></a><span data-ttu-id="7cc41-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cc41-118">Example</span></span>  
 <span data-ttu-id="7cc41-119">Poniższy przykład łączy <xref:System.Linq.Queryable.Skip%2A> i <xref:System.Linq.Queryable.Take%2A> metody Pomiń pierwsze 50 rekordów, a następnie wróć dalej 10.</span><span class="sxs-lookup"><span data-stu-id="7cc41-119">The following example combines the <xref:System.Linq.Queryable.Skip%2A> and <xref:System.Linq.Queryable.Take%2A> methods to skip the first 50 records and then return the next 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#18](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#18)]
 [!code-vb[DLinqQueryExamples#18](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#18)]  
  
 <span data-ttu-id="7cc41-120"><xref:System.Linq.Queryable.Take%2A>i <xref:System.Linq.Queryable.Skip%2A> operacje są jasno określone tylko względem uporządkowane zestawy.</span><span class="sxs-lookup"><span data-stu-id="7cc41-120"><xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> operations are well defined only against ordered sets.</span></span> <span data-ttu-id="7cc41-121">Semantyka nieuporządkowaną zestawów lub multisets jest niezdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="7cc41-121">The semantics for unordered sets or multisets is undefined.</span></span>  
  
 <span data-ttu-id="7cc41-122">Ze względu na ograniczenia dotyczące kolejności w programie SQL [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbuje przenieść kolejność argument <xref:System.Linq.Queryable.Take%2A> lub <xref:System.Linq.Queryable.Skip%2A> operatora wynik operatora.</span><span class="sxs-lookup"><span data-stu-id="7cc41-122">Because of the limitations on ordering in SQL, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tries to move the ordering of the argument of the <xref:System.Linq.Queryable.Take%2A> or <xref:System.Linq.Queryable.Skip%2A> operator to the result of the operator.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cc41-123">Tłumaczenie jest różne dla [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] i [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cc41-123">Translation is different for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)] and [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span> <span data-ttu-id="7cc41-124">Jeśli planujesz używać <xref:System.Linq.Queryable.Skip%2A> z zapytaniem żadnych złożoności, użyj [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7cc41-124">If you plan to use <xref:System.Linq.Queryable.Skip%2A> with a query of any complexity, use [!INCLUDE[sqprsqlong](../../../../../../includes/sqprsqlong-md.md)].</span></span>  
  
 <span data-ttu-id="7cc41-125">Należy rozważyć [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kwerendy [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="7cc41-125">Consider the following [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query for [!INCLUDE[ss2k](../../../../../../includes/ss2k-md.md)]:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#19](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#19)]
 [!code-vb[DLinqQueryExamples#19](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#19)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7cc41-126">Przenosi kolejności w celu w języku SQL w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="7cc41-126"> moves the ordering to the end in the SQL code, as follows:</span></span>  
  
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
  
 <span data-ttu-id="7cc41-127">Gdy <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są połączone, wszystkie określona kolejność muszą być zgodne.</span><span class="sxs-lookup"><span data-stu-id="7cc41-127">When <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are chained together, all the specified ordering must be consistent.</span></span> <span data-ttu-id="7cc41-128">W przeciwnym razie wyniki są niezdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="7cc41-128">Otherwise, the results are undefined.</span></span>  
  
 <span data-ttu-id="7cc41-129">Dla nieujemną, stałych argumentów całkowitych oparte na specyfikacji SQL zarówno <xref:System.Linq.Queryable.Take%2A> i <xref:System.Linq.Queryable.Skip%2A> są dobrze zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="7cc41-129">For non-negative, constant integral arguments based on the SQL specification, both <xref:System.Linq.Queryable.Take%2A> and <xref:System.Linq.Queryable.Skip%2A> are well-defined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc41-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cc41-130">See Also</span></span>  
 [<span data-ttu-id="7cc41-131">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="7cc41-131">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="7cc41-132">Translacja Operator zapytania standardowe</span><span class="sxs-lookup"><span data-stu-id="7cc41-132">Standard Query Operator Translation</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
