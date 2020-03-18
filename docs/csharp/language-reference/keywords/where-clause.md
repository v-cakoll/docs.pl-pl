---
title: gdzie klauzula - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 33616e4eacb484b9c6eda3862cd86fdd1e6df165
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173487"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="7fcd0-102">Klauzula where (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7fcd0-102">where clause (C# Reference)</span></span>

<span data-ttu-id="7fcd0-103">Klauzula `where` jest używana w wyrażeniu kwerendy, aby określić, które elementy ze źródła danych zostaną zwrócone w wyrażeniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="7fcd0-104">Stosuje warunek logiczny *(predykat)* do każdego elementu źródłowego (odwołuje się do zmiennej zakresu) i zwraca te, dla których określony warunek jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="7fcd0-105">Wyrażenie pojedynczej kwerendy `where` może zawierać wiele klauzul, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="7fcd0-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fcd0-106">Example</span></span>

<span data-ttu-id="7fcd0-107">W poniższym przykładzie `where` klauzula odfiltrowuje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="7fcd0-108">Jeśli usuniesz klauzulę, `where` wszystkie numery ze źródła danych zostaną zwrócone.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="7fcd0-109">Wyrażenie `num < 5` jest predykatem, który jest stosowany do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="7fcd0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fcd0-110">Example</span></span>

<span data-ttu-id="7fcd0-111">W ramach `where` jednej klauzuli można określić tyle predykatów, ile jest to konieczne przy użyciu [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) i [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="7fcd0-112">W poniższym przykładzie kwerenda określa dwa predykaty, aby wybrać tylko liczby parzyste, które są mniejsze niż pięć.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="7fcd0-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="7fcd0-113">Example</span></span>

<span data-ttu-id="7fcd0-114">Klauzula `where` może zawierać jedną lub więcej metod, które zwracają wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="7fcd0-115">W poniższym przykładzie `where` klauzula używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="7fcd0-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fcd0-116">Remarks</span></span>

<span data-ttu-id="7fcd0-117">Klauzula `where` jest mechanizmfiltrowania.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="7fcd0-118">Może być umieszczony prawie w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem nie może być pierwszą lub ostatnią klauzulą.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="7fcd0-119">Klauzula `where` może pojawić się przed lub po klauzuli [grupy](group-clause.md) w zależności od tego, czy trzeba filtrować elementy źródłowe przed lub po ich zgrupowaniu.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="7fcd0-120">Jeśli określony predykat nie jest prawidłowy dla elementów w źródle danych, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="7fcd0-121">Jest to jedna z zalet silnego sprawdzania typu zapewnianego przez LINQ.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-121">This is one benefit of the strong type-checking provided by LINQ.</span></span>

<span data-ttu-id="7fcd0-122">W czasie kompilacji `where` słowo kluczowe jest konwertowane na wywołanie do standardowego <xref:System.Linq.Enumerable.Where%2A> operatora kwerendy metody.</span><span class="sxs-lookup"><span data-stu-id="7fcd0-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="7fcd0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fcd0-123">See also</span></span>

- [<span data-ttu-id="7fcd0-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7fcd0-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="7fcd0-125">z klauzuli</span><span class="sxs-lookup"><span data-stu-id="7fcd0-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="7fcd0-126">klauzula wyboru</span><span class="sxs-lookup"><span data-stu-id="7fcd0-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="7fcd0-127">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="7fcd0-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="7fcd0-128">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="7fcd0-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="7fcd0-129">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7fcd0-129">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
