---
title: SELECT — klauzula - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 7c61fb18c37ed65a62975a75506d4265c52f2a98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660674"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="4b715-102">select — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4b715-102">select clause (C# Reference)</span></span>

<span data-ttu-id="4b715-103">W wyrażeniu zapytania `select` klauzula Określa typ wartości, które zostaną wygenerowane, gdy zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="4b715-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="4b715-104">Wynik jest oparty na obliczanie poprzedniego klauzul i wszystkie wyrażenia w `select` klauzuli sam.</span><span class="sxs-lookup"><span data-stu-id="4b715-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="4b715-105">Wyrażenie zapytania musi kończyć się albo `select` klauzuli lub [grupy](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4b715-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="4b715-106">W poniższym przykładzie przedstawiono prosty `select` klauzula w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="4b715-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="4b715-107">Typ sekwencji generowany przez `select` klauzula Określa typ zmiennej zapytania `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="4b715-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="4b715-108">W najprostszym przypadku `select` klauzula określa tylko zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="4b715-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="4b715-109">Powoduje to, że zwracana sekwencja zawiera elementy tego samego typu co źródło danych.</span><span class="sxs-lookup"><span data-stu-id="4b715-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="4b715-110">Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4b715-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="4b715-111">Jednak `select` klauzuli również zapewnia zaawansowany mechanizm przekształcenie (lub *przewidywania*) dane źródłowe do nowych typów.</span><span class="sxs-lookup"><span data-stu-id="4b715-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="4b715-112">Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="4b715-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="4b715-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="4b715-113">Example</span></span>

<span data-ttu-id="4b715-114">W poniższym przykładzie przedstawiono różne formy `select` klauzuli może potrwać.</span><span class="sxs-lookup"><span data-stu-id="4b715-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="4b715-115">W każdym zapytaniu Pamiętaj relacji między `select` klauzuli i typu *zmienna zapytania* (`studentQuery1`, `studentQuery2`i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="4b715-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="4b715-116">Jak pokazano na `studentQuery8` w poprzednim przykładzie, czasami konieczne może być elementy zwracana sekwencja zawiera tylko podzbiór właściwości elementy źródłowe.</span><span class="sxs-lookup"><span data-stu-id="4b715-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="4b715-117">Poprzez zapewnienie możliwie najmniejsze zwracanej sekwencji można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="4b715-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="4b715-118">Można to zrobić, tworząc typ anonimowy w `select` klauzula i za pomocą inicjatora obiektów, aby go zainicjować za pomocą odpowiednich właściwości z elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4b715-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="4b715-119">Na przykład jak to zrobić, zobacz [inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="4b715-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="4b715-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4b715-120">Remarks</span></span>

<span data-ttu-id="4b715-121">W czasie kompilacji `select` klauzula jest tłumaczona na wywołanie metody do <xref:System.Linq.Enumerable.Select%2A> standardowego operatora zapytania.</span><span class="sxs-lookup"><span data-stu-id="4b715-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="4b715-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b715-122">See also</span></span>

- [<span data-ttu-id="4b715-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4b715-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4b715-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="4b715-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="4b715-125">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="4b715-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="4b715-126">Partial (metoda) (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4b715-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="4b715-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="4b715-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="4b715-128">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="4b715-128">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="4b715-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="4b715-129">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)