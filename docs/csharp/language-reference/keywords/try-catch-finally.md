---
title: try-catch-finally — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 3419ad46d5bbe13bb4308ad15b7819d615cdbe86
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244729"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="7dbee-102">try-catch-finally (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7dbee-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="7dbee-103">Wspólne użycie `catch` i `finally` razem, jest do uzyskania i używania zasobów w `try` zablokować, pracę z wyjątkowych okolicznościach w `catch` zablokować, a także zwalniać zasoby w `finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="7dbee-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="7dbee-104">Aby uzyskać więcej informacji i przykłady, ponownego zgłaszania wyjątków, zobacz [try-catch —](try-catch.md) i [zgłaszanie wyjątków](../../../standard/exceptions/index.md).</span><span class="sxs-lookup"><span data-stu-id="7dbee-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="7dbee-105">Aby uzyskać więcej informacji na temat `finally` blokowania, zobacz [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="7dbee-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="7dbee-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7dbee-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="7dbee-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7dbee-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7dbee-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7dbee-108">See also</span></span>

- [<span data-ttu-id="7dbee-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7dbee-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7dbee-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7dbee-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7dbee-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="7dbee-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7dbee-112">Instrukcje try, throw i catch (C++)</span><span class="sxs-lookup"><span data-stu-id="7dbee-112">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="7dbee-113">Instrukcje obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="7dbee-113">Exception Handling Statements</span></span>](exception-handling-statements.md)
- [<span data-ttu-id="7dbee-114">throw</span><span class="sxs-lookup"><span data-stu-id="7dbee-114">throw</span></span>](throw.md)
- [<span data-ttu-id="7dbee-115">Instrukcje: Jawne zgłaszanie wyjątków</span><span class="sxs-lookup"><span data-stu-id="7dbee-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="7dbee-116">using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7dbee-116">using Statement</span></span>](using-statement.md)