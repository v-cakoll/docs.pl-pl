---
title: BREAK — instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 9dc71cce3cc0ca4035df483d2b3a3ab9a3bab9c5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44046593"
---
# <a name="break-c-reference"></a><span data-ttu-id="714ef-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="714ef-102">break (C# Reference)</span></span>

<span data-ttu-id="714ef-103">`break` Kończy się najbliższej otaczającej pętli lub [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcji, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="714ef-103">The `break` statement terminates the closest enclosing loop or [switch](../../../csharp/language-reference/keywords/switch.md) statement in which it appears.</span></span> <span data-ttu-id="714ef-104">Kontrola jest przekazywana do instrukcji następującej instrukcji zakończone, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="714ef-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="714ef-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="714ef-105">Example</span></span>

<span data-ttu-id="714ef-106">W tym przykładzie instrukcji warunkowej zawiera licznik, który ma zostać liczba z zakresu od 1 do 100; jednak `break` kończy pętli po liczby 4.</span><span class="sxs-lookup"><span data-stu-id="714ef-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="714ef-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="714ef-107">Example</span></span>

<span data-ttu-id="714ef-108">W tym przykładzie `break` instrukcja jest używane do zerwać pętlę zagnieżdżonych wewnętrzną i zwraca formantu do zewnętrzna pętla.</span><span class="sxs-lookup"><span data-stu-id="714ef-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="714ef-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="714ef-109">Example</span></span>

<span data-ttu-id="714ef-110">W tym przykładzie pokazano użycie `break` w [Przełącz](../../../csharp/language-reference/keywords/switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="714ef-110">This example demonstrates the use of `break` in a [switch](../../../csharp/language-reference/keywords/switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="714ef-111">Jeśli wprowadzono `4`, dane wyjściowe będą:</span><span class="sxs-lookup"><span data-stu-id="714ef-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="714ef-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="714ef-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="714ef-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="714ef-113">See Also</span></span>

- [<span data-ttu-id="714ef-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="714ef-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="714ef-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="714ef-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="714ef-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="714ef-116">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="714ef-117">switch</span><span class="sxs-lookup"><span data-stu-id="714ef-117">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)  
- [<span data-ttu-id="714ef-118">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="714ef-118">Jump Statements</span></span>](../../../csharp/language-reference/keywords/jump-statements.md)  
- [<span data-ttu-id="714ef-119">Instrukcje iteracji</span><span class="sxs-lookup"><span data-stu-id="714ef-119">Iteration Statements</span></span>](../../../csharp/language-reference/keywords/iteration-statements.md)
