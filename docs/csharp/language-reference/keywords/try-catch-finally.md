---
title: try-catch-finally- C# Reference
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713043"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="45c4e-102">try-catch-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="45c4e-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="45c4e-103">Typowym zastosowaniem `catch` i `finally` jednocześnie jest uzyskanie zasobów i używanie ich w bloku `try`, zaradzenie sobie z wyjątkowymi okolicznościami w bloku `catch` i zwolnienie zasobów w bloku `finally`.</span><span class="sxs-lookup"><span data-stu-id="45c4e-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="45c4e-104">Aby uzyskać więcej informacji i przykładów dotyczących ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i [wyrzucanie wyjątków](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="45c4e-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="45c4e-105">Aby uzyskać więcej informacji na temat bloku `finally`, zobacz [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="45c4e-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="45c4e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="45c4e-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="45c4e-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45c4e-107">C# language specification</span></span>

<span data-ttu-id="45c4e-108">Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="45c4e-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="45c4e-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45c4e-109">See also</span></span>

- [<span data-ttu-id="45c4e-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45c4e-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="45c4e-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45c4e-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="45c4e-112">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="45c4e-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="45c4e-113">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="45c4e-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="45c4e-114">throw</span><span class="sxs-lookup"><span data-stu-id="45c4e-114">throw</span></span>](throw.md)
- [<span data-ttu-id="45c4e-115">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="45c4e-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="45c4e-116">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="45c4e-116">using Statement</span></span>](using-statement.md)
