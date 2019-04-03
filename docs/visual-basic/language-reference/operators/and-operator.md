---
title: And — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818621"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="7833a-102">And — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7833a-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="7833a-103">Wykonuje logiczną na dwóch `Boolean` wyrażeń lub koniunkcję bitową na dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="7833a-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7833a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7833a-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7833a-105">Części</span><span class="sxs-lookup"><span data-stu-id="7833a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7833a-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7833a-106">Required.</span></span> <span data-ttu-id="7833a-107">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="7833a-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="7833a-108">Dla porównania logiczna `result` jest logicznego połączenia dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="7833a-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="7833a-109">W przypadku operacji bitowej `result` jest wartość liczbowa reprezentująca koniunkcję bitową na dwóch wzorców bitowych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="7833a-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="7833a-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7833a-110">Required.</span></span> <span data-ttu-id="7833a-111">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="7833a-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="7833a-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7833a-112">Required.</span></span> <span data-ttu-id="7833a-113">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="7833a-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7833a-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7833a-114">Remarks</span></span>  
 <span data-ttu-id="7833a-115">Dla porównania logiczna `result` jest `True` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` zwrócić `True`.</span><span class="sxs-lookup"><span data-stu-id="7833a-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="7833a-116">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="7833a-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="7833a-117">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-117">If `expression1` is</span></span>|<span data-ttu-id="7833a-118">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-118">And `expression2` is</span></span>|<span data-ttu-id="7833a-119">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="7833a-120">Wartość logiczna porównania `And` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="7833a-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="7833a-121">[AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `False`, następnie `expression2` nie jest oceniany.</span><span class="sxs-lookup"><span data-stu-id="7833a-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="7833a-122">Gdy jest stosowany do wartości liczbowych `And` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="7833a-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="7833a-123">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-123">If bit in `expression1` is</span></span>|<span data-ttu-id="7833a-124">I bitu w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-124">And bit in `expression2` is</span></span>|<span data-ttu-id="7833a-125">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="7833a-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="7833a-126">1</span><span class="sxs-lookup"><span data-stu-id="7833a-126">1</span></span>|<span data-ttu-id="7833a-127">1</span><span class="sxs-lookup"><span data-stu-id="7833a-127">1</span></span>|<span data-ttu-id="7833a-128">1</span><span class="sxs-lookup"><span data-stu-id="7833a-128">1</span></span>|  
|<span data-ttu-id="7833a-129">1</span><span class="sxs-lookup"><span data-stu-id="7833a-129">1</span></span>|<span data-ttu-id="7833a-130">0</span><span class="sxs-lookup"><span data-stu-id="7833a-130">0</span></span>|<span data-ttu-id="7833a-131">0</span><span class="sxs-lookup"><span data-stu-id="7833a-131">0</span></span>|  
|<span data-ttu-id="7833a-132">0</span><span class="sxs-lookup"><span data-stu-id="7833a-132">0</span></span>|<span data-ttu-id="7833a-133">1</span><span class="sxs-lookup"><span data-stu-id="7833a-133">1</span></span>|<span data-ttu-id="7833a-134">0</span><span class="sxs-lookup"><span data-stu-id="7833a-134">0</span></span>|  
|<span data-ttu-id="7833a-135">0</span><span class="sxs-lookup"><span data-stu-id="7833a-135">0</span></span>|<span data-ttu-id="7833a-136">0</span><span class="sxs-lookup"><span data-stu-id="7833a-136">0</span></span>|<span data-ttu-id="7833a-137">0</span><span class="sxs-lookup"><span data-stu-id="7833a-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="7833a-138">Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wyniki.</span><span class="sxs-lookup"><span data-stu-id="7833a-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="7833a-139">Typy danych</span><span class="sxs-lookup"><span data-stu-id="7833a-139">Data Types</span></span>  
 <span data-ttu-id="7833a-140">Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.</span><span class="sxs-lookup"><span data-stu-id="7833a-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="7833a-141">Dla porównania Boolean, typ danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7833a-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="7833a-142">Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="7833a-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="7833a-143">Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="7833a-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7833a-144">`And` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="7833a-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7833a-145">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="7833a-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7833a-146">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7833a-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7833a-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="7833a-147">Example</span></span>  
 <span data-ttu-id="7833a-148">W poniższym przykładzie użyto `And` operator przeprowadzić logicznego połączenia dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="7833a-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="7833a-149">Wynik jest `Boolean` wartość wskazującą, czy oba wyrażenia są `True`.</span><span class="sxs-lookup"><span data-stu-id="7833a-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="7833a-150">Poprzedni przykład generuje wyniki `True` i `False`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7833a-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7833a-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="7833a-151">Example</span></span>  
 <span data-ttu-id="7833a-152">W poniższym przykładzie użyto `And` operatora, aby wykonać połączenie logiczne na poszczególnych bity dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="7833a-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="7833a-153">Bit we wzorcu wynik jest ustawiona, jeśli odpowiednich bitów w operandy są ustawione na 1.</span><span class="sxs-lookup"><span data-stu-id="7833a-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="7833a-154">Poprzedni przykład generuje wyniki, 8, 2 i 0, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="7833a-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7833a-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7833a-155">See also</span></span>

- [<span data-ttu-id="7833a-156">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7833a-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="7833a-157">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7833a-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7833a-158">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="7833a-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7833a-159">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="7833a-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="7833a-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7833a-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
