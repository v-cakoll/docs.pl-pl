---
title: "Klauzula orderby (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- orderby
- orderby_CSharpKeyword
helpviewer_keywords:
- orderby clause [C#]
- orderby keyword [C#]
ms.assetid: 21f87f48-d69d-4e95-9a52-6fec47b37e1f
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc688e7ba164dcca71d13b2d79d30f1373c4778e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="orderby-clause-c-reference"></a><span data-ttu-id="24324-102">Klauzula orderby (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="24324-102">orderby clause (C# Reference)</span></span>
<span data-ttu-id="24324-103">W wyrażeniu zapytania `orderby` klauzuli powoduje, że zwrócony sekwencji lub podsekwencji (grupa) mają być sortowane w kolejności rosnącej lub malejącej.</span><span class="sxs-lookup"><span data-stu-id="24324-103">In a query expression, the `orderby` clause causes the returned sequence or subsequence (group) to be sorted in either ascending or descending order.</span></span> <span data-ttu-id="24324-104">Można określić wiele kluczy w celu wykonywania operacji dodatkowej sortowania jeden lub więcej.</span><span class="sxs-lookup"><span data-stu-id="24324-104">Multiple keys can be specified in order to perform one or more secondary sort operations.</span></span> <span data-ttu-id="24324-105">Sortowanie jest wykonywane przez domyślna funkcja porównująca dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="24324-105">The sorting is performed by the default comparer for the type of the element.</span></span> <span data-ttu-id="24324-106">Domyślna kolejność sortowania jest rosnąca.</span><span class="sxs-lookup"><span data-stu-id="24324-106">The default sort order is ascending.</span></span> <span data-ttu-id="24324-107">Można również określić Niestandardowa funkcja porównująca.</span><span class="sxs-lookup"><span data-stu-id="24324-107">You can also specify a custom comparer.</span></span> <span data-ttu-id="24324-108">Jednak jest tylko dostępne przy użyciu składni oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="24324-108">However, it is only available by using method-based syntax.</span></span> <span data-ttu-id="24324-109">Aby uzyskać więcej informacji, zobacz [sortowanie danych](../../programming-guide/concepts/linq/sorting-data.md).</span><span class="sxs-lookup"><span data-stu-id="24324-109">For more information, see [Sorting Data](../../programming-guide/concepts/linq/sorting-data.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24324-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="24324-110">Example</span></span>  
 <span data-ttu-id="24324-111">W poniższym przykładzie słów w kolejności alfabetycznej, zaczynając od A sortuje pierwszego zapytania i drugiego zapytania sortuje te same wyrazy w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="24324-111">In the following example, the first query sorts the words in alphabetical order starting from A, and second query sorts the same words in descending order.</span></span> <span data-ttu-id="24324-112">( `ascending` — Słowo kluczowe jest wartością domyślną sortowania i można je pominąć.)</span><span class="sxs-lookup"><span data-stu-id="24324-112">(The `ascending` keyword is the default sort value and can be omitted.)</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="24324-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="24324-113">Example</span></span>  
 <span data-ttu-id="24324-114">Poniższy przykład wykonuje głównej sortowania na studentów nazwisk, a następnie dodatkowej sortowania na ich imiona.</span><span class="sxs-lookup"><span data-stu-id="24324-114">The following example performs a primary sort on the students' last names, and then a secondary sort on their first names.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/orderby-clause_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="24324-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24324-115">Remarks</span></span>  
 <span data-ttu-id="24324-116">W czasie kompilacji `orderby` klauzuli są tłumaczone na wywołanie <xref:System.Linq.Enumerable.OrderBy%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="24324-116">At compile time, the `orderby` clause is translated to a call to the <xref:System.Linq.Enumerable.OrderBy%2A> method.</span></span> <span data-ttu-id="24324-117">Wiele kluczy w `orderby` klauzuli przełożyć na <xref:System.Linq.Enumerable.ThenBy%2A> wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="24324-117">Multiple keys in the `orderby` clause translate to <xref:System.Linq.Enumerable.ThenBy%2A> method calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24324-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24324-118">See Also</span></span>  
 [<span data-ttu-id="24324-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="24324-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="24324-120">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="24324-120">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="24324-121">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="24324-121">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="24324-122">Group — klauzula</span><span class="sxs-lookup"><span data-stu-id="24324-122">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)  
 [<span data-ttu-id="24324-123">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="24324-123">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
