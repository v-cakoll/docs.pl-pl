---
title: Grupowanie elementów w sekwencji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1d50c8b4-f550-4775-bbb6-eab6e874cb43
ms.openlocfilehash: 50887acefdd5d0feaf9d0885e9ee842f44f0ef65
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915056"
---
# <a name="group-elements-in-a-sequence"></a><span data-ttu-id="91fec-102">Grupowanie elementów w sekwencji</span><span class="sxs-lookup"><span data-stu-id="91fec-102">Group Elements in a Sequence</span></span>
<span data-ttu-id="91fec-103"><xref:System.Linq.Enumerable.GroupBy%2A> Operator Grupuje elementy sekwencji.</span><span class="sxs-lookup"><span data-stu-id="91fec-103">The <xref:System.Linq.Enumerable.GroupBy%2A> operator groups the elements of a sequence.</span></span> <span data-ttu-id="91fec-104">W poniższych przykładach użyto bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="91fec-104">The following examples use the Northwind database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91fec-105">Wartości pustej kolumny <xref:System.Linq.Enumerable.GroupBy%2A> w zapytaniach mogą <xref:System.InvalidOperationException>czasami zgłosić.</span><span class="sxs-lookup"><span data-stu-id="91fec-105">Null column values in <xref:System.Linq.Enumerable.GroupBy%2A> queries can sometimes throw an <xref:System.InvalidOperationException>.</span></span> <span data-ttu-id="91fec-106">Aby uzyskać więcej informacji, zobacz sekcję "GroupBy InvalidOperationException" w temacie [Rozwiązywanie problemów](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="91fec-106">For more information, see the "GroupBy InvalidOperationException" section of [Troubleshooting](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91fec-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-107">Example</span></span>  
 <span data-ttu-id="91fec-108">Poniższy przykład partycjonowania `Products` przez `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="91fec-108">The following example partitions `Products` by `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#27](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#27)]
 [!code-vb[DLinqQueryExamples#27](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#27)]  
  
## <a name="example"></a><span data-ttu-id="91fec-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-109">Example</span></span>  
 <span data-ttu-id="91fec-110">Poniższy przykład używa <xref:System.Linq.Enumerable.Max%2A> , aby znaleźć maksymalną cenę jednostkową dla każdej `CategoryID`z nich.</span><span class="sxs-lookup"><span data-stu-id="91fec-110">The following example uses <xref:System.Linq.Enumerable.Max%2A> to find the maximum unit price for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#28](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#28)]
 [!code-vb[DLinqQueryExamples#28](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#28)]  
  
## <a name="example"></a><span data-ttu-id="91fec-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-111">Example</span></span>  
 <span data-ttu-id="91fec-112">W poniższym przykładzie zastosowano średnią, aby `UnitPrice` znaleźć średnią dla każdej z nich. `CategoryID`</span><span class="sxs-lookup"><span data-stu-id="91fec-112">The following example uses Average to find the average `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#29](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#29)]
 [!code-vb[DLinqQueryExamples#29](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="91fec-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-113">Example</span></span>  
 <span data-ttu-id="91fec-114">Poniższy przykład używa <xref:System.Linq.Queryable.Sum%2A> , aby znaleźć sumę `UnitPrice` dla każdej z `CategoryID`nich.</span><span class="sxs-lookup"><span data-stu-id="91fec-114">The following example uses <xref:System.Linq.Queryable.Sum%2A> to find the total `UnitPrice` for each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#30](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#30)]
 [!code-vb[DLinqQueryExamples#30](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="91fec-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-115">Example</span></span>  
 <span data-ttu-id="91fec-116">Poniższy przykład używa <xref:System.Linq.Queryable.Count%2A> , aby znaleźć liczbę `Products` wycofanych w każdym z nich `CategoryID`.</span><span class="sxs-lookup"><span data-stu-id="91fec-116">The following example uses <xref:System.Linq.Queryable.Count%2A> to find the number of discontinued `Products` in each `CategoryID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#31](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#31)]
 [!code-vb[DLinqQueryExamples#31](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="91fec-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-117">Example</span></span>  
 <span data-ttu-id="91fec-118">W poniższym przykładzie zastosowano następującą `where` klauzulę, aby znaleźć wszystkie kategorie, które mają co najmniej 10 produktów.</span><span class="sxs-lookup"><span data-stu-id="91fec-118">The following example uses a following `where` clause to find all categories that have at least 10 products.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#32](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#32)]
 [!code-vb[DLinqQueryExamples#32](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#32)]  
  
## <a name="example"></a><span data-ttu-id="91fec-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-119">Example</span></span>  
 <span data-ttu-id="91fec-120">Poniższy przykład grupuje produkty według `CategoryID` i `SupplierID`.</span><span class="sxs-lookup"><span data-stu-id="91fec-120">The following example groups products by `CategoryID` and `SupplierID`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#33](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#33)]
 [!code-vb[DLinqQueryExamples#33](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#33)]  
  
## <a name="example"></a><span data-ttu-id="91fec-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-121">Example</span></span>  
 <span data-ttu-id="91fec-122">Poniższy przykład zwraca dwie sekwencje produktów.</span><span class="sxs-lookup"><span data-stu-id="91fec-122">The following example returns two sequences of products.</span></span> <span data-ttu-id="91fec-123">Pierwsza sekwencja zawiera produkty z ceną jednostkową mniejszą lub równą 10.</span><span class="sxs-lookup"><span data-stu-id="91fec-123">The first sequence contains products with unit price less than or equal to 10.</span></span> <span data-ttu-id="91fec-124">Druga sekwencja zawiera produkty z ceną jednostkową większą niż 10.</span><span class="sxs-lookup"><span data-stu-id="91fec-124">The second sequence contains products with unit price greater than 10.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#34](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#34)]
 [!code-vb[DLinqQueryExamples#34](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#34)]  
  
## <a name="example"></a><span data-ttu-id="91fec-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="91fec-125">Example</span></span>  
 <span data-ttu-id="91fec-126"><xref:System.Linq.Queryable.GroupBy%2A> Operator może przyjmować tylko jeden argument klucza.</span><span class="sxs-lookup"><span data-stu-id="91fec-126">The <xref:System.Linq.Queryable.GroupBy%2A> operator can take only a single key argument.</span></span> <span data-ttu-id="91fec-127">Jeśli zachodzi potrzeba pogrupowania przez więcej niż jeden klucz, należy utworzyć typ anonimowy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91fec-127">If you need to group by more than one key, you must create an anonymous type, as in the following example:</span></span>  
  
 [!code-csharp[DLinqQueryExamples#35](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#35)]
 [!code-vb[DLinqQueryExamples#35](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#35)]  
  
## <a name="see-also"></a><span data-ttu-id="91fec-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91fec-128">See also</span></span>

- [<span data-ttu-id="91fec-129">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="91fec-129">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="91fec-130">Pobieranie przykładowych baz danych</span><span class="sxs-lookup"><span data-stu-id="91fec-130">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
