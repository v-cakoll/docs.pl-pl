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
ms.openlocfilehash: b127c50f3319d4fe7c4890fc3bffb295baa37466
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936672"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="e3910-102">Mod — operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3910-102">Mod operator (Visual Basic)</span></span>
<span data-ttu-id="e3910-103">Dzieli dwie liczby i zwraca tylko resztę z dzielenia.</span><span class="sxs-lookup"><span data-stu-id="e3910-103">Divides two numbers and returns only the remainder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3910-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3910-104">Syntax</span></span>  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a><span data-ttu-id="e3910-105">Części</span><span class="sxs-lookup"><span data-stu-id="e3910-105">Parts</span></span>  
 `number1`  
 <span data-ttu-id="e3910-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3910-106">Required.</span></span> <span data-ttu-id="e3910-107">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="e3910-107">Any numeric expression.</span></span>  
  
 `number2`  
 <span data-ttu-id="e3910-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e3910-108">Required.</span></span> <span data-ttu-id="e3910-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="e3910-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="e3910-110">Obsługiwane typy</span><span class="sxs-lookup"><span data-stu-id="e3910-110">Supported types</span></span>  
 <span data-ttu-id="e3910-111">Wszystkich typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="e3910-111">All numeric types.</span></span> <span data-ttu-id="e3910-112">Obejmuje to typy bez znaku i błędy liczb zmiennopozycyjnych i `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e3910-112">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="e3910-113">Wynik</span><span class="sxs-lookup"><span data-stu-id="e3910-113">Result</span></span>

<span data-ttu-id="e3910-114">Wynik jest resztę po `number1` jest dzielona przez `number2`.</span><span class="sxs-lookup"><span data-stu-id="e3910-114">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="e3910-115">Na przykład, wyrażenie `14 Mod 4` daje w wyniku 2.</span><span class="sxs-lookup"><span data-stu-id="e3910-115">For example, the expression `14 Mod 4` evaluates to 2.</span></span>  

> [!NOTE]
> <span data-ttu-id="e3910-116">Istnieje różnica pomiędzy *resztę* i *modulo* w matematyce, przy użyciu różne wyniki dla liczb ujemnych.</span><span class="sxs-lookup"><span data-stu-id="e3910-116">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="e3910-117">`Mod` Operatora w języku Visual Basic .NET Framework `op_Modulus` operatora i podstawowych [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) instrukcja IL wykonywać wszystkie operacje resztę.</span><span class="sxs-lookup"><span data-stu-id="e3910-117">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="e3910-118">Wynik `Mod` operacja zachowuje znak dzielna `number1`, a więc może być dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="e3910-118">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="e3910-119">Wynik jest zawsze w zakresie (-`number2`, `number2`), wyłączności.</span><span class="sxs-lookup"><span data-stu-id="e3910-119">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="e3910-120">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e3910-120">For example:</span></span>

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

## <a name="remarks"></a><span data-ttu-id="e3910-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3910-121">Remarks</span></span>  
 <span data-ttu-id="e3910-122">Jeśli `number1` lub `number2` jest wartość zmiennoprzecinkowa jest zwracana zmiennoprzecinkową resztę z dzielenia.</span><span class="sxs-lookup"><span data-stu-id="e3910-122">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="e3910-123">Typ danych wyniku jest najmniejszego typu danych, który może pomieścić wszystkich możliwych wartości, które wynikają z dzielenia z typami danych `number1` i `number2`.</span><span class="sxs-lookup"><span data-stu-id="e3910-123">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>  
  
 <span data-ttu-id="e3910-124">Jeśli `number1` lub `number2` daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), jest ona traktowana jak zero.</span><span class="sxs-lookup"><span data-stu-id="e3910-124">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
 <span data-ttu-id="e3910-125">Operatory powiązane są następujące:</span><span class="sxs-lookup"><span data-stu-id="e3910-125">Related operators include the following:</span></span>  
  
- <span data-ttu-id="e3910-126">[\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) Zwraca iloraz liczb całkowitych z dzielenia.</span><span class="sxs-lookup"><span data-stu-id="e3910-126">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="e3910-127">Na przykład, wyrażenie `14 \ 4` daje w wyniku 3.</span><span class="sxs-lookup"><span data-stu-id="e3910-127">For example, the expression `14 \ 4` evaluates to 3.</span></span>  
  
- <span data-ttu-id="e3910-128">[/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) zwraca pełny iloraz, w tym resztę, jako liczba zmiennoprzecinkowa.</span><span class="sxs-lookup"><span data-stu-id="e3910-128">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="e3910-129">Na przykład, wyrażenie `14 / 4` daje w wyniku 3.5.</span><span class="sxs-lookup"><span data-stu-id="e3910-129">For example, the expression `14 / 4` evaluates to 3.5.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="e3910-130">Próba dzielenia przez zero</span><span class="sxs-lookup"><span data-stu-id="e3910-130">Attempted division by zero</span></span>  
 <span data-ttu-id="e3910-131">Jeśli `number2` daje w wyniku wartość zero, zachowanie `Mod` operator zależy od typu danych operandu.</span><span class="sxs-lookup"><span data-stu-id="e3910-131">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands.</span></span> <span data-ttu-id="e3910-132">Zgłasza dzielenia liczby całkowitej <xref:System.DivideByZeroException> wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e3910-132">An integral division throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="e3910-133">Zwraca dzielenia liczb zmiennopozycyjnych <xref:System.Double.NaN>.</span><span class="sxs-lookup"><span data-stu-id="e3910-133">A floating-point division returns <xref:System.Double.NaN>.</span></span>  
  
## <a name="equivalent-formula"></a><span data-ttu-id="e3910-134">Równoważne formuły</span><span class="sxs-lookup"><span data-stu-id="e3910-134">Equivalent formula</span></span>  
 <span data-ttu-id="e3910-135">Wyrażenie `a Mod b` odpowiada jednej z następujących formuł:</span><span class="sxs-lookup"><span data-stu-id="e3910-135">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a><span data-ttu-id="e3910-136">Zmiennoprzecinkowe niedokładności</span><span class="sxs-lookup"><span data-stu-id="e3910-136">Floating-point imprecision</span></span>  
 <span data-ttu-id="e3910-137">Podczas pracy z liczb zmiennoprzecinkowych, należy pamiętać, że nie zawsze mają precyzyjną formie dziesiętnej w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e3910-137">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="e3910-138">Może to prowadzić do nieoczekiwanych wyników z niektórych operacji, takich jak porównania wartości i `Mod` operatora.</span><span class="sxs-lookup"><span data-stu-id="e3910-138">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="e3910-139">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z typów danych](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="e3910-139">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="e3910-140">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="e3910-140">Overloading</span></span>  
 <span data-ttu-id="e3910-141">`Mod` Operator może być *przeciążone*, co oznacza, że klasy lub struktury zdefiniować ponownie jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e3910-141">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="e3910-142">Jeśli kod ma zastosowanie `Mod` do wystąpienia klasy lub struktury, która obejmuje takie przeciążenia, upewnij się, zrozumieć zachowania zmieniony.</span><span class="sxs-lookup"><span data-stu-id="e3910-142">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e3910-143">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e3910-143">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3910-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3910-144">Example</span></span>  
 <span data-ttu-id="e3910-145">W poniższym przykładzie użyto `Mod` operator dzielenia dwóch liczb i zwraca tylko resztę.</span><span class="sxs-lookup"><span data-stu-id="e3910-145">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="e3910-146">Jeśli albo liczba jest liczba zmiennoprzecinkowa, wynik jest liczba zmiennoprzecinkowa, który reprezentuje resztę.</span><span class="sxs-lookup"><span data-stu-id="e3910-146">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="e3910-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3910-147">Example</span></span>  
 <span data-ttu-id="e3910-148">W poniższym przykładzie pokazano potencjał niedokładności argumentów operacji zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="e3910-148">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="e3910-149">W pierwszej instrukcji argumenty operacji są `Double`, a 0.2 jest nieskończenie powtarzające się ułamek binarne, przy użyciu przechowywaną wartość 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="e3910-149">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="e3910-150">W drugiej instrukcji literału wpisz znak `D` wymusza oba operandy `Decimal`, i 0.2 jej reprezentacji dokładne.</span><span class="sxs-lookup"><span data-stu-id="e3910-150">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="e3910-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3910-151">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="e3910-152">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="e3910-152">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="e3910-153">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3910-153">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e3910-154">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e3910-154">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e3910-155">Rozwiązywanie problemów związanych z typami danych</span><span class="sxs-lookup"><span data-stu-id="e3910-155">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="e3910-156">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3910-156">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="e3910-157">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3910-157">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
