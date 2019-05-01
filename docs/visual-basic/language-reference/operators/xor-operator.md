---
title: Xor — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 0cba3a995fb1ab774c8a5308e58f0b6905fc23f3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781176"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="1bb5f-102">Xor — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bb5f-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="1bb5f-103">Wykonuje logiczne wykluczenie na dwóch `Boolean` wyrażeń lub bitowego wykluczenia dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bb5f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1bb5f-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="1bb5f-105">Części</span><span class="sxs-lookup"><span data-stu-id="1bb5f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1bb5f-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-106">Required.</span></span> <span data-ttu-id="1bb5f-107">Wszelkie `Boolean` lub zmienna liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="1bb5f-108">Dla porównania logiczna `result` jest wykluczenie logiczne (wyłączne rozłączenie logiczne) z dwóch `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="1bb5f-109">W przypadku operacji bitowej `result` jest wartością liczbową, reprezentujący bitowe wykluczenie dwóch wzorców bitowych liczbowych (wyłączne bitowego rozłączenia).</span><span class="sxs-lookup"><span data-stu-id="1bb5f-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="1bb5f-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-110">Required.</span></span> <span data-ttu-id="1bb5f-111">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="1bb5f-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-112">Required.</span></span> <span data-ttu-id="1bb5f-113">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bb5f-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1bb5f-114">Remarks</span></span>  
 <span data-ttu-id="1bb5f-115">Dla porównania logiczna `result` jest `True` tylko wtedy, gdy dokładnie jeden z `expression1` i `expression2` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="1bb5f-116">Oznacza to, że tylko wtedy, gdy `expression1` i `expression2` oceny do przeciwnego `Boolean` wartości.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="1bb5f-117">W poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="1bb5f-118">Jeśli `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-118">If `expression1` is</span></span>|<span data-ttu-id="1bb5f-119">I `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-119">And `expression2` is</span></span>|<span data-ttu-id="1bb5f-120">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="1bb5f-121">Wartość logiczna porównania `Xor` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="1bb5f-122">Nie ma odpowiednika short-circuiting do `Xor`, ponieważ wynik zależy od zawsze oba operandy.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="1bb5f-123">Aby uzyskać *zwarcie* operatorów logicznych, zobacz [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) i [orelse — Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="1bb5f-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="1bb5f-124">W przypadku operacji bitowej `Xor` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="1bb5f-125">Jeśli bit w `expression1` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-125">If bit in `expression1` is</span></span>|<span data-ttu-id="1bb5f-126">I bitu w `expression2` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-126">And bit in `expression2` is</span></span>|<span data-ttu-id="1bb5f-127">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="1bb5f-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="1bb5f-128">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-128">1</span></span>|<span data-ttu-id="1bb5f-129">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-129">1</span></span>|<span data-ttu-id="1bb5f-130">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-130">0</span></span>|  
|<span data-ttu-id="1bb5f-131">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-131">1</span></span>|<span data-ttu-id="1bb5f-132">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-132">0</span></span>|<span data-ttu-id="1bb5f-133">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-133">1</span></span>|  
|<span data-ttu-id="1bb5f-134">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-134">0</span></span>|<span data-ttu-id="1bb5f-135">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-135">1</span></span>|<span data-ttu-id="1bb5f-136">1</span><span class="sxs-lookup"><span data-stu-id="1bb5f-136">1</span></span>|  
|<span data-ttu-id="1bb5f-137">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-137">0</span></span>|<span data-ttu-id="1bb5f-138">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-138">0</span></span>|<span data-ttu-id="1bb5f-139">0</span><span class="sxs-lookup"><span data-stu-id="1bb5f-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="1bb5f-140">Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="1bb5f-141">Na przykład 5 `Xor` 3 to 6.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="1bb5f-142">Aby zobaczyć, dlaczego jest to tak, Konwertuj do ich reprezentacji binarnych, 101 i 011 5 i 3.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="1bb5f-143">Następnie użyj poprzedniej tabeli, aby określić, że 101 Xor 011 wynosi 110, czyli reprezentacja binarna liczba dziesiętna 6.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="1bb5f-144">Typy danych</span><span class="sxs-lookup"><span data-stu-id="1bb5f-144">Data Types</span></span>  
 <span data-ttu-id="1bb5f-145">Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="1bb5f-146">Aby uzyskać `Boolean` jest typ danych wyniku porównania, `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="1bb5f-147">Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="1bb5f-148">Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="1bb5f-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1bb5f-149">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="1bb5f-149">Overloading</span></span>  
 <span data-ttu-id="1bb5f-150">`Xor` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1bb5f-151">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="1bb5f-152">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1bb5f-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb5f-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bb5f-153">Example</span></span>  
 <span data-ttu-id="1bb5f-154">W poniższym przykładzie użyto `Xor` operatora wykonywanego wykluczenie logiczne (rozłączenie logiczne wyłączne) na dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="1bb5f-155">Wynik jest `Boolean` wartość wskazującą, czy jest dokładnie jedno wyrażenie `True`.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="1bb5f-156">Poprzedni przykład generuje wyniki `False`, `True`, i `False`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bb5f-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bb5f-157">Example</span></span>  
 <span data-ttu-id="1bb5f-158">W poniższym przykładzie użyto `Xor` operatora wykonywanego wykluczenie logiczne (rozłączenie logiczne wyłączne) na poszczególnych bity dwóch wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="1bb5f-159">Bit we wzorcu wynik jest ustawiona, jeśli dokładnie jeden z odpowiednich bitów w operandów jest ustawiona na 1.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="1bb5f-160">Poprzedni przykład generuje wyniki, 2, 12 i 14, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="1bb5f-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bb5f-161">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bb5f-161">See also</span></span>

- [<span data-ttu-id="1bb5f-162">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bb5f-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="1bb5f-163">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bb5f-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1bb5f-164">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1bb5f-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1bb5f-165">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bb5f-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
