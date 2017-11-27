---
title: "Przykłady wyrażeń zapytania (LINQ do DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f743fbc7-faff-45e5-af1e-61577d87f0cc
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1967575aa7a287064d6da54d929ce095e89ee24f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="query-expression-examples-linq-to-dataset"></a><span data-ttu-id="fa078-102">Przykłady wyrażeń zapytania (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="fa078-102">Query Expression Examples (LINQ to DataSet)</span></span>
<span data-ttu-id="fa078-103">Ta sekcja zawiera [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programowania, przykłady w składni wyrażeń zapytania, które używają standardowych operatorów zapytań.</span><span class="sxs-lookup"><span data-stu-id="fa078-103">This section provides [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] programming examples in query expression syntax that use the standard query operators.</span></span> <span data-ttu-id="fa078-104"><xref:System.Data.DataSet> Używane w tym przykładzie jest wypełniany przy użyciu `FillDataSet` metodę, która została określona w [podczas ładowania danych do zestawu danych](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="fa078-104">The <xref:System.Data.DataSet> used in these examples is populated by using the `FillDataSet` method, which is specified in [Loading Data Into a DataSet](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md).</span></span> <span data-ttu-id="fa078-105">Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span><span class="sxs-lookup"><span data-stu-id="fa078-105">For more information, see [Standard Query Operators Overview](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa078-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fa078-106">In This Section</span></span>  
 [<span data-ttu-id="fa078-107">Projekcji</span><span class="sxs-lookup"><span data-stu-id="fa078-107">Projection</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-projection-linq-to-dataset.md)  
 <span data-ttu-id="fa078-108">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Select%2A> i <xref:System.Linq.Enumerable.SelectMany%2A> metod do badania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fa078-108">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fa078-109">Ograniczenie</span><span class="sxs-lookup"><span data-stu-id="fa078-109">Restriction</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-restriction-linq-to-dataset.md)  
 <span data-ttu-id="fa078-110">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Where%2A> metody query <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fa078-110">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Where%2A> method to query a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fa078-111">Podział na partycje</span><span class="sxs-lookup"><span data-stu-id="fa078-111">Partitioning</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-partitioning.md)  
 <span data-ttu-id="fa078-112">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Skip%2A> i <xref:System.Linq.Enumerable.Take%2A> metod do badania <xref:System.Data.DataSet> i partycji wyniki.</span><span class="sxs-lookup"><span data-stu-id="fa078-112">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods to query a <xref:System.Data.DataSet> and partition the results.</span></span>  
  
 [<span data-ttu-id="fa078-113">Kolejność</span><span class="sxs-lookup"><span data-stu-id="fa078-113">Ordering</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-ordering-linq-to-dataset.md)  
 <span data-ttu-id="fa078-114">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, i <xref:System.Linq.Enumerable.ThenByDescending%2A> metod do badania <xref:System.Data.DataSet> i kolejność wyników.</span><span class="sxs-lookup"><span data-stu-id="fa078-114">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results.</span></span>  
  
 [<span data-ttu-id="fa078-115">Operatory — element</span><span class="sxs-lookup"><span data-stu-id="fa078-115">Element Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-element-operators.md)  
 <span data-ttu-id="fa078-116">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.First%2A> i <xref:System.Linq.Enumerable.ElementAt%2A> metody w celu uzyskania <xref:System.Data.DataRow> elementy z <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fa078-116">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.First%2A> and <xref:System.Linq.Enumerable.ElementAt%2A> methods to get <xref:System.Data.DataRow> elements from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="fa078-117">Operatory agregacji</span><span class="sxs-lookup"><span data-stu-id="fa078-117">Aggregate Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-aggregate-operators.md)  
 <span data-ttu-id="fa078-118">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, i <xref:System.Linq.Enumerable.Sum%2A> metod do badania <xref:System.Data.DataSet> i agregowanie danych.</span><span class="sxs-lookup"><span data-stu-id="fa078-118">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data.</span></span>  
  
 [<span data-ttu-id="fa078-119">Dołącz do operatorów</span><span class="sxs-lookup"><span data-stu-id="fa078-119">Join Operators</span></span>](../../../../docs/framework/data/adonet/query-expression-syntax-examples-join-operators.md)  
 <span data-ttu-id="fa078-120">Przykłady w tym temacie przedstawiają sposób użycia <xref:System.Linq.Enumerable.GroupJoin%2A> i <xref:System.Linq.Enumerable.Join%2A> metod do badania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="fa078-120">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa078-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa078-121">See Also</span></span>  
 [<span data-ttu-id="fa078-122">Przykłady zapytań — metoda</span><span class="sxs-lookup"><span data-stu-id="fa078-122">Method-Based Query Examples</span></span>](../../../../docs/framework/data/adonet/method-based-query-examples-linq-to-dataset.md)  
 [<span data-ttu-id="fa078-123">Przykłady Operator specyficzne dla zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fa078-123">DataSet-Specific Operator Examples</span></span>](../../../../docs/framework/data/adonet/dataset-specific-operator-examples-linq-to-dataset.md)  
 [<span data-ttu-id="fa078-124">LINQ do DataSet przykłady</span><span class="sxs-lookup"><span data-stu-id="fa078-124">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
