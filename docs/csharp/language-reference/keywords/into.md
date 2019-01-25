---
title: do - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: b209062a2a3e563ea8e70cb7883d9bbfa3662231
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631519"
---
# <a name="into-c-reference"></a><span data-ttu-id="5f907-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5f907-102">into (C# Reference)</span></span>

<span data-ttu-id="5f907-103">`into` Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowych identyfikatora do przechowywania wyników [grupy](group-clause.md), [sprzężenia](join-clause.md) lub [wybierz](select-clause.md) klauzuli na nowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="5f907-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="5f907-104">Sam ten identyfikator może być generator zapytania dodatkowych poleceń.</span><span class="sxs-lookup"><span data-stu-id="5f907-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="5f907-105">Gdy są używane w `group` lub `select` klauzuli użytkowania nowy identyfikator jest czasami określane jako *kontynuacji*.</span><span class="sxs-lookup"><span data-stu-id="5f907-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="5f907-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="5f907-106">Example</span></span>

<span data-ttu-id="5f907-107">Poniższy przykład pokazuje użycie `into` — słowo kluczowe, aby włączyć identyfikator tymczasowy `fruitGroup` mającego wnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="5f907-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="5f907-108">Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metody na każdym grupy i wybierz tylko te grupy, które zawiera dwa lub więcej słów.</span><span class="sxs-lookup"><span data-stu-id="5f907-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="5f907-109">Korzystanie z `into` w `group` klauzula jest konieczne tylko wtedy, gdy chcesz wykonać operacje zapytań dodatkowe w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="5f907-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="5f907-110">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5f907-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="5f907-111">Na przykład użycie `into` w `join` klauzuli, zobacz [klauzuli join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5f907-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5f907-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f907-112">See also</span></span>

- [<span data-ttu-id="5f907-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="5f907-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="5f907-114">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="5f907-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="5f907-115">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="5f907-115">group clause</span></span>](group-clause.md)
