---
title: klauzula WHERE- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 15df6339cec9eabadf5aa4c184d7504c4e065032
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421933"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="ae8ee-102">Klauzula where (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ae8ee-102">where clause (C# Reference)</span></span>

<span data-ttu-id="ae8ee-103">Klauzula `where` jest używana w wyrażeniu zapytania, aby określić, które elementy ze źródła danych będą zwracane w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="ae8ee-104">Stosuje warunek logiczny (*predykat*) do każdego elementu źródłowego (do którego odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="ae8ee-105">Pojedyncze wyrażenie zapytania może zawierać wiele klauzul `where`, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="ae8ee-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae8ee-106">Example</span></span>

<span data-ttu-id="ae8ee-107">W poniższym przykładzie klauzula `where` filtruje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="ae8ee-108">Jeśli usuniesz klauzulę `where`, zostaną zwrócone wszystkie liczby ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="ae8ee-109">Wyrażenie `num < 5` jest predykatem stosowanym do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="ae8ee-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae8ee-110">Example</span></span>

<span data-ttu-id="ae8ee-111">W ramach jednej klauzuli `where` można określić dowolną liczbę predykatów, używając [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) i [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operatorów.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="ae8ee-112">W poniższym przykładzie zapytanie określa dwa predykaty w celu wybrania tylko liczb parzystych mniejszych niż pięć.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="ae8ee-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae8ee-113">Example</span></span>

<span data-ttu-id="ae8ee-114">Klauzula `where` może zawierać jedną lub więcej metod, które zwracają wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="ae8ee-115">W poniższym przykładzie klauzula `where` używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="ae8ee-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ae8ee-116">Remarks</span></span>

<span data-ttu-id="ae8ee-117">Klauzula `where` jest mechanizmem filtrowania.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="ae8ee-118">Można ją umieścić niemal w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem sytuacji, w której nie może być pierwszą lub ostatnią klauzulą.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="ae8ee-119">Klauzula `where` może pojawić się przed lub po klauzuli [Group](group-clause.md) w zależności od tego, czy należy filtrować elementy źródłowe przed lub po zgrupowaniu.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="ae8ee-120">Jeśli określony predykat jest nieprawidłowy dla elementów w źródle danych, zostanie zwrócony błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="ae8ee-121">Jest to jedna z zalet ścisłego sprawdzania typu zapewnianego przez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ae8ee-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="ae8ee-122">W czasie kompilacji słowo kluczowe `where` jest konwertowane na wywołanie metody standardowego operatora zapytań <xref:System.Linq.Enumerable.Where%2A>.</span><span class="sxs-lookup"><span data-stu-id="ae8ee-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae8ee-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae8ee-123">See also</span></span>

- [<span data-ttu-id="ae8ee-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ae8ee-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="ae8ee-125">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="ae8ee-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="ae8ee-126">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="ae8ee-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="ae8ee-127">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="ae8ee-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="ae8ee-128">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="ae8ee-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="ae8ee-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="ae8ee-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
