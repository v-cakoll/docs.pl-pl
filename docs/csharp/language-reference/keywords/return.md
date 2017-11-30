---
title: "return (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 90c84b51c6ee57864eac552bc488c9f9c15e9394
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="return-c-reference"></a><span data-ttu-id="a67d4-102">return (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a67d4-102">return (C# Reference)</span></span>
<span data-ttu-id="a67d4-103">`return` Instrukcji kończy wykonywanie metody, w którym pojawi się i zwraca sterowania do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="a67d4-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="a67d4-104">Może on również zwrócić wartość opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="a67d4-104">It can also return an optional value.</span></span> <span data-ttu-id="a67d4-105">Jeśli metoda jest `void` typu `return` instrukcji można pominąć.</span><span class="sxs-lookup"><span data-stu-id="a67d4-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>  
  
 <span data-ttu-id="a67d4-106">Jeśli znajduje się wewnątrz instrukcji return `try` bloku `finally` bloku, jeśli istnieje, zostanie wykonana przed kontroli zwraca do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="a67d4-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a67d4-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a67d4-107">Example</span></span>  
 <span data-ttu-id="a67d4-108">W poniższym przykładzie metoda `CalculateArea()` zwraca zmiennej lokalnej `area` jako [podwójne](../../../csharp/language-reference/keywords/double.md) wartość.</span><span class="sxs-lookup"><span data-stu-id="a67d4-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](../../../csharp/language-reference/keywords/double.md) value.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/return_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a67d4-109">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a67d4-109">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a67d4-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a67d4-110">See Also</span></span>  
 [<span data-ttu-id="a67d4-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a67d4-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a67d4-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a67d4-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a67d4-113">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a67d4-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a67d4-114">Return — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a67d4-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)  
 [<span data-ttu-id="a67d4-115">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="a67d4-115">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
