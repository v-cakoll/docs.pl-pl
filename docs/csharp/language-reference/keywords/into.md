---
title: "into (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2400143e66c68942cdec3ebfa04cfdd8cfe983
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="into-c-reference"></a><span data-ttu-id="76908-102">into (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="76908-102">into (C# Reference)</span></span>
<span data-ttu-id="76908-103">`into` Kontekstowe słowo kluczowe może służyć do tworzenia tymczasowego identyfikatora do przechowywania wyników [grupy](../../../csharp/language-reference/keywords/group-clause.md), [sprzężenia](../../../csharp/language-reference/keywords/join-clause.md) lub [wybierz](../../../csharp/language-reference/keywords/select-clause.md) klauzuli do nowego identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="76908-103">The `into` contextual keyword can be used to create a temporary identifier to store the results of a [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) or [select](../../../csharp/language-reference/keywords/select-clause.md) clause into a new identifier.</span></span> <span data-ttu-id="76908-104">Sam ten identyfikator może być generator zapytań dodatkowych poleceń.</span><span class="sxs-lookup"><span data-stu-id="76908-104">This identifier can itself be a generator for additional query commands.</span></span> <span data-ttu-id="76908-105">W przypadku używania w `group` lub `select` klauzuli, użyj nowego identyfikatora czasami nazywa się *kontynuacji*.</span><span class="sxs-lookup"><span data-stu-id="76908-105">When used in a `group` or `select` clause, the use of the new identifier is sometimes referred to as a *continuation*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76908-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="76908-106">Example</span></span>  
 <span data-ttu-id="76908-107">W poniższym przykładzie przedstawiono użycie `into` — słowo kluczowe, aby włączyć tymczasowy identyfikator `fruitGroup` mającego wnioskowany typ `IGrouping`.</span><span class="sxs-lookup"><span data-stu-id="76908-107">The following example shows the use of the `into` keyword to enable a temporary identifier `fruitGroup` which has an inferred type of `IGrouping`.</span></span> <span data-ttu-id="76908-108">Za pomocą identyfikatora, można wywołać <xref:System.Linq.Enumerable.Count%2A> metody dla każdej grupy i wybierz tylko tych grup, które zawierają co najmniej dwa wyrazy.</span><span class="sxs-lookup"><span data-stu-id="76908-108">By using the identifier, you can invoke the <xref:System.Linq.Enumerable.Count%2A> method on each group and select only those groups that contain two or more words.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/into_1.cs)]  
  
 <span data-ttu-id="76908-109">Korzystanie z `into` w `group` klauzuli jest konieczne tylko wtedy, gdy chcesz wykonać operacje kwerend dodatkowe w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="76908-109">The use of `into` in a `group` clause is only necessary when you want to perform additional query operations on each group.</span></span> <span data-ttu-id="76908-110">Aby uzyskać więcej informacji, zobacz [klauzuli group](../../../csharp/language-reference/keywords/group-clause.md).</span><span class="sxs-lookup"><span data-stu-id="76908-110">For more information, see [group clause](../../../csharp/language-reference/keywords/group-clause.md).</span></span>  
  
 <span data-ttu-id="76908-111">Na przykład użycie `into` w `join` klauzuli, zobacz [klauzuli join](../../../csharp/language-reference/keywords/join-clause.md).</span><span class="sxs-lookup"><span data-stu-id="76908-111">For an example of the use of `into` in a `join` clause, see [join clause](../../../csharp/language-reference/keywords/join-clause.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76908-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76908-112">See Also</span></span>  
 [<span data-ttu-id="76908-113">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="76908-113">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="76908-114">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="76908-114">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="76908-115">Group — klauzula</span><span class="sxs-lookup"><span data-stu-id="76908-115">group clause</span></span>](../../../csharp/language-reference/keywords/group-clause.md)
