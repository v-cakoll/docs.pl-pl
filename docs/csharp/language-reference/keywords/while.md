---
title: while - C# Odwołanie
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712796"
---
# <a name="while-c-reference"></a><span data-ttu-id="56db6-102">while (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="56db6-102">while (C# Reference)</span></span>

<span data-ttu-id="56db6-103">Instrukcja `while` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza .</span><span class="sxs-lookup"><span data-stu-id="56db6-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="56db6-104">Ponieważ to wyrażenie jest oceniane przed każdym `while` wykonaniem pętli, pętla wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="56db6-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="56db6-105">Różni się to od pętli [do,](do.md) która wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="56db6-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="56db6-106">W dowolnym momencie `while` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="56db6-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="56db6-107">Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56db6-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="56db6-108">Jeśli wyrażenie oblicza `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="56db6-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="56db6-109">W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="56db6-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="56db6-110">Możesz również wyjść `while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56db6-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="56db6-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="56db6-111">Example</span></span>

<span data-ttu-id="56db6-112">W poniższym przykładzie przedstawiono `while` użycie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="56db6-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="56db6-113">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="56db6-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="56db6-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="56db6-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="56db6-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="56db6-115">C# language specification</span></span>

<span data-ttu-id="56db6-116">Aby uzyskać więcej informacji, zobacz [While instrukcji](~/_csharplang/spec/statements.md#the-while-statement) sekcji [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="56db6-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="56db6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56db6-117">See also</span></span>

- [<span data-ttu-id="56db6-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="56db6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="56db6-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="56db6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="56db6-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="56db6-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="56db6-121">do instrukcji</span><span class="sxs-lookup"><span data-stu-id="56db6-121">do statement</span></span>](do.md)
