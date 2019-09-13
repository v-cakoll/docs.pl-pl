---
title: Mod — Operator (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: 08e3eec08ba099e6f5c7796a459c55de09afa917
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929334"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="b97fa-102">Mod — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b97fa-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="b97fa-103">Dzieli dwie liczby i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="b97fa-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="b97fa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b97fa-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="b97fa-105">Części</span><span class="sxs-lookup"><span data-stu-id="b97fa-105">Parts</span></span>

`result` \
<span data-ttu-id="b97fa-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b97fa-106">Required.</span></span> <span data-ttu-id="b97fa-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="b97fa-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="b97fa-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b97fa-108">Required.</span></span> <span data-ttu-id="b97fa-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b97fa-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="b97fa-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b97fa-110">Required.</span></span> <span data-ttu-id="b97fa-111">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b97fa-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="b97fa-112">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="b97fa-112">Supported types</span></span>

<span data-ttu-id="b97fa-113">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="b97fa-113">All numeric types.</span></span> <span data-ttu-id="b97fa-114">Obejmuje to typy niepodpisane i zmiennoprzecinkowe oraz `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="b97fa-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="b97fa-115">Wynik</span><span class="sxs-lookup"><span data-stu-id="b97fa-115">Result</span></span>

<span data-ttu-id="b97fa-116">Wynik jest resztą po `number1` poddzieleniu przez. `number2`</span><span class="sxs-lookup"><span data-stu-id="b97fa-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="b97fa-117">Na przykład wyrażenie `14 Mod 4` ma wartość 2.</span><span class="sxs-lookup"><span data-stu-id="b97fa-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="b97fa-118">Istnieje różnica między *resztą* i *modulo* w postaci matematyki z różnymi wynikami dla liczb ujemnych.</span><span class="sxs-lookup"><span data-stu-id="b97fa-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="b97fa-119">Operator w Visual Basic, operator .NET Framework `op_Modulus` i źródłowa instrukcja [REM](<xref:System.Reflection.Emit.OpCodes.Rem>) Il All wykonują resztę operacji. `Mod`</span><span class="sxs-lookup"><span data-stu-id="b97fa-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="b97fa-120">Wynik `Mod` operacji zachowuje znak dywidendy, `number1`a więc może być dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="b97fa-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="b97fa-121">Wynik jest zawsze z zakresu (-`number2`, `number2`), z wyłączeniem.</span><span class="sxs-lookup"><span data-stu-id="b97fa-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="b97fa-122">Przykład:</span><span class="sxs-lookup"><span data-stu-id="b97fa-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="b97fa-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b97fa-123">Remarks</span></span>

<span data-ttu-id="b97fa-124">`number1` Jeśli lub `number2` jest wartością zmiennoprzecinkową, zwracana jest pozostała część podziału zmiennoprzecinkowego.</span><span class="sxs-lookup"><span data-stu-id="b97fa-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="b97fa-125">Typ danych wyniku to najmniejszy typ danych, który może zawierać wszystkie możliwe wartości wynikające z dzielenia z typami `number1` danych i. `number2`</span><span class="sxs-lookup"><span data-stu-id="b97fa-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="b97fa-126">Jeśli `number1` lub`number2` zwróci wartość [Nothing](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="b97fa-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="b97fa-127">Operatory pokrewne obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="b97fa-127">Related operators include the following:</span></span>

- <span data-ttu-id="b97fa-128">[Operator \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) zwraca iloraz całkowity dzielenia.</span><span class="sxs-lookup"><span data-stu-id="b97fa-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="b97fa-129">Na przykład wyrażenie `14 \ 4` ma wartość 3.</span><span class="sxs-lookup"><span data-stu-id="b97fa-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="b97fa-130">[Operator/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) zwraca pełny iloraz, łącznie z resztą, jako liczbę zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="b97fa-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="b97fa-131">Na przykład wyrażenie `14 / 4` ma wartość 3,5.</span><span class="sxs-lookup"><span data-stu-id="b97fa-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="b97fa-132">Próba dzielenia przez zero</span><span class="sxs-lookup"><span data-stu-id="b97fa-132">Attempted division by zero</span></span>

<span data-ttu-id="b97fa-133">Jeśli `number2` wartość jest równa zero, zachowanie `Mod` operatora zależy od typu danych operandów:</span><span class="sxs-lookup"><span data-stu-id="b97fa-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="b97fa-134">W przypadku, gdy `number2` nie można określić w czasie kompilacji i generuje błąd `BC30542 Division by zero occurred while evaluating this expression` czasu `number2` kompilacji, jeśli wartość jest szacowana na zero w czasie kompilacji. <xref:System.DivideByZeroException></span><span class="sxs-lookup"><span data-stu-id="b97fa-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="b97fa-135">Podział liczby zmiennoprzecinkowej zwraca <xref:System.Double.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b97fa-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="b97fa-136">Odpowiednik formuły</span><span class="sxs-lookup"><span data-stu-id="b97fa-136">Equivalent formula</span></span>

<span data-ttu-id="b97fa-137">Wyrażenie `a Mod b` jest równoważne jednej z następujących formuł:</span><span class="sxs-lookup"><span data-stu-id="b97fa-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="b97fa-138">Niedokładność zmiennoprzecinkowa</span><span class="sxs-lookup"><span data-stu-id="b97fa-138">Floating-point imprecision</span></span>

<span data-ttu-id="b97fa-139">Podczas pracy z liczbami zmiennoprzecinkowymi należy pamiętać, że nie zawsze mają precyzyjną reprezentację dziesiętną w pamięci.</span><span class="sxs-lookup"><span data-stu-id="b97fa-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="b97fa-140">Może to prowadzić do nieoczekiwanych wyników niektórych operacji, takich jak porównywanie wartości `Mod` i operator.</span><span class="sxs-lookup"><span data-stu-id="b97fa-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="b97fa-141">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typami danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="b97fa-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="b97fa-142">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b97fa-142">Overloading</span></span>

<span data-ttu-id="b97fa-143">Operator może być przeciążony, co oznacza, że Klasa lub struktura mogą definiować jego zachowanie. `Mod`</span><span class="sxs-lookup"><span data-stu-id="b97fa-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="b97fa-144">Jeśli Twój kod odnosi `Mod` się do wystąpienia klasy lub struktury, która zawiera takie Przeciążenie, należy poznać jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b97fa-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b97fa-145">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b97fa-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="b97fa-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="b97fa-146">Example</span></span>

<span data-ttu-id="b97fa-147">Poniższy przykład używa operatora, `Mod` aby podzielić dwie liczby i zwrócić tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="b97fa-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="b97fa-148">Jeśli liczba jest liczbą zmiennoprzecinkową, wynik jest liczbą zmiennoprzecinkową, która reprezentuje resztę.</span><span class="sxs-lookup"><span data-stu-id="b97fa-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="b97fa-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="b97fa-149">Example</span></span>

<span data-ttu-id="b97fa-150">Poniższy przykład ilustruje potencjalną niedokładność argumentów operacji zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="b97fa-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="b97fa-151">W pierwszej instrukcji operandy są `Double`i 0,2 to nieskończonie powtarzające się ułamek binarny z przechowywaną wartością 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="b97fa-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="b97fa-152">W drugiej instrukcji znak `D` typu literału wymusza oba operandy do `Decimal`, i 0,2 ma dokładną reprezentację.</span><span class="sxs-lookup"><span data-stu-id="b97fa-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="b97fa-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b97fa-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="b97fa-154">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="b97fa-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b97fa-155">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b97fa-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b97fa-156">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b97fa-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b97fa-157">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="b97fa-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="b97fa-158">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b97fa-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="b97fa-159">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b97fa-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
