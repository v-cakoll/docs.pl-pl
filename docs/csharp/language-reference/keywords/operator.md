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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="operator-c-reference"></a><span data-ttu-id="5a87c-102">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5a87c-102">operator (C# Reference)</span></span>
<span data-ttu-id="5a87c-103">Użyj `operator` — słowo kluczowe przeciążenia operatora wbudowane lub udzielenia konwersji zdefiniowanej przez użytkownika w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5a87c-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a87c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a87c-104">Example</span></span>  
 <span data-ttu-id="5a87c-105">Poniżej znajduje się bardzo uproszczonego klasę liczbami ułamkowymi.</span><span class="sxs-lookup"><span data-stu-id="5a87c-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="5a87c-106">Przeciąża `+` i `*` operatory przeprowadzić ułamkowych Dodawanie i mnożenie i udostępnia również operatora konwersji tego konwertuje `Fraction` typ `double` typu.</span><span class="sxs-lookup"><span data-stu-id="5a87c-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>  
  
 [!code-csharp[csrefKeywordsConversion#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5a87c-107">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a87c-107">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5a87c-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a87c-108">See Also</span></span>  
 [<span data-ttu-id="5a87c-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="5a87c-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5a87c-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5a87c-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a87c-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5a87c-111">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5a87c-112">implicit</span><span class="sxs-lookup"><span data-stu-id="5a87c-112">implicit</span></span>](../../../csharp/language-reference/keywords/implicit.md)  
 [<span data-ttu-id="5a87c-113">explicit</span><span class="sxs-lookup"><span data-stu-id="5a87c-113">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="5a87c-114">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="5a87c-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
