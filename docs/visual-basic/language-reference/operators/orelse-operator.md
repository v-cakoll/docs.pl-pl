---
title: OrElse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860142"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="dbb3b-102">OrElse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbb3b-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="dbb3b-103">Wykonuje łączną sumę logiczną na dwóch wyrażeniach zwarcie.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbb3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dbb3b-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="dbb3b-105">Części</span><span class="sxs-lookup"><span data-stu-id="dbb3b-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="dbb3b-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-106">Required.</span></span> <span data-ttu-id="dbb3b-107">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="dbb3b-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-108">Required.</span></span> <span data-ttu-id="dbb3b-109">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="dbb3b-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-110">Required.</span></span> <span data-ttu-id="dbb3b-111">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbb3b-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbb3b-112">Remarks</span></span>  
 <span data-ttu-id="dbb3b-113">Operacja logiczna jest nazywany *zwarcie* Jeśli skompilowany kod może obejść przedziały oceny jedno wyrażenie w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="dbb3b-114">Jeśli wynik pierwsze wyrażenie obliczane określi ostateczny wynik operacji, nie ma potrzeby do oceny, drugie wyrażenie, ponieważ nie można zmienić, wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="dbb3b-115">Zwarcie może poprawić wydajność, jeśli pominięto wyrażenie jest złożone, czy obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="dbb3b-116">Jeśli do jednego lub obu tych wyrażeń `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="dbb3b-117">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="dbb3b-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="dbb3b-118">If `expression1` is</span></span>|<span data-ttu-id="dbb3b-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="dbb3b-119">And `expression2` is</span></span>|<span data-ttu-id="dbb3b-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="dbb3b-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="dbb3b-121">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="dbb3b-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="dbb3b-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="dbb3b-122">Data Types</span></span>  
 <span data-ttu-id="dbb3b-123">`OrElse` Operator jest zdefiniowany tylko w przypadku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="dbb3b-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="dbb3b-124">Visual Basic konwertuje każdy argument konieczny do `Boolean` przed obliczając wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="dbb3b-125">Jeśli wynik jest przypisany do typu numerycznego, Visual Basic konwertuje go z `Boolean` do tego typu tak, aby `False` staje się `0` i `True` staje się `-1`.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="dbb3b-126">Aby uzyskać więcej informacji, zobacz [logiczna konwersje typów](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="dbb3b-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="dbb3b-127">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="dbb3b-127">Overloading</span></span>  
 <span data-ttu-id="dbb3b-128">[Operatora Or](../../../visual-basic/language-reference/operators/or-operator.md) i [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dbb3b-129">Przeciążanie `Or` i `IsTrue` operatory wpływa na zachowanie `OrElse` operatora.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="dbb3b-130">Jeśli kod używa `OrElse` dla klasy lub struktury, która przeciążenia `Or` i `IsTrue`, należy zrozumieć ich zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="dbb3b-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="dbb3b-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbb3b-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbb3b-132">Example</span></span>  
 <span data-ttu-id="dbb3b-133">W poniższym przykładzie użyto `OrElse` operator przeprowadzić logicznego rozłączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="dbb3b-134">Wynik jest `Boolean` wartość wskazującą, czy jest spełniony jeden z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="dbb3b-135">Jeśli pierwsze wyrażenie jest `True`, drugi nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="dbb3b-136">Poprzedni przykład generuje wyniki `True`, `True`, i `False` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="dbb3b-137">Podczas obliczania `firstCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `True`.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="dbb3b-138">Jednak drugie wyrażenie jest obliczane w obliczeniach kluczowych `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbb3b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbb3b-139">Example</span></span>  
 <span data-ttu-id="dbb3b-140">W poniższym przykładzie przedstawiono `If`... `Then` instrukcji zawierającej dwóch wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="dbb3b-141">Jeśli pierwsza zwraca wywołanie `True`, druga procedura nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="dbb3b-142">Może to dawać nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane po uruchomieniu tej sekcji kodu.</span><span class="sxs-lookup"><span data-stu-id="dbb3b-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="dbb3b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbb3b-143">See also</span></span>

- [<span data-ttu-id="dbb3b-144">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbb3b-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="dbb3b-145">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbb3b-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="dbb3b-146">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="dbb3b-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="dbb3b-147">Or, operator</span><span class="sxs-lookup"><span data-stu-id="dbb3b-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="dbb3b-148">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="dbb3b-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="dbb3b-149">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dbb3b-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
