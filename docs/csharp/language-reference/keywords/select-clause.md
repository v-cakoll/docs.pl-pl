---
title: "select — Klauzula (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f40bc26d1812e76ac618c5a0ddf23c4cef2700d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="0ae59-102">select — Klauzula (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0ae59-102">select clause (C# Reference)</span></span>
<span data-ttu-id="0ae59-103">W wyrażeniu zapytania `select` klauzuli Określa typ wartości, które będą tworzone podczas wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="0ae59-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="0ae59-104">Wynik jest oparta na obliczanie poprzedniego klauzule i wszystkie wyrażenia w `select` klauzuli samej siebie.</span><span class="sxs-lookup"><span data-stu-id="0ae59-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="0ae59-105">Wyrażenia zapytania musi kończyć się albo `select` klauzuli lub [grupy](../../../csharp/language-reference/keywords/group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0ae59-105">A query expression must terminate with either a `select` clause or a [group](../../../csharp/language-reference/keywords/group-clause.md) clause.</span></span>  
  
 <span data-ttu-id="0ae59-106">W poniższym przykładzie przedstawiono prosty `select` klauzuli w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="0ae59-106">The following example shows a simple `select` clause in a query expression.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_1.cs)]  
  
 <span data-ttu-id="0ae59-107">Typ sekwencji utworzonego przez `select` klauzuli określa typu zmienną zapytania `queryHighScores`.</span><span class="sxs-lookup"><span data-stu-id="0ae59-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="0ae59-108">Ogólnie rzecz biorąc `select` klauzuli właśnie Określa zmienną zakresu.</span><span class="sxs-lookup"><span data-stu-id="0ae59-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="0ae59-109">Powoduje to, że zwrócony sekwencja zawierać elementów tego samego typu jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0ae59-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="0ae59-110">Aby uzyskać więcej informacji, zobacz [relacje typu w operacjach zapytań LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="0ae59-110">For more information, see [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="0ae59-111">Jednak `select` klauzuli również zapewnia zaawansowany mechanizm Przekształcanie (lub *projekcji*) źródła danych na nowe typy.</span><span class="sxs-lookup"><span data-stu-id="0ae59-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="0ae59-112">Aby uzyskać więcej informacji, zobacz [Przekształcanie danych za pomocą LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span><span class="sxs-lookup"><span data-stu-id="0ae59-112">For more information, see [Data Transformations with LINQ (C#)](../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae59-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ae59-113">Example</span></span>  
 <span data-ttu-id="0ae59-114">W poniższym przykładzie przedstawiono różne formy `select` klauzuli może potrwać.</span><span class="sxs-lookup"><span data-stu-id="0ae59-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="0ae59-115">W każdym zapytaniu, należy zwrócić uwagę relacji między `select` klauzul i typ *zmienną zapytania* (`studentQuery1`, `studentQuery2`i tak dalej).</span><span class="sxs-lookup"><span data-stu-id="0ae59-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/select-clause_2.cs)]  
  
 <span data-ttu-id="0ae59-116">Jak pokazano w `studentQuery8` w poprzednim przykładzie, czasem może zaistnieć elementy zwrócony sekwencji zawiera tylko podzbiór właściwości elementów źródła.</span><span class="sxs-lookup"><span data-stu-id="0ae59-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="0ae59-117">Utrzymując możliwie najmniejsze zwrócony sekwencji można zmniejszyć wymagania dotyczące pamięci i przyspieszenie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="0ae59-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="0ae59-118">Można to zrobić przez utworzenie typu anonimowego w `select` klauzul i zainicjować go odpowiednie właściwości z elementu źródłowego za pomocą inicjatora obiektów.</span><span class="sxs-lookup"><span data-stu-id="0ae59-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="0ae59-119">Na przykład jak to zrobić, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="0ae59-119">For an example of how to do this, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ae59-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0ae59-120">Remarks</span></span>  
 <span data-ttu-id="0ae59-121">W czasie kompilacji `select` klauzuli są tłumaczone na wywołanie metody <xref:System.Linq.Enumerable.Select%2A> — operator zapytań standardowa.</span><span class="sxs-lookup"><span data-stu-id="0ae59-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae59-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ae59-122">See Also</span></span>  
 [<span data-ttu-id="0ae59-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0ae59-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0ae59-124">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="0ae59-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="0ae59-125">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="0ae59-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
 [<span data-ttu-id="0ae59-126">Partial — metoda () (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0ae59-126">partial (Method) (C# Reference)</span></span>](../../../csharp/language-reference/keywords/partial-method.md)  
 [<span data-ttu-id="0ae59-127">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="0ae59-127">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="0ae59-128">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="0ae59-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="0ae59-129">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="0ae59-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
