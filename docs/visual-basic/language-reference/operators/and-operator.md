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
ms.openlocfilehash: bd6ebbf5f53a7cf187b5d8ce7630080d44d46df2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591618"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="fb49c-102">And — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb49c-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="fb49c-103">Wykonuje logiczne koniunkcje dla dwóch wyrażeń `Boolean` lub bitowego połączenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="fb49c-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb49c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fb49c-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="fb49c-105">Części</span><span class="sxs-lookup"><span data-stu-id="fb49c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="fb49c-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb49c-106">Required.</span></span> <span data-ttu-id="fb49c-107">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="fb49c-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="fb49c-108">W przypadku porównania logicznego `result` jest koniunkcją logiczną dwóch wartości `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="fb49c-109">W przypadku operacji bitowych `result` to wartość liczbowa reprezentująca bitowe połączenia dwóch wzorców bitowych liczb.</span><span class="sxs-lookup"><span data-stu-id="fb49c-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="fb49c-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb49c-110">Required.</span></span> <span data-ttu-id="fb49c-111">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="fb49c-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="fb49c-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="fb49c-112">Required.</span></span> <span data-ttu-id="fb49c-113">Dowolny `Boolean` lub wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="fb49c-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb49c-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fb49c-114">Remarks</span></span>  
 <span data-ttu-id="fb49c-115">W przypadku porównania logicznego wartość `result` jest `True`, jeśli i tylko wtedy, gdy obie `expression1` i `expression2` są oceniane do `True`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="fb49c-116">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="fb49c-117">Jeśli `expression1` to</span><span class="sxs-lookup"><span data-stu-id="fb49c-117">If `expression1` is</span></span>|<span data-ttu-id="fb49c-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="fb49c-118">And `expression2` is</span></span>|<span data-ttu-id="fb49c-119">Wartość `result` to</span><span class="sxs-lookup"><span data-stu-id="fb49c-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="fb49c-120">W porównaniu wartości logicznej operator `And` zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="fb49c-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="fb49c-121">[Operator AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *krótkie obwody*, co oznacza, że jeśli `expression1` jest `False`, wówczas `expression2` nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="fb49c-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="fb49c-122">W przypadku zastosowania do wartości numerycznych operator `And` wykonuje bitowe porównanie identycznie rozłożonych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="fb49c-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="fb49c-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="fb49c-123">If bit in `expression1` is</span></span>|<span data-ttu-id="fb49c-124">I bit w `expression2` to</span><span class="sxs-lookup"><span data-stu-id="fb49c-124">And bit in `expression2` is</span></span>|<span data-ttu-id="fb49c-125">Bit w `result` to</span><span class="sxs-lookup"><span data-stu-id="fb49c-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="fb49c-126">1</span><span class="sxs-lookup"><span data-stu-id="fb49c-126">1</span></span>|<span data-ttu-id="fb49c-127">1</span><span class="sxs-lookup"><span data-stu-id="fb49c-127">1</span></span>|<span data-ttu-id="fb49c-128">1</span><span class="sxs-lookup"><span data-stu-id="fb49c-128">1</span></span>|  
|<span data-ttu-id="fb49c-129">1</span><span class="sxs-lookup"><span data-stu-id="fb49c-129">1</span></span>|<span data-ttu-id="fb49c-130">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-130">0</span></span>|<span data-ttu-id="fb49c-131">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-131">0</span></span>|  
|<span data-ttu-id="fb49c-132">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-132">0</span></span>|<span data-ttu-id="fb49c-133">1</span><span class="sxs-lookup"><span data-stu-id="fb49c-133">1</span></span>|<span data-ttu-id="fb49c-134">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-134">0</span></span>|  
|<span data-ttu-id="fb49c-135">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-135">0</span></span>|<span data-ttu-id="fb49c-136">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-136">0</span></span>|<span data-ttu-id="fb49c-137">0</span><span class="sxs-lookup"><span data-stu-id="fb49c-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="fb49c-138">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wyniki.</span><span class="sxs-lookup"><span data-stu-id="fb49c-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="fb49c-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fb49c-139">Data Types</span></span>  
 <span data-ttu-id="fb49c-140">Jeśli operandy składają się z jednego wyrażenia `Boolean` i jednego wyrażenia liczbowego, Visual Basic konwertuje wyrażenie `Boolean` na wartość liczbową (– 1 dla `True` i 0 dla `False`) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="fb49c-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="fb49c-141">W przypadku porównania wartości logicznych typem danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="fb49c-142">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="fb49c-143">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="fb49c-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb49c-144">Operator `And` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb49c-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="fb49c-145">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="fb49c-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="fb49c-146">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fb49c-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb49c-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb49c-147">Example</span></span>  
 <span data-ttu-id="fb49c-148">Poniższy przykład używa operatora `And` do wykonywania logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb49c-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="fb49c-149">Wynikiem jest wartość `Boolean`, która reprezentuje, czy oba wyrażenia są `True`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="fb49c-150">Powyższy przykład daje wyniki odpowiednio dla `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="fb49c-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb49c-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb49c-151">Example</span></span>  
 <span data-ttu-id="fb49c-152">Poniższy przykład używa operatora `And` do wykonywania logicznego połączenia na poszczególnych bitach dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="fb49c-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="fb49c-153">Bit w wzorcu wyniku jest ustawiany, jeśli odpowiadające im bity w operandach są ustawione na 1.</span><span class="sxs-lookup"><span data-stu-id="fb49c-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="fb49c-154">Poprzedni przykład daje wyniki odpowiednio 8, 2 i 0.</span><span class="sxs-lookup"><span data-stu-id="fb49c-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb49c-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fb49c-155">See also</span></span>

- [<span data-ttu-id="fb49c-156">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb49c-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="fb49c-157">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb49c-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="fb49c-158">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="fb49c-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="fb49c-159">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="fb49c-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="fb49c-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb49c-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
