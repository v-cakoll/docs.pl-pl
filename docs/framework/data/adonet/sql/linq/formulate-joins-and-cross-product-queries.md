---
title: Sformułować sprzężenia i iloczyn wektorowy zapytania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 20b46ce37d93119330e336f583ac68b5c1dc4c4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360264"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="c46de-102">Sformułować sprzężenia i iloczyn wektorowy zapytania</span><span class="sxs-lookup"><span data-stu-id="c46de-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="c46de-103">Poniższe przykłady przedstawiają sposób łączenia wyniki z wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="c46de-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c46de-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-104">Example</span></span>  
 <span data-ttu-id="c46de-105">W poniższym przykładzie użyto obcego klucza nawigacji w `From` klauzuli w języku Visual Basic (`from` klauzuli w języku C#) aby zaznaczyć wszystkich zleceń dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="c46de-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="c46de-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-106">Example</span></span>  
 <span data-ttu-id="c46de-107">W poniższym przykładzie użyto obcego klucza nawigacji w `Where` klauzuli w języku Visual Basic (`where` klauzuli w języku C#) do filtrowania wyjście z akcji `Products` którego `Supplier` znajduje się w Stanach Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="c46de-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="c46de-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-108">Example</span></span>  
 <span data-ttu-id="c46de-109">W poniższym przykładzie użyto obcego klucza nawigacji w `From` klauzuli w języku Visual Basic (`from` klauzuli w języku C#) do filtrowania dla pracowników w Seattle, a z listy ich terytorium.</span><span class="sxs-lookup"><span data-stu-id="c46de-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="c46de-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-110">Example</span></span>  
 <span data-ttu-id="c46de-111">W poniższym przykładzie użyto obcego klucza nawigacji w `Select` klauzuli w języku Visual Basic (`select` klauzuli w języku C#) do filtrowania dla par pracownikom, gdy pracownik raporty do innych i gdzie jest taka sama zarówno pracowników `City`.</span><span class="sxs-lookup"><span data-stu-id="c46de-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="c46de-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-112">Example</span></span>  
 <span data-ttu-id="c46de-113">W poniższym przykładzie w języku Visual Basic wygląda dla wszystkich klientów i zamówień upewnia się, że zamówienia są dopasowane do klientów i gwarantuje, że dla każdego klienta na tej liście podano nazwę kontaktu.</span><span class="sxs-lookup"><span data-stu-id="c46de-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="c46de-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-114">Example</span></span>  
 <span data-ttu-id="c46de-115">Poniższy przykład jawnie łączy dwie tabele i projekty wyników z obu tabel.</span><span class="sxs-lookup"><span data-stu-id="c46de-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="c46de-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-116">Example</span></span>  
 <span data-ttu-id="c46de-117">Poniższy przykład tworzy sprzężenie jawnie trzy tabele i projekty wyniki każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="c46de-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="c46de-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-118">Example</span></span>  
 <span data-ttu-id="c46de-119">Poniższy przykład przedstawia sposób osiągnięcia `LEFT OUTER JOIN` przy użyciu `DefaultIfEmpty()`.</span><span class="sxs-lookup"><span data-stu-id="c46de-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="c46de-120">`DefaultIfEmpty()` Metoda zwraca wartość null, gdy ma nie `Order` dla `Employee`.</span><span class="sxs-lookup"><span data-stu-id="c46de-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="c46de-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-121">Example</span></span>  
 <span data-ttu-id="c46de-122">Następujące przykładowe projekty `let` wyniku w sprzężeniu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c46de-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="c46de-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-123">Example</span></span>  
 <span data-ttu-id="c46de-124">W poniższym przykładzie przedstawiono `join` za pomocą klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="c46de-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="c46de-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="c46de-125">Example</span></span>  
 <span data-ttu-id="c46de-126">Poniższy przykład przedstawia sposób tworzenia `join` gdzie jednej stronie dopuszcza wartość null, a drugi nie.</span><span class="sxs-lookup"><span data-stu-id="c46de-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="c46de-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c46de-127">See Also</span></span>  
 [<span data-ttu-id="c46de-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="c46de-128">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
