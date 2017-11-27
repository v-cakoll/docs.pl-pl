---
title: "implicit (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords: implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a><span data-ttu-id="3268a-102">implicit (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3268a-102">implicit (C# Reference)</span></span>
<span data-ttu-id="3268a-103">`implicit` — Słowo kluczowe służy do deklarowania niejawne typu zdefiniowanego przez użytkownika operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="3268a-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="3268a-104">Użycia, aby włączyć niejawne konwersje między typu zdefiniowanego przez użytkownika i innego typu, jeśli jest gwarantowana konwersji, aby nie spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="3268a-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3268a-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3268a-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="3268a-106">Eliminując niepotrzebnego rzutowania niejawne konwersje może poprawić czytelność kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="3268a-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="3268a-107">Jednak ponieważ niejawne konwersje nie wymagają programistów jawnie rzutowania z typu na drugi, należy uważać, aby uniknąć nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="3268a-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="3268a-108">Ogólnie rzecz biorąc operatory niejawnej konwersji należy nigdy nie zgłaszają wyjątki i nigdy nie utracić informacje, aby używać bezpiecznego bez świadomości programisty.</span><span class="sxs-lookup"><span data-stu-id="3268a-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="3268a-109">Jeśli operator konwersji nie spełniają tych kryteriów, powinien być oznaczony `explicit`.</span><span class="sxs-lookup"><span data-stu-id="3268a-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="3268a-110">Aby uzyskać więcej informacji, zobacz [przy użyciu operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="3268a-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3268a-111">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3268a-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3268a-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3268a-112">See Also</span></span>  
 [<span data-ttu-id="3268a-113">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="3268a-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3268a-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3268a-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3268a-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="3268a-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="3268a-116">jawne</span><span class="sxs-lookup"><span data-stu-id="3268a-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="3268a-117">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3268a-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="3268a-118">Porady: Implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="3268a-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
