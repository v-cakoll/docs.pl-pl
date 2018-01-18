---
title: "Sformułować sprzężenia i iloczyn wektorowy zapytania"
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
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5f652f25d04480afb3df1f623347eee23d3ed258
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="2d908-102">Sformułować sprzężenia i iloczyn wektorowy zapytania</span><span class="sxs-lookup"><span data-stu-id="2d908-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="2d908-103">Poniższe przykłady przedstawiają sposób łączenia wyniki z wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="2d908-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d908-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-104">Example</span></span>  
 <span data-ttu-id="2d908-105">W poniższym przykładzie użyto obcego klucza nawigacji w `From` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzuli w języku C#) aby zaznaczyć wszystkich zleceń dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="2d908-105">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="2d908-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-106">Example</span></span>  
 <span data-ttu-id="2d908-107">W poniższym przykładzie użyto obcego klucza nawigacji w `Where` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` klauzuli w języku C#) do filtrowania wyjście z akcji `Products` którego `Supplier` znajduje się w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="2d908-107">The following example uses foreign key navigation in the `Where` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="2d908-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-108">Example</span></span>  
 <span data-ttu-id="2d908-109">W poniższym przykładzie użyto obcego klucza nawigacji w `From` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` klauzuli w języku C#) do filtrowania dla pracowników w Seattle, a z listy ich terytorium.</span><span class="sxs-lookup"><span data-stu-id="2d908-109">The following example uses foreign key navigation in the `From` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="2d908-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-110">Example</span></span>  
 <span data-ttu-id="2d908-111">W poniższym przykładzie użyto obcego klucza nawigacji w `Select` w klauzuli [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` klauzuli w języku C#) do filtrowania dla par pracownikom, gdy pracownik raporty do innych i gdzie jest taka sama zarówno pracowników `City`.</span><span class="sxs-lookup"><span data-stu-id="2d908-111">The following example uses foreign key navigation in the `Select` clause in [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="2d908-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-112">Example</span></span>  
 <span data-ttu-id="2d908-113">Następujące [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] przykład wygląda dla wszystkich klientów i zamówień upewnia się, że zamówienia są dopasowane do klientów, a gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.</span><span class="sxs-lookup"><span data-stu-id="2d908-113">The following [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="2d908-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-114">Example</span></span>  
 <span data-ttu-id="2d908-115">Poniższy przykład jawnie łączy dwie tabele i projekty wyników z obu tabel.</span><span class="sxs-lookup"><span data-stu-id="2d908-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="2d908-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-116">Example</span></span>  
 <span data-ttu-id="2d908-117">Poniższy przykład tworzy sprzężenie jawnie trzy tabele i projekty wyniki każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="2d908-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="2d908-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-118">Example</span></span>  
 <span data-ttu-id="2d908-119">Poniższy przykład przedstawia sposób osiągnięcia `LEFT OUTER JOIN` przy użyciu `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="2d908-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="2d908-120">`DefaultIfEmpty()` Metoda zwraca wartość null, gdy ma nie `Order` dla `Employee`.</span><span class="sxs-lookup"><span data-stu-id="2d908-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="2d908-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-121">Example</span></span>  
 <span data-ttu-id="2d908-122">Następujące przykładowe projekty `let` wyniku w sprzężeniu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2d908-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="2d908-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-123">Example</span></span>  
 <span data-ttu-id="2d908-124">W poniższym przykładzie przedstawiono `join` za pomocą klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="2d908-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="2d908-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d908-125">Example</span></span>  
 <span data-ttu-id="2d908-126">Poniższy przykład przedstawia sposób tworzenia `join` gdzie jednej stronie dopuszcza wartość null, a drugi nie.</span><span class="sxs-lookup"><span data-stu-id="2d908-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="2d908-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d908-127">See Also</span></span>  
 [<span data-ttu-id="2d908-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="2d908-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
