---
title: instrukcja goto — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 076f793e880a7b4d1e8872d80e88c44cdf077541
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715273"
---
# <a name="goto-c-reference"></a><span data-ttu-id="0ded9-102">goto (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0ded9-102">goto (C# Reference)</span></span>

<span data-ttu-id="0ded9-103">Instrukcja `goto` przenosi formant programu bezpośrednio do instrukcji z etykietą.</span><span class="sxs-lookup"><span data-stu-id="0ded9-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="0ded9-104">Typowym zastosowaniem `goto` jest przeniesienie kontroli do określonej etykiety switch-case lub etykiety domyślnej w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0ded9-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="0ded9-105">Instrukcja `goto` jest również przydatne, aby wydostać się z głęboko zagnieżdżonych pętli.</span><span class="sxs-lookup"><span data-stu-id="0ded9-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="0ded9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ded9-106">Example</span></span>

<span data-ttu-id="0ded9-107">W poniższym przykładzie `goto` przedstawiono użycie w [instrukcji switch.](switch.md)</span><span class="sxs-lookup"><span data-stu-id="0ded9-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="0ded9-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0ded9-108">Example</span></span>

<span data-ttu-id="0ded9-109">W poniższym przykładzie `goto` przedstawiono użycie do wyrwania się z pętli zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="0ded9-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="0ded9-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0ded9-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0ded9-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ded9-111">See also</span></span>

- [<span data-ttu-id="0ded9-112">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="0ded9-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0ded9-113">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="0ded9-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0ded9-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0ded9-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0ded9-115">goto, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="0ded9-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
