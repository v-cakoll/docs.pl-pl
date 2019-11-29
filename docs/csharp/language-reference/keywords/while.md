---
title: While — C# odwołanie
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: fad0ceae9cf1080e7f4b553e0808fd531fd28c57
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552379"
---
# <a name="while-c-reference"></a><span data-ttu-id="c9ced-102">while (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c9ced-102">while (C# Reference)</span></span>

<span data-ttu-id="c9ced-103">Instrukcja `while` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="c9ced-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="c9ced-104">Ponieważ to wyrażenie jest oceniane przed każdym wykonaniem pętli, pętla `while` wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="c9ced-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="c9ced-105">Różni się to od [pętli do](do.md) , która wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="c9ced-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="c9ced-106">W dowolnym momencie w bloku instrukcji `while` można przerwać pętlę przy użyciu instrukcji [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="c9ced-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="c9ced-107">Możesz przejść bezpośrednio do oceny wyrażenia `while` przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="c9ced-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c9ced-108">Jeśli wyrażenie zwróci wartość `true`, wykonywanie jest kontynuowane na pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="c9ced-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="c9ced-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="c9ced-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="c9ced-110">Możesz również wyjść z pętli `while` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="c9ced-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="c9ced-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9ced-111">Example</span></span>

<span data-ttu-id="c9ced-112">Poniższy przykład pokazuje użycie instrukcji `while`.</span><span class="sxs-lookup"><span data-stu-id="c9ced-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="c9ced-113">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="c9ced-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="c9ced-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="c9ced-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c9ced-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c9ced-115">C# language specification</span></span>

<span data-ttu-id="c9ced-116">Aby uzyskać więcej informacji, zobacz sekcję [while](~/_csharplang/spec/statements.md#the-while-statement) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c9ced-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9ced-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9ced-117">See also</span></span>

- [<span data-ttu-id="c9ced-118">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="c9ced-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c9ced-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9ced-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c9ced-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c9ced-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c9ced-121">do — instrukcja</span><span class="sxs-lookup"><span data-stu-id="c9ced-121">do statement</span></span>](do.md)
