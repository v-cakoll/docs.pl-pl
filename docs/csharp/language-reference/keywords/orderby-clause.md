---
title: Klauzula orderby (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: de649a7e1608e6a653f3280bfd5c4e52a3b661be
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563000"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="dcc2a-102">Klauzula orderby (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="dcc2a-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="dcc2a-103">W wyrażeniu zapytania `orderby` klauzuli powoduje, że zwracana sekwencja lub podsekwencję (grupa) mają być sortowane w porządku rosnącym lub malejącym.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="dcc2a-104">Można określić wiele kluczy w celu wykonywania operacji dodatkowej sortowania jeden lub więcej.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="dcc2a-105">Sortowanie jest wykonywane przez domyślny moduł porównujący dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="dcc2a-106">Domyślna kolejność sortowania jest rosnąca.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-106">The default sort order is ascending.</span></span> <span data-ttu-id="dcc2a-107">Można również określić Niestandardowa funkcja porównująca.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="dcc2a-108">Jednak go jest dostępna tylko za pomocą składni oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="dcc2a-109">Aby uzyskać więcej informacji, zobacz [sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="dcc2a-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="dcc2a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc2a-110">Example</span></span>

<span data-ttu-id="dcc2a-111">W poniższym przykładzie pierwsze zapytanie sortuje słów w kolejności alfabetycznej, zaczynając od A, i drugie zapytanie sortuje te same wyrazy w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="dcc2a-112">( `ascending` — Słowo kluczowe jest wartością domyślną sortowania i można je pominąć.)</span><span class="sxs-lookup"><span data-stu-id="dcc2a-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="dcc2a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="dcc2a-113">Example</span></span>

<span data-ttu-id="dcc2a-114">Poniższy przykład wykonuje głównej Sortuj według nazwiska uczniów i drugiego sortowania na ich imiona.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="dcc2a-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcc2a-115">Remarks</span></span>

<span data-ttu-id="dcc2a-116">W czasie kompilacji `orderby` klauzula jest tłumaczona na wywołanie <xref:System.Linq.Enumerable.OrderBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="dcc2a-117">Wiele kluczy w `orderby` klauzuli przełożyć na <xref:System.Linq.Enumerable.ThenBy%2A> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="dcc2a-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="dcc2a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcc2a-118">See also</span></span>

- [<span data-ttu-id="dcc2a-119">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="dcc2a-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dcc2a-120">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="dcc2a-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="dcc2a-121">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="dcc2a-121">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="dcc2a-122">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="dcc2a-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="dcc2a-123">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="dcc2a-123">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)