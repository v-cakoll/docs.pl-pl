---
title: Odwołanie do języka C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: d75dd816278a876fa05d133e5eb189d606300a5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401930"
---
# <a name="do-c-reference"></a><span data-ttu-id="9557c-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9557c-102">do (C# Reference)</span></span>

<span data-ttu-id="9557c-103">`do`Instrukcja wykonuje instrukcję lub blok instrukcji, gdy określone wyrażenie logiczne zwraca wartość `true` .</span><span class="sxs-lookup"><span data-stu-id="9557c-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="9557c-104">Ponieważ to wyrażenie jest oceniane po każdym wykonaniu pętli, `do-while` Pętla wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="9557c-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="9557c-105">Różni się to od pętli [while](while.md) , która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="9557c-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="9557c-106">W dowolnym momencie w `do` bloku instrukcji można przerwać pętlę przy użyciu instrukcji [Break](break.md) .</span><span class="sxs-lookup"><span data-stu-id="9557c-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="9557c-107">Możesz przejść bezpośrednio do oceny `while` wyrażenia przy użyciu instrukcji [Continue](continue.md) .</span><span class="sxs-lookup"><span data-stu-id="9557c-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9557c-108">Jeśli wyrażenie zwróci wartość `true` , wykonywanie jest kontynuowane na pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="9557c-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="9557c-109">W przeciwnym razie wykonywanie jest kontynuowane po pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="9557c-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="9557c-110">Możesz również wyjść z `do-while` pętli przez instrukcje [goto](goto.md), [Return](return.md)lub [throw](throw.md) .</span><span class="sxs-lookup"><span data-stu-id="9557c-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="9557c-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="9557c-111">Example</span></span>

<span data-ttu-id="9557c-112">W poniższym przykładzie pokazano sposób użycia `do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9557c-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="9557c-113">Wybierz pozycję **Uruchom** , aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="9557c-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="9557c-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="9557c-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="9557c-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9557c-115">C# language specification</span></span>

<span data-ttu-id="9557c-116">Aby uzyskać więcej informacji, zobacz sekcję do [instrukcji](~/_csharplang/spec/statements.md#the-do-statement) w [specyfikacji języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="9557c-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="9557c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9557c-117">See also</span></span>

- [<span data-ttu-id="9557c-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9557c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9557c-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9557c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9557c-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9557c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9557c-121">while, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9557c-121">while statement</span></span>](while.md)
