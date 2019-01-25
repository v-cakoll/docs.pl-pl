---
title: Wykonywanie niestandardowych operacji łączenia (LINQ w C#)
description: Dowiedz się, jak wykonać niestandardowych operacji łączenia LINQ w C#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857869"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="a3657-103">Wykonywanie niestandardowych operacji łączenia</span><span class="sxs-lookup"><span data-stu-id="a3657-103">Perform custom join operations</span></span>

<span data-ttu-id="a3657-104">W tym przykładzie pokazano, jak wykonywanie operacji łączenia, które nie są możliwe dzięki `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a3657-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="a3657-105">W wyrażeniu zapytania `join` klauzula jest ograniczona do i zoptymalizowane pod kątem, equijoins, które są najbardziej typowe rodzaj operacji tworzenia sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="a3657-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="a3657-106">Wykonując sprzężenie będzie prawdopodobnie zawsze uzyskać najlepszą wydajność, za pomocą `join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a3657-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="a3657-107">Jednak `join` nie można używać klauzuli w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="a3657-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="a3657-108">Gdy sprzężenia jest uzależniona na wyrażeniu nierówności (innych niż equijoin).</span><span class="sxs-lookup"><span data-stu-id="a3657-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="a3657-109">Gdy sprzężenia jest uzależniona na więcej niż jedno wyrażenie równości lub nierówności.</span><span class="sxs-lookup"><span data-stu-id="a3657-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="a3657-110">Gdy trzeba wprowadzić zmienną zakresu tymczasowy dla sekwencji po prawej stronie (wewnętrzny) przed wykonaniem operacji dołączania.</span><span class="sxs-lookup"><span data-stu-id="a3657-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="a3657-111">Do wykonania sprzężenia, które nie są equijoins, możesz użyć wielu `from` klauzule niezależnie wprowadzenie każdego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a3657-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="a3657-112">Następnie Zastosuj wyrażenie predykatu w `where` klauzuli do zmiennej zakresu dla każdego źródła.</span><span class="sxs-lookup"><span data-stu-id="a3657-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="a3657-113">Wyrażenie może również mieć postać wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="a3657-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="a3657-114">Nie należy mylić tego rodzaju operacji tworzenia sprzężenia niestandardowe z użyciem wielu `from` klauzul do dostępu do kolekcji wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="a3657-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="a3657-115">Aby uzyskać więcej informacji, zobacz [klauzuli join](../language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a3657-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="a3657-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3657-116">Example</span></span>

<span data-ttu-id="a3657-117">Pierwsza metoda w poniższym przykładzie przedstawiono prosty sprzężenie krzyżowe.</span><span class="sxs-lookup"><span data-stu-id="a3657-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="a3657-118">Sprzężenia krzyżowego należy używać ostrożnie, ponieważ mogą one powodować bardzo dużych zestawów wyników.</span><span class="sxs-lookup"><span data-stu-id="a3657-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="a3657-119">Jednakże mogą być użyteczne w niektórych scenariuszach tworzenia źródłowych sekwencji, wobec których są uruchamiane dodatkowe zapytania.</span><span class="sxs-lookup"><span data-stu-id="a3657-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="a3657-120">Druga metoda generuje sekwencję wszystkie produkty, których identyfikator kategorii znajduje się na liście kategorii po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a3657-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="a3657-121">Zwróć uwagę na użycie `let` klauzuli i `Contains` metodę, aby utworzyć tablicę tymczasową.</span><span class="sxs-lookup"><span data-stu-id="a3657-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="a3657-122">Również jest możliwe, aby utworzyć tablicę przed zapytania i wyeliminować pierwszy `from` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a3657-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="a3657-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3657-123">Example</span></span>

<span data-ttu-id="a3657-124">W poniższym przykładzie zapytanie należy przyłączyć dwie sekwencje oparta na zgodności kluczy, które w przypadku sekwencji wewnętrzny (prawa strona), nie można uzyskać przed klauzuli join, sam.</span><span class="sxs-lookup"><span data-stu-id="a3657-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="a3657-125">Jeśli wykonano to połączenie przy użyciu `join` klauzuli, a następnie `Split` metody musi być wywoływana dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="a3657-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="a3657-126">Korzystanie z wielu `from` klauzule Umożliwia zapytanie, aby uniknąć obciążenie związane z wywołania metody powtórzony.</span><span class="sxs-lookup"><span data-stu-id="a3657-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="a3657-127">Jednak ponieważ `join` jest zoptymalizowana w tym konkretnym przypadku nadal może być szybsze niż użycie wielu `from` klauzul.</span><span class="sxs-lookup"><span data-stu-id="a3657-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="a3657-128">Wyniki będą się różnić w zależności przede wszystkim na sposób kosztownych jest wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="a3657-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="a3657-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3657-129">See also</span></span>

- [<span data-ttu-id="a3657-130">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="a3657-130">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="a3657-131">join, klauzula</span><span class="sxs-lookup"><span data-stu-id="a3657-131">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="a3657-132">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="a3657-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
