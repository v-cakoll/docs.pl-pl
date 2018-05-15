---
title: while (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 23c5ca3bb7dc401a894a6c3918fbaec9a9306153
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="while-c-reference"></a><span data-ttu-id="6ec10-102">while (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6ec10-102">while (C# Reference)</span></span>
<span data-ttu-id="6ec10-103">`while` Instrukcji wykonuje instrukcję lub blok instrukcji, dopóki wynikiem obliczenia określonego wyrażenia jest `false`.</span><span class="sxs-lookup"><span data-stu-id="6ec10-103">The `while` statement executes a statement or a block of statements until a specified expression evaluates to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ec10-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ec10-104">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6ec10-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ec10-105">Example</span></span>  
 [!code-csharp[csrefKeywordsIteration#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="6ec10-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ec10-106">Example</span></span>  
 <span data-ttu-id="6ec10-107">Ponieważ test `while` wyrażenie ma miejsce przed każdym wykonywania pętli, `while` pętla jest wykonywana zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="6ec10-107">Because the test of the `while` expression takes place before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="6ec10-108">To różni się od [czy](../../../csharp/language-reference/keywords/do.md) pętli, które wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="6ec10-108">This differs from the [do](../../../csharp/language-reference/keywords/do.md) loop, which executes one or more times.</span></span>  
  
 <span data-ttu-id="6ec10-109">A `while` pętli może zostać zakończony, kiedy [podziału](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [zwracać](../../../csharp/language-reference/keywords/return.md), lub [throw](../../../csharp/language-reference/keywords/throw.md) instrukcji przekazuje sterowanie poza pętli.</span><span class="sxs-lookup"><span data-stu-id="6ec10-109">A `while` loop can be terminated when a [break](../../../csharp/language-reference/keywords/break.md), [goto](../../../csharp/language-reference/keywords/goto.md), [return](../../../csharp/language-reference/keywords/return.md), or [throw](../../../csharp/language-reference/keywords/throw.md) statement transfers control outside the loop.</span></span> <span data-ttu-id="6ec10-110">Aby przekazanie sterowania do następnej iteracji bez wyjścia z pętli, należy użyć [kontynuować](../../../csharp/language-reference/keywords/continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6ec10-110">To pass control to the next iteration without exiting the loop, use the [continue](../../../csharp/language-reference/keywords/continue.md) statement.</span></span> <span data-ttu-id="6ec10-111">Zwróć uwagę różnice w danych wyjściowych w trzech poprzednich przykładach, w zależności od tego, gdzie `int n` jest zwiększany.</span><span class="sxs-lookup"><span data-stu-id="6ec10-111">Notice the difference in output in the three previous examples, depending on where `int n` is incremented.</span></span> <span data-ttu-id="6ec10-112">W przykładzie poniżej żadnych danych wyjściowych jest generowany.</span><span class="sxs-lookup"><span data-stu-id="6ec10-112">In the example below no output is generated.</span></span>  
  
 [!code-csharp[csrefKeywordsIteration#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/while_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6ec10-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ec10-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ec10-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ec10-114">See Also</span></span>  
 [<span data-ttu-id="6ec10-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="6ec10-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6ec10-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6ec10-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6ec10-117">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6ec10-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6ec10-118">while, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="6ec10-118">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
 [<span data-ttu-id="6ec10-119">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="6ec10-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
