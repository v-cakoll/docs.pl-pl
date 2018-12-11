---
title: Continue — instrukcja - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: fbb5d170f10c0a4b6c6edeae6c3f4a549de65525
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243905"
---
# <a name="continue-c-reference"></a><span data-ttu-id="9bc63-102">continue (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9bc63-102">continue (C# Reference)</span></span>

<span data-ttu-id="9bc63-103">`continue` Instrukcji przekazuje kontrolę do kolejnej iteracji otaczającej [podczas](../../../csharp/language-reference/keywords/while.md), [czy](../../../csharp/language-reference/keywords/do.md), [dla](../../../csharp/language-reference/keywords/for.md), lub [foreach](../../../csharp/language-reference/keywords/foreach-in.md) oświadczenie, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="9bc63-103">The `continue` statement passes control to the next iteration of the enclosing [while](../../../csharp/language-reference/keywords/while.md), [do](../../../csharp/language-reference/keywords/do.md), [for](../../../csharp/language-reference/keywords/for.md), or [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="9bc63-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="9bc63-104">Example</span></span>

<span data-ttu-id="9bc63-105">W tym przykładzie licznik jest ustawiana na liczba z zakresu od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="9bc63-105">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="9bc63-106">Za pomocą `continue` instrukcji w połączeniu z wyrażeniem `(i < 9)`, instrukcji między `continue` wraz z upływem `for` są pomijane ciała.</span><span class="sxs-lookup"><span data-stu-id="9bc63-106">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="9bc63-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9bc63-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="9bc63-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bc63-108">See also</span></span>

- [<span data-ttu-id="9bc63-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9bc63-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9bc63-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9bc63-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9bc63-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9bc63-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="9bc63-112">break, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9bc63-112">break Statement</span></span>](/cpp/cpp/break-statement-cpp)  
- [<span data-ttu-id="9bc63-113">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="9bc63-113">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)