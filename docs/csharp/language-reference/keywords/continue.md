---
title: instrukcja continue - C# Odwołanie
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 83b43b31eacf0ed835ee3d7a919538eb9f1dd1e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713660"
---
# <a name="continue-c-reference"></a><span data-ttu-id="e7faf-102">continue (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e7faf-102">continue (C# Reference)</span></span>

<span data-ttu-id="e7faf-103">Instrukcja `continue` przechodzi kontrolę do następnej iteracji otaczającego [podczas](./while.md), [zrobić](./do.md), [dla](./for.md), lub [foreach](./foreach-in.md) instrukcji, w którym się pojawia.</span><span class="sxs-lookup"><span data-stu-id="e7faf-103">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="e7faf-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7faf-104">Example</span></span>

<span data-ttu-id="e7faf-105">W tym przykładzie licznik jest inicjowany do zliczania od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="e7faf-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="e7faf-106">Za pomocą `continue` instrukcji w połączeniu z `(i < 9)` `continue` wyrażeniem , `for` instrukcje między i na końcu treści są pomijane.</span><span class="sxs-lookup"><span data-stu-id="e7faf-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="e7faf-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e7faf-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e7faf-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7faf-108">See also</span></span>

- [<span data-ttu-id="e7faf-109">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="e7faf-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e7faf-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="e7faf-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e7faf-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e7faf-111">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e7faf-112">break, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e7faf-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
