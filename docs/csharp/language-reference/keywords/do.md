---
title: do - C# Odwołanie
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713599"
---
# <a name="do-c-reference"></a><span data-ttu-id="ca082-102">do (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ca082-102">do (C# Reference)</span></span>

<span data-ttu-id="ca082-103">Instrukcja `do` wykonuje instrukcję lub blok instrukcji, podczas gdy określone `true`wyrażenie logiczne oblicza .</span><span class="sxs-lookup"><span data-stu-id="ca082-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="ca082-104">Ponieważ wyrażenie to jest oceniane po każdym `do-while` wykonaniu pętli, pętla wykonuje jeden lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="ca082-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="ca082-105">Różni się to od [while](while.md) pętli, która wykonuje zero lub więcej razy.</span><span class="sxs-lookup"><span data-stu-id="ca082-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="ca082-106">W dowolnym momencie `do` w bloku instrukcji można wyrwać się z pętli za pomocą [instrukcji break.](break.md)</span><span class="sxs-lookup"><span data-stu-id="ca082-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="ca082-107">Można przejść bezpośrednio do oceny `while` wyrażenia przy użyciu [continue](continue.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ca082-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ca082-108">Jeśli wyrażenie oblicza `true`, wykonanie jest kontynuowane w pierwszej instrukcji w pętli.</span><span class="sxs-lookup"><span data-stu-id="ca082-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ca082-109">W przeciwnym razie wykonanie jest kontynuowane w pierwszej instrukcji po pętli.</span><span class="sxs-lookup"><span data-stu-id="ca082-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="ca082-110">Możesz również wyjść `do-while` z pętli przez [goto](goto.md), [return](return.md), lub [throw](throw.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ca082-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="ca082-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca082-111">Example</span></span>

<span data-ttu-id="ca082-112">W poniższym przykładzie przedstawiono `do` użycie instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ca082-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="ca082-113">Wybierz **uruchom,** aby uruchomić przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="ca082-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="ca082-114">Następnie można zmodyfikować kod i uruchomić go ponownie.</span><span class="sxs-lookup"><span data-stu-id="ca082-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="ca082-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ca082-115">C# language specification</span></span>

<span data-ttu-id="ca082-116">Aby uzyskać więcej informacji, zobacz [sekcję instrukcji do](~/_csharplang/spec/statements.md#the-do-statement) [specyfikacji języka Języka C#.](/dotnet/csharp/language-reference/language-specification/introduction)</span><span class="sxs-lookup"><span data-stu-id="ca082-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="ca082-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca082-117">See also</span></span>

- [<span data-ttu-id="ca082-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ca082-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ca082-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ca082-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ca082-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ca082-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ca082-121">podczas gdy oświadczenie</span><span class="sxs-lookup"><span data-stu-id="ca082-121">while statement</span></span>](while.md)
