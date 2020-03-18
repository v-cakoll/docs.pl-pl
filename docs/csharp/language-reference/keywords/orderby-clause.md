---
title: klauzula orderby - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
ms.openlocfilehash: cd76b2c33fe1a1a986bc05e3c3ed5f22809686ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173578"
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="f2026-102">Klauzula orderby (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f2026-102">orderby clause (C# Reference)</span></span>

<span data-ttu-id="f2026-103">W wyrażeniu `orderby` kwerendy klauzula powoduje, że zwracana sekwencja lub podsekwencja (grupa) mają być sortowane w kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="f2026-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="f2026-104">Można określić wiele kluczy w celu wykonania jednej lub więcej pomocniczych operacji sortowania.</span><span class="sxs-lookup"><span data-stu-id="f2026-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="f2026-105">Sortowanie jest wykonywane przez domyślny porównywarka dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="f2026-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="f2026-106">Domyślna kolejność sortowania jest rosnąco.</span><span class="sxs-lookup"><span data-stu-id="f2026-106">The default sort order is ascending.</span></span> <span data-ttu-id="f2026-107">Można również określić niestandardowego porównania.</span><span class="sxs-lookup"><span data-stu-id="f2026-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="f2026-108">Jednak jest on aplikowane tylko przy użyciu składni opartej na metodach.</span><span class="sxs-lookup"><span data-stu-id="f2026-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="f2026-109">Aby uzyskać więcej informacji, zobacz [Sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="f2026-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>

## <a name="example"></a><span data-ttu-id="f2026-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2026-110">Example</span></span>

<span data-ttu-id="f2026-111">W poniższym przykładzie pierwsza kwerenda sortuje wyrazy w kolejności alfabetycznej, począwszy od A, a druga kwerenda sortuje te same wyrazy w porządku malejącym.</span><span class="sxs-lookup"><span data-stu-id="f2026-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="f2026-112">(Słowo `ascending` kluczowe jest domyślną wartością sortowania i można je pominąć).</span><span class="sxs-lookup"><span data-stu-id="f2026-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>

[!code-csharp[cscsrefQueryKeywords#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#20)]

## <a name="example"></a><span data-ttu-id="f2026-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2026-113">Example</span></span>

<span data-ttu-id="f2026-114">Poniższy przykład wykonuje sortowanie podstawowe na nazwiska uczniów, a następnie sortowanie dodatkowe na ich imiona.</span><span class="sxs-lookup"><span data-stu-id="f2026-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>

[!code-csharp[cscsrefQueryKeywords#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Orderby.cs#22)]

## <a name="remarks"></a><span data-ttu-id="f2026-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2026-115">Remarks</span></span>

<span data-ttu-id="f2026-116">W czasie kompilacji `orderby` klauzula jest tłumaczona <xref:System.Linq.Enumerable.OrderBy%2A> na wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="f2026-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="f2026-117">Wiele kluczy `orderby` w <xref:System.Linq.Enumerable.ThenBy%2A> klauzuli przetłumaczyć na wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="f2026-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2026-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2026-118">See also</span></span>

- [<span data-ttu-id="f2026-119">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f2026-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2026-120">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f2026-120">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f2026-121">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="f2026-121">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="f2026-122">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="f2026-122">group clause</span></span>](group-clause.md)
- [<span data-ttu-id="f2026-123">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f2026-123">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
