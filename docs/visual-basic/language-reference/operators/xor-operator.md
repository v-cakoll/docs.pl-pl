---
title: Xor — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: d82018a3018e2cf4362b9904ed127c20f56f6f0c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701268"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="91ccd-102">Xor — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91ccd-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="91ccd-103">Wykonuje logiczne wykluczenie dwóch wyrażeń `Boolean` lub bitowego wykluczenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="91ccd-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ccd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91ccd-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="91ccd-105">Części</span><span class="sxs-lookup"><span data-stu-id="91ccd-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="91ccd-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="91ccd-106">Required.</span></span> <span data-ttu-id="91ccd-107">Dowolna `Boolean` lub zmienna numeryczna.</span><span class="sxs-lookup"><span data-stu-id="91ccd-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="91ccd-108">W przypadku porównania logicznego wartość `result` jest wykluczeniem logicznym (wyłączne odłączenie logiczne) dwóch wartości `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="91ccd-109">W przypadku operacji bitowych `result` to wartość liczbowa, która reprezentuje wykluczenie bitowe (wyłączne rozłączenie bitowe) dwóch liczbowych wzorców bitowych.</span><span class="sxs-lookup"><span data-stu-id="91ccd-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="91ccd-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="91ccd-110">Required.</span></span> <span data-ttu-id="91ccd-111">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="91ccd-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="91ccd-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="91ccd-112">Required.</span></span> <span data-ttu-id="91ccd-113">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="91ccd-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91ccd-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91ccd-114">Remarks</span></span>  
 <span data-ttu-id="91ccd-115">W przypadku porównania logicznego `result` jest `True`, jeśli dokładnie jeden z `expression1` i `expression2` zostanie oszacowany jako `True`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="91ccd-116">To znaczy, jeśli i tylko wtedy, gdy `expression1` i `expression2` będą oceniane w przeciwieństwie do wartości `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="91ccd-117">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="91ccd-118">Jeśli `expression1` to</span><span class="sxs-lookup"><span data-stu-id="91ccd-118">If `expression1` is</span></span>|<span data-ttu-id="91ccd-119">I `expression2` to</span><span class="sxs-lookup"><span data-stu-id="91ccd-119">And `expression2` is</span></span>|<span data-ttu-id="91ccd-120">Wartość `result` to</span><span class="sxs-lookup"><span data-stu-id="91ccd-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="91ccd-121">W porównaniu wartości logicznej operator `Xor` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="91ccd-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="91ccd-122">Nie ma żadnych krótkich obwodów dla `Xor`, ponieważ wynik zawsze zależy od obu operandów.</span><span class="sxs-lookup"><span data-stu-id="91ccd-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="91ccd-123">Aby uzyskać *krótkie* operatory logiczne, zobacz [operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) i [operator OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="91ccd-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="91ccd-124">W przypadku operacji bitowych operator `Xor` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="91ccd-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="91ccd-125">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="91ccd-125">If bit in `expression1` is</span></span>|<span data-ttu-id="91ccd-126">I bit w `expression2` to</span><span class="sxs-lookup"><span data-stu-id="91ccd-126">And bit in `expression2` is</span></span>|<span data-ttu-id="91ccd-127">Bit w `result` to</span><span class="sxs-lookup"><span data-stu-id="91ccd-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="91ccd-128">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-128">1</span></span>|<span data-ttu-id="91ccd-129">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-129">1</span></span>|<span data-ttu-id="91ccd-130">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-130">0</span></span>|  
|<span data-ttu-id="91ccd-131">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-131">1</span></span>|<span data-ttu-id="91ccd-132">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-132">0</span></span>|<span data-ttu-id="91ccd-133">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-133">1</span></span>|  
|<span data-ttu-id="91ccd-134">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-134">0</span></span>|<span data-ttu-id="91ccd-135">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-135">1</span></span>|<span data-ttu-id="91ccd-136">1</span><span class="sxs-lookup"><span data-stu-id="91ccd-136">1</span></span>|  
|<span data-ttu-id="91ccd-137">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-137">0</span></span>|<span data-ttu-id="91ccd-138">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-138">0</span></span>|<span data-ttu-id="91ccd-139">0</span><span class="sxs-lookup"><span data-stu-id="91ccd-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="91ccd-140">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="91ccd-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="91ccd-141">Na przykład 5 `Xor` 3 to 6.</span><span class="sxs-lookup"><span data-stu-id="91ccd-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="91ccd-142">Aby sprawdzić, dlaczego jest to zrobione, przekonwertuj 5 i 3 na ich reprezentacje binarne, 101 i 011.</span><span class="sxs-lookup"><span data-stu-id="91ccd-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="91ccd-143">Następnie użyj poprzedniej tabeli, aby określić, że 101 XOR 011 wynosi 110, czyli reprezentację binarną liczby dziesiętnej 6.</span><span class="sxs-lookup"><span data-stu-id="91ccd-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="91ccd-144">Typy danych</span><span class="sxs-lookup"><span data-stu-id="91ccd-144">Data Types</span></span>  
 <span data-ttu-id="91ccd-145">Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="91ccd-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="91ccd-146">W przypadku porównania `Boolean` typ danych wyniku to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="91ccd-147">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="91ccd-148">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="91ccd-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="91ccd-149">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="91ccd-149">Overloading</span></span>  
 <span data-ttu-id="91ccd-150">Operator `Xor` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="91ccd-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="91ccd-151">Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="91ccd-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="91ccd-152">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="91ccd-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="91ccd-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="91ccd-153">Example</span></span>  
 <span data-ttu-id="91ccd-154">Poniższy przykład używa operatora `Xor` do przeprowadzenia logicznego wykluczenia (wyłączne logiczne rozłączenie) w dwóch wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="91ccd-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="91ccd-155">Wynikiem jest wartość `Boolean`, która reprezentuje, czy dokładnie jedno z wyrażeń jest `True`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="91ccd-156">W poprzednim przykładzie są generowane odpowiednio wyniki `False`, `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="91ccd-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91ccd-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="91ccd-157">Example</span></span>  
 <span data-ttu-id="91ccd-158">Poniższy przykład używa operatora `Xor` do przeprowadzenia logicznego wykluczenia (wyłączne logiczne rozłączenie) w poszczególnych bitach dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="91ccd-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="91ccd-159">Bit w wzorcu wyniku jest ustawiony, jeśli dokładnie jeden z odpowiednich bitów w operandach jest ustawiony na 1.</span><span class="sxs-lookup"><span data-stu-id="91ccd-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="91ccd-160">W poprzednim przykładzie wyniki są odpowiednio 2, 12 i 14.</span><span class="sxs-lookup"><span data-stu-id="91ccd-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ccd-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91ccd-161">See also</span></span>

- [<span data-ttu-id="91ccd-162">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91ccd-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="91ccd-163">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91ccd-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="91ccd-164">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="91ccd-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="91ccd-165">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91ccd-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
