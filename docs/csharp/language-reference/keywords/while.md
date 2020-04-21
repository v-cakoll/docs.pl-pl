---
title: while - C# Reference
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738753"
---
# <a name="while-c-reference"></a><span data-ttu-id="e681a-102">while (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e681a-102">while (C# Reference)</span></span>

<span data-ttu-id="e681a-103">Instrukcja `while` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia .</span><span class="sxs-lookup"><span data-stu-id="e681a-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="e681a-104">Ponieważ to wyrażenie jest oceniane przed każdym `while` wykonaniem pętli, pętla wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="e681a-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="e681a-105">To różni się od [pętli do,](do.md) która wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="e681a-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="e681a-106">W dowolnym momencie w bloku `while` instrukcji można wyrwać z pętli przy użyciu instrukcji [break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="e681a-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="e681a-107">Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e681a-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="e681a-108">Jeśli wyrażenie ocenia `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="e681a-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="e681a-109">W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="e681a-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="e681a-110">Można również wyjść `while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e681a-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="e681a-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e681a-111">Example</span></span>

<span data-ttu-id="e681a-112">W poniższym przykładzie `while` przedstawiono użycie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e681a-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="e681a-113">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="e681a-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="e681a-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="e681a-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="e681a-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e681a-115">C# language specification</span></span>

<span data-ttu-id="e681a-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="e681a-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="e681a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e681a-117">See also</span></span>

- [<span data-ttu-id="e681a-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="e681a-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e681a-119">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="e681a-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e681a-120">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="e681a-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e681a-121">instrukcja do</span><span class="sxs-lookup"><span data-stu-id="e681a-121">do statement</span></span>](do.md)
