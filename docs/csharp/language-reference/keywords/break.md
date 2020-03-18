---
title: instrukcja break - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713750"
---
# <a name="break-c-reference"></a><span data-ttu-id="c12ec-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c12ec-102">break (C# Reference)</span></span>

<span data-ttu-id="c12ec-103">Instrukcja `break` kończy najbliższą otaczającej pętli lub [switch](./switch.md) instrukcji, w którym pojawia się.</span><span class="sxs-lookup"><span data-stu-id="c12ec-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="c12ec-104">Formant jest przekazywany do instrukcji, która następuje zakończone instrukcji, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="c12ec-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="c12ec-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c12ec-105">Example</span></span>

<span data-ttu-id="c12ec-106">W tym przykładzie instrukcja warunkowa zawiera licznik, który ma liczyć od 1 do 100; jednak instrukcja `break` kończy pętlę po 4 liczy.</span><span class="sxs-lookup"><span data-stu-id="c12ec-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="c12ec-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="c12ec-107">Example</span></span>

<span data-ttu-id="c12ec-108">W tym przykładzie przedstawiono `break` użycie w [instrukcji switch.](./switch.md)</span><span class="sxs-lookup"><span data-stu-id="c12ec-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="c12ec-109">Jeśli wprowadzono, `4`wyjście będzie:</span><span class="sxs-lookup"><span data-stu-id="c12ec-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="c12ec-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c12ec-110">Example</span></span>

<span data-ttu-id="c12ec-111">W tym przykładzie `break` instrukcja jest używana do wyrwania się z wewnętrznej pętli zagnieżdżonej i przywrócenia formantu do pętli zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="c12ec-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="c12ec-112">Formant jest zwracany _tylko_ jeden poziom w górę w pętli zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="c12ec-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="c12ec-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="c12ec-113">Example</span></span>

<span data-ttu-id="c12ec-114">W tym przykładzie `break` instrukcja jest używana tylko do wyrwania się z bieżącej gałęzi podczas każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="c12ec-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="c12ec-115">Sama pętla nie ma wpływu `break` przez wystąpienia, które należą do zagnieżdżonej [instrukcji switch.](./switch.md)</span><span class="sxs-lookup"><span data-stu-id="c12ec-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="c12ec-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c12ec-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c12ec-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c12ec-117">See also</span></span>

- [<span data-ttu-id="c12ec-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="c12ec-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c12ec-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="c12ec-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c12ec-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="c12ec-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c12ec-121">Przełącznik</span><span class="sxs-lookup"><span data-stu-id="c12ec-121">switch</span></span>](./switch.md)
