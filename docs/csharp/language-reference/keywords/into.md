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
ms.openlocfilehash: 4445674c77be397bd6e1d7e385dbd839fbb916aa
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238185"
---
# <a name="into-c-reference"></a><span data-ttu-id="ea2b1-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ea2b1-102">into (C# Reference)</span></span>

<span data-ttu-id="ea2b1-103">`into` Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowych identyfikatora do przechowywania wyników [grupy](group-clause.md), [sprzężenia](join-clause.md) lub [wybierz](select-clause.md) klauzuli na nowy identyfikator.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="ea2b1-104">Sam ten identyfikator może być generator zapytania dodatkowych poleceń.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="ea2b1-105">Gdy są używane w `group` lub `select` klauzuli użytkowania nowy identyfikator jest czasami określane jako *kontynuacji*.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="ea2b1-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea2b1-106">Example</span></span>

<span data-ttu-id="ea2b1-107">Poniższy przykład pokazuje użycie `into` — słowo kluczowe, aby włączyć identyfikator tymczasowy `fruitGroup` mającego wnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="ea2b1-108">Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metody na każdym grupy i wybierz tylko te grupy, które zawiera dwa lub więcej słów.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="ea2b1-109">Korzystanie z `into` w `group` klauzula jest konieczne tylko wtedy, gdy chcesz wykonać operacje zapytań dodatkowe w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="ea2b1-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="ea2b1-110">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ea2b1-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="ea2b1-111">Na przykład użycie `into` w `join` klauzuli, zobacz [klauzuli join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ea2b1-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ea2b1-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea2b1-112">See also</span></span>

- [<span data-ttu-id="ea2b1-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="ea2b1-113">Query Keywords (LINQ)</span></span>](query-keywords.md)  
- [<span data-ttu-id="ea2b1-114">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="ea2b1-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="ea2b1-115">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="ea2b1-115">group clause</span></span>](group-clause.md)  