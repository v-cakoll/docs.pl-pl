---
title: implicit (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215020"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="f77b5-102">implicit (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f77b5-102">implicit (C# Reference)</span></span>
<span data-ttu-id="f77b5-103">`implicit` — Słowo kluczowe służy do deklarowania niejawne typu zdefiniowanego przez użytkownika operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="f77b5-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="f77b5-104">Użycia, aby włączyć niejawne konwersje między typu zdefiniowanego przez użytkownika i innego typu, jeśli jest gwarantowana konwersji, aby nie spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="f77b5-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f77b5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="f77b5-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="f77b5-106">Eliminując niepotrzebnego rzutowania niejawne konwersje może poprawić czytelność kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f77b5-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="f77b5-107">Jednak ponieważ niejawne konwersje nie wymagają programistów jawnie rzutowania z typu na drugi, należy uważać, aby uniknąć nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="f77b5-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="f77b5-108">Ogólnie rzecz biorąc operatory niejawnej konwersji należy nigdy nie zgłaszają wyjątki i nigdy nie utracić informacje, aby używać bezpiecznego bez świadomości programisty.</span><span class="sxs-lookup"><span data-stu-id="f77b5-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="f77b5-109">Jeśli operator konwersji nie spełniają tych kryteriów, powinien być oznaczony `explicit`.</span><span class="sxs-lookup"><span data-stu-id="f77b5-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="f77b5-110">Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="f77b5-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="f77b5-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f77b5-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f77b5-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f77b5-112">See Also</span></span>  
 [<span data-ttu-id="f77b5-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="f77b5-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f77b5-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f77b5-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f77b5-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f77b5-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f77b5-116">explicit</span><span class="sxs-lookup"><span data-stu-id="f77b5-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="f77b5-117">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f77b5-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="f77b5-118">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="f77b5-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
