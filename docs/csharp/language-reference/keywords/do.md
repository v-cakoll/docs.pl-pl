---
title: do - Odwołanie do języka C#
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738907"
---
# <a name="do-c-reference"></a><span data-ttu-id="1a9e7-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1a9e7-102">do (C# Reference)</span></span>

<span data-ttu-id="1a9e7-103">Instrukcja `do` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne ocenia .</span><span class="sxs-lookup"><span data-stu-id="1a9e7-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="1a9e7-104">Ponieważ to wyrażenie jest oceniane po każdym `do-while` wykonaniu pętli, pętla wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="1a9e7-105">To różni się od [while](while.md) pętli, która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="1a9e7-106">W dowolnym momencie w bloku `do` instrukcji można wyrwać z pętli przy użyciu instrukcji [break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="1a9e7-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="1a9e7-107">Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="1a9e7-108">Jeśli wyrażenie ocenia `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="1a9e7-109">W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="1a9e7-110">Można również wyjść `do-while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="1a9e7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a9e7-111">Example</span></span>

<span data-ttu-id="1a9e7-112">W poniższym przykładzie `do` przedstawiono użycie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="1a9e7-113">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="1a9e7-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="1a9e7-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="1a9e7-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1a9e7-115">C# language specification</span></span>

<span data-ttu-id="1a9e7-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="1a9e7-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a9e7-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a9e7-117">See also</span></span>

- [<span data-ttu-id="1a9e7-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="1a9e7-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1a9e7-119">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="1a9e7-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1a9e7-120">C# Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="1a9e7-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1a9e7-121">podczas gdy oświadczenie</span><span class="sxs-lookup"><span data-stu-id="1a9e7-121">while statement</span></span>](while.md)
