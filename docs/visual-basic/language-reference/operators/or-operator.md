---
title: Or — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 03decb4ad32e8ff2c03e3b64a272bce779282973
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701239"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="83969-102">Or — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83969-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="83969-103">Wykonuje logiczne rozłączenie dwóch wyrażeń `Boolean` lub bitowego rozłączenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="83969-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83969-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83969-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="83969-105">Części</span><span class="sxs-lookup"><span data-stu-id="83969-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="83969-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="83969-106">Required.</span></span> <span data-ttu-id="83969-107">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="83969-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="83969-108">W przypadku porównania `Boolean` `result` to łączne logiczne rozłączenie dwóch wartości `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="83969-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="83969-109">W przypadku operacji bitowych `result` jest wartością liczbową reprezentującą łączny czas rozłączenia dwóch wzorców bitowych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="83969-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="83969-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="83969-110">Required.</span></span> <span data-ttu-id="83969-111">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="83969-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="83969-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="83969-112">Required.</span></span> <span data-ttu-id="83969-113">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="83969-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83969-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83969-114">Remarks</span></span>  
 <span data-ttu-id="83969-115">W przypadku porównania `Boolean` `result` jest `False`, jeśli i tylko wtedy, gdy `expression1` i `expression2` zostaną oszacowane do `False`.</span><span class="sxs-lookup"><span data-stu-id="83969-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="83969-116">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="83969-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="83969-117">Jeśli `expression1` to</span><span class="sxs-lookup"><span data-stu-id="83969-117">If `expression1` is</span></span>|<span data-ttu-id="83969-118">I `expression2` to</span><span class="sxs-lookup"><span data-stu-id="83969-118">And `expression2` is</span></span>|<span data-ttu-id="83969-119">Wartość `result` to</span><span class="sxs-lookup"><span data-stu-id="83969-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="83969-120">W porównaniu do `Boolean` operator `Or` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="83969-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="83969-121">[Operator OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *krótkie obwody*, co oznacza, że jeśli `expression1` jest `True`, wówczas `expression2` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="83969-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="83969-122">W przypadku operacji bitowych operator `Or` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="83969-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="83969-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="83969-123">If bit in `expression1` is</span></span>|<span data-ttu-id="83969-124">I bit w `expression2` to</span><span class="sxs-lookup"><span data-stu-id="83969-124">And bit in `expression2` is</span></span>|<span data-ttu-id="83969-125">Bit w `result` to</span><span class="sxs-lookup"><span data-stu-id="83969-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="83969-126">1</span><span class="sxs-lookup"><span data-stu-id="83969-126">1</span></span>|<span data-ttu-id="83969-127">1</span><span class="sxs-lookup"><span data-stu-id="83969-127">1</span></span>|<span data-ttu-id="83969-128">1</span><span class="sxs-lookup"><span data-stu-id="83969-128">1</span></span>|  
|<span data-ttu-id="83969-129">1</span><span class="sxs-lookup"><span data-stu-id="83969-129">1</span></span>|<span data-ttu-id="83969-130">0</span><span class="sxs-lookup"><span data-stu-id="83969-130">0</span></span>|<span data-ttu-id="83969-131">1</span><span class="sxs-lookup"><span data-stu-id="83969-131">1</span></span>|  
|<span data-ttu-id="83969-132">0</span><span class="sxs-lookup"><span data-stu-id="83969-132">0</span></span>|<span data-ttu-id="83969-133">1</span><span class="sxs-lookup"><span data-stu-id="83969-133">1</span></span>|<span data-ttu-id="83969-134">1</span><span class="sxs-lookup"><span data-stu-id="83969-134">1</span></span>|  
|<span data-ttu-id="83969-135">0</span><span class="sxs-lookup"><span data-stu-id="83969-135">0</span></span>|<span data-ttu-id="83969-136">0</span><span class="sxs-lookup"><span data-stu-id="83969-136">0</span></span>|<span data-ttu-id="83969-137">0</span><span class="sxs-lookup"><span data-stu-id="83969-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="83969-138">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="83969-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="83969-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="83969-139">Data Types</span></span>  
 <span data-ttu-id="83969-140">Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="83969-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="83969-141">W przypadku porównania `Boolean` typ danych wyniku to `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="83969-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="83969-142">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="83969-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="83969-143">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="83969-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="83969-144">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="83969-144">Overloading</span></span>  
 <span data-ttu-id="83969-145">Operator `Or` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="83969-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="83969-146">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="83969-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="83969-147">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="83969-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83969-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="83969-148">Example</span></span>  
 <span data-ttu-id="83969-149">W poniższym przykładzie za pomocą operatora `Or` można wykonać łączne logiczne rozłączenie dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="83969-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="83969-150">Wynikiem jest wartość `Boolean`, która reprezentuje, czy jeden z dwóch wyrażeń jest `True`.</span><span class="sxs-lookup"><span data-stu-id="83969-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="83969-151">W powyższym przykładzie wyniki są odpowiednio `True`, `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="83969-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83969-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="83969-152">Example</span></span>  
 <span data-ttu-id="83969-153">Poniższy przykład używa operatora `Or`, aby wykonać łączne logiczne rozłączenie dla poszczególnych bitów dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="83969-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="83969-154">Bit w wzorcu wyniku jest ustawiany, jeśli jeden z odpowiednich bitów w operandach jest ustawiony na 1.</span><span class="sxs-lookup"><span data-stu-id="83969-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="83969-155">Powyższy przykład daje wyniki odpowiednio 10, 14 i 14.</span><span class="sxs-lookup"><span data-stu-id="83969-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83969-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83969-156">See also</span></span>

- [<span data-ttu-id="83969-157">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83969-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="83969-158">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83969-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="83969-159">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="83969-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="83969-160">OrElse, operator</span><span class="sxs-lookup"><span data-stu-id="83969-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="83969-161">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83969-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
