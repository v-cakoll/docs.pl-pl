---
title: instrukcja break- C# Reference
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: ef276fd9e8da0ea25695c5afdf06a300bbd2a123
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713750"
---
# <a name="break-c-reference"></a><span data-ttu-id="360e2-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="360e2-102">break (C# Reference)</span></span>

<span data-ttu-id="360e2-103">Instrukcja `break` kończy najbliższą otaczającą pętlę lub instrukcję [Switch](./switch.md) , w której występuje.</span><span class="sxs-lookup"><span data-stu-id="360e2-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="360e2-104">Kontrolka jest przenoszona do instrukcji, która następuje po instrukcji zakończony (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="360e2-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="360e2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="360e2-105">Example</span></span>

<span data-ttu-id="360e2-106">W tym przykładzie Instrukcja warunkowa zawiera licznik, który powinien być liczony od 1 do 100; Jednakże instrukcja `break` przerywa pętlę po 4 zliczenia.</span><span class="sxs-lookup"><span data-stu-id="360e2-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="360e2-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="360e2-107">Example</span></span>

<span data-ttu-id="360e2-108">Ten przykład ilustruje użycie `break` w instrukcji [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="360e2-108">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="360e2-109">W przypadku wprowadzenia `4`dane wyjściowe byłyby następujące:</span><span class="sxs-lookup"><span data-stu-id="360e2-109">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="360e2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="360e2-110">Example</span></span>

<span data-ttu-id="360e2-111">W tym przykładzie instrukcja `break` jest używana do przerywania wewnętrznej pętli zagnieżdżonej i zwracania kontroli do pętli zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="360e2-111">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="360e2-112">Formant jest zwracany _tylko_ jeden poziom w pętli zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="360e2-112">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="360e2-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="360e2-113">Example</span></span>

<span data-ttu-id="360e2-114">W tym przykładzie instrukcja `break` jest używana tylko do rozbicia z bieżącej gałęzi podczas każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="360e2-114">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="360e2-115">W pętli nie ma wpływ wystąpienia `break` należące do zagnieżdżonej instrukcji [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="360e2-115">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="360e2-116">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="360e2-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="360e2-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="360e2-117">See also</span></span>

- [<span data-ttu-id="360e2-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="360e2-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="360e2-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="360e2-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="360e2-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="360e2-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="360e2-121">switch</span><span class="sxs-lookup"><span data-stu-id="360e2-121">switch</span></span>](./switch.md)
