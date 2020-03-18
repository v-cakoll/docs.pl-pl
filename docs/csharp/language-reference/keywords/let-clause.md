---
title: klauzula let - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173591"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="7e3f0-102">Klauzula Let (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7e3f0-102">let clause (C# Reference)</span></span>

<span data-ttu-id="7e3f0-103">W wyrażeniu kwerendy czasami jest przydatne do przechowywania wyniku wyrażenia podrzędnego w celu użycia go w kolejnych klauzul.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="7e3f0-104">Można to zrobić `let` za pomocą słowa kluczowego, który tworzy nową zmienną zakresu i inicjuje go z wynikiem wyrażenia, które podajesz.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="7e3f0-105">Po zainicjowania z wartością zmiennej zakresu nie można użyć do przechowywania innej wartości.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="7e3f0-106">Jednak jeśli zmienna zakresu zawiera typ zapytań, można go zbadać.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="7e3f0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e3f0-107">Example</span></span>

<span data-ttu-id="7e3f0-108">W poniższym `let` przykładzie jest używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="7e3f0-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="7e3f0-109">Aby utworzyć typ wyliczany, który sam może być przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="7e3f0-110">Aby włączyć kwerendę `ToLower` do wywołania tylko `word`jeden raz na zmiennej zakresu .</span><span class="sxs-lookup"><span data-stu-id="7e3f0-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="7e3f0-111">Bez `let`użycia , trzeba `ToLower` by wywołać w każdym `where` predykatu w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="7e3f0-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="7e3f0-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e3f0-112">See also</span></span>

- [<span data-ttu-id="7e3f0-113">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="7e3f0-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="7e3f0-114">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7e3f0-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="7e3f0-115">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="7e3f0-115">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="7e3f0-116">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="7e3f0-116">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="7e3f0-117">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="7e3f0-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)
