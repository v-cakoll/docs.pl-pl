---
title: BREAK, instrukcja - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 18be5171329dd43c419e977a1799e2e72c32404d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662117"
---
# <a name="break-c-reference"></a><span data-ttu-id="df4b3-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="df4b3-102">break (C# Reference)</span></span>

<span data-ttu-id="df4b3-103">`break` Kończy się najbliższej otaczającej pętli lub [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcji, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="df4b3-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="df4b3-104">Kontrola jest przekazywana do instrukcji następującej instrukcji zakończone, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="df4b3-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="df4b3-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="df4b3-105">Example</span></span>

<span data-ttu-id="df4b3-106">W tym przykładzie instrukcji warunkowej zawiera licznik, który ma zostać liczba z zakresu od 1 do 100; jednak `break` kończy pętli po liczby 4.</span><span class="sxs-lookup"><span data-stu-id="df4b3-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="df4b3-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="df4b3-107">Example</span></span>

<span data-ttu-id="df4b3-108">W tym przykładzie `break` instrukcja jest używane do zerwać pętlę zagnieżdżonych wewnętrzną i zwraca formantu do zewnętrzna pętla.</span><span class="sxs-lookup"><span data-stu-id="df4b3-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="df4b3-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="df4b3-109">Example</span></span>

<span data-ttu-id="df4b3-110">W tym przykładzie pokazano użycie `break` w [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df4b3-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="df4b3-111">Jeśli wprowadzono `4`, dane wyjściowe będą:</span><span class="sxs-lookup"><span data-stu-id="df4b3-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="df4b3-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="df4b3-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="df4b3-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df4b3-113">See also</span></span>

- [<span data-ttu-id="df4b3-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="df4b3-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="df4b3-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="df4b3-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="df4b3-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="df4b3-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="df4b3-117">switch</span><span class="sxs-lookup"><span data-stu-id="df4b3-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
- [<span data-ttu-id="df4b3-118">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="df4b3-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)
- [<span data-ttu-id="df4b3-119">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="df4b3-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
