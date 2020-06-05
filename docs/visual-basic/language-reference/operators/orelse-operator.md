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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401410"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="1dfe3-102">OrElse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dfe3-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="1dfe3-103">Wykonuje krótkie rozłączne logiczne rozłączenie dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dfe3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1dfe3-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1dfe3-105">Części</span><span class="sxs-lookup"><span data-stu-id="1dfe3-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1dfe3-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-106">Required.</span></span> <span data-ttu-id="1dfe3-107">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="1dfe3-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-108">Required.</span></span> <span data-ttu-id="1dfe3-109">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1dfe3-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-110">Required.</span></span> <span data-ttu-id="1dfe3-111">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dfe3-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1dfe3-112">Remarks</span></span>  
 <span data-ttu-id="1dfe3-113">Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="1dfe3-114">Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="1dfe3-115">Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="1dfe3-116">Jeśli w obu wyrażeniach lub obu tych wyrażeń `True` jest wynikiem, `result` jest `True` .</span><span class="sxs-lookup"><span data-stu-id="1dfe3-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="1dfe3-117">W poniższej tabeli przedstawiono sposób `result` określania.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1dfe3-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="1dfe3-118">If `expression1` is</span></span>|<span data-ttu-id="1dfe3-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="1dfe3-119">And `expression2` is</span></span>|<span data-ttu-id="1dfe3-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="1dfe3-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="1dfe3-121">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="1dfe3-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="1dfe3-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1dfe3-122">Data Types</span></span>  
 <span data-ttu-id="1dfe3-123">`OrElse`Operator jest zdefiniowany tylko dla [typu danych Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="1dfe3-123">The `OrElse` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="1dfe3-124">Visual Basic konwertuje każdy operand w miarę potrzeb do `Boolean` przed obliczeniem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="1dfe3-125">Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` staje się `0` i `True` staje się `-1` .</span><span class="sxs-lookup"><span data-stu-id="1dfe3-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="1dfe3-126">Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="1dfe3-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="1dfe3-127">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="1dfe3-127">Overloading</span></span>  
 <span data-ttu-id="1dfe3-128">Operator [or](or-operator.md) i [operator IsTrue](istrue-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-128">The [Or Operator](or-operator.md) and the [IsTrue Operator](istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1dfe3-129">Przeciążanie `Or` operatorów i `IsTrue` wpływa na zachowanie `OrElse` operatora.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="1dfe3-130">Jeśli Twój kod używa `OrElse` klasy lub struktury, która przeciąża `Or` i `IsTrue` , pamiętaj o zrozumieniu ich redefiniowanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="1dfe3-131">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1dfe3-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfe3-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dfe3-132">Example</span></span>  
 <span data-ttu-id="1dfe3-133">Poniższy przykład używa `OrElse` operatora do wykonywania logicznego rozłączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="1dfe3-134">Wynik jest `Boolean` wartością, która reprezentuje, czy jedno z dwóch wyrażeń ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="1dfe3-135">Jeśli pierwsze wyrażenie ma wartość `True` , sekunda nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="1dfe3-136">Powyższy przykład daje wyniki `True` , `True` i `False` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="1dfe3-137">W obliczeniach `firstCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwsze jest już `True` .</span><span class="sxs-lookup"><span data-stu-id="1dfe3-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="1dfe3-138">Drugie wyrażenie jest jednak oceniane w obliczeniach `secondCheck` .</span><span class="sxs-lookup"><span data-stu-id="1dfe3-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1dfe3-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="1dfe3-139">Example</span></span>  
 <span data-ttu-id="1dfe3-140">W poniższym przykładzie pokazano `If` instrukcję... `Then` zawierające dwa wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="1dfe3-141">Jeśli pierwsze wywołanie zwraca `True` , Druga procedura nie jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="1dfe3-142">Może to spowodować nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane, gdy ta sekcja kodu zostanie uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="1dfe3-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="1dfe3-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1dfe3-143">See also</span></span>

- [<span data-ttu-id="1dfe3-144">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dfe3-144">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="1dfe3-145">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1dfe3-145">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="1dfe3-146">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1dfe3-146">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="1dfe3-147">Or, operator</span><span class="sxs-lookup"><span data-stu-id="1dfe3-147">Or Operator</span></span>](or-operator.md)
- [<span data-ttu-id="1dfe3-148">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="1dfe3-148">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="1dfe3-149">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1dfe3-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
