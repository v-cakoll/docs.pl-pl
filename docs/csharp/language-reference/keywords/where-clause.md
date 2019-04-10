---
title: gdzie klauzula - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 470fcfde7a5e68887fa3a6e99cb8881073ffeba5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341390"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="c49bd-102">Klauzula where (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c49bd-102">where clause (C# Reference)</span></span>

<span data-ttu-id="c49bd-103">`where` Klauzula jest używany w wyrażeniu zapytania, aby określić, które elementy ze źródła danych zostaną zwrócone w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="c49bd-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="c49bd-104">Ma to zastosowanie warunek logiczny (*predykatu*) do każdego elementu źródłowego (odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="c49bd-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="c49bd-105">Wyrażenie jedno zapytanie może zawierać więcej niż jednego `where` klauzul i jedną klauzulę może zawierać wiele podwyrażenia predykatu.</span><span class="sxs-lookup"><span data-stu-id="c49bd-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="c49bd-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49bd-106">Example</span></span>

<span data-ttu-id="c49bd-107">W poniższym przykładzie `where` klauzuli odfiltrowuje wszystkie liczby z wyjątkiem tych, które są mniej niż pięć.</span><span class="sxs-lookup"><span data-stu-id="c49bd-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="c49bd-108">Jeśli usuniesz `where` klauzuli, zostaną zwrócone wszystkie numery ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c49bd-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="c49bd-109">Wyrażenie `num < 5` jest predykat, która jest stosowana do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="c49bd-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="c49bd-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49bd-110">Example</span></span>

<span data-ttu-id="c49bd-111">W obrębie pojedynczego `where` klauzuli, można określić dowolną liczbę predykatów zgodnie z potrzebami przy użyciu [ && ](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) i [ &#124; &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="c49bd-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="c49bd-112">W poniższym przykładzie zapytanie określa predykatów dwa, aby wybrać tylko liczby parzyste z zakresu, które są mniej niż pięć.</span><span class="sxs-lookup"><span data-stu-id="c49bd-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="c49bd-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c49bd-113">Example</span></span>

<span data-ttu-id="c49bd-114">A `where` klauzula może zawierać jedną lub więcej metod, które zwracają wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="c49bd-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="c49bd-115">W poniższym przykładzie `where` klauzuli używa metody w celu ustalenia, czy bieżąca wartość zmiennej zakresu jest parzysta lub nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="c49bd-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="c49bd-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c49bd-116">Remarks</span></span>

<span data-ttu-id="c49bd-117">`where` Klauzula jest mechanizm filtrowania.</span><span class="sxs-lookup"><span data-stu-id="c49bd-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="c49bd-118">Jego można umieścić praktycznie dowolnym miejscu w wyrażeniu zapytania z tym nie może być pierwszej lub ostatniej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c49bd-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="c49bd-119">A `where` klauzula może występować przed lub po [grupy](group-clause.md) klauzuli w zależności od tego, czy masz do filtrowania elementów źródła przed lub po ich grupowania.</span><span class="sxs-lookup"><span data-stu-id="c49bd-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="c49bd-120">Jeśli określony predykat nie jest prawidłowy dla elementów w źródle danych, spowoduje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c49bd-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="c49bd-121">To jest jedną z zalet silne sprawdzania typów dostarczonych przez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c49bd-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="c49bd-122">W czasie kompilacji `where` — słowo kluczowe jest konwertowana na wywołanie <xref:System.Linq.Enumerable.Where%2A> metody standardowej kwerendy operatora.</span><span class="sxs-lookup"><span data-stu-id="c49bd-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="c49bd-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c49bd-123">See also</span></span>

- [<span data-ttu-id="c49bd-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c49bd-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="c49bd-125">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="c49bd-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="c49bd-126">select — Klauzula</span><span class="sxs-lookup"><span data-stu-id="c49bd-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="c49bd-127">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="c49bd-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="c49bd-128">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="c49bd-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="c49bd-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="c49bd-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)