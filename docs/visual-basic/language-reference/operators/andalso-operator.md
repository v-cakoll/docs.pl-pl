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
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608323"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="9c5f5-102">AndAlso — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c5f5-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="9c5f5-103">Wykonuje zwarcie logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c5f5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9c5f5-104">Syntax</span></span>  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9c5f5-105">Części</span><span class="sxs-lookup"><span data-stu-id="9c5f5-105">Parts</span></span>  
  
|<span data-ttu-id="9c5f5-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9c5f5-106">Term</span></span>|<span data-ttu-id="9c5f5-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9c5f5-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="9c5f5-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-108">Required.</span></span> <span data-ttu-id="9c5f5-109">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-109">Any `Boolean` expression.</span></span> <span data-ttu-id="9c5f5-110">Wynik jest `Boolean` wynik porównania dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="9c5f5-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-111">Required.</span></span> <span data-ttu-id="9c5f5-112">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="9c5f5-113">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-113">Required.</span></span> <span data-ttu-id="9c5f5-114">Wszelkie `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c5f5-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9c5f5-115">Remarks</span></span>  
 <span data-ttu-id="9c5f5-116">Operacja logiczna jest nazywany *zwarcie* Jeśli skompilowany kod może obejść przedziały oceny jedno wyrażenie w zależności od wyniku innego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="9c5f5-117">Jeśli wynik pierwsze wyrażenie obliczane określi ostateczny wynik operacji, nie ma potrzeby do oceny, drugie wyrażenie, ponieważ nie można zmienić, wynik końcowy.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="9c5f5-118">Zwarcie może poprawić wydajność, jeśli pominięto wyrażenie jest złożone, czy obejmuje wywołania procedur.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="9c5f5-119">Jeśli oba wyrażenia mają `True`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="9c5f5-120">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9c5f5-121">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="9c5f5-121">If `expression1` is</span></span>|<span data-ttu-id="9c5f5-122">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="9c5f5-122">And `expression2` is</span></span>|<span data-ttu-id="9c5f5-123">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="9c5f5-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="9c5f5-124">(nie oceniono)</span><span class="sxs-lookup"><span data-stu-id="9c5f5-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="9c5f5-125">Typy danych</span><span class="sxs-lookup"><span data-stu-id="9c5f5-125">Data Types</span></span>  
 <span data-ttu-id="9c5f5-126">`AndAlso` Operator jest zdefiniowany tylko w przypadku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f5-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="9c5f5-127">Visual Basic konwertuje każdy argument konieczny do `Boolean` i wykonuje operację całkowicie w `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-127">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="9c5f5-128">Jeśli wynik jest przypisany do typu numerycznego, Visual Basic konwertuje go z `Boolean` do tego typu.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="9c5f5-129">Może to powodować nieoczekiwane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-129">This could produce unexpected behavior.</span></span> <span data-ttu-id="9c5f5-130">Na przykład `5 AndAlso 12` skutkuje `–1` podczas konwersji na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-130">For example, `5 AndAlso 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9c5f5-131">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="9c5f5-131">Overloading</span></span>  
 <span data-ttu-id="9c5f5-132">[Operatora](../../../visual-basic/language-reference/operators/and-operator.md) i [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) może być *przeciążone*, co oznacza, że klasa lub Struktura można ponownie zdefiniować ich zachowania, gdy argument operacji ma typ, który klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-132">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9c5f5-133">Przeciążanie `And` i `IsFalse` operatory wpływa na zachowanie `AndAlso` operatora.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="9c5f5-134">Jeśli kod używa `AndAlso` dla klasy lub struktury, która przeciążenia `And` i `IsFalse`, należy zrozumieć ich zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="9c5f5-135">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f5-135">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c5f5-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c5f5-136">Example</span></span>  
 <span data-ttu-id="9c5f5-137">W poniższym przykładzie użyto `AndAlso` operator przeprowadzić logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="9c5f5-138">Wynik jest `Boolean` wartość wskazującą, czy cały conjoined wyrażenie ma wartość true.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="9c5f5-139">Jeśli pierwsze wyrażenie jest `False`, drugi nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="9c5f5-140">Poprzedni przykład generuje wyniki `True`, `False`, i `False`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="9c5f5-141">Podczas obliczania `secondCheck`, drugie wyrażenie nie jest oceniany, ponieważ pierwszy jest już `False`.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="9c5f5-142">Jednak drugie wyrażenie jest obliczane w obliczeniach kluczowych `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c5f5-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="9c5f5-143">Example</span></span>  
 <span data-ttu-id="9c5f5-144">W poniższym przykładzie przedstawiono `Function` procedury, która wyszukuje danej wartości wśród elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="9c5f5-145">Jeśli tablica jest pusta lub przekroczeniu długość tablicy `While` instrukcji Testuj elementu tablicy względem wartości wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="9c5f5-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="9c5f5-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9c5f5-146">See also</span></span>

- [<span data-ttu-id="9c5f5-147">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9c5f5-147">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9c5f5-148">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c5f5-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9c5f5-149">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="9c5f5-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9c5f5-150">And, operator</span><span class="sxs-lookup"><span data-stu-id="9c5f5-150">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="9c5f5-151">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="9c5f5-151">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="9c5f5-152">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c5f5-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
