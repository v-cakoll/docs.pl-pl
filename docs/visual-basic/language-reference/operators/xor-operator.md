---
title: Xor, operator
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
ms.openlocfilehash: 999050314d674fa98833083d84796e471c22971d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406343"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="c9c29-102">Xor — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9c29-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="c9c29-103">Wykonuje logiczne wykluczenie dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c9c29-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9c29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c9c29-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c9c29-105">Części</span><span class="sxs-lookup"><span data-stu-id="c9c29-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="c9c29-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c9c29-106">Required.</span></span> <span data-ttu-id="c9c29-107">Dowolna `Boolean` lub zmienna numeryczna.</span><span class="sxs-lookup"><span data-stu-id="c9c29-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="c9c29-108">W przypadku porównania logicznego `result` jest to logiczne wykluczenie (wyłączne odłączenie logiczne) dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="c9c29-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="c9c29-109">W przypadku operacji bitowych `result` jest wartością liczbową, która reprezentuje wykluczenie bitowe (wyłączne rozłączenie bitowe) dwóch liczbowych wzorców bitowych.</span><span class="sxs-lookup"><span data-stu-id="c9c29-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="c9c29-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c9c29-110">Required.</span></span> <span data-ttu-id="c9c29-111">`Boolean`Wyrażenie dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="c9c29-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="c9c29-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c9c29-112">Required.</span></span> <span data-ttu-id="c9c29-113">`Boolean`Wyrażenie dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="c9c29-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9c29-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c9c29-114">Remarks</span></span>  
 <span data-ttu-id="c9c29-115">W przypadku porównania logicznego, `result` jest `True` if i tylko wtedy, gdy dokładnie jeden z `expression1` i jest `expression2` obliczany do `True` .</span><span class="sxs-lookup"><span data-stu-id="c9c29-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="c9c29-116">To znaczy, jeśli i tylko wtedy, gdy `expression1` i `expression2` szacują wartości przeciwne `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c9c29-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="c9c29-117">W poniższej tabeli przedstawiono sposób `result` określania.</span><span class="sxs-lookup"><span data-stu-id="c9c29-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="c9c29-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-118">If `expression1` is</span></span>|<span data-ttu-id="c9c29-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-119">And `expression2` is</span></span>|<span data-ttu-id="c9c29-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="c9c29-121">W porównaniu wartości logicznej `Xor` operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="c9c29-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="c9c29-122">Nie ma żadnych krótkich obwodów `Xor` , ponieważ wynik zawsze zależy od obu operandów.</span><span class="sxs-lookup"><span data-stu-id="c9c29-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="c9c29-123">Aby uzyskać *krótkie* operatory logiczne, zobacz [operator AndAlso](andalso-operator.md) i [operator OrElse](orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c9c29-123">For *short-circuiting* logical operators, see [AndAlso Operator](andalso-operator.md) and [OrElse Operator](orelse-operator.md).</span></span>  
  
 <span data-ttu-id="c9c29-124">W przypadku operacji bitowych `Xor` operator wykonuje bitowe porównanie identycznie ustawionych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w zależności od `result` poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="c9c29-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="c9c29-125">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-125">If bit in `expression1` is</span></span>|<span data-ttu-id="c9c29-126">I bit w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-126">And bit in `expression2` is</span></span>|<span data-ttu-id="c9c29-127">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="c9c29-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="c9c29-128">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-128">1</span></span>|<span data-ttu-id="c9c29-129">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-129">1</span></span>|<span data-ttu-id="c9c29-130">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-130">0</span></span>|  
|<span data-ttu-id="c9c29-131">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-131">1</span></span>|<span data-ttu-id="c9c29-132">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-132">0</span></span>|<span data-ttu-id="c9c29-133">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-133">1</span></span>|  
|<span data-ttu-id="c9c29-134">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-134">0</span></span>|<span data-ttu-id="c9c29-135">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-135">1</span></span>|<span data-ttu-id="c9c29-136">1</span><span class="sxs-lookup"><span data-stu-id="c9c29-136">1</span></span>|  
|<span data-ttu-id="c9c29-137">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-137">0</span></span>|<span data-ttu-id="c9c29-138">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-138">0</span></span>|<span data-ttu-id="c9c29-139">0</span><span class="sxs-lookup"><span data-stu-id="c9c29-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="c9c29-140">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="c9c29-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="c9c29-141">Na przykład 5 `Xor` 3 to 6.</span><span class="sxs-lookup"><span data-stu-id="c9c29-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="c9c29-142">Aby sprawdzić, dlaczego jest to zrobione, przekonwertuj 5 i 3 na ich reprezentacje binarne, 101 i 011.</span><span class="sxs-lookup"><span data-stu-id="c9c29-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="c9c29-143">Następnie użyj poprzedniej tabeli, aby określić, że 101 XOR 011 wynosi 110, czyli reprezentację binarną liczby dziesiętnej 6.</span><span class="sxs-lookup"><span data-stu-id="c9c29-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="c9c29-144">Typy danych</span><span class="sxs-lookup"><span data-stu-id="c9c29-144">Data Types</span></span>  
 <span data-ttu-id="c9c29-145">Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False` ) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="c9c29-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="c9c29-146">Dla `Boolean` porównania, typ danych wyniku `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c9c29-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="c9c29-147">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2` .</span><span class="sxs-lookup"><span data-stu-id="c9c29-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="c9c29-148">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="c9c29-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c9c29-149">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c9c29-149">Overloading</span></span>  
 <span data-ttu-id="c9c29-150">`Xor`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c9c29-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c9c29-151">Jeśli kod używa tego operatora dla takiej klasy lub struktury, upewnij się, że rozumiesz jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="c9c29-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="c9c29-152">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c9c29-152">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c29-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9c29-153">Example</span></span>  
 <span data-ttu-id="c9c29-154">Poniższy przykład używa `Xor` operatora do przeprowadzenia logicznego wykluczenia (wyłączne logiczne rozłączenie) w dwóch wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="c9c29-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="c9c29-155">Wynik jest `Boolean` wartością, która reprezentuje, czy dokładnie jedno wyrażenie jest `True` .</span><span class="sxs-lookup"><span data-stu-id="c9c29-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="c9c29-156">Poprzedni przykład daje wyniki `False` , `True` i `False` , odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c9c29-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c29-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9c29-157">Example</span></span>  
 <span data-ttu-id="c9c29-158">Poniższy przykład używa `Xor` operatora do wykonywania logicznego wykluczenia (wyłączne logiczne rozłączenie) w poszczególnych bitach dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="c9c29-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="c9c29-159">Bit w wzorcu wyniku jest ustawiony, jeśli dokładnie jeden z odpowiednich bitów w operandach jest ustawiony na 1.</span><span class="sxs-lookup"><span data-stu-id="c9c29-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="c9c29-160">W poprzednim przykładzie wyniki są odpowiednio 2, 12 i 14.</span><span class="sxs-lookup"><span data-stu-id="c9c29-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c29-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9c29-161">See also</span></span>

- [<span data-ttu-id="c9c29-162">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9c29-162">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="c9c29-163">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c9c29-163">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c9c29-164">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="c9c29-164">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c9c29-165">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9c29-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
