---
title: And — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913170"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="9ce87-102">And — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ce87-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="9ce87-103">Wykonuje logiczną koniunkcję w dwóch `Boolean` wyrażeniach lub bitowego połączenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="9ce87-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ce87-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ce87-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9ce87-105">Części</span><span class="sxs-lookup"><span data-stu-id="9ce87-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9ce87-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9ce87-106">Required.</span></span> <span data-ttu-id="9ce87-107">Wyrażenie `Boolean` dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9ce87-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="9ce87-108">W przypadku porównania `result` logicznego jest koniunkcja logiczna dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="9ce87-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="9ce87-109">W przypadku operacji `result` bitowych jest wartością liczbową reprezentującą bitowe połączenia dwóch wzorców bitowych liczb.</span><span class="sxs-lookup"><span data-stu-id="9ce87-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="9ce87-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9ce87-110">Required.</span></span> <span data-ttu-id="9ce87-111">Wyrażenie `Boolean` dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9ce87-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9ce87-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="9ce87-112">Required.</span></span> <span data-ttu-id="9ce87-113">Wyrażenie `Boolean` dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="9ce87-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ce87-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ce87-114">Remarks</span></span>  
 <span data-ttu-id="9ce87-115">`result` W przypadku porównania wartości logicznych `True` jest if i tylko wtedy `expression1` , `expression2` gdy oba `True`i są oceniane do.</span><span class="sxs-lookup"><span data-stu-id="9ce87-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="9ce87-116">W poniższej tabeli przedstawiono sposób `result` określania.</span><span class="sxs-lookup"><span data-stu-id="9ce87-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9ce87-117">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-117">If `expression1` is</span></span>|<span data-ttu-id="9ce87-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-118">And `expression2` is</span></span>|<span data-ttu-id="9ce87-119">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="9ce87-120">W porównaniu `And` wartości logicznej operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="9ce87-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="9ce87-121">[Operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *krótkie obwody*, co oznacza, że `expression1` jeśli jest `False`, `expression2` to nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="9ce87-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="9ce87-122">W przypadku zastosowania do wartości `And` numerycznych operator wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zależności od poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ce87-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="9ce87-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-123">If bit in `expression1` is</span></span>|<span data-ttu-id="9ce87-124">I bit w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-124">And bit in `expression2` is</span></span>|<span data-ttu-id="9ce87-125">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="9ce87-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="9ce87-126">1</span><span class="sxs-lookup"><span data-stu-id="9ce87-126">1</span></span>|<span data-ttu-id="9ce87-127">1</span><span class="sxs-lookup"><span data-stu-id="9ce87-127">1</span></span>|<span data-ttu-id="9ce87-128">1</span><span class="sxs-lookup"><span data-stu-id="9ce87-128">1</span></span>|  
|<span data-ttu-id="9ce87-129">1</span><span class="sxs-lookup"><span data-stu-id="9ce87-129">1</span></span>|<span data-ttu-id="9ce87-130">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-130">0</span></span>|<span data-ttu-id="9ce87-131">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-131">0</span></span>|  
|<span data-ttu-id="9ce87-132">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-132">0</span></span>|<span data-ttu-id="9ce87-133">1</span><span class="sxs-lookup"><span data-stu-id="9ce87-133">1</span></span>|<span data-ttu-id="9ce87-134">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-134">0</span></span>|  
|<span data-ttu-id="9ce87-135">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-135">0</span></span>|<span data-ttu-id="9ce87-136">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-136">0</span></span>|<span data-ttu-id="9ce87-137">0</span><span class="sxs-lookup"><span data-stu-id="9ce87-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="9ce87-138">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wyniki.</span><span class="sxs-lookup"><span data-stu-id="9ce87-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9ce87-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9ce87-139">Data Types</span></span>  
 <span data-ttu-id="9ce87-140">Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic `Boolean` konwertuje wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="9ce87-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="9ce87-141">W przypadku porównania wartości logicznych typem danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9ce87-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="9ce87-142">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów `expression1` danych i. `expression2`</span><span class="sxs-lookup"><span data-stu-id="9ce87-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9ce87-143">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="9ce87-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ce87-144">Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `And`</span><span class="sxs-lookup"><span data-stu-id="9ce87-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9ce87-145">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9ce87-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9ce87-146">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9ce87-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce87-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ce87-147">Example</span></span>  
 <span data-ttu-id="9ce87-148">Poniższy przykład używa `And` operatora do wykonywania logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9ce87-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="9ce87-149">Wynik jest `Boolean` wartością, która reprezentuje, czy oba wyrażenia są `True`.</span><span class="sxs-lookup"><span data-stu-id="9ce87-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="9ce87-150">Powyższy przykład daje wyniki `True` odpowiednio i. `False`</span><span class="sxs-lookup"><span data-stu-id="9ce87-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ce87-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="9ce87-151">Example</span></span>  
 <span data-ttu-id="9ce87-152">Poniższy przykład używa `And` operatora do wykonywania logicznego połączenia na poszczególnych bitach dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="9ce87-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="9ce87-153">Bit w wzorcu wyniku jest ustawiany, jeśli odpowiadające im bity w operandach są ustawione na 1.</span><span class="sxs-lookup"><span data-stu-id="9ce87-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="9ce87-154">Poprzedni przykład daje wyniki odpowiednio 8, 2 i 0.</span><span class="sxs-lookup"><span data-stu-id="9ce87-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ce87-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ce87-155">See also</span></span>

- [<span data-ttu-id="9ce87-156">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ce87-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9ce87-157">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce87-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9ce87-158">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="9ce87-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9ce87-159">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="9ce87-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="9ce87-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ce87-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
