---
title: C# odwołanie do
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: dc1e2ee004c21bb3d05155eec3e42ea80bf641a1
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608639"
---
# <a name="into-c-reference"></a><span data-ttu-id="f5a38-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f5a38-102">into (C# Reference)</span></span>

<span data-ttu-id="f5a38-103">Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](group-clause.md), sprzężenia lub [zaznaczania](select-clause.md) do nowego identyfikatora. [](join-clause.md) `into`</span><span class="sxs-lookup"><span data-stu-id="f5a38-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](group-clause.md), [join](join-clause.md) or [select](select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="f5a38-104">Ten identyfikator może być generatorem dla dodatkowych poleceń zapytań.</span><span class="sxs-lookup"><span data-stu-id="f5a38-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="f5a38-105">W przypadku użycia w `group` klauzuli `select` or, użycie nowego identyfikatora jest czasami określane jako *kontynuacja*.</span><span class="sxs-lookup"><span data-stu-id="f5a38-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>

## <a name="example"></a><span data-ttu-id="f5a38-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5a38-106">Example</span></span>

<span data-ttu-id="f5a38-107">W poniższym przykładzie pokazano użycie `into` słowa kluczowego, aby włączyć tymczasowy identyfikator `fruitGroup` , który ma wnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="f5a38-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="f5a38-108">Używając identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metodę dla każdej grupy i wybrać tylko te grupy, które zawierają dwa lub więcej wyrazów.</span><span class="sxs-lookup"><span data-stu-id="f5a38-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

<span data-ttu-id="f5a38-109">`into` Użycie`group` w klauzuli jest wymagane tylko wtedy, gdy chcesz wykonać dodatkowe operacje na zapytania dla każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="f5a38-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="f5a38-110">Aby uzyskać więcej informacji, zobacz artykuł [kluzula group](group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f5a38-110">For more information, see [group clause](group-clause.md).</span></span>

<span data-ttu-id="f5a38-111">Aby zapoznać się z przykładem użycia `into` `join` w klauzuli, zobacz [Klauzula join](join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="f5a38-111">For an example of the use of `into` in a `join` clause, see [join clause](join-clause.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5a38-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5a38-112">See also</span></span>

- [<span data-ttu-id="f5a38-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f5a38-113">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f5a38-114">Wyrażenia zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="f5a38-114">LINQ Query Expressions</span></span>](../../programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="f5a38-115">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="f5a38-115">group clause</span></span>](group-clause.md)
