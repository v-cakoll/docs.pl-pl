---
title: select klauzula - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: 68ea7ad6fc7cf5580dbdd0ae7f012f36566db0dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173513"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="01399-102">select — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="01399-102">select clause (C# Reference)</span></span>

<span data-ttu-id="01399-103">W wyrażeniu `select` kwerendy klauzula określa typ wartości, które zostaną wyprodukowane podczas wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="01399-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="01399-104">Wynik opiera się na ocenie wszystkich poprzednich klauzul i na `select` wszelkich wyrażeniach w samej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="01399-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="01399-105">Wyrażenie kwerendy musi zakończyć `select` się klauzulą lub klauzulą [grupową.](group-clause.md)</span><span class="sxs-lookup"><span data-stu-id="01399-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="01399-106">W poniższym przykładzie `select` przedstawiono prostą klauzulę w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="01399-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="01399-107">Typ sekwencji produkowane przez `select` klauzulę określa typ zmiennej `queryHighScores`kwerendy .</span><span class="sxs-lookup"><span data-stu-id="01399-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="01399-108">W najprostszym przypadku `select` klauzula określa tylko zmienną zakresu.</span><span class="sxs-lookup"><span data-stu-id="01399-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="01399-109">Powoduje to, że zwrócona sekwencja zawiera elementy tego samego typu co źródło danych.</span><span class="sxs-lookup"><span data-stu-id="01399-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="01399-110">Aby uzyskać więcej informacji, zobacz [Wpisywanie relacji w operacjach kwerend LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="01399-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="01399-111">Jednak klauzula `select` zapewnia również zaawansowany mechanizm przekształcania (lub *projekcji)* danych źródłowych w nowe typy.</span><span class="sxs-lookup"><span data-stu-id="01399-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="01399-112">Aby uzyskać więcej informacji, zobacz [Transformacje danych z LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="01399-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="01399-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="01399-113">Example</span></span>

<span data-ttu-id="01399-114">W poniższym przykładzie przedstawiono wszystkie `select` różne formy, które może podjąć klauzula.</span><span class="sxs-lookup"><span data-stu-id="01399-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="01399-115">W każdym zapytaniu należy `select` zwrócić uwagę na relację między `studentQuery2`klauzulą a typem *zmiennej zapytania* (`studentQuery1`, i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="01399-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="01399-116">Jak pokazano w `studentQuery8` poprzednim przykładzie, czasami może chcesz elementy zwróconej sekwencji zawierać tylko podzbiór właściwości elementów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="01399-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="01399-117">Utrzymując zwróconą sekwencję tak małą, jak to możliwe, można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="01399-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="01399-118">Można to osiągnąć, tworząc typ `select` anonimowy w klauzuli i przy użyciu inicjatora obiektu, aby zainicjować go z odpowiednimi właściwościami z elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="01399-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="01399-119">Aby uzyskać przykład, jak to zrobić, zobacz [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="01399-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="01399-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01399-120">Remarks</span></span>

<span data-ttu-id="01399-121">W czasie kompilacji `select` klauzula jest tłumaczona <xref:System.Linq.Enumerable.Select%2A> na wywołanie metody do standardowego operatora kwerendy.</span><span class="sxs-lookup"><span data-stu-id="01399-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="01399-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01399-122">See also</span></span>

- [<span data-ttu-id="01399-123">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="01399-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="01399-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="01399-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="01399-125">z klauzuli</span><span class="sxs-lookup"><span data-stu-id="01399-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="01399-126">częściowe (metoda) (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="01399-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="01399-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="01399-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="01399-128">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="01399-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="01399-129">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="01399-129">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
