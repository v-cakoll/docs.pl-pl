---
title: Concatenation — Operatory
ms.date: 07/20/2015
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
ms.openlocfilehash: c123438a86a2c3293a99770107d970535fcdbdf8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388793"
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="ff648-102">Operatory łączenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff648-102">Concatenation Operators in Visual Basic</span></span>

<span data-ttu-id="ff648-103">Operatory łączenia sprzęga wiele ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="ff648-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="ff648-104">Istnieją dwa operatory łączenia `+` i `&` .</span><span class="sxs-lookup"><span data-stu-id="ff648-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="ff648-105">Oba te elementy wykonują podstawową operację łączenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff648-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>

```vb
Dim x As String = "Mic" & "ro" & "soft"
Dim y As String = "Mic" + "ro" + "soft"
' The preceding statements set both x and y to "Microsoft".
```

<span data-ttu-id="ff648-106">Te operatory mogą również łączyć `String` zmienne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ff648-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>

[!code-vb[VbVbalrOperators#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#76)]

## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="ff648-107">Różnice między dwoma operatorami łączenia</span><span class="sxs-lookup"><span data-stu-id="ff648-107">Differences Between the Two Concatenation Operators</span></span>

<span data-ttu-id="ff648-108">[Operator +](../../../language-reference/operators/addition-operator.md) ma podstawowy cel dodawania dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="ff648-108">The [+ Operator](../../../language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="ff648-109">Może jednak również łączyć argumenty operacji numerycznych z argumentami operacji ciągu.</span><span class="sxs-lookup"><span data-stu-id="ff648-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="ff648-110">`+`Operator ma złożony zestaw reguł, które określają, czy dodać, połączyć, sygnalizować błąd kompilatora lub zgłosić wyjątek czasu wykonywania <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="ff648-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="ff648-111">[Operator&](../../../language-reference/operators/concatenation-operator.md) jest zdefiniowany tylko dla `String` operandów i zawsze rozszerza jego operandy do `String` , niezależnie od ustawienia `Option Strict` .</span><span class="sxs-lookup"><span data-stu-id="ff648-111">The [& Operator](../../../language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="ff648-112">`&`Operator jest zalecany w przypadku łączenia ciągów, ponieważ jest zdefiniowany wyłącznie dla ciągów i zmniejsza szanse na wygenerowanie niezamierzonej konwersji.</span><span class="sxs-lookup"><span data-stu-id="ff648-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>

## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="ff648-113">Wydajność: ciąg i StringBuilder</span><span class="sxs-lookup"><span data-stu-id="ff648-113">Performance: String and StringBuilder</span></span>

<span data-ttu-id="ff648-114">Jeśli wykonasz znaczącą liczbę operacji manipulowania dla ciągu, takich jak łączenie, usuwanie i zamiany, wydajność może wynikać z <xref:System.Text.StringBuilder> klasy w <xref:System.Text> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ff648-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="ff648-115">Wykonanie dodatkowej instrukcji w celu utworzenia i zainicjowania <xref:System.Text.StringBuilder> obiektu, a także innej instrukcji Przekształć jej końcową wartość na `String` , ale możesz odzyskać ten czas, ponieważ <xref:System.Text.StringBuilder> może to przyspieszyć.</span><span class="sxs-lookup"><span data-stu-id="ff648-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff648-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff648-116">See also</span></span>

- [<span data-ttu-id="ff648-117">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ff648-117">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="ff648-118">Typy metod manipulowania ciągami w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff648-118">Types of String Manipulation Methods in Visual Basic</span></span>](../strings/types-of-string-manipulation-methods.md)
- [<span data-ttu-id="ff648-119">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff648-119">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ff648-120">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff648-120">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="ff648-121">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff648-121">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
