---
title: goto — instrukcja - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: 675893f02a0022b403d2afc018d24d6f826b8f75
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421805"
---
# <a name="goto-c-reference"></a><span data-ttu-id="7b72d-102">goto (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7b72d-102">goto (C# Reference)</span></span>

<span data-ttu-id="7b72d-103">`goto` Instrukcja przekazuje kontrolę nad programem bezpośrednio do instrukcji oznaczonej etykietą.</span><span class="sxs-lookup"><span data-stu-id="7b72d-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="7b72d-104">Typowym zastosowaniem `goto` jest kontrola jest przekazywana do określoną etykietą przypadku switch lub etykieta domyślna w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7b72d-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="7b72d-105">`goto` Instrukcji warto wykorzystać pętli głęboko zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="7b72d-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="7b72d-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b72d-106">Example</span></span>

<span data-ttu-id="7b72d-107">Poniższy przykład demonstruje użycie `goto` w [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7b72d-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="7b72d-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b72d-108">Example</span></span>

<span data-ttu-id="7b72d-109">Poniższy przykład demonstruje użycie `goto` umożliwiające rozbicie z zagnieżdżonej pętli.</span><span class="sxs-lookup"><span data-stu-id="7b72d-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="7b72d-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7b72d-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b72d-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b72d-111">See also</span></span>

- [<span data-ttu-id="7b72d-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7b72d-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b72d-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7b72d-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b72d-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7b72d-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b72d-115">goto, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="7b72d-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
