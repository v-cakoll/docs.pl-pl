---
title: "Grupowanie elementów w sekwencji"
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
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b3cf24760c826cf3dac75305eedb33b732869ff1
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="317cf-102">Grupowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="317cf-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="317cf-103"><xref:System.Linq.Enumerable.GroupBy%2A> Operator grupuje elementy sekwencji.</span><span class="sxs-lookup"><span data-stu-id="317cf-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="317cf-104">Poniższe przykłady użycia bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="317cf-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="317cf-105">Kolumny wartości null <xref:System.Linq.Enumerable.GroupBy%2A> zapytania czasami może zgłosić <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="317cf-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="317cf-106">Aby uzyskać więcej informacji, zobacz sekcję "GroupBy InvalidOperationException" [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="317cf-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="317cf-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-107">Example</span></span>  
 <span data-ttu-id="317cf-108">Następujące partycje przykładowe `Products` przez `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="317cf-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-109">Example</span></span>  
 <span data-ttu-id="317cf-110">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Max%2A> można znaleźć maksymalna jednostka ceny dla każdej `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="317cf-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-111">Example</span></span>  
 <span data-ttu-id="317cf-112">W poniższym przykładzie użyto średnia do obliczenia średniej `UnitPrice` dla każdego `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="317cf-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-113">Example</span></span>  
 <span data-ttu-id="317cf-114">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Sum%2A> można znaleźć łączną liczbę `UnitPrice` dla każdego `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="317cf-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-115">Example</span></span>  
 <span data-ttu-id="317cf-116">W poniższym przykładzie użyto <xref:System.Linq.Queryable.Count%2A> przerywane, aby znaleźć liczbę `Products` w każdym `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="317cf-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-117">Example</span></span>  
 <span data-ttu-id="317cf-118">W poniższym przykładzie użyto następujących `where` klauzuli, aby znaleźć wszystkie kategorie, które mają co najmniej 10 produktów.</span><span class="sxs-lookup"><span data-stu-id="317cf-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="317cf-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-119">Example</span></span>  
 <span data-ttu-id="317cf-120">Poniższy przykład grupy produktów przez `CategoryID` i `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="317cf-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="317cf-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-121">Example</span></span>  
 <span data-ttu-id="317cf-122">Poniższy przykład zwraca dwóch sekwencji produktów.</span><span class="sxs-lookup"><span data-stu-id="317cf-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="317cf-123">Pierwszy sekwencja zawiera produkty z cenie jednostkowej mniejsza lub równa 10.</span><span class="sxs-lookup"><span data-stu-id="317cf-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="317cf-124">Drugi sekwencja zawiera produkty z cenie jednostkowej większe niż 10.</span><span class="sxs-lookup"><span data-stu-id="317cf-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="317cf-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="317cf-125">Example</span></span>  
 <span data-ttu-id="317cf-126"><xref:System.Linq.Queryable.GroupBy%2A> Operator może zająć tylko jeden argument klucza.</span><span class="sxs-lookup"><span data-stu-id="317cf-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="317cf-127">Jeśli potrzebujesz grupy przez więcej niż jednego klucza, należy utworzyć typu anonimowego, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="317cf-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="317cf-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="317cf-128">See Also</span></span>  
 [<span data-ttu-id="317cf-129">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="317cf-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="317cf-130">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="317cf-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
