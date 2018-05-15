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
ms.openlocfilehash: 549d14cc35d285ac2e4a02a37dd201cc669c5627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="5e512-102">AndAlso — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e512-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="5e512-103">Wykonuje skrótowe połączenie logiczne dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="5e512-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e512-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e512-104">Syntax</span></span>  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5e512-105">Części</span><span class="sxs-lookup"><span data-stu-id="5e512-105">Parts</span></span>  
  
|<span data-ttu-id="5e512-106">Termin</span><span class="sxs-lookup"><span data-stu-id="5e512-106">Term</span></span>|<span data-ttu-id="5e512-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="5e512-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="5e512-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e512-108">Required.</span></span> <span data-ttu-id="5e512-109">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5e512-109">Any `Boolean` expression.</span></span> <span data-ttu-id="5e512-110">W rezultacie `Boolean` wynik porównania dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="5e512-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="5e512-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e512-111">Required.</span></span> <span data-ttu-id="5e512-112">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5e512-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="5e512-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e512-113">Required.</span></span> <span data-ttu-id="5e512-114">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5e512-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e512-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e512-115">Remarks</span></span>  
 <span data-ttu-id="5e512-116">Operacja logiczna jest określany jako *zwarcie* Jeśli skompilowanego kodu można pominąć obliczania jednego wyrażenia w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5e512-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="5e512-117">Jeśli wynik pierwsze wyrażenie obliczane określa końcowego wyniku operacji, jest niepotrzebna można oszacować wyrażenia drugiego, ponieważ nie można zmienić wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="5e512-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="5e512-118">Zwarcie może zwiększyć wydajność, jeśli pominięto wyrażenie jest złożony, czy obejmuje on wywołań procedur.</span><span class="sxs-lookup"><span data-stu-id="5e512-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="5e512-119">Jeśli oba wyrażenia mają `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5e512-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="5e512-120">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="5e512-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="5e512-121">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="5e512-121">If `expression1` is</span></span>|<span data-ttu-id="5e512-122">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="5e512-122">And `expression2` is</span></span>|<span data-ttu-id="5e512-123">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="5e512-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="5e512-124">(nie jest oceniany)</span><span class="sxs-lookup"><span data-stu-id="5e512-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="5e512-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="5e512-125">Data Types</span></span>  
 <span data-ttu-id="5e512-126">`AndAlso` Operator jest zdefiniowana tylko dla [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="5e512-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="5e512-127">Visual Basic konwertuje każdy argument operacji niezbędny do `Boolean` i wykonuje operację wyłącznie w `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5e512-127">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="5e512-128">Przypisz wynik do typu liczbowego, Visual Basic przekonwertuje go z `Boolean` dla tego typu.</span><span class="sxs-lookup"><span data-stu-id="5e512-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="5e512-129">Można to osiągnąć nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="5e512-129">This could produce unexpected behavior.</span></span> <span data-ttu-id="5e512-130">Na przykład `5 AndAlso 12` powoduje `–1` po konwersji na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5e512-130">For example, `5 AndAlso 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5e512-131">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="5e512-131">Overloading</span></span>  
 <span data-ttu-id="5e512-132">[i operatora](../../../visual-basic/language-reference/operators/and-operator.md) i [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury można zmienić ich zachowania, gdy argument operacji ma typ, który klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5e512-132">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5e512-133">Przeciążanie `And` i `IsFalse` operatory wpływa na działanie `AndAlso` operatora.</span><span class="sxs-lookup"><span data-stu-id="5e512-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="5e512-134">Jeśli używa Twój kod `AndAlso` na klasę lub strukturę, która overloads `And` i `IsFalse`, trzeba koniecznie zapoznać się ich zachowanie ponownie zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="5e512-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="5e512-135">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5e512-135">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e512-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e512-136">Example</span></span>  
 <span data-ttu-id="5e512-137">W poniższym przykładzie użyto `AndAlso` operatora, aby wykonać koniunkcję logiczną na dwóch wyrażeniach.</span><span class="sxs-lookup"><span data-stu-id="5e512-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="5e512-138">Wynik jest `Boolean` wartość wskazującą, czy cały conjoined wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="5e512-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="5e512-139">Jeśli pierwsze wyrażenie jest `False`, drugie nie jest obliczane.</span><span class="sxs-lookup"><span data-stu-id="5e512-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_1.vb)]  
  
 <span data-ttu-id="5e512-140">Powyższy przykład produkuje wyniki `True`, `False`, i `False`odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="5e512-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="5e512-141">Podczas obliczania `secondCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `False`.</span><span class="sxs-lookup"><span data-stu-id="5e512-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="5e512-142">Jednak drugie wyrażenie jest obliczane w obliczeniach `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="5e512-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e512-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e512-143">Example</span></span>  
 <span data-ttu-id="5e512-144">W poniższym przykładzie przedstawiono `Function` procedury, która przeszukuje dla danej wartości między elementami tablicy.</span><span class="sxs-lookup"><span data-stu-id="5e512-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="5e512-145">Jeśli tablica jest pusta lub przekroczeniu długości tablicy `While` instrukcji nie sprawdza elementu tablicy względem wartości wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="5e512-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/andalso-operator_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5e512-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e512-146">See Also</span></span>  
 [<span data-ttu-id="5e512-147">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e512-147">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="5e512-148">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e512-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="5e512-149">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5e512-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="5e512-150">And, operator</span><span class="sxs-lookup"><span data-stu-id="5e512-150">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)  
 [<span data-ttu-id="5e512-151">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="5e512-151">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="5e512-152">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e512-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
