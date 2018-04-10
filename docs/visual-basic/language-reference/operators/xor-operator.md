---
title: Xor — Operator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b14f11f2df2df9c29e88e9188390cfe245d2cb58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="00ec8-102">Xor — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00ec8-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="00ec8-103">Wykonuje logiczne wykluczenie na dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="00ec8-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ec8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00ec8-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="00ec8-105">Części</span><span class="sxs-lookup"><span data-stu-id="00ec8-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="00ec8-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="00ec8-106">Required.</span></span> <span data-ttu-id="00ec8-107">Wszelkie `Boolean` lub zmienna numeryczna.</span><span class="sxs-lookup"><span data-stu-id="00ec8-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="00ec8-108">Dla porównania Boolean `result` jest wykluczenie logiczne (wyłączne rozłączenie logiczne) z dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="00ec8-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="00ec8-109">Dla Operacje bitowe `result` wartość liczbową reprezentujący z bitowego wykluczenia dwa wzorce bit liczbowych (wyłączne z bitowego rozłączenia).</span><span class="sxs-lookup"><span data-stu-id="00ec8-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="00ec8-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="00ec8-110">Required.</span></span> <span data-ttu-id="00ec8-111">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="00ec8-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="00ec8-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="00ec8-112">Required.</span></span> <span data-ttu-id="00ec8-113">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="00ec8-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00ec8-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00ec8-114">Remarks</span></span>  
 <span data-ttu-id="00ec8-115">Dla porównania Boolean `result` jest `True` tylko wtedy, gdy dokładnie jeden z `expression1` i `expression2` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="00ec8-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="00ec8-116">Oznacza to, że tylko wtedy, gdy `expression1` i `expression2` oceny do przeciwnego `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="00ec8-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="00ec8-117">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="00ec8-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="00ec8-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-118">If `expression1` is</span></span>|<span data-ttu-id="00ec8-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-119">And `expression2` is</span></span>|<span data-ttu-id="00ec8-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="00ec8-121">Logiczna porównania `Xor` operator zawsze ocenia oba wyrażenia, które mogą obejmować tworzenie wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="00ec8-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="00ec8-122">Nie ma odpowiednika short-circuiting do `Xor`, ponieważ wynik zależy od zawsze oba argumenty.</span><span class="sxs-lookup"><span data-stu-id="00ec8-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="00ec8-123">Dla *zwarcie* operatorów logicznych, zobacz [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) i [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="00ec8-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="00ec8-124">Dla Operacje bitowe `Xor` operator przeprowadza porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiedniej `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="00ec8-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="00ec8-125">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-125">If bit in `expression1` is</span></span>|<span data-ttu-id="00ec8-126">I bit w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-126">And bit in `expression2` is</span></span>|<span data-ttu-id="00ec8-127">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="00ec8-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="00ec8-128">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-128">1</span></span>|<span data-ttu-id="00ec8-129">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-129">1</span></span>|<span data-ttu-id="00ec8-130">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-130">0</span></span>|  
|<span data-ttu-id="00ec8-131">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-131">1</span></span>|<span data-ttu-id="00ec8-132">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-132">0</span></span>|<span data-ttu-id="00ec8-133">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-133">1</span></span>|  
|<span data-ttu-id="00ec8-134">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-134">0</span></span>|<span data-ttu-id="00ec8-135">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-135">1</span></span>|<span data-ttu-id="00ec8-136">1</span><span class="sxs-lookup"><span data-stu-id="00ec8-136">1</span></span>|  
|<span data-ttu-id="00ec8-137">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-137">0</span></span>|<span data-ttu-id="00ec8-138">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-138">0</span></span>|<span data-ttu-id="00ec8-139">0</span><span class="sxs-lookup"><span data-stu-id="00ec8-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="00ec8-140">Ponieważ operatory logiczne i bitowe mają niższy priorytet niż inne arytmetyczne operatorów, wszystkie operacje bitowe powinny być ujęte w nawiasy, aby zapewnić dokładne wykonywania.</span><span class="sxs-lookup"><span data-stu-id="00ec8-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="00ec8-141">Na przykład 5 `Xor` 3 to 6.</span><span class="sxs-lookup"><span data-stu-id="00ec8-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="00ec8-142">Aby sprawdzić, dlaczego jest tak, Konwertuj na ich binarne oświadczenia 101 i 011 5 i 3.</span><span class="sxs-lookup"><span data-stu-id="00ec8-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="00ec8-143">Następnie użyj poprzedniej tabeli, aby określić, że 101 Xor 011 jest 110, która jest binarna reprezentacja liczbę dziesiętną 6.</span><span class="sxs-lookup"><span data-stu-id="00ec8-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="00ec8-144">Typy danych</span><span class="sxs-lookup"><span data-stu-id="00ec8-144">Data Types</span></span>  
 <span data-ttu-id="00ec8-145">Jeśli operandy składają się z jednego `Boolean` wyrażenie i jednego wyrażenia liczbowego, Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje operacji.</span><span class="sxs-lookup"><span data-stu-id="00ec8-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="00ec8-146">Aby uzyskać `Boolean` jest typ danych w wyniku porównania, `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="00ec8-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="00ec8-147">Porównanie bitowe, typu danych jest typ liczbowy odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="00ec8-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="00ec8-148">Znajdują się w tabeli "Relacyjnych i operator porównania" [typy danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="00ec8-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="00ec8-149">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="00ec8-149">Overloading</span></span>  
 <span data-ttu-id="00ec8-150">`Xor` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="00ec8-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="00ec8-151">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="00ec8-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="00ec8-152">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="00ec8-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ec8-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="00ec8-153">Example</span></span>  
 <span data-ttu-id="00ec8-154">W poniższym przykładzie użyto `Xor` operatora, aby wykonać wykluczenie logiczne (rozłączenie logiczne wyłączne) na dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="00ec8-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="00ec8-155">Wynik jest `Boolean` wartość wskazującą, czy jest dokładnie jedno z wyrażeń `True`.</span><span class="sxs-lookup"><span data-stu-id="00ec8-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 <span data-ttu-id="00ec8-156">Poprzedni przykład tworzy wyniki `False`, `True`, i `False`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="00ec8-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00ec8-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="00ec8-157">Example</span></span>  
 <span data-ttu-id="00ec8-158">W poniższym przykładzie użyto `Xor` operatora, aby wykonać wykluczenie logiczne (rozłączenie logiczne wyłączne) na poszczególnych bitów dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="00ec8-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="00ec8-159">Bit we wzorcu wynik jest ustawiona, jeśli dokładnie jeden z odpowiednich bitów w operandy jest ustawiona na 1.</span><span class="sxs-lookup"><span data-stu-id="00ec8-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 <span data-ttu-id="00ec8-160">Poprzedni przykład tworzy odpowiednio wyniki z 2, 12 i 14.</span><span class="sxs-lookup"><span data-stu-id="00ec8-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ec8-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00ec8-161">See Also</span></span>  
 [<span data-ttu-id="00ec8-162">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00ec8-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="00ec8-163">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00ec8-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="00ec8-164">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="00ec8-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="00ec8-165">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00ec8-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
