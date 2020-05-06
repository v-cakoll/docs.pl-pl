---
title: klauzula Let — odwołanie w C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: a6eee9a23fa28b78343e6479106eaa24ecf4caa6
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795368"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="49f11-102">Klauzula Let (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="49f11-102">let clause (C# Reference)</span></span>

<span data-ttu-id="49f11-103">W wyrażeniu zapytania czasami warto przechowywać wynik wyrażenia podrzędnego w celu użycia go w kolejnych klauzulach.</span><span class="sxs-lookup"><span data-stu-id="49f11-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="49f11-104">Można to zrobić za pomocą `let` słowa kluczowego, które tworzy nową zmienną zakresu i inicjuje ją z wynikiem podania wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="49f11-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="49f11-105">Po zainicjowaniu z wartością zmienna zakresu nie może być używana do przechowywania innej wartości.</span><span class="sxs-lookup"><span data-stu-id="49f11-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="49f11-106">Jeśli jednak zmienna zakresu zawiera typ queryable, może to być zapytanie.</span><span class="sxs-lookup"><span data-stu-id="49f11-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="49f11-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="49f11-107">Example</span></span>

<span data-ttu-id="49f11-108">W poniższym przykładzie `let` jest używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="49f11-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="49f11-109">Aby utworzyć wyliczalny typ, który może być badany.</span><span class="sxs-lookup"><span data-stu-id="49f11-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="49f11-110">Aby włączyć wywoływanie `ToLower` zapytania tylko raz dla zmiennej `word`zakresu.</span><span class="sxs-lookup"><span data-stu-id="49f11-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="49f11-111">Bez użycia `let`, należy wywołać `ToLower` każdy predykat w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="49f11-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="49f11-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49f11-112">See also</span></span>

- [<span data-ttu-id="49f11-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="49f11-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="49f11-114">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="49f11-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="49f11-115">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="49f11-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="49f11-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="49f11-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="49f11-117">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="49f11-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
