---
title: Operator — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929875"
---
# <a name="operator-c-reference"></a><span data-ttu-id="eaf9e-102">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eaf9e-102">operator (C# Reference)</span></span>

<span data-ttu-id="eaf9e-103">Użyj `operator` — słowo kluczowe przeciążenia wbudowanym operatorem lub podać konwersja zdefiniowana przez użytkownika, w deklaracji klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="eaf9e-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

## <a name="example"></a><span data-ttu-id="eaf9e-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="eaf9e-104">Example</span></span>

<span data-ttu-id="eaf9e-105">Poniżej znajduje się bardzo uproszczone klasę cyfry ułamkowe.</span><span class="sxs-lookup"><span data-stu-id="eaf9e-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="eaf9e-106">Przeciąża `+` i `*` operatory przeprowadzić ułamkowe Dodawanie i mnożenie, a także operator konwersji na to, że konwertuje `Fraction` typ `double` typu.</span><span class="sxs-lookup"><span data-stu-id="eaf9e-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="eaf9e-107">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eaf9e-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eaf9e-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eaf9e-108">See also</span></span>

- [<span data-ttu-id="eaf9e-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eaf9e-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eaf9e-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eaf9e-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eaf9e-111">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="eaf9e-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="eaf9e-112">implicit</span><span class="sxs-lookup"><span data-stu-id="eaf9e-112">implicit</span></span>](implicit.md)
- [<span data-ttu-id="eaf9e-113">explicit</span><span class="sxs-lookup"><span data-stu-id="eaf9e-113">explicit</span></span>](explicit.md)
- [<span data-ttu-id="eaf9e-114">Instrukcje: implementowanie zdefiniowanych przez użytkownika konwersji struktur</span><span class="sxs-lookup"><span data-stu-id="eaf9e-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
