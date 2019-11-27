---
title: OrElse, operator
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
ms.openlocfilehash: 361de44711c3b41411f2fa1dd81a3dd8db6b01e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348232"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="b6a25-102">OrElse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6a25-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="b6a25-103">Wykonuje krótkie rozłączne logiczne rozłączenie dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b6a25-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a25-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b6a25-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b6a25-105">Części</span><span class="sxs-lookup"><span data-stu-id="b6a25-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b6a25-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b6a25-106">Required.</span></span> <span data-ttu-id="b6a25-107">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b6a25-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b6a25-108">Required.</span></span> <span data-ttu-id="b6a25-109">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b6a25-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b6a25-110">Required.</span></span> <span data-ttu-id="b6a25-111">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6a25-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b6a25-112">Remarks</span></span>  
 <span data-ttu-id="b6a25-113">Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b6a25-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="b6a25-114">Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="b6a25-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="b6a25-115">Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="b6a25-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="b6a25-116">Jeśli jedno lub oba wyrażenia mają wartość `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="b6a25-117">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b6a25-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="b6a25-118">If `expression1` is</span></span>|<span data-ttu-id="b6a25-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="b6a25-119">And `expression2` is</span></span>|<span data-ttu-id="b6a25-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="b6a25-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="b6a25-121">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="b6a25-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="b6a25-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="b6a25-122">Data Types</span></span>  
 <span data-ttu-id="b6a25-123">Operator `OrElse` jest zdefiniowany tylko dla [typu danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="b6a25-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="b6a25-124">Visual Basic konwertuje każdy operand jako niezbędny do `Boolean` przed obliczeniem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b6a25-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="b6a25-125">Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` staje się `0`, a `True` staje się `-1`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="b6a25-126">Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="b6a25-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="b6a25-127">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="b6a25-127">Overloading</span></span>  
 <span data-ttu-id="b6a25-128">Operator [or](../../../visual-basic/language-reference/operators/or-operator.md) i [operator IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b6a25-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b6a25-129">Przeciążanie operatorów `Or` i `IsTrue` wpływa na zachowanie operatora `OrElse`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="b6a25-130">Jeśli kod używa `OrElse` na klasie lub strukturze, która przeciąża `Or` i `IsTrue`, należy zrozumieć swoje niezdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="b6a25-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="b6a25-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b6a25-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a25-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6a25-132">Example</span></span>  
 <span data-ttu-id="b6a25-133">Poniższy przykład używa operatora `OrElse` do wykonywania logicznego rozłączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b6a25-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="b6a25-134">Wynikiem jest wartość `Boolean`, która reprezentuje, czy jeden z dwóch wyrażeń ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="b6a25-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="b6a25-135">Jeśli pierwsze wyrażenie jest `True`, sekunda nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="b6a25-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="b6a25-136">Powyższy przykład daje wyniki odpowiednio `True`, `True`i `False`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="b6a25-137">W obliczeniach `firstCheck`drugie wyrażenie nie jest oceniane, ponieważ pierwszy jest już `True`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="b6a25-138">Drugie wyrażenie jest jednak oceniane podczas obliczania `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="b6a25-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6a25-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="b6a25-139">Example</span></span>  
 <span data-ttu-id="b6a25-140">Poniższy przykład przedstawia instrukcje `If`...`Then` zawierające dwa wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="b6a25-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="b6a25-141">Jeśli pierwsze wywołanie zwraca `True`, Druga procedura nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b6a25-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="b6a25-142">Może to spowodować nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane, gdy ta sekcja kodu zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="b6a25-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="b6a25-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b6a25-143">See also</span></span>

- [<span data-ttu-id="b6a25-144">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6a25-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="b6a25-145">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6a25-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b6a25-146">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="b6a25-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b6a25-147">Or, operator</span><span class="sxs-lookup"><span data-stu-id="b6a25-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="b6a25-148">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="b6a25-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="b6a25-149">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b6a25-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
