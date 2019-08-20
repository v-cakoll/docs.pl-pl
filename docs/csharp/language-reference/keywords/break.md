---
title: instrukcja break- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 77d18d12cd0fabb26906a5b58dc3939da6214a29
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602245"
---
# <a name="break-c-reference"></a><span data-ttu-id="3c69a-102">break (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3c69a-102">break (C# Reference)</span></span>

<span data-ttu-id="3c69a-103">Instrukcja kończy najbliższą otaczającą pętlę lub instrukcję Switch, w której występuje. [](./switch.md) `break`</span><span class="sxs-lookup"><span data-stu-id="3c69a-103">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="3c69a-104">Kontrolka jest przenoszona do instrukcji, która następuje po instrukcji zakończony (jeśli istnieje).</span><span class="sxs-lookup"><span data-stu-id="3c69a-104">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="3c69a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c69a-105">Example</span></span>

<span data-ttu-id="3c69a-106">W tym przykładzie Instrukcja warunkowa zawiera licznik, który powinien być liczony od 1 do 100; `break` Jednakże instrukcja kończy pętlę po 4 zliczenia.</span><span class="sxs-lookup"><span data-stu-id="3c69a-106">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="3c69a-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c69a-107">Example</span></span>

<span data-ttu-id="3c69a-108">W tym przykładzie `break` instrukcja jest używana do przerywania wewnętrznej pętli zagnieżdżonej i zwracania kontroli do pętli zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="3c69a-108">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="3c69a-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="3c69a-109">Example</span></span>

<span data-ttu-id="3c69a-110">Ten przykład ilustruje użycie `break` w instrukcji [Switch](./switch.md) .</span><span class="sxs-lookup"><span data-stu-id="3c69a-110">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="3c69a-111">W przypadku wprowadzenia `4`danych wyjściowych będzie:</span><span class="sxs-lookup"><span data-stu-id="3c69a-111">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="c-language-specification"></a><span data-ttu-id="3c69a-112">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3c69a-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3c69a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c69a-113">See also</span></span>

- [<span data-ttu-id="3c69a-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3c69a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3c69a-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3c69a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3c69a-116">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3c69a-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3c69a-117">switch</span><span class="sxs-lookup"><span data-stu-id="3c69a-117">switch</span></span>](./switch.md)
