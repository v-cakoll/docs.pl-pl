---
title: Klauzula Let (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 62294df7f0f2ebb3249dffd72ba4910fbae984c8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881788"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="f4ddd-102">Klauzula Let (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f4ddd-102">let clause (C# Reference)</span></span>

<span data-ttu-id="f4ddd-103">W wyrażeniu zapytania jest czasami warto przechowywać wyników wyrażeń podrzędnych do jej używania w kolejnych klauzul.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="f4ddd-104">Można to zrobić za pomocą `let` słowo kluczowe, które tworzy nową zmienną zakresu i inicjuje ją z wynikiem wyrażenia dostarczasz.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="f4ddd-105">Po zainicjowaniu z wartością, zmienna zakresu nie może służyć do przechowywania inną wartość.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="f4ddd-106">Jednakże jeśli typ odpytywalny jest przechowywana w zmiennej zakresu, może być badana.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-106">However, if the range variable holds a queryable type, it can be queried.</span></span>

## <a name="example"></a><span data-ttu-id="f4ddd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="f4ddd-107">Example</span></span>

<span data-ttu-id="f4ddd-108">W poniższym przykładzie `let` jest używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="f4ddd-108">In the following example `let` is used in two ways:</span></span>

1. <span data-ttu-id="f4ddd-109">Aby utworzyć typ wyliczalny, który sam można wykonywać zapytania.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-109">To create an enumerable type that can itself be queried.</span></span>

2. <span data-ttu-id="f4ddd-110">Aby włączyć zapytanie, aby wywołać `ToLower` tylko jeden raz na zmiennej zakresu `word`.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="f4ddd-111">Bez użycia `let`, trzeba wywoływać `ToLower` w każdej predykat w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f4ddd-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a><span data-ttu-id="f4ddd-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4ddd-112">See also</span></span>

- [<span data-ttu-id="f4ddd-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f4ddd-113">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="f4ddd-114">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f4ddd-114">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="f4ddd-115">Language Integrated Query (LINQ)</span><span class="sxs-lookup"><span data-stu-id="f4ddd-115">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
- [<span data-ttu-id="f4ddd-116">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="f4ddd-116">Getting Started with LINQ in C#</span></span>](../../programming-guide/concepts/linq/getting-started-with-linq.md)
- [<span data-ttu-id="f4ddd-117">Obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="f4ddd-117">Handle exceptions in query expressions</span></span>](../../linq/handle-exceptions-in-query-expressions.md)