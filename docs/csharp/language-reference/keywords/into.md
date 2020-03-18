---
title: do - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713625"
---
# <a name="into-c-reference"></a><span data-ttu-id="c5374-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c5374-102">into (C# Reference)</span></span>

<span data-ttu-id="c5374-103">Kontekstowe `into` słowo kluczowe może służyć do utworzenia tymczasowego identyfikatora do przechowywania wyników [grupy,](group-clause.md) [sprzężenia](join-clause.md) lub [wybierz](select-clause.md) klauzulę w nowym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="c5374-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="c5374-104">Ten identyfikator może być generatorem dla dodatkowych poleceń kwerendy.</span><span class="sxs-lookup"><span data-stu-id="c5374-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="c5374-105">W przypadku `group` użycia `select` w lub klauzuli, użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.</span><span class="sxs-lookup"><span data-stu-id="c5374-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="c5374-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5374-106">Example</span></span>

<span data-ttu-id="c5374-107">W poniższym przykładzie przedstawiono `into` użycie słowa kluczowego `fruitGroup` w celu włączenia tymczasowego identyfikatora, który ma wywnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="c5374-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="c5374-108">Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metodę w każdej grupie i wybrać tylko te grupy, które zawierają dwa lub więcej słów.</span><span class="sxs-lookup"><span data-stu-id="c5374-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="c5374-109">Użycie `into` w klauzuli `group` jest konieczne tylko wtedy, gdy chcesz wykonać dodatkowe operacje kwerendy na każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="c5374-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="c5374-110">Aby uzyskać więcej informacji, zobacz [klauzulę group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c5374-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="c5374-111">Na przykład użycia `into` w klauzuli, `join` zobacz join [klauzuli](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="c5374-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c5374-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c5374-112">See also</span></span>

- [<span data-ttu-id="c5374-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="c5374-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="c5374-114">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="c5374-114">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="c5374-115">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="c5374-115">group clause</span></span>](group-clause.md)
