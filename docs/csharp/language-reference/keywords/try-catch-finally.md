---
title: try-catch-finally- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 9f2c82fb140e18454491660d17b570db0a8a2aef
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168589"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="12c0b-102">try-catch-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="12c0b-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="12c0b-103">Typowym zastosowaniem `catch` i `finally` razem jest uzyskanie zasobów `try` i korzystanie z nich w `catch` bloku, zaradzenie sobie z wyjątkowymi okolicznościami w bloku i zwolnienie zasobów `finally` w bloku.</span><span class="sxs-lookup"><span data-stu-id="12c0b-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="12c0b-104">Aby uzyskać więcej informacji i przykładów dotyczących ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i wyrzucanie [wyjątków](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="12c0b-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="12c0b-105">Aby uzyskać więcej informacji na `finally` temat bloku, zobacz [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="12c0b-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="12c0b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="12c0b-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="12c0b-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="12c0b-107">C# language specification</span></span>

<span data-ttu-id="12c0b-108">Aby uzyskać więcej informacji, zobacz sekcję [try instrukcji](~/_csharplang/spec/statements.md#the-try-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="12c0b-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="12c0b-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12c0b-109">See also</span></span>

- [<span data-ttu-id="12c0b-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="12c0b-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12c0b-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="12c0b-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="12c0b-112">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="12c0b-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="12c0b-113">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="12c0b-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="12c0b-114">throw</span><span class="sxs-lookup"><span data-stu-id="12c0b-114">throw</span></span>](throw.md)
- [<span data-ttu-id="12c0b-115">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="12c0b-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="12c0b-116">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="12c0b-116">using Statement</span></span>](using-statement.md)
