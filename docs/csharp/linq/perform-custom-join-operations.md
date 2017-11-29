---
title: "Wykonywanie niestandardowych operacji łączenia"
description: "Jak wykonywanie niestandardowych operacji łączenia."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: fef146c92a5cbbf21f8f1688f221c2bd45c99de7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="34a31-104">Wykonywanie niestandardowych operacji łączenia</span><span class="sxs-lookup"><span data-stu-id="34a31-104">Perform custom join operations</span></span>

<span data-ttu-id="34a31-105">W tym przykładzie przedstawiono sposób wykonywania operacji łączenia, które nie są możliwe za pomocą `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="34a31-105">This example shows how to perform join operations that are not possible with the `join` clause.</span></span> <span data-ttu-id="34a31-106">W wyrażeniu zapytania `join` jest ograniczona do klauzuli i zoptymalizowane pod kątem, typ equijoins, które są najbardziej typowych operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="34a31-106">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="34a31-107">Wykonując sprzężenie będzie prawdopodobnie zawsze uzyskać najlepszą wydajność, za pomocą `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="34a31-107">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>  
  
 <span data-ttu-id="34a31-108">Jednak `join` nie można użyć klauzuli w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="34a31-108">However, the `join` clause cannot be used in the following cases:</span></span>  
  
-   <span data-ttu-id="34a31-109">Gdy sprzężenie jest uzależniona od wyrażenia nierówności (z systemem innym niż equijoin).</span><span class="sxs-lookup"><span data-stu-id="34a31-109">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>  
  
-   <span data-ttu-id="34a31-110">Gdy sprzężenie jest uzależniona od więcej niż jedno wyrażenie równości i nierówności.</span><span class="sxs-lookup"><span data-stu-id="34a31-110">When the join is predicated on more than one expression of equality or inequality.</span></span>  
  
-   <span data-ttu-id="34a31-111">Jeśli użytkownik ma wprowadzić zmienną zakresu tymczasowy dla sekwencji (wewnętrzny) po prawej stronie przed operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="34a31-111">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>  
  
 <span data-ttu-id="34a31-112">Aby wykonanie sprzężeń, które nie są equijoins, można użyć wielu `from` klauzule niezależnie wprowadzenie każdego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="34a31-112">To perform joins that are not equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="34a31-113">Następnie Zastosuj wyrażenie predykatu w `where` klauzuli do zmiennej zakresu dla każdego źródła.</span><span class="sxs-lookup"><span data-stu-id="34a31-113">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="34a31-114">Wyrażenie, które również mogą mieć formę wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="34a31-114">The expression also can take the form of a method call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34a31-115">Nie należy mylić tego rodzaju sprzężenia niestandardowe operacji z użyciem wielu `from` klauzule można uzyskać dostępu do kolekcji wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="34a31-115">Do not confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="34a31-116">Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="34a31-116">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34a31-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="34a31-117">Example</span></span>  
 <span data-ttu-id="34a31-118">Pierwsza metoda w poniższym przykładzie przedstawiono prosty sprzężenia krzyżowego.</span><span class="sxs-lookup"><span data-stu-id="34a31-118">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="34a31-119">Sprzężenia krzyżowego należy używać ostrożnie, ponieważ mogą one powodować bardzo dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="34a31-119">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="34a31-120">Jednak mogą być użyteczne w niektórych scenariuszach tworzenia sekwencji źródła, z którymi są uruchamiane dodatkowych zapytań.</span><span class="sxs-lookup"><span data-stu-id="34a31-120">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>  
  
 <span data-ttu-id="34a31-121">Druga metoda tworzy sekwencję wszystkie produkty, których identyfikator kategorii znajduje się na liście Kategoria po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="34a31-121">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="34a31-122">Zwróć uwagę na użycie `let` klauzuli i `Contains` metodę w celu utworzenia tablicy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="34a31-122">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="34a31-123">Również istnieje możliwość utworzenia tablicy przed zapytania i eliminowania pierwszy `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="34a31-123">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#64](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="34a31-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="34a31-124">Example</span></span>  
 <span data-ttu-id="34a31-125">W poniższym przykładzie zapytanie musi zostać dołączony do dwóch sekwencji oparta na zgodności kluczy, które w przypadku sekwencji wewnętrzny (po prawej stronie), nie można uzyskać przed sam klauzuli join.</span><span class="sxs-lookup"><span data-stu-id="34a31-125">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="34a31-126">Jeśli wykonano tego przyłączenia z `join` klauzuli, a następnie `Split` metoda musi zostać wywołana dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="34a31-126">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="34a31-127">Użycie wielu `from` klauzule Umożliwia zapytanie, aby uniknąć zadań wywołania metody powtórzony.</span><span class="sxs-lookup"><span data-stu-id="34a31-127">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="34a31-128">Ponieważ jednak `join` jest zoptymalizowana w tym przypadku może nadal być szybciej niż przy użyciu wielu `from` klauzul.</span><span class="sxs-lookup"><span data-stu-id="34a31-128">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="34a31-129">Wyniki będą się różnić w zależności od głównie koszt jest wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="34a31-129">The results will vary depending primarily on how expensive the method call is.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#13](../../../samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="34a31-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34a31-130">See also</span></span>  
 [<span data-ttu-id="34a31-131">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="34a31-131">LINQ query expressions</span></span>](index.md)  
 [<span data-ttu-id="34a31-132">JOIN — klauzula</span><span class="sxs-lookup"><span data-stu-id="34a31-132">join clause</span></span>](../language-reference/keywords/join-clause.md)  
 [<span data-ttu-id="34a31-133">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="34a31-133">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
