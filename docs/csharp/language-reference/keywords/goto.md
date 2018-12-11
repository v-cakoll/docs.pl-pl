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
ms.openlocfilehash: bfc997631cc147bf5718ec91a57e2995cead052f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236768"
---
# <a name="goto-c-reference"></a><span data-ttu-id="a3eda-102">goto (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a3eda-102">goto (C# Reference)</span></span>

<span data-ttu-id="a3eda-103">`goto` Instrukcja przekazuje kontrolę nad programem bezpośrednio do instrukcji oznaczonej etykietą.</span><span class="sxs-lookup"><span data-stu-id="a3eda-103">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="a3eda-104">Typowym zastosowaniem `goto` jest kontrola jest przekazywana do określoną etykietą przypadku switch lub etykieta domyślna w `switch` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a3eda-104">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="a3eda-105">`goto` Instrukcji warto wykorzystać pętli głęboko zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="a3eda-105">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="a3eda-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3eda-106">Example</span></span>

<span data-ttu-id="a3eda-107">Poniższy przykład demonstruje użycie `goto` w [Przełącz](switch.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a3eda-107">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="a3eda-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3eda-108">Example</span></span>

<span data-ttu-id="a3eda-109">Poniższy przykład demonstruje użycie `goto` umożliwiające rozbicie z zagnieżdżonej pętli.</span><span class="sxs-lookup"><span data-stu-id="a3eda-109">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="a3eda-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a3eda-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a3eda-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3eda-111">See also</span></span>

- [<span data-ttu-id="a3eda-112">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a3eda-112">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="a3eda-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a3eda-113">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="a3eda-114">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a3eda-114">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="a3eda-115">goto, instrukcja (C++)</span><span class="sxs-lookup"><span data-stu-id="a3eda-115">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)  
- [<span data-ttu-id="a3eda-116">Instrukcje skoku</span><span class="sxs-lookup"><span data-stu-id="a3eda-116">Jump Statements</span></span>](jump-statements.md)  
