---
title: implicit (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 70379136fd4b14403eac919ac15590250b17b416
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521206"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="d530f-102">implicit (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d530f-102">implicit (C# Reference)</span></span>

<span data-ttu-id="d530f-103">`implicit` Słowo kluczowe jest używane do deklarowania niejawnego typu zdefiniowanego przez użytkownika operatora konwersji.</span><span class="sxs-lookup"><span data-stu-id="d530f-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="d530f-104">Umożliwia włączanie niejawnych konwersji między typem zdefiniowanym przez użytkownika i innego typu, jeśli konwersja daje gwarancję spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="d530f-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>

## <a name="example"></a><span data-ttu-id="d530f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d530f-105">Example</span></span>

[!code-csharp[csrefKeywordsConversion#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#5)]

<span data-ttu-id="d530f-106">Dzięki wyeliminowaniu zbędnych rzutowania, niejawne konwersje można zwiększyć czytelność kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d530f-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="d530f-107">Jednak ponieważ niejawne konwersje nie wymagają programistom jawnie rzutowane z jednego typu na drugi, należy uważać, aby uniknąć nieoczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="d530f-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="d530f-108">Ogólnie rzecz biorąc operatory niejawnej konwersji powinno nigdy nie zgłaszają wyjątków i nigdy nie utracą informacje, aby używane bezpiecznie bez świadomości programisty.</span><span class="sxs-lookup"><span data-stu-id="d530f-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="d530f-109">Jeśli operator konwersji nie spełniają te kryteria, powinien być oznaczony `explicit`.</span><span class="sxs-lookup"><span data-stu-id="d530f-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="d530f-110">Aby uzyskać więcej informacji, zobacz [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d530f-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d530f-111">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d530f-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d530f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d530f-112">See also</span></span>

- [<span data-ttu-id="d530f-113">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d530f-113">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="d530f-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d530f-114">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="d530f-115">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="d530f-115">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="d530f-116">explicit</span><span class="sxs-lookup"><span data-stu-id="d530f-116">explicit</span></span>](explicit.md)  
- [<span data-ttu-id="d530f-117">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d530f-117">operator (C# Reference)</span></span>](operator.md)  
- [<span data-ttu-id="d530f-118">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="d530f-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
