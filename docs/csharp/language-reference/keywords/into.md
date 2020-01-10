---
title: C# odwołanie do
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: f0f5ff1e56a65e83385f814df2fadd957f53561e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713625"
---
# <a name="into-c-reference"></a><span data-ttu-id="95433-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="95433-102">into (C# Reference)</span></span>

<span data-ttu-id="95433-103">Kontekstowe słowo kluczowe `into` może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](group-clause.md), [sprzężenia](join-clause.md) lub [zaznaczania](select-clause.md) do nowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="95433-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="95433-104">Ten identyfikator może być generatorem dla dodatkowych poleceń zapytań.</span><span class="sxs-lookup"><span data-stu-id="95433-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="95433-105">W przypadku użycia w klauzuli `group` lub `select` użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.</span><span class="sxs-lookup"><span data-stu-id="95433-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="95433-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="95433-106">Example</span></span>

<span data-ttu-id="95433-107">Poniższy przykład ilustruje użycie słowa kluczowego `into`, aby włączyć tymczasowy identyfikator `fruitGroup`, który ma wnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="95433-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="95433-108">Używając identyfikatora, można wywołać metodę <xref:System.Linq.Enumerable.Count%2A> dla każdej grupy i wybrać tylko te grupy, które zawierają dwa lub więcej wyrazów.</span><span class="sxs-lookup"><span data-stu-id="95433-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="95433-109">Użycie `into` w klauzuli `group` jest konieczne tylko wtedy, gdy chcesz wykonać dodatkowe operacje zapytań dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="95433-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="95433-110">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="95433-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="95433-111">Aby zapoznać się z przykładem użycia `into` w klauzuli `join`, zobacz [Klauzula join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="95433-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="95433-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95433-112">See also</span></span>

- [<span data-ttu-id="95433-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="95433-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="95433-114">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="95433-114">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="95433-115">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="95433-115">group clause</span></span>](group-clause.md)
