---
title: Wykonywanie operacji sprzężenia niestandardowego (LINQ w języku C#)
description: Dowiedz się, jak wykonywać niestandardowe operacje sprzężenia LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: 56a2a4a5-7299-497d-b3c3-23c848678911
ms.openlocfilehash: 7051007c67bd64cd11ede2f4d5352ce3d497255f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659855"
---
# <a name="perform-custom-join-operations"></a><span data-ttu-id="0c72f-103">Wykonywanie niestandardowych operacji sprzęgania</span><span class="sxs-lookup"><span data-stu-id="0c72f-103">Perform custom join operations</span></span>

<span data-ttu-id="0c72f-104">W tym przykładzie pokazano, jak wykonać operacje sprzężenia, które nie są możliwe z klauzulą. `join`</span><span class="sxs-lookup"><span data-stu-id="0c72f-104">This example shows how to perform join operations that aren't possible with the `join` clause.</span></span> <span data-ttu-id="0c72f-105">W wyrażeniu `join` kwerendy klauzula jest ograniczona i zoptymalizowana dla, równorzędnych, które są zdecydowanie najbardziej typowym typem operacji sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="0c72f-105">In a query expression, the `join` clause is limited to, and optimized for, equijoins, which are by far the most common type of join operation.</span></span> <span data-ttu-id="0c72f-106">Podczas wykonywania równorzędne, prawdopodobnie zawsze uzyskać najlepszą `join` wydajność przy użyciu klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0c72f-106">When performing an equijoin, you will probably always get the best performance by using the `join` clause.</span></span>

<span data-ttu-id="0c72f-107">Jednak że `join` klauzula ta nie może być używana w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="0c72f-107">However, the `join` clause cannot be used in the following cases:</span></span>

- <span data-ttu-id="0c72f-108">Gdy sprzężenie opiera się na wyrażenie nierówności (non-equijoin).</span><span class="sxs-lookup"><span data-stu-id="0c72f-108">When the join is predicated on an expression of inequality (a non-equijoin).</span></span>

- <span data-ttu-id="0c72f-109">Gdy sprzężenie opiera się na więcej niż jednym wyrażeniu równości lub nierówności.</span><span class="sxs-lookup"><span data-stu-id="0c72f-109">When the join is predicated on more than one expression of equality or inequality.</span></span>

- <span data-ttu-id="0c72f-110">Gdy trzeba wprowadzić tymczasową zmienną zakresu dla prawej strony (wewnętrznej) sekwencji przed operacją sprzężenia.</span><span class="sxs-lookup"><span data-stu-id="0c72f-110">When you have to introduce a temporary range variable for the right side (inner) sequence before the join operation.</span></span>

 <span data-ttu-id="0c72f-111">Aby wykonać sprzężenia, które nie są równorzędne, można użyć wielu `from` klauzul, aby wprowadzić każde źródło danych niezależnie.</span><span class="sxs-lookup"><span data-stu-id="0c72f-111">To perform joins that aren't equijoins, you can use multiple `from` clauses to introduce each data source independently.</span></span> <span data-ttu-id="0c72f-112">Następnie należy zastosować wyrażenie predykatu `where` w klauzuli do zmiennej zakresu dla każdego źródła.</span><span class="sxs-lookup"><span data-stu-id="0c72f-112">You then apply a predicate expression in a `where` clause to the range variable for each source.</span></span> <span data-ttu-id="0c72f-113">Wyrażenie może również przybrać formę wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="0c72f-113">The expression also can take the form of a method call.</span></span>

> [!NOTE]
> <span data-ttu-id="0c72f-114">Nie należy mylić tego rodzaju niestandardowej operacji `from` sprzężenia z użyciem wielu klauzul, aby uzyskać dostęp do kolekcji wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="0c72f-114">Don't confuse this kind of custom join operation with the use of multiple `from` clauses to access inner collections.</span></span> <span data-ttu-id="0c72f-115">Aby uzyskać więcej informacji, zobacz [klauzulę join .](../language-reference/keywords/join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0c72f-115">For more information, see [join clause](../language-reference/keywords/join-clause.md).</span></span>

## <a name="example"></a><span data-ttu-id="0c72f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c72f-116">Example</span></span>

<span data-ttu-id="0c72f-117">Pierwsza metoda w poniższym przykładzie pokazuje proste sprzężenie krzyżowe.</span><span class="sxs-lookup"><span data-stu-id="0c72f-117">The first method in the following example shows a simple cross join.</span></span> <span data-ttu-id="0c72f-118">Sprzężenia krzyżowe muszą być używane z ostrożnością, ponieważ mogą one powodować bardzo duże zestawy wyników.</span><span class="sxs-lookup"><span data-stu-id="0c72f-118">Cross joins must be used with caution because they can produce very large result sets.</span></span> <span data-ttu-id="0c72f-119">Jednak mogą być przydatne w niektórych scenariuszach do tworzenia sekwencji źródłowych, względem których są uruchamiane dodatkowe kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0c72f-119">However, they can be useful in some scenarios for creating source sequences against which additional queries are run.</span></span>

<span data-ttu-id="0c72f-120">Druga metoda tworzy sekwencję wszystkich produktów, których identyfikator kategorii znajduje się na liście kategorii po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="0c72f-120">The second method produces a sequence of all the products whose category ID is listed in the category list on the left side.</span></span> <span data-ttu-id="0c72f-121">Należy zwrócić uwagę `let` na `Contains` użycie klauzuli i metody do tworzenia tablicy tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="0c72f-121">Note the use of the `let` clause and the `Contains` method to create a temporary array.</span></span> <span data-ttu-id="0c72f-122">Istnieje również możliwość utworzenia tablicy przed kwerendą `from` i wyeliminowanie pierwszej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0c72f-122">It also is possible to create the array before the query and eliminate the first `from` clause.</span></span>

[!code-csharp[csProgGuideLINQ#64](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_1.cs)]

## <a name="example"></a><span data-ttu-id="0c72f-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c72f-123">Example</span></span>

<span data-ttu-id="0c72f-124">W poniższym przykładzie kwerenda musi łączyć dwie sekwencje oparte na pasujące klucze, które w przypadku wewnętrznej (po prawej stronie) sekwencji, nie można uzyskać przed join klauzuli, sam.</span><span class="sxs-lookup"><span data-stu-id="0c72f-124">In the following example, the query must join two sequences based on matching keys that, in the case of the inner (right side) sequence, cannot be obtained prior to the join clause itself.</span></span> <span data-ttu-id="0c72f-125">Jeśli to sprzężenie `join` zostały wykonane `Split` z klauzulą, a następnie metoda musiałaby zostać wywołana dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="0c72f-125">If this join were performed with a `join` clause, then the `Split` method would have to be called for each element.</span></span> <span data-ttu-id="0c72f-126">Użycie wielu `from` klauzul umożliwia kwerendy, aby uniknąć narzutów powtarzające się wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="0c72f-126">The use of multiple `from` clauses enables the query to avoid the overhead of the repeated method call.</span></span> <span data-ttu-id="0c72f-127">Jednak ponieważ `join` jest zoptymalizowany, w tym konkretnym przypadku `from` nadal może być szybsze niż przy użyciu wielu klauzul.</span><span class="sxs-lookup"><span data-stu-id="0c72f-127">However, since `join` is optimized, in this particular case it might still be faster than using multiple `from` clauses.</span></span> <span data-ttu-id="0c72f-128">Wyniki będą się różnić w zależności od tego, jak drogie jest wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="0c72f-128">The results will vary depending primarily on how expensive the method call is.</span></span>

[!code-csharp[csProgGuideLINQ#13](~/samples/snippets/csharp/concepts/linq/how-to-perform-custom-join-operations_2.cs)]

## <a name="see-also"></a><span data-ttu-id="0c72f-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c72f-129">See also</span></span>

- [<span data-ttu-id="0c72f-130">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0c72f-130">Language Integrated Query (LINQ)</span></span>](index.md)
- [<span data-ttu-id="0c72f-131">klauzula sprzężenia</span><span class="sxs-lookup"><span data-stu-id="0c72f-131">join clause</span></span>](../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="0c72f-132">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="0c72f-132">Order the results of a join clause</span></span>](order-the-results-of-a-join-clause.md)
