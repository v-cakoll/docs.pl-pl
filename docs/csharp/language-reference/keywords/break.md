---
title: "break (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords: break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b533d325be41683ed6f56e9e63b3c11ddde9cb17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="break-c-reference"></a><span data-ttu-id="2e042-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2e042-102">break (C# Reference)</span></span>
<span data-ttu-id="2e042-103">`break` Instrukcji kończy najbliższej otaczającej pętli lub [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji, w której znajduje się.</span><span class="sxs-lookup"><span data-stu-id="2e042-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="2e042-104">Kontrola jest przekazywana do instrukcji następującej instrukcji zakończone, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="2e042-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e042-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e042-105">Example</span></span>  
 <span data-ttu-id="2e042-106">W tym przykładzie instrukcji warunkowej zawiera licznika, który ma zostać liczba z zakresu od 1 do 100; jednak `break` instrukcji pętli kończy się po liczby 4.</span><span class="sxs-lookup"><span data-stu-id="2e042-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="2e042-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e042-107">Example</span></span>  
 <span data-ttu-id="2e042-108">W tym przykładzie `break` używana jest instrukcja break poza wewnętrzny pętli zagnieżdżonych i zwrócić kontrolkę do zewnętrznego pętli.</span><span class="sxs-lookup"><span data-stu-id="2e042-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="2e042-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e042-109">Example</span></span>  
 <span data-ttu-id="2e042-110">W tym przykładzie przedstawiono użycie `break` w [przełącznika](../../../csharp/language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2e042-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>  
  
 [!code-csharp[csrefKeywordsJump#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/break_3.cs)]  
  
 <span data-ttu-id="2e042-111">Jeśli wprowadzono `4`, będą dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="2e042-111">If you entered `4`, the output would be:</span></span>  
  
```  
Enter your selection (1, 2, or 3): 4  
Sorry, invalid selection.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="2e042-112">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2e042-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e042-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e042-113">See Also</span></span>  
 [<span data-ttu-id="2e042-114">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2e042-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2e042-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2e042-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2e042-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2e042-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2e042-117">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="2e042-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
 [<span data-ttu-id="2e042-118">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="2e042-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
 [<span data-ttu-id="2e042-119">Iteracja — instrukcje</span><span class="sxs-lookup"><span data-stu-id="2e042-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
