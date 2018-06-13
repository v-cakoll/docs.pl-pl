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
ms.openlocfilehash: 9d625db1231687cdad2e24303b2e08ecf736a50c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269643"
---
# <a name="let-clause-c-reference"></a><span data-ttu-id="9c2ec-102">Klauzula Let (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9c2ec-102">let clause (C# Reference)</span></span>
<span data-ttu-id="9c2ec-103">W wyrażeniu zapytania czasami jest przydatne do przechowywania wynik wyrażenia podrzędnego, aby można było go używać w klauzulach kolejne.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-103">In a query expression, it is sometimes useful to store the result of a sub-expression in order to use it in subsequent clauses.</span></span> <span data-ttu-id="9c2ec-104">Można to zrobić z `let` — słowo kluczowe, która tworzy nową zmienną zakresu i inicjowania wynik wyrażenia, należy podać.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-104">You can do this with the `let` keyword, which creates a new range variable and initializes it with the result of the expression you supply.</span></span> <span data-ttu-id="9c2ec-105">Po zainicjowany z wartością, zmienna zakresu nie może służyć do przechowywania innej wartości.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-105">Once initialized with a value, the range variable cannot be used to store another value.</span></span> <span data-ttu-id="9c2ec-106">Jednak jeśli posiada kolejność typu zmienną zakresu może być badana.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-106">However, if the range variable holds a queryable type, it can be queried.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c2ec-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c2ec-107">Example</span></span>  
 <span data-ttu-id="9c2ec-108">W poniższym przykładzie `let` jest używany na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="9c2ec-108">In the following example `let` is used in two ways:</span></span>  
  
1.  <span data-ttu-id="9c2ec-109">Aby utworzyć typ wyliczalny, który może sam być badana.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-109">To create an enumerable type that can itself be queried.</span></span>  
  
2.  <span data-ttu-id="9c2ec-110">Aby umożliwić wykonanie zapytania w celu wywołania `ToLower` tylko jeden raz na zmienną zakresu `word`.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-110">To enable the query to call `ToLower` only one time on the range variable `word`.</span></span> <span data-ttu-id="9c2ec-111">Bez użycia `let`, należy wywołać `ToLower` w każdym predykatu w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9c2ec-111">Without using `let`, you would have to call `ToLower` in each predicate in the `where` clause.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#28](../../../csharp/language-reference/keywords/codesnippet/CSharp/let-clause_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c2ec-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c2ec-112">See Also</span></span>  
 [<span data-ttu-id="9c2ec-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9c2ec-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9c2ec-114">Słowa kluczowe zapytania (LINQ)</span><span class="sxs-lookup"><span data-stu-id="9c2ec-114">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
 [<span data-ttu-id="9c2ec-115">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9c2ec-115">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="9c2ec-116">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="9c2ec-116">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)  
 [<span data-ttu-id="9c2ec-117">Porady: obsługa wyjątków w wyrażeniach zapytań</span><span class="sxs-lookup"><span data-stu-id="9c2ec-117">How to: Handle Exceptions in Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/how-to-handle-exceptions-in-query-expressions.md)
