---
title: try-catch-finally - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713043"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="ae9b2-102">try-catch-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ae9b2-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="ae9b2-103">Powszechnym zastosowaniem `catch` `finally` i razem jest uzyskanie i `try` wykorzystanie zasobów w bloku, radzić sobie z wyjątkowymi okolicznościami w `catch` bloku i zwolnić zasoby w `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ae9b2-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="ae9b2-104">Aby uzyskać więcej informacji i przykłady dotyczące ponownego zgłaszania wyjątków, zobacz [try-catch](try-catch.md) i [zgłaszanie wyjątków](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ae9b2-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="ae9b2-105">Aby uzyskać więcej `finally` informacji o bloku, zobacz [wypróbuj na końcu](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="ae9b2-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae9b2-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae9b2-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="ae9b2-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ae9b2-107">C# language specification</span></span>

<span data-ttu-id="ae9b2-108">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja wypróbuj](~/_csharplang/spec/statements.md#the-try-statement) [specyfikację języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="ae9b2-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ae9b2-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ae9b2-109">See also</span></span>

- [<span data-ttu-id="ae9b2-110">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="ae9b2-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ae9b2-111">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="ae9b2-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ae9b2-112">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ae9b2-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ae9b2-113">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="ae9b2-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="ae9b2-114">throw</span><span class="sxs-lookup"><span data-stu-id="ae9b2-114">throw</span></span>](throw.md)
- [<span data-ttu-id="ae9b2-115">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="ae9b2-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="ae9b2-116">za pomocą instrukcji</span><span class="sxs-lookup"><span data-stu-id="ae9b2-116">using Statement</span></span>](using-statement.md)
