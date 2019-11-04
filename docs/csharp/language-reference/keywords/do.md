---
title: do- C# odwołanie
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 08f964b1e5c78a429dc50f81398d840f58ec4b13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422835"
---
# <a name="do-c-reference"></a><span data-ttu-id="0c19f-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0c19f-102">do (C# Reference)</span></span>

<span data-ttu-id="0c19f-103">Instrukcja `do` wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne daje w wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="0c19f-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="0c19f-104">Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, pętla `do-while` wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="0c19f-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="0c19f-105">Różni się to od pętli [while](while.md) , która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="0c19f-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="0c19f-106">W dowolnym momencie w bloku instrukcji `do` można przerwać pętlę przy użyciu instrukcji [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="0c19f-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="0c19f-107">Możesz przejść bezpośrednio do oceny wyrażenia `while` przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="0c19f-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="0c19f-108">Jeśli wyrażenie zwróci wartość `true`, wykonywanie jest kontynuowane na pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="0c19f-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="0c19f-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="0c19f-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="0c19f-110">Możesz również wyjść z pętli `do-while` przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="0c19f-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="0c19f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c19f-111">Example</span></span>

<span data-ttu-id="0c19f-112">Poniższy przykład pokazuje użycie instrukcji `do`.</span><span class="sxs-lookup"><span data-stu-id="0c19f-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="0c19f-113">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="0c19f-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="0c19f-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="0c19f-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="0c19f-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0c19f-115">C# language specification</span></span>

<span data-ttu-id="0c19f-116">Aby uzyskać więcej informacji, zobacz sekcję do [instrukcji](~/_csharplang/spec/statements.md#the-do-statement) [ C# języka Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="0c19f-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c19f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c19f-117">See also</span></span>

- [<span data-ttu-id="0c19f-118">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="0c19f-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0c19f-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0c19f-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0c19f-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0c19f-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0c19f-121">while, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0c19f-121">while statement</span></span>](while.md)
