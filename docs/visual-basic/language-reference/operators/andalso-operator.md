---
title: AndAlso, operator
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
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371937"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="2f7e8-102">AndAlso — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f7e8-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="2f7e8-103">Wykonuje krótkie koniunkcje logiczne dla dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f7e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f7e8-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="2f7e8-105">Części</span><span class="sxs-lookup"><span data-stu-id="2f7e8-105">Parts</span></span>  
  
|<span data-ttu-id="2f7e8-106">Termin</span><span class="sxs-lookup"><span data-stu-id="2f7e8-106">Term</span></span>|<span data-ttu-id="2f7e8-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="2f7e8-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="2f7e8-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-108">Required.</span></span> <span data-ttu-id="2f7e8-109">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-109">Any `Boolean` expression.</span></span> <span data-ttu-id="2f7e8-110">Wynik jest `Boolean` wynikiem porównania dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="2f7e8-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-111">Required.</span></span> <span data-ttu-id="2f7e8-112">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="2f7e8-113">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-113">Required.</span></span> <span data-ttu-id="2f7e8-114">Dowolne `Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f7e8-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f7e8-115">Remarks</span></span>  
 <span data-ttu-id="2f7e8-116">Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="2f7e8-117">Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="2f7e8-118">Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="2f7e8-119">Jeśli oba wyrażenia są szacowane do `True` , `result` is `True` .</span><span class="sxs-lookup"><span data-stu-id="2f7e8-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="2f7e8-120">W poniższej tabeli przedstawiono sposób `result` określania.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="2f7e8-121">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="2f7e8-121">If `expression1` is</span></span>|<span data-ttu-id="2f7e8-122">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="2f7e8-122">And `expression2` is</span></span>|<span data-ttu-id="2f7e8-123">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="2f7e8-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="2f7e8-124">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="2f7e8-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="2f7e8-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="2f7e8-125">Data Types</span></span>  
 <span data-ttu-id="2f7e8-126">`AndAlso`Operator jest zdefiniowany tylko dla [typu danych Boolean](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="2f7e8-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="2f7e8-127">Visual Basic konwertuje każdy operand w miarę potrzeb do `Boolean` przed obliczeniem wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="2f7e8-128">Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` staje się `0` i `True` staje się `-1` .</span><span class="sxs-lookup"><span data-stu-id="2f7e8-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="2f7e8-129">Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="2f7e8-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="2f7e8-130">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="2f7e8-130">Overloading</span></span>  
 <span data-ttu-id="2f7e8-131">Operator [and](and-operator.md) i [operator IsFalse](isfalse-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2f7e8-132">Przeciążanie `And` operatorów i `IsFalse` wpływa na zachowanie `AndAlso` operatora.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="2f7e8-133">Jeśli Twój kod używa `AndAlso` klasy lub struktury, która przeciąża `And` i `IsFalse` , pamiętaj o zrozumieniu ich redefiniowanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="2f7e8-134">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2f7e8-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f7e8-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f7e8-135">Example</span></span>  
 <span data-ttu-id="2f7e8-136">Poniższy przykład używa `AndAlso` operatora do wykonywania logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="2f7e8-137">Wynik jest `Boolean` wartością, która reprezentuje, czy całe przyłączone wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="2f7e8-138">Jeśli pierwsze wyrażenie ma wartość `False` , sekunda nie jest szacowana.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="2f7e8-139">Powyższy przykład daje wyniki `True` , `False` i, `False` odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="2f7e8-140">W obliczeniach `secondCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwsze jest już `False` .</span><span class="sxs-lookup"><span data-stu-id="2f7e8-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="2f7e8-141">Drugie wyrażenie jest jednak oceniane w obliczeniach `thirdCheck` .</span><span class="sxs-lookup"><span data-stu-id="2f7e8-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f7e8-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="2f7e8-142">Example</span></span>  
 <span data-ttu-id="2f7e8-143">Poniższy przykład pokazuje `Function` procedurę, która wyszukuje daną wartość wśród elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="2f7e8-144">Jeśli tablica jest pusta lub długość tablicy została przekroczona, `While` instrukcja nie przetestuje elementu Array względem wartości wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2f7e8-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="2f7e8-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f7e8-145">See also</span></span>

- [<span data-ttu-id="2f7e8-146">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f7e8-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="2f7e8-147">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f7e8-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="2f7e8-148">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="2f7e8-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="2f7e8-149">And, operator</span><span class="sxs-lookup"><span data-stu-id="2f7e8-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="2f7e8-150">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="2f7e8-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="2f7e8-151">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2f7e8-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
