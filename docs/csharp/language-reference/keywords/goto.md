---
title: goto — instrukcja C# -Reference
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715273"
---
# <a name="goto-c-reference"></a><span data-ttu-id="2217b-102">goto (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="2217b-102">goto (C# Reference)</span></span>

<span data-ttu-id="2217b-103">Instrukcja `goto` przekazuje kontrolę programu bezpośrednio do instrukcji oznaczonej etykietą.</span><span class="sxs-lookup"><span data-stu-id="2217b-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="2217b-104">Typowym zastosowaniem `goto` jest przeniesienie kontroli do konkretnej etykiety przypadku przełącznika lub etykiety domyślnej w instrukcji `switch`.</span><span class="sxs-lookup"><span data-stu-id="2217b-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="2217b-105">Instrukcja `goto` jest również przydatna do uzyskiwania z głęboko zagnieżdżonych pętli.</span><span class="sxs-lookup"><span data-stu-id="2217b-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="2217b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="2217b-106">Example</span></span>

<span data-ttu-id="2217b-107">Poniższy przykład ilustruje użycie `goto` w instrukcji [Switch](switch.md) .</span><span class="sxs-lookup"><span data-stu-id="2217b-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="2217b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="2217b-108">Example</span></span>

<span data-ttu-id="2217b-109">Poniższy przykład ilustruje użycie `goto` do dzielenia z zagnieżdżonych pętli.</span><span class="sxs-lookup"><span data-stu-id="2217b-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="2217b-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2217b-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2217b-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2217b-111">See also</span></span>

- [<span data-ttu-id="2217b-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2217b-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2217b-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2217b-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2217b-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="2217b-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2217b-115">goto, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="2217b-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
