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
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835241"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="cfcbb-102">OrElse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfcbb-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="cfcbb-103">Wykonuje krótkie rozłączne logiczne rozłączenie dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfcbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cfcbb-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="cfcbb-105">Części</span><span class="sxs-lookup"><span data-stu-id="cfcbb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cfcbb-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-106">Required.</span></span> <span data-ttu-id="cfcbb-107">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="cfcbb-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-108">Required.</span></span> <span data-ttu-id="cfcbb-109">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="cfcbb-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-110">Required.</span></span> <span data-ttu-id="cfcbb-111">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfcbb-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cfcbb-112">Remarks</span></span>  
 <span data-ttu-id="cfcbb-113">Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="cfcbb-114">Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="cfcbb-115">Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="cfcbb-116">Jeśli lub oba wyrażenia obliczają `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="cfcbb-117">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="cfcbb-118">Jeśli `expression1` to</span><span class="sxs-lookup"><span data-stu-id="cfcbb-118">If `expression1` is</span></span>|<span data-ttu-id="cfcbb-119">I `expression2` to</span><span class="sxs-lookup"><span data-stu-id="cfcbb-119">And `expression2` is</span></span>|<span data-ttu-id="cfcbb-120">Wartość `result` to</span><span class="sxs-lookup"><span data-stu-id="cfcbb-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="cfcbb-121">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="cfcbb-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="cfcbb-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="cfcbb-122">Data Types</span></span>  
 <span data-ttu-id="cfcbb-123">Operator `OrElse` jest zdefiniowany tylko dla [typu danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="cfcbb-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="cfcbb-124">Visual Basic konwertuje każdy operand w miarę potrzeb, aby `Boolean` przed szacowaniem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="cfcbb-125">Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` będzie `0` i `True` staje się `-1`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="cfcbb-126">Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="cfcbb-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="cfcbb-127">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="cfcbb-127">Overloading</span></span>  
 <span data-ttu-id="cfcbb-128">Operator [or](../../../visual-basic/language-reference/operators/or-operator.md) i [operator IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cfcbb-129">Przeciążanie operatorów `Or` i `IsTrue` wpływa na zachowanie operatora `OrElse`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="cfcbb-130">Jeśli kod używa `OrElse` na klasie lub strukturze, która przeciąża `Or` i `IsTrue`, należy zrozumieć swoje ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="cfcbb-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cfcbb-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfcbb-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfcbb-132">Example</span></span>  
 <span data-ttu-id="cfcbb-133">Poniższy przykład używa operatora `OrElse` w celu logicznego rozłączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="cfcbb-134">Wynikiem jest wartość `Boolean`, która reprezentuje, czy jedno z dwóch wyrażeń ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="cfcbb-135">Jeśli pierwsze wyrażenie jest `True`, sekunda nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="cfcbb-136">Powyższy przykład daje wyniki `True`, `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="cfcbb-137">W obliczeniach `firstCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwszy jest już `True`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="cfcbb-138">Drugie wyrażenie jest jednak oceniane przy obliczaniu wartości `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfcbb-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="cfcbb-139">Example</span></span>  
 <span data-ttu-id="cfcbb-140">W poniższym przykładzie pokazano instrukcję `If`... `Then`, która zawiera dwa wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="cfcbb-141">Jeśli pierwsze wywołanie zwraca `True`, Druga procedura nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="cfcbb-142">Może to spowodować nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane, gdy ta sekcja kodu zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="cfcbb-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="cfcbb-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cfcbb-143">See also</span></span>

- [<span data-ttu-id="cfcbb-144">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfcbb-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="cfcbb-145">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfcbb-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="cfcbb-146">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="cfcbb-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="cfcbb-147">Or, operator</span><span class="sxs-lookup"><span data-stu-id="cfcbb-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="cfcbb-148">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="cfcbb-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="cfcbb-149">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfcbb-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
