---
title: Continue — instrukcja C# -Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 74d166dbcf03b868baf464864e4c246f789df9cc
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605873"
---
# <a name="continue-c-reference"></a><span data-ttu-id="775b3-102">continue (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="775b3-102">continue (C# Reference)</span></span>

<span data-ttu-id="775b3-103">[](./while.md) [](./do.md) [](./foreach-in.md) [](./for.md)Instrukcja przekazuje formant do następnej iteracji otaczającej instrukcji while, do, for lub foreach, w której występuje. `continue`</span><span class="sxs-lookup"><span data-stu-id="775b3-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="775b3-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="775b3-104">Example</span></span>

<span data-ttu-id="775b3-105">W tym przykładzie licznik jest zainicjowany do zliczenia z 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="775b3-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="775b3-106">Używając `continue` instrukcji w połączeniu z wyrażeniem `(i < 9)`, instrukcje między `continue` i końcem `for` treści są pomijane.</span><span class="sxs-lookup"><span data-stu-id="775b3-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="775b3-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="775b3-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="775b3-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="775b3-108">See also</span></span>

- [<span data-ttu-id="775b3-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="775b3-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="775b3-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="775b3-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="775b3-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="775b3-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="775b3-112">break, instrukcja</span><span class="sxs-lookup"><span data-stu-id="775b3-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
