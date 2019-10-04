---
title: AndAlso — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835228"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="42e1d-102">AndAlso — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42e1d-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="42e1d-103">Wykonuje krótkie koniunkcje logiczne dla dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="42e1d-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42e1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42e1d-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="42e1d-105">Części</span><span class="sxs-lookup"><span data-stu-id="42e1d-105">Parts</span></span>  
  
|<span data-ttu-id="42e1d-106">Termin</span><span class="sxs-lookup"><span data-stu-id="42e1d-106">Term</span></span>|<span data-ttu-id="42e1d-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="42e1d-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="42e1d-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="42e1d-108">Required.</span></span> <span data-ttu-id="42e1d-109">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-109">Any `Boolean` expression.</span></span> <span data-ttu-id="42e1d-110">Wynikiem porównania dwóch wyrażeń jest wynik `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="42e1d-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="42e1d-111">Required.</span></span> <span data-ttu-id="42e1d-112">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="42e1d-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="42e1d-113">Required.</span></span> <span data-ttu-id="42e1d-114">Dowolne wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42e1d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42e1d-115">Remarks</span></span>  
 <span data-ttu-id="42e1d-116">Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="42e1d-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="42e1d-117">Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="42e1d-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="42e1d-118">Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="42e1d-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="42e1d-119">Jeśli oba wyrażenia są szacowane do `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="42e1d-120">W poniższej tabeli przedstawiono sposób określania `result`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="42e1d-121">Jeśli `expression1` to</span><span class="sxs-lookup"><span data-stu-id="42e1d-121">If `expression1` is</span></span>|<span data-ttu-id="42e1d-122">I `expression2` to</span><span class="sxs-lookup"><span data-stu-id="42e1d-122">And `expression2` is</span></span>|<span data-ttu-id="42e1d-123">Wartość `result` to</span><span class="sxs-lookup"><span data-stu-id="42e1d-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="42e1d-124">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="42e1d-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="42e1d-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="42e1d-125">Data Types</span></span>  
 <span data-ttu-id="42e1d-126">Operator `AndAlso` jest zdefiniowany tylko dla [typu danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="42e1d-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="42e1d-127">Visual Basic konwertuje każdy operand w miarę potrzeb, aby `Boolean` przed szacowaniem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="42e1d-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="42e1d-128">Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` będzie `0` i `True` staje się `-1`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="42e1d-129">Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="42e1d-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="42e1d-130">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="42e1d-130">Overloading</span></span>  
 <span data-ttu-id="42e1d-131">Operator [and](../../../visual-basic/language-reference/operators/and-operator.md) i [operator IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="42e1d-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="42e1d-132">Przeciążanie operatorów `And` i `IsFalse` wpływa na zachowanie operatora `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="42e1d-133">Jeśli kod używa `AndAlso` na klasie lub strukturze, która przeciąża `And` i `IsFalse`, należy zrozumieć swoje ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="42e1d-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="42e1d-134">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="42e1d-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42e1d-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="42e1d-135">Example</span></span>  
 <span data-ttu-id="42e1d-136">Poniższy przykład używa operatora `AndAlso` do wykonywania logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="42e1d-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="42e1d-137">Wynikiem jest wartość `Boolean`, która reprezentuje, czy całe przyłączone wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="42e1d-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="42e1d-138">Jeśli pierwsze wyrażenie jest `False`, sekunda nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="42e1d-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="42e1d-139">W powyższym przykładzie wyniki są odpowiednio `True`, `False` i `False`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="42e1d-140">W obliczeniach `secondCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwszy jest już `False`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="42e1d-141">Drugie wyrażenie jest jednak oceniane przy obliczaniu wartości `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="42e1d-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42e1d-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="42e1d-142">Example</span></span>  
 <span data-ttu-id="42e1d-143">Poniższy przykład pokazuje procedurę `Function`, która wyszukuje daną wartość wśród elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="42e1d-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="42e1d-144">Jeśli tablica jest pusta lub długość tablicy została przekroczona, instrukcja `While` nie przetestuje elementu Array względem wartości wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="42e1d-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="42e1d-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42e1d-145">See also</span></span>

- [<span data-ttu-id="42e1d-146">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42e1d-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="42e1d-147">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e1d-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="42e1d-148">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="42e1d-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="42e1d-149">And, operator</span><span class="sxs-lookup"><span data-stu-id="42e1d-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="42e1d-150">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="42e1d-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="42e1d-151">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42e1d-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
