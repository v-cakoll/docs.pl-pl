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
ms.openlocfilehash: c2af3864ef19dbf835397968af0913cd62994305
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54494434"
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="cde72-102">Or — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cde72-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="cde72-103">Dokonuje logicznego rozłączenia dwóch `Boolean` wyrażeń lub bitowego rozłączenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="cde72-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cde72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cde72-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="cde72-105">Części</span><span class="sxs-lookup"><span data-stu-id="cde72-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cde72-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cde72-106">Required.</span></span> <span data-ttu-id="cde72-107">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="cde72-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="cde72-108">Aby uzyskać `Boolean` porównania, `result` jest łączną sumę logiczną na dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="cde72-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="cde72-109">W przypadku operacji bitowej `result` jest wartość liczbowa reprezentująca włącznie bitowego rozłączenia dwóch wzorców bitowych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="cde72-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="cde72-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cde72-110">Required.</span></span> <span data-ttu-id="cde72-111">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="cde72-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="cde72-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="cde72-112">Required.</span></span> <span data-ttu-id="cde72-113">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="cde72-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cde72-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cde72-114">Remarks</span></span>  
 <span data-ttu-id="cde72-115">Dla `Boolean` porównania, `result` jest `False` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` zwrócić `False`.</span><span class="sxs-lookup"><span data-stu-id="cde72-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="cde72-116">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="cde72-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="cde72-117">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-117">If `expression1` is</span></span>|<span data-ttu-id="cde72-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-118">And `expression2` is</span></span>|<span data-ttu-id="cde72-119">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="cde72-120">W `Boolean` porównania, `Or` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="cde72-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="cde72-121">[OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `True`, następnie `expression2` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="cde72-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="cde72-122">W przypadku operacji bitowej `Or` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="cde72-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="cde72-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-123">If bit in `expression1` is</span></span>|<span data-ttu-id="cde72-124">I bitu w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-124">And bit in `expression2` is</span></span>|<span data-ttu-id="cde72-125">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="cde72-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="cde72-126">1</span><span class="sxs-lookup"><span data-stu-id="cde72-126">1</span></span>|<span data-ttu-id="cde72-127">1</span><span class="sxs-lookup"><span data-stu-id="cde72-127">1</span></span>|<span data-ttu-id="cde72-128">1</span><span class="sxs-lookup"><span data-stu-id="cde72-128">1</span></span>|  
|<span data-ttu-id="cde72-129">1</span><span class="sxs-lookup"><span data-stu-id="cde72-129">1</span></span>|<span data-ttu-id="cde72-130">0</span><span class="sxs-lookup"><span data-stu-id="cde72-130">0</span></span>|<span data-ttu-id="cde72-131">1</span><span class="sxs-lookup"><span data-stu-id="cde72-131">1</span></span>|  
|<span data-ttu-id="cde72-132">0</span><span class="sxs-lookup"><span data-stu-id="cde72-132">0</span></span>|<span data-ttu-id="cde72-133">1</span><span class="sxs-lookup"><span data-stu-id="cde72-133">1</span></span>|<span data-ttu-id="cde72-134">1</span><span class="sxs-lookup"><span data-stu-id="cde72-134">1</span></span>|  
|<span data-ttu-id="cde72-135">0</span><span class="sxs-lookup"><span data-stu-id="cde72-135">0</span></span>|<span data-ttu-id="cde72-136">0</span><span class="sxs-lookup"><span data-stu-id="cde72-136">0</span></span>|<span data-ttu-id="cde72-137">0</span><span class="sxs-lookup"><span data-stu-id="cde72-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="cde72-138">Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="cde72-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="cde72-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="cde72-139">Data Types</span></span>  
 <span data-ttu-id="cde72-140">Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.</span><span class="sxs-lookup"><span data-stu-id="cde72-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="cde72-141">Aby uzyskać `Boolean` jest typ danych wyniku porównania, `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cde72-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="cde72-142">Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="cde72-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="cde72-143">Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="cde72-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="cde72-144">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="cde72-144">Overloading</span></span>  
 <span data-ttu-id="cde72-145">`Or` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cde72-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cde72-146">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="cde72-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cde72-147">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cde72-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde72-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="cde72-148">Example</span></span>  
 <span data-ttu-id="cde72-149">W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cde72-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="cde72-150">Wynik jest `Boolean` wartość wskazującą, czy jest jeden z dwóch wyrażeń `True`.</span><span class="sxs-lookup"><span data-stu-id="cde72-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 <span data-ttu-id="cde72-151">Poprzedni przykład generuje wyniki `True`, `True`, i `False`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="cde72-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cde72-152">Przykład</span><span class="sxs-lookup"><span data-stu-id="cde72-152">Example</span></span>  
 <span data-ttu-id="cde72-153">W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na poszczególnych bity dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="cde72-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="cde72-154">Bit we wzorcu wynik jest ustawiona, jeśli albo odpowiednich bitów w operandów jest ustawiona na 1.</span><span class="sxs-lookup"><span data-stu-id="cde72-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 <span data-ttu-id="cde72-155">Poprzedni przykład generuje wyniki, 10, 14 oraz 14, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="cde72-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde72-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cde72-156">See also</span></span>
- [<span data-ttu-id="cde72-157">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cde72-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="cde72-158">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cde72-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cde72-159">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="cde72-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cde72-160">OrElse, operator</span><span class="sxs-lookup"><span data-stu-id="cde72-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [<span data-ttu-id="cde72-161">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cde72-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
