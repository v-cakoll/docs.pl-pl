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
ms.openlocfilehash: aceda6cfd33a53388a5afb046359c4dcfddfd1f8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602020"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="1d550-102">Klauzula where (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1d550-102">where clause (C# Reference)</span></span>

<span data-ttu-id="1d550-103">`where` Klauzula jest używana w wyrażeniu zapytania, aby określić, które elementy ze źródła danych będą zwracane w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="1d550-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="1d550-104">Stosuje warunek logiczny (*predykat*) do każdego elementu źródłowego (do którego odwołuje się zmienna zakresu) i zwraca te, dla których określony warunek ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="1d550-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="1d550-105">Pojedyncze wyrażenie zapytania może zawierać wiele `where` klauzul, a pojedyncza klauzula może zawierać wiele podwyrażeń predykatu.</span><span class="sxs-lookup"><span data-stu-id="1d550-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>

## <a name="example"></a><span data-ttu-id="1d550-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d550-106">Example</span></span>

<span data-ttu-id="1d550-107">W poniższym przykładzie `where` klauzula filtruje wszystkie liczby z wyjątkiem tych, które są mniejsze niż pięć.</span><span class="sxs-lookup"><span data-stu-id="1d550-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="1d550-108">Usunięcie `where` klauzuli spowoduje zwrócenie wszystkich liczb ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="1d550-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="1d550-109">Wyrażenie `num < 5` jest predykatem, który jest stosowany do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="1d550-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a><span data-ttu-id="1d550-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d550-110">Example</span></span>

<span data-ttu-id="1d550-111">W obrębie jednej `where` klauzuli można określić dowolną liczbę predykatów, [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) używając operatorów i [ &#124; ](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) .</span><span class="sxs-lookup"><span data-stu-id="1d550-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) and [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="1d550-112">W poniższym przykładzie zapytanie określa dwa predykaty w celu wybrania tylko liczb parzystych mniejszych niż pięć.</span><span class="sxs-lookup"><span data-stu-id="1d550-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a><span data-ttu-id="1d550-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d550-113">Example</span></span>

<span data-ttu-id="1d550-114">`where` Klauzula może zawierać jedną lub więcej metod, które zwracają wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="1d550-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="1d550-115">W poniższym przykładzie `where` klauzula używa metody, aby określić, czy bieżąca wartość zmiennej zakresu jest parzysta czy nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="1d550-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a><span data-ttu-id="1d550-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d550-116">Remarks</span></span>

<span data-ttu-id="1d550-117">`where` Klauzula jest mechanizmem filtrowania.</span><span class="sxs-lookup"><span data-stu-id="1d550-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="1d550-118">Można ją umieścić niemal w dowolnym miejscu w wyrażeniu zapytania, z wyjątkiem sytuacji, w której nie może być pierwszą lub ostatnią klauzulą.</span><span class="sxs-lookup"><span data-stu-id="1d550-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="1d550-119">Klauzula może pojawić się przed lub po klauzuli Group w zależności od tego, czy konieczne jest Filtrowanie elementów źródłowych przed lub po zgrupowaniu. [](group-clause.md) `where`</span><span class="sxs-lookup"><span data-stu-id="1d550-119">A `where` clause may appear either before or after a [group](group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>

<span data-ttu-id="1d550-120">Jeśli określony predykat jest nieprawidłowy dla elementów w źródle danych, zostanie zwrócony błąd czasu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1d550-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="1d550-121">Jest to jedna korzyść dla ścisłego sprawdzania typu zapewnianego przez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1d550-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>

<span data-ttu-id="1d550-122">W czasie `where` kompilacji słowo kluczowe jest konwertowane na wywołanie <xref:System.Linq.Enumerable.Where%2A> metody standardowego operatora zapytań.</span><span class="sxs-lookup"><span data-stu-id="1d550-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d550-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d550-123">See also</span></span>

- [<span data-ttu-id="1d550-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1d550-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="1d550-125">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="1d550-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="1d550-126">select, klauzula</span><span class="sxs-lookup"><span data-stu-id="1d550-126">select clause</span></span>](select-clause.md)
- [<span data-ttu-id="1d550-127">Filtrowanie danych</span><span class="sxs-lookup"><span data-stu-id="1d550-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)
- [<span data-ttu-id="1d550-128">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="1d550-128">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="1d550-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="1d550-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
