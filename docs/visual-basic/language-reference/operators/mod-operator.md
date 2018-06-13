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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5120823f4e001fc3aff71f267176311e2465597a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604853"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="39112-102">Mod — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39112-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="39112-103">Dzieli dwie liczby i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="39112-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39112-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39112-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="39112-105">Części</span><span class="sxs-lookup"><span data-stu-id="39112-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="39112-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="39112-106">Required.</span></span> <span data-ttu-id="39112-107">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="39112-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="39112-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="39112-108">Required.</span></span> <span data-ttu-id="39112-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="39112-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="39112-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="39112-110">Supported types</span></span>  
 <span data-ttu-id="39112-111">Wszystkie typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="39112-111">All numeric types.</span></span> <span data-ttu-id="39112-112">Obejmuje to typy bez znaku i zmiennoprzecinkowych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="39112-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="39112-113">Wynik</span><span class="sxs-lookup"><span data-stu-id="39112-113">Result</span></span>

<span data-ttu-id="39112-114">Wynik jest resztę po `number1` przez `number2`.</span><span class="sxs-lookup"><span data-stu-id="39112-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="39112-115">Na przykład, wyrażenie `14 Mod 4` ocenia się na 2.</span><span class="sxs-lookup"><span data-stu-id="39112-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="39112-116">Ma różnicy między *pozostałej* i *modulo* w systemu dziesiętnego, różne wyniki dla wartości ujemne.</span><span class="sxs-lookup"><span data-stu-id="39112-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="39112-117">`Mod` Operatora w języku Visual Basic .NET Framework `op_Modulus` operatora i podstawowej [rem]<xref:System.Reflection.Emit.OpCodes.Rem> wszystkie operacja pozostałej instrukcji IL.</span><span class="sxs-lookup"><span data-stu-id="39112-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem]<xref:System.Reflection.Emit.OpCodes.Rem> IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="39112-118">Wynik `Mod` operacja zachowuje znak dzielna `number1`, a więc może być liczbą dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="39112-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="39112-119">Wynik jest zawsze w zakresie (-`number2`, `number2`), wyłącznego.</span><span class="sxs-lookup"><span data-stu-id="39112-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="39112-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="39112-120">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="39112-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="39112-121">Remarks</span></span>  
 <span data-ttu-id="39112-122">Jeśli dowolny `number1` lub `number2` jest wartość zmiennoprzecinkową zmiennoprzecinkowe pozostałej części podziału jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="39112-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="39112-123">Typ danych wyniku to najmniejsza typu danych, który może posiadać wszystkie możliwe wartości wynikających z dzielenia z typami danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="39112-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="39112-124">Jeśli `number1` lub `number2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest traktowany jako zero.</span><span class="sxs-lookup"><span data-stu-id="39112-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="39112-125">Operatory powiązane są następujące:</span><span class="sxs-lookup"><span data-stu-id="39112-125">Related operators include the following:</span></span>  
  
-   <span data-ttu-id="39112-126">[\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczbą całkowitą z dzielenia.</span><span class="sxs-lookup"><span data-stu-id="39112-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="39112-127">Na przykład, wyrażenie `14 \ 4` daje w wyniku 3.</span><span class="sxs-lookup"><span data-stu-id="39112-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
-   <span data-ttu-id="39112-128">[/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) Zwraca iloraz pełne, łącznie z pozostałą, jako liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="39112-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="39112-129">Na przykład, wyrażenie `14 / 4` daje w wyniku 3.5.</span><span class="sxs-lookup"><span data-stu-id="39112-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="39112-130">Próba dzielenia przez zero</span><span class="sxs-lookup"><span data-stu-id="39112-130">Attempted division by zero</span></span>  
 <span data-ttu-id="39112-131">Jeśli `number2` daje w wyniku wartość zero, zachowanie `Mod` operator zależy od typu danych operandów.</span><span class="sxs-lookup"><span data-stu-id="39112-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="39112-132">Zgłasza całkowitą dzielenia <xref:System.DivideByZeroException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="39112-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="39112-133">Zwraca dzielenia liczb zmiennoprzecinkowych <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="39112-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="39112-134">Formuła równoważne</span><span class="sxs-lookup"><span data-stu-id="39112-134">Equivalent formula</span></span>  
 <span data-ttu-id="39112-135">Wyrażenie `a Mod b` odpowiada jednej z następujących formuły:</span><span class="sxs-lookup"><span data-stu-id="39112-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="39112-136">Zmiennoprzecinkowe błędu</span><span class="sxs-lookup"><span data-stu-id="39112-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="39112-137">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają dokładne dziesiętna reprezentacja w pamięci.</span><span class="sxs-lookup"><span data-stu-id="39112-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="39112-138">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="39112-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="39112-139">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="39112-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="39112-140">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="39112-140">Overloading</span></span>  
 <span data-ttu-id="39112-141">`Mod` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania.</span><span class="sxs-lookup"><span data-stu-id="39112-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="39112-142">Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która obejmuje takie przeciążenia, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="39112-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="39112-143">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="39112-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39112-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="39112-144">Example</span></span>  
 <span data-ttu-id="39112-145">W poniższym przykładzie użyto `Mod` operator do dzielenia dwie liczby i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="39112-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="39112-146">Jeśli liczba zmiennoprzecinkowa, albo liczbą wynik jest reprezentujący Pozostała liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="39112-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="39112-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="39112-147">Example</span></span>  
 <span data-ttu-id="39112-148">W poniższym przykładzie pokazano ryzyko błędu argumentów operacji zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="39112-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="39112-149">W pierwszej instrukcji argumenty operacji są `Double`, i 0,2 jest nieskończenie identycznych ułamek binarnego z wartością przechowywaną 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="39112-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="39112-150">W drugim instrukcji literału znaku typu `D` wymusza oba argumenty do `Decimal`, i 0,2 ma reprezentację dokładne.</span><span class="sxs-lookup"><span data-stu-id="39112-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/mod-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="39112-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39112-151">See also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 [<span data-ttu-id="39112-152">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="39112-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="39112-153">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39112-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="39112-154">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="39112-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="39112-155">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="39112-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="39112-156">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39112-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="39112-157">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39112-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
