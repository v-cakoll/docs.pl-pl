---
title: Or, operator
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
ms.openlocfilehash: 657b2a473b23789a8ba25fbd11c6b83538fa7803
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401423"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="f6b6d-102">Or — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b6d-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="f6b6d-103">Wykonuje logiczne rozłączenie dwóch `Boolean` wyrażeń lub bitowego rozłączenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6b6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6b6d-104">Syntax</span></span>  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="f6b6d-105">Części</span><span class="sxs-lookup"><span data-stu-id="f6b6d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="f6b6d-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-106">Required.</span></span> <span data-ttu-id="f6b6d-107">`Boolean`Wyrażenie dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="f6b6d-108">W przypadku `Boolean` porównania `result` jest to łączne logiczne rozłączenie dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="f6b6d-109">W przypadku operacji bitowych `result` jest wartością liczbową reprezentującą łączny czas rozłączenia dwóch wzorców bitowych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="f6b6d-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-110">Required.</span></span> <span data-ttu-id="f6b6d-111">`Boolean`Wyrażenie dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="f6b6d-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-112">Required.</span></span> <span data-ttu-id="f6b6d-113">`Boolean`Wyrażenie dowolne lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6b6d-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6b6d-114">Remarks</span></span>  
 <span data-ttu-id="f6b6d-115">W przypadku `Boolean` porównania `result` ma wartość `False` i tylko wtedy, gdy oba i są `expression1` `expression2` oceniane do `False` .</span><span class="sxs-lookup"><span data-stu-id="f6b6d-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="f6b6d-116">W poniższej tabeli przedstawiono sposób `result` określania.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="f6b6d-117">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-117">If `expression1` is</span></span>|<span data-ttu-id="f6b6d-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-118">And `expression2` is</span></span>|<span data-ttu-id="f6b6d-119">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="f6b6d-120">W `Boolean` porównaniu `Or` operator zawsze oblicza oba wyrażenia, które mogą obejmować wykonywanie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="f6b6d-121">[Operator OrElse](orelse-operator.md) wykonuje *krótkie obwody*, co oznacza, że jeśli `expression1` jest `True` , `expression2` to nie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-121">The [OrElse Operator](orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="f6b6d-122">W przypadku operacji bitowych `Or` operator wykonuje bitowe porównanie identycznie ustawionych bitów w dwóch wyrażeniach liczbowych i ustawia odpowiedni bit w zależności od `result` poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="f6b6d-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-123">If bit in `expression1` is</span></span>|<span data-ttu-id="f6b6d-124">I bit w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-124">And bit in `expression2` is</span></span>|<span data-ttu-id="f6b6d-125">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="f6b6d-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="f6b6d-126">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-126">1</span></span>|<span data-ttu-id="f6b6d-127">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-127">1</span></span>|<span data-ttu-id="f6b6d-128">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-128">1</span></span>|  
|<span data-ttu-id="f6b6d-129">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-129">1</span></span>|<span data-ttu-id="f6b6d-130">0</span><span class="sxs-lookup"><span data-stu-id="f6b6d-130">0</span></span>|<span data-ttu-id="f6b6d-131">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-131">1</span></span>|  
|<span data-ttu-id="f6b6d-132">0</span><span class="sxs-lookup"><span data-stu-id="f6b6d-132">0</span></span>|<span data-ttu-id="f6b6d-133">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-133">1</span></span>|<span data-ttu-id="f6b6d-134">1</span><span class="sxs-lookup"><span data-stu-id="f6b6d-134">1</span></span>|  
|<span data-ttu-id="f6b6d-135">0</span><span class="sxs-lookup"><span data-stu-id="f6b6d-135">0</span></span>|<span data-ttu-id="f6b6d-136">0</span><span class="sxs-lookup"><span data-stu-id="f6b6d-136">0</span></span>|<span data-ttu-id="f6b6d-137">0</span><span class="sxs-lookup"><span data-stu-id="f6b6d-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f6b6d-138">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne operatory arytmetyczne i relacyjne, każda operacja bitowa powinna być ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="f6b6d-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="f6b6d-139">Data Types</span></span>  
 <span data-ttu-id="f6b6d-140">Jeśli operandy składają się z jednego `Boolean` wyrażenia i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenie na wartość liczbową (– 1 dla `True` i 0 dla `False` ) i wykonuje operację bitową.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="f6b6d-141">Dla `Boolean` porównania, typ danych wyniku `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f6b6d-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="f6b6d-142">W przypadku porównania bitowego typem danych wynik jest typ liczbowy odpowiedni dla typów danych `expression1` i `expression2` .</span><span class="sxs-lookup"><span data-stu-id="f6b6d-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="f6b6d-143">Zobacz tabelę "porównania relacyjne i bitowe" w [typach danych wyników operatora](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="f6b6d-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f6b6d-144">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="f6b6d-144">Overloading</span></span>  
 <span data-ttu-id="f6b6d-145">`Or`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f6b6d-146">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f6b6d-147">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f6b6d-147">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b6d-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6b6d-148">Example</span></span>  
 <span data-ttu-id="f6b6d-149">Poniższy przykład używa operatora, `Or` Aby wykonać łączne logiczne rozłączenie dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="f6b6d-150">Wynik jest `Boolean` wartością, która reprezentuje, czy jedno z dwóch wyrażeń jest `True` .</span><span class="sxs-lookup"><span data-stu-id="f6b6d-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 <span data-ttu-id="f6b6d-151">Powyższy przykład daje wyniki `True` , `True` i, `False` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6b6d-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6b6d-152">Example</span></span>  
 <span data-ttu-id="f6b6d-153">Poniższy przykład używa operatora, `Or` Aby wykonać łączne logiczne rozłączenie dla poszczególnych bitów dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="f6b6d-154">Bit w wzorcu wyniku jest ustawiany, jeśli jeden z odpowiednich bitów w operandach jest ustawiony na 1.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 <span data-ttu-id="f6b6d-155">Powyższy przykład daje wyniki odpowiednio 10, 14 i 14.</span><span class="sxs-lookup"><span data-stu-id="f6b6d-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6b6d-156">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f6b6d-156">See also</span></span>

- [<span data-ttu-id="f6b6d-157">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b6d-157">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="f6b6d-158">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6b6d-158">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f6b6d-159">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="f6b6d-159">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f6b6d-160">OrElse, operator</span><span class="sxs-lookup"><span data-stu-id="f6b6d-160">OrElse Operator</span></span>](orelse-operator.md)
- [<span data-ttu-id="f6b6d-161">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6b6d-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
