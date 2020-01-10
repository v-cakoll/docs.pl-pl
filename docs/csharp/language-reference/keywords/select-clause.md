---
title: Wybierz klauzulę C# -odwołanie
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: b4d25f80e4cdb08fbc28fa4db3cb1c790b1145e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713095"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="1be8d-102">select — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1be8d-102">select clause (C# Reference)</span></span>

<span data-ttu-id="1be8d-103">W wyrażeniu zapytania klauzula `select` określa typ wartości, które zostaną utworzone podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="1be8d-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="1be8d-104">Wynik jest oparty na ocenie wszystkich poprzednich klauzul i w dowolnych wyrażeniach w samej klauzuli `select`.</span><span class="sxs-lookup"><span data-stu-id="1be8d-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="1be8d-105">Wyrażenie zapytania musi kończyć się klauzulą `select` lub klauzulą [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="1be8d-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="1be8d-106">W poniższym przykładzie pokazano prostą klauzulę `select` w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="1be8d-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="1be8d-107">Typ sekwencji utworzonej przez klauzulę `select` określa typ zmiennej zapytania `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="1be8d-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="1be8d-108">W najprostszym przypadku klauzula `select` określa tylko zmienną zakresu.</span><span class="sxs-lookup"><span data-stu-id="1be8d-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="1be8d-109">Powoduje to, że zwracana sekwencja zawiera elementy tego samego typu co źródło danych.</span><span class="sxs-lookup"><span data-stu-id="1be8d-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="1be8d-110">Aby uzyskać więcej informacji, zobacz temat [relacje typu w operacjach zapytań LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="1be8d-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="1be8d-111">Jednak klauzula `select` zapewnia również zaawansowany mechanizm przekształcania (lub *projekcji*) danych źródłowych na nowe typy.</span><span class="sxs-lookup"><span data-stu-id="1be8d-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="1be8d-112">Aby uzyskać więcej informacji, zobacz [Przekształcanie danych zaC#pomocą LINQ ()](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="1be8d-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="1be8d-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1be8d-113">Example</span></span>

<span data-ttu-id="1be8d-114">W poniższym przykładzie pokazano wszystkie różne formy, które mogą wykonać `select` klauzulę.</span><span class="sxs-lookup"><span data-stu-id="1be8d-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="1be8d-115">W każdym zapytaniu Zwróć uwagę na relacje między klauzulą `select` i typem *zmiennej zapytania* (`studentQuery1`, `studentQuery2`itd.).</span><span class="sxs-lookup"><span data-stu-id="1be8d-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="1be8d-116">Jak pokazano w `studentQuery8` w poprzednim przykładzie, czasami można chcieć, aby elementy zwracanej sekwencji zawierały tylko podzestaw właściwości elementów źródłowych.</span><span class="sxs-lookup"><span data-stu-id="1be8d-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="1be8d-117">Przez pozostawienie zwróconej sekwencji jak najmniejszej ilości, można zmniejszyć wymagania dotyczące pamięci i zwiększyć szybkość wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="1be8d-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="1be8d-118">Można to zrobić przez utworzenie typu anonimowego w klauzuli `select` i użycie inicjatora obiektów w celu zainicjowania go z odpowiednimi właściwościami z elementu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1be8d-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="1be8d-119">Aby uzyskać przykład, jak to zrobić, zobacz [Inicjatory obiektów i kolekcji](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="1be8d-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="1be8d-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1be8d-120">Remarks</span></span>

<span data-ttu-id="1be8d-121">W czasie kompilacji klauzula `select` jest tłumaczona na wywołanie metody do standardowego operatora zapytania <xref:System.Linq.Enumerable.Select%2A>.</span><span class="sxs-lookup"><span data-stu-id="1be8d-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="1be8d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1be8d-122">See also</span></span>

- [<span data-ttu-id="1be8d-123">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1be8d-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1be8d-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="1be8d-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="1be8d-125">from, klauzula</span><span class="sxs-lookup"><span data-stu-id="1be8d-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="1be8d-126">częściowe (Metoda) (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="1be8d-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="1be8d-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="1be8d-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="1be8d-128">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="1be8d-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="1be8d-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="1be8d-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
