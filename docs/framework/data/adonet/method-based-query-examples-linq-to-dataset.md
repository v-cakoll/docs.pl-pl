---
title: "Przykłady zapytań — metoda (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d340775c-7f39-4087-a290-5cbec6cfa68e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 313364f71c463a320816bb92113f3b720146fe25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="method-based-query-examples-linq-to-dataset"></a><span data-ttu-id="271d4-102">Przykłady zapytań — metoda (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="271d4-102">Method-Based Query Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="271d4-103">Ta sekcja zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programowania, przykłady w składni zapytania oparte na metodzie, które używają standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="271d4-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in method-based query syntax that use the standard query operators.</span></span> <span data-ttu-id="271d4-104"><xref:System.Data.DataSet> Używane w tym przykładzie jest wypełniany przy użyciu `FillDataSet` metodę, która została określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="271d4-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="271d4-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="271d4-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="271d4-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="271d4-106">In This Section</span></span>  
 [<span data-ttu-id="271d4-107">Projekcja</span><span class="sxs-lookup"><span data-stu-id="271d4-107">Projection</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-projection.md)  
 <span data-ttu-id="271d4-108">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> metod do badania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="271d4-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="271d4-109">Partycjonowanie</span><span class="sxs-lookup"><span data-stu-id="271d4-109">Partitioning</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-partitioning-linq.md)  
 <span data-ttu-id="271d4-110">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> metod do badania <xref:System.Data.DataSet> i partycji wyniki.</span><span class="sxs-lookup"><span data-stu-id="271d4-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="271d4-111">Szeregowanie</span><span class="sxs-lookup"><span data-stu-id="271d4-111">Ordering</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="271d4-112">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, i <xref:System.Linq.Enumerable.ThenByDescending%2A> metod do badania <xref:System.Data.DataSet> i kolejność wyników.</span><span class="sxs-lookup"><span data-stu-id="271d4-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="271d4-113">Operatory zestawu</span><span class="sxs-lookup"><span data-stu-id="271d4-113">Set Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-set-operators.md)  
 <span data-ttu-id="271d4-114">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, i <xref:System.Linq.Enumerable.Union%2A> operatory do wykonywania operacji na podstawie wartości porównania zestawów wierszy danych.</span><span class="sxs-lookup"><span data-stu-id="271d4-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Intersect%2A>, and <xref:System.Linq.Enumerable.Union%2A> operators to perform value-based comparison operations on sets of data rows.</span></span>  
  
 [<span data-ttu-id="271d4-115">Operatory konwersji</span><span class="sxs-lookup"><span data-stu-id="271d4-115">Conversion Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-conversion-operators.md)  
 <span data-ttu-id="271d4-116">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, i <xref:System.Linq.Enumerable.ToList%2A> metod, aby natychmiast wykonać wyrażenia zapytania.</span><span class="sxs-lookup"><span data-stu-id="271d4-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.ToArray%2A>, <xref:System.Linq.Enumerable.ToDictionary%2A>, and <xref:System.Linq.Enumerable.ToList%2A> methods to immediately execute a query expression.</span></span>  
  
 [<span data-ttu-id="271d4-117">Operatory elementu</span><span class="sxs-lookup"><span data-stu-id="271d4-117">Element Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-element-operators.md)  
 <span data-ttu-id="271d4-118">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.First%2A> i <xref:System.Linq.Enumerable.ElementAt%2A> metody w celu uzyskania <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="271d4-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="271d4-119">Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="271d4-119">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="271d4-120">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do badania <xref:System.Data.DataSet> i agregowanie danych.</span><span class="sxs-lookup"><span data-stu-id="271d4-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="271d4-121">Łączenie</span><span class="sxs-lookup"><span data-stu-id="271d4-121">Join</span></span>](../../../../docs/framework/data/adonet/method-based-query-syntax-examples-join-linq-to-dataset.md)  
 <span data-ttu-id="271d4-122">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do badania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="271d4-122">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="271d4-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="271d4-123">See Also</span></span>  
 [<span data-ttu-id="271d4-124">Przykłady wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="271d4-124">Query Expression Examples</span></span>](../../../../docs/framework/data/adonet/query-expression-examples-linq-to-dataset.md)  
 [<span data-ttu-id="271d4-125">Przykłady operatorów specyficznych dla zestawu danych</span><span class="sxs-lookup"><span data-stu-id="271d4-125">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="271d4-126">Przykłady LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="271d4-126">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
