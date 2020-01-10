---
title: OrderBy — klauzula C# -Reference
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: d88b2b40f63f0616cfd54e8abb62f1bc2183f776
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713297"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="b4362-102">Klauzula orderby (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="b4362-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="b4362-103">W wyrażeniu zapytania klauzula `orderby` powoduje, że zwracaną sekwencję lub podsekwencję (grupę) można sortować w kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="b4362-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="b4362-104">Można określić wiele kluczy, aby wykonać jedną lub więcej pomocniczych operacji sortowania.</span><span class="sxs-lookup"><span data-stu-id="b4362-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="b4362-105">Sortowanie jest wykonywane przez domyślną funkcję porównującą dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="b4362-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="b4362-106">Domyślna kolejność sortowania to Ascending.</span><span class="sxs-lookup"><span data-stu-id="b4362-106">The default sort order is ascending.</span></span> <span data-ttu-id="b4362-107">Można również określić niestandardową funkcję porównującą.</span><span class="sxs-lookup"><span data-stu-id="b4362-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="b4362-108">Jednak jest on dostępny tylko przy użyciu składni opartej na metodzie.</span><span class="sxs-lookup"><span data-stu-id="b4362-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="b4362-109">Aby uzyskać więcej informacji, zobacz [Sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="b4362-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4362-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4362-110">Example</span></span>

<span data-ttu-id="b4362-111">W poniższym przykładzie pierwsze zapytanie sortuje wyrazy w kolejności alfabetycznej, zaczynając od A, a drugie zapytanie sortuje te same wyrazy w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="b4362-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="b4362-112">(`ascending` słowo kluczowe jest domyślną wartością sortowania i można je pominąć).</span><span class="sxs-lookup"><span data-stu-id="b4362-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="b4362-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4362-113">Example</span></span>

<span data-ttu-id="b4362-114">Poniższy przykład wykonuje sortowanie podstawowe dla nazwisk uczniów, a następnie pomocnicze sortowanie według ich imion.</span><span class="sxs-lookup"><span data-stu-id="b4362-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="b4362-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4362-115">Remarks</span></span>

<span data-ttu-id="b4362-116">W czasie kompilacji klauzula `orderby` jest tłumaczona na wywołanie metody <xref:System.Linq.Enumerable.OrderBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4362-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="b4362-117">Wiele kluczy w klauzuli `orderby` przetłumaczy na wywołania metody <xref:System.Linq.Enumerable.ThenBy%2A>.</span><span class="sxs-lookup"><span data-stu-id="b4362-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4362-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4362-118">See also</span></span>

- [<span data-ttu-id="b4362-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b4362-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b4362-120">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b4362-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="b4362-121">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="b4362-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="b4362-122">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="b4362-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="b4362-123">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="b4362-123">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
