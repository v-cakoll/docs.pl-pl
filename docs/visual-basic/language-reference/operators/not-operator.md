---
title: Not — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: cd93316ada1fcf0997922f71a8efc5a3cf411d09
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614617"
---
# <a name="not-operator-visual-basic"></a><span data-ttu-id="63b51-102">Not — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b51-102">Not Operator (Visual Basic)</span></span>
<span data-ttu-id="63b51-103">Wykonuje logiczną negację na `Boolean` wyrażenie lub bitowego zaprzeczenia wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="63b51-103">Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63b51-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="63b51-104">Syntax</span></span>  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a><span data-ttu-id="63b51-105">Części</span><span class="sxs-lookup"><span data-stu-id="63b51-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="63b51-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="63b51-106">Required.</span></span> <span data-ttu-id="63b51-107">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="63b51-107">Any `Boolean` or numeric expression.</span></span>  
  
 `expression`  
 <span data-ttu-id="63b51-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="63b51-108">Required.</span></span> <span data-ttu-id="63b51-109">Wszelkie `Boolean` lub wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="63b51-109">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63b51-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63b51-110">Remarks</span></span>  
 <span data-ttu-id="63b51-111">Aby uzyskać `Boolean` wyrażenia, w poniższej tabeli przedstawiono sposób `result` jest określana.</span><span class="sxs-lookup"><span data-stu-id="63b51-111">For `Boolean` expressions, the following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="63b51-112">Jeśli `expression` jest</span><span class="sxs-lookup"><span data-stu-id="63b51-112">If `expression` is</span></span>|<span data-ttu-id="63b51-113">Wartość `result` jest</span><span class="sxs-lookup"><span data-stu-id="63b51-113">The value of `result` is</span></span>|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 <span data-ttu-id="63b51-114">Dla wyrażeń liczbowych `Not` operator odwraca wartości bitowe dowolne wyrażenie numeryczne i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.</span><span class="sxs-lookup"><span data-stu-id="63b51-114">For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="63b51-115">Jeśli bit w `expression` jest</span><span class="sxs-lookup"><span data-stu-id="63b51-115">If bit in `expression` is</span></span>|<span data-ttu-id="63b51-116">Bit w `result` jest</span><span class="sxs-lookup"><span data-stu-id="63b51-116">The bit in `result` is</span></span>|  
|-------------------------------|----------------------------|  
|<span data-ttu-id="63b51-117">1</span><span class="sxs-lookup"><span data-stu-id="63b51-117">1</span></span>|<span data-ttu-id="63b51-118">0</span><span class="sxs-lookup"><span data-stu-id="63b51-118">0</span></span>|  
|<span data-ttu-id="63b51-119">0</span><span class="sxs-lookup"><span data-stu-id="63b51-119">0</span></span>|<span data-ttu-id="63b51-120">1</span><span class="sxs-lookup"><span data-stu-id="63b51-120">1</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="63b51-121">Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.</span><span class="sxs-lookup"><span data-stu-id="63b51-121">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="63b51-122">Typy danych</span><span class="sxs-lookup"><span data-stu-id="63b51-122">Data Types</span></span>  
 <span data-ttu-id="63b51-123">Logiczna Negacja, typ danych wyniku jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="63b51-123">For a Boolean negation, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="63b51-124">Dla Negacja, typ danych wyniku jest taka sama, jak w przypadku `expression`.</span><span class="sxs-lookup"><span data-stu-id="63b51-124">For a bitwise negation, the result data type is the same as that of `expression`.</span></span> <span data-ttu-id="63b51-125">Jednakże jeśli wyrażenie ma `Decimal`, wynik jest `Long`.</span><span class="sxs-lookup"><span data-stu-id="63b51-125">However, if expression is `Decimal`, the result is `Long`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="63b51-126">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="63b51-126">Overloading</span></span>  
 <span data-ttu-id="63b51-127">`Not` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="63b51-127">The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="63b51-128">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="63b51-128">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="63b51-129">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="63b51-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b51-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="63b51-130">Example</span></span>  
 <span data-ttu-id="63b51-131">W poniższym przykładzie użyto `Not` operator do przeprowadzania Negacja logiczna `Boolean` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="63b51-131">The following example uses the `Not` operator to perform logical negation on a `Boolean` expression.</span></span> <span data-ttu-id="63b51-132">Wynik jest `Boolean` wartość, która reprezentuje odwrotnej wartość wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="63b51-132">The result is a `Boolean` value that represents the reverse of the value of the expression.</span></span>  
  
 [!code-vb[VbVbalrOperators#33](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_1.vb)]  
  
 <span data-ttu-id="63b51-133">Poprzedni przykład generuje wyniki `False` i `True`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="63b51-133">The preceding example produces results of `False` and `True`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b51-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="63b51-134">Example</span></span>  
 <span data-ttu-id="63b51-135">W poniższym przykładzie użyto `Not` operator przeprowadzić Negacja logiczna pojedynczych bitów wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="63b51-135">The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression.</span></span> <span data-ttu-id="63b51-136">Bit we wzorcu wynik jest ustawiony do tyłu odnośny bit we wzorcu operand, łącznie z bitem.</span><span class="sxs-lookup"><span data-stu-id="63b51-136">The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.</span></span>  
  
 [!code-vb[VbVbalrOperators#34](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/not-operator_2.vb)]  
  
 <span data-ttu-id="63b51-137">Poprzedni przykład generuje wyniki – 11, –9 i –7, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="63b51-137">The preceding example produces results of –11, –9, and –7, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b51-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63b51-138">See also</span></span>
- [<span data-ttu-id="63b51-139">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b51-139">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="63b51-140">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63b51-140">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="63b51-141">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="63b51-141">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="63b51-142">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63b51-142">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
