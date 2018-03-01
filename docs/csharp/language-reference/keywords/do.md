---
title: "do (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d24078d3fb985f643fb66aa456900d03d2ff3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="do-c-reference"></a><span data-ttu-id="43c6f-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="43c6f-102">do (C# Reference)</span></span>
<span data-ttu-id="43c6f-103">`do` Instrukcji, która wykonuje instrukcję lub blok instrukcji wielokrotnie aż wynikiem obliczenia określonego wyrażenia jest `false`.</span><span class="sxs-lookup"><span data-stu-id="43c6f-103">The `do` statement executes a statement or a block of statements repeatedly until a specified expression evaluates to `false`.</span></span> <span data-ttu-id="43c6f-104">Treści pętli musi być ujęta w nawiasy klamrowe, `{}`, chyba że składa się z jednej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43c6f-104">The body of the loop must be enclosed in braces, `{}`, unless it consists of a single statement.</span></span> <span data-ttu-id="43c6f-105">W takim przypadku nawiasy klamrowe są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="43c6f-105">In that case, the braces are optional.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43c6f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="43c6f-106">Example</span></span>  
 <span data-ttu-id="43c6f-107">W poniższym przykładzie `do-while` instrukcje pętli wykonania tak długo, jak zmienna `x` jest mniejsza niż 5.</span><span class="sxs-lookup"><span data-stu-id="43c6f-107">In the following example, the `do-while` loop statements execute as long as the variable `x` is less than 5.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/do_1.cs)]  
  
 <span data-ttu-id="43c6f-108">W odróżnieniu od [podczas](../../../csharp/language-reference/keywords/while.md) instrukcji `do-while` pętla jest wykonywana raz przed Obliczanie wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="43c6f-108">Unlike the [while](../../../csharp/language-reference/keywords/while.md) statement, a `do-while` loop is executed one time before the conditional expression is evaluated.</span></span>  
  
 <span data-ttu-id="43c6f-109">W dowolnym punktu `do-while` bloku, mogą być dzielone poza przy użyciu pętli [podziału](../../../csharp/language-reference/keywords/break.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43c6f-109">At any point in the `do-while` block, you can break out of the loop using the [break](../../../csharp/language-reference/keywords/break.md) statement.</span></span> <span data-ttu-id="43c6f-110">Można przejść bezpośrednio do `while` instrukcja obliczania wyrażeń przy użyciu [kontynuować](../../../csharp/language-reference/keywords/continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43c6f-110">You can step directly to the `while` expression evaluation statement by using the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="43c6f-111">Jeśli `while` wyrażenie ma wartość true, wykonywanie będzie kontynuowane przy pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="43c6f-111">If the `while` expression evaluates to true, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="43c6f-112">Jeśli wyrażenie ma wartość false, wykonywanie będzie kontynuowane przy pierwszej instrukcji po `do-while` pętli.</span><span class="sxs-lookup"><span data-stu-id="43c6f-112">If the expression evaluates to false, execution continues at the first statement after the `do-while` loop.</span></span>  
  
 <span data-ttu-id="43c6f-113">A `do-while` pętli również można został zakończony przez [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="43c6f-113">A `do-while` loop can also be exited by the [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statements.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="43c6f-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="43c6f-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43c6f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43c6f-115">See Also</span></span>  
 [<span data-ttu-id="43c6f-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="43c6f-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="43c6f-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="43c6f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="43c6f-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="43c6f-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="43c6f-119">czy-while — instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="43c6f-119">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
 [<span data-ttu-id="43c6f-120">Iteracja — instrukcje</span><span class="sxs-lookup"><span data-stu-id="43c6f-120">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
