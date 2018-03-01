---
title: "And — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="543cc-102">And — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="543cc-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="543cc-103">Wykonuje koniunkcję logiczną na dwóch `Boolean` wyrażeń lub koniunkcję bitową na dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="543cc-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="543cc-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="543cc-105">Części</span><span class="sxs-lookup"><span data-stu-id="543cc-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="543cc-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="543cc-106">Required.</span></span> <span data-ttu-id="543cc-107">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="543cc-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="543cc-108">Dla porównania Boolean `result` jest logicznego połączenia dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="543cc-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="543cc-109">Dla Operacje bitowe `result` wartość liczbową reprezentujący koniunkcję wzorców liczbowych bit dwa.</span><span class="sxs-lookup"><span data-stu-id="543cc-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="543cc-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="543cc-110">Required.</span></span> <span data-ttu-id="543cc-111">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="543cc-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="543cc-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="543cc-112">Required.</span></span> <span data-ttu-id="543cc-113">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="543cc-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="543cc-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="543cc-114">Remarks</span></span>  
 <span data-ttu-id="543cc-115">Dla porównania Boolean `result` jest `True` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` obliczać `True`.</span><span class="sxs-lookup"><span data-stu-id="543cc-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="543cc-116">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="543cc-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="543cc-117">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-117">If `expression1` is</span></span>|<span data-ttu-id="543cc-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-118">And `expression2` is</span></span>|<span data-ttu-id="543cc-119">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="543cc-120">Logiczna porównania `And` operator zawsze ocenia oba wyrażenia, które mogą obejmować tworzenie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="543cc-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="543cc-121">[AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `False`, następnie `expression2` nie jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="543cc-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="543cc-122">Po zastosowaniu do wartości numerycznych `And` operator przeprowadza porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="543cc-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="543cc-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-123">If bit in `expression1` is</span></span>|<span data-ttu-id="543cc-124">I bit w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-124">And bit in `expression2` is</span></span>|<span data-ttu-id="543cc-125">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="543cc-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="543cc-126">1</span><span class="sxs-lookup"><span data-stu-id="543cc-126">1</span></span>|<span data-ttu-id="543cc-127">1</span><span class="sxs-lookup"><span data-stu-id="543cc-127">1</span></span>|<span data-ttu-id="543cc-128">1</span><span class="sxs-lookup"><span data-stu-id="543cc-128">1</span></span>|  
|<span data-ttu-id="543cc-129">1</span><span class="sxs-lookup"><span data-stu-id="543cc-129">1</span></span>|<span data-ttu-id="543cc-130">0</span><span class="sxs-lookup"><span data-stu-id="543cc-130">0</span></span>|<span data-ttu-id="543cc-131">0</span><span class="sxs-lookup"><span data-stu-id="543cc-131">0</span></span>|  
|<span data-ttu-id="543cc-132">0</span><span class="sxs-lookup"><span data-stu-id="543cc-132">0</span></span>|<span data-ttu-id="543cc-133">1</span><span class="sxs-lookup"><span data-stu-id="543cc-133">1</span></span>|<span data-ttu-id="543cc-134">0</span><span class="sxs-lookup"><span data-stu-id="543cc-134">0</span></span>|  
|<span data-ttu-id="543cc-135">0</span><span class="sxs-lookup"><span data-stu-id="543cc-135">0</span></span>|<span data-ttu-id="543cc-136">0</span><span class="sxs-lookup"><span data-stu-id="543cc-136">0</span></span>|<span data-ttu-id="543cc-137">0</span><span class="sxs-lookup"><span data-stu-id="543cc-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="543cc-138">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wyniki.</span><span class="sxs-lookup"><span data-stu-id="543cc-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="543cc-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="543cc-139">Data Types</span></span>  
 <span data-ttu-id="543cc-140">Jeśli operandy składają się z jednego `Boolean` wyrażenie i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje operacji.</span><span class="sxs-lookup"><span data-stu-id="543cc-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="543cc-141">Porównanie Boolean, typ danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="543cc-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="543cc-142">Porównanie bitowe, typu danych jest typ liczbowy odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="543cc-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="543cc-143">Znajdują się w tabeli "Relacyjnych i operator porównania" [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="543cc-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="543cc-144">`And` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="543cc-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="543cc-145">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="543cc-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="543cc-146">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="543cc-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="543cc-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="543cc-147">Example</span></span>  
 <span data-ttu-id="543cc-148">W poniższym przykładzie użyto `And` operatora, aby wykonać koniunkcję logiczną na dwóch wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="543cc-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="543cc-149">Wynik jest `Boolean` wartość wskazującą, czy oba wyrażenia są `True`.</span><span class="sxs-lookup"><span data-stu-id="543cc-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="543cc-150">Powyższy przykład produkuje wyniki `True` i `False`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="543cc-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="543cc-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="543cc-151">Example</span></span>  
 <span data-ttu-id="543cc-152">W poniższym przykładzie użyto `And` operatora, aby wykonać połączenie logiczne na poszczególnych bitów dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="543cc-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="543cc-153">Bit we wzorcu wynik jest ustawiona, jeśli odpowiednich bitów w operandy zostaną ustawione na 1.</span><span class="sxs-lookup"><span data-stu-id="543cc-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="543cc-154">Powyższy przykład produkuje wyniki 8, 2 i 0, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="543cc-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543cc-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="543cc-155">See Also</span></span>  
 [<span data-ttu-id="543cc-156">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="543cc-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="543cc-157">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="543cc-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="543cc-158">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="543cc-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="543cc-159">AndAlso — Operator</span><span class="sxs-lookup"><span data-stu-id="543cc-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="543cc-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="543cc-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
