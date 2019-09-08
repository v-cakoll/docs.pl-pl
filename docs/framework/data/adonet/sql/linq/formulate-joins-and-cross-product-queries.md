---
title: Formułowanie połączeń i zapytań między produktami
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8072ede-0521-4670-9bec-1778ceeb875b
ms.openlocfilehash: 002a644ff5d48b25351228dcd74330707491d6c8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782093"
---
# <a name="formulate-joins-and-cross-product-queries"></a><span data-ttu-id="1d890-102">Formułowanie połączeń i zapytań między produktami</span><span class="sxs-lookup"><span data-stu-id="1d890-102">Formulate Joins and Cross-Product Queries</span></span>
<span data-ttu-id="1d890-103">W poniższych przykładach pokazano, jak połączyć wyniki z wielu tabel.</span><span class="sxs-lookup"><span data-stu-id="1d890-103">The following examples show how to combine results from multiple tables.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d890-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-104">Example</span></span>  
 <span data-ttu-id="1d890-105">Poniższy przykład używa nawigacji klucza obcego w `From` klauzuli w Visual Basic (`from` klauzula in C#), aby wybrać wszystkie zamówienia dla klientów w Londynie.</span><span class="sxs-lookup"><span data-stu-id="1d890-105">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to select all orders for customers in London.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#47](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#47)]
 [!code-vb[DLinqQueryExamples#47](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#47)]  
  
## <a name="example"></a><span data-ttu-id="1d890-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-106">Example</span></span>  
 <span data-ttu-id="1d890-107">W poniższym przykładzie jest używana Nawigacja klucza obcego w `Where` klauzuli w Visual Basic (`where` klauzula in C#), aby odfiltrować elementy poza `Products` magazynem `Supplier` , których wartość znajduje się w Stany Zjednoczone.</span><span class="sxs-lookup"><span data-stu-id="1d890-107">The following example uses foreign key navigation in the `Where` clause in Visual Basic (`where` clause in C#) to filter for out-of-stock `Products` whose `Supplier` is in the United States.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#48](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#48)]
 [!code-vb[DLinqQueryExamples#48](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#48)]  
  
## <a name="example"></a><span data-ttu-id="1d890-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-108">Example</span></span>  
 <span data-ttu-id="1d890-109">Poniższy przykład używa nawigacji klucza obcego w `From` klauzuli w Visual Basic (`from` klauzula in C#), aby odfiltrować pracowników w Seattle i wyświetlić listę ich terytoriów.</span><span class="sxs-lookup"><span data-stu-id="1d890-109">The following example uses foreign key navigation in the `From` clause in Visual Basic (`from` clause in C#) to filter for employees in Seattle and to list their territories.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#49](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#49)]  
  
## <a name="example"></a><span data-ttu-id="1d890-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-110">Example</span></span>  
 <span data-ttu-id="1d890-111">W poniższym przykładzie jest używana Nawigacja klucza obcego w `Select` klauzuli w Visual Basic (`select` klauzula in C#), aby odfiltrować pary pracowników, w których jeden pracownik raportuje do drugiego i gdzie oba pracownicy są `City`z tego samego.</span><span class="sxs-lookup"><span data-stu-id="1d890-111">The following example uses foreign key navigation in the `Select` clause in Visual Basic (`select` clause in C#) to filter for pairs of employees where one employee reports to the other and where both employees are from the same `City`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#50](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#50)]
 [!code-vb[DLinqQueryExamples#50](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50)]  
  
## <a name="example"></a><span data-ttu-id="1d890-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-112">Example</span></span>  
 <span data-ttu-id="1d890-113">Poniższy Visual Basic przykład szuka wszystkich klientów i zamówień, upewnia się, że zamówienia są dopasowane do klientów i gwarantuje, że dla każdego klienta na tej liście zostanie podana nazwa kontaktu.</span><span class="sxs-lookup"><span data-stu-id="1d890-113">The following Visual Basic example looks for all customers and orders, makes sure that the orders are matched to customers, and guarantees that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#50v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#50v)]  
  
## <a name="example"></a><span data-ttu-id="1d890-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-114">Example</span></span>  
 <span data-ttu-id="1d890-115">Poniższy przykład jawnie łączy dwie tabele i projekty w obu tabelach.</span><span class="sxs-lookup"><span data-stu-id="1d890-115">The following example explicitly joins two tables and projects results from both tables.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#51](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#51)]
 [!code-vb[DLinqQueryExamples#51](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#51)]  
  
## <a name="example"></a><span data-ttu-id="1d890-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-116">Example</span></span>  
 <span data-ttu-id="1d890-117">Poniższy przykład jawnie sprzęga trzy tabele i projekty z każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="1d890-117">The following example explicitly joins three tables and projects results from each of them.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#52](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#52)]
 [!code-vb[DLinqQueryExamples#52](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#52)]  
  
## <a name="example"></a><span data-ttu-id="1d890-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-118">Example</span></span>  
 <span data-ttu-id="1d890-119">Poniższy przykład pokazuje, jak osiągnąć `LEFT OUTER JOIN` za pomocą. `DefaultIfEmpty()`</span><span class="sxs-lookup"><span data-stu-id="1d890-119">The following example shows how to achieve a `LEFT OUTER JOIN` by using `DefaultIfEmpty()`.</span></span> <span data-ttu-id="1d890-120">Metoda zwraca wartość null, `Employee`Jeśli nie `Order` ma dla elementu. `DefaultIfEmpty()`</span><span class="sxs-lookup"><span data-stu-id="1d890-120">The `DefaultIfEmpty()` method returns null when there is no `Order` for the `Employee`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#53](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#53)]
 [!code-vb[DLinqQueryExamples#53](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#53)]  
  
## <a name="example"></a><span data-ttu-id="1d890-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-121">Example</span></span>  
 <span data-ttu-id="1d890-122">Poniższy przykład tworzy w `let` projekcie wyrażenie wynikłe z sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="1d890-122">The following example projects a `let` expression resulting from a join.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#54](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#54)]
 [!code-vb[DLinqQueryExamples#54](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#54)]  
  
## <a name="example"></a><span data-ttu-id="1d890-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-123">Example</span></span>  
 <span data-ttu-id="1d890-124">Poniższy przykład przedstawia `join` z kluczem złożonym.</span><span class="sxs-lookup"><span data-stu-id="1d890-124">The following example shows a `join` with a composite key.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#55](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#55)]
 [!code-vb[DLinqQueryExamples#55](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#55)]  
  
## <a name="example"></a><span data-ttu-id="1d890-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d890-125">Example</span></span>  
 <span data-ttu-id="1d890-126">Poniższy przykład pokazuje, jak utworzyć `join` miejsce, gdzie jedna strona ma wartość null, a druga nie.</span><span class="sxs-lookup"><span data-stu-id="1d890-126">The following example shows how to construct a `join` where one side is nullable and the other is not.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#56](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#56)]
 [!code-vb[DLinqQueryExamples#56](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#56)]  
  
## <a name="see-also"></a><span data-ttu-id="1d890-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d890-127">See also</span></span>

- [<span data-ttu-id="1d890-128">Przykłady zapytań</span><span class="sxs-lookup"><span data-stu-id="1d890-128">Query Examples</span></span>](query-examples.md)
