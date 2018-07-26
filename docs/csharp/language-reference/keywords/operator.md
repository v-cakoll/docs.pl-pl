---
title: operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: d633a46e21f913aa8c05289dccfb63e71efd697e
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959549"
---
# <a name="operator-c-reference"></a><span data-ttu-id="06cfb-102">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="06cfb-102">operator (C# Reference)</span></span>
<span data-ttu-id="06cfb-103">Użyj `operator` — słowo kluczowe przeciążenia wbudowanym operatorem lub podać konwersja zdefiniowana przez użytkownika, w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="06cfb-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06cfb-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="06cfb-104">Example</span></span>  
 <span data-ttu-id="06cfb-105">Poniżej znajduje się bardzo uproszczone klasę cyfry ułamkowe.</span><span class="sxs-lookup"><span data-stu-id="06cfb-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="06cfb-106">Przeciąża `+` i `*` operatory przeprowadzić ułamkowe Dodawanie i mnożenie, a także operator konwersji na to, że konwertuje `Fraction` typ `double` typu.</span><span class="sxs-lookup"><span data-stu-id="06cfb-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="06cfb-107">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06cfb-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="06cfb-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06cfb-108">See Also</span></span>  
 [<span data-ttu-id="06cfb-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="06cfb-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="06cfb-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="06cfb-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06cfb-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="06cfb-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="06cfb-112">implicit</span><span class="sxs-lookup"><span data-stu-id="06cfb-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="06cfb-113">explicit</span><span class="sxs-lookup"><span data-stu-id="06cfb-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="06cfb-114">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="06cfb-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
