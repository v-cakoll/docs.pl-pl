---
title: Skuteczna kombinacja operatorów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841267"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="f9c23-102">Skuteczna kombinacja operatorów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9c23-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="f9c23-103">Złożonych wyrażeń może zawierać wiele różnych operatorów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="f9c23-104">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="f9c23-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="f9c23-105">Tworzenie złożonych wyrażeń, takiego jak w poprzednim przykładzie wymaga dogłębnej wiedzy w zakresie zasad pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="f9c23-106">Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="f9c23-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="f9c23-107">Wyrażenia w nawiasach</span><span class="sxs-lookup"><span data-stu-id="f9c23-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="f9c23-108">Często ma operacje, aby przejść w innym porządku niż określonej przez priorytet operatorów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="f9c23-109">Rozważmy następujący przykład.</span><span class="sxs-lookup"><span data-stu-id="f9c23-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="f9c23-110">Poprzedni przykład mnoży `z` przez `y`, następnie dodaje wynik do `4`.</span><span class="sxs-lookup"><span data-stu-id="f9c23-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="f9c23-111">Ale jeśli chcesz dodać `y` i `4` przed pomnożenia wyniku przez `z`, pierwszeństwo operatorów normalne można zastąpić za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="f9c23-112">Umieszczając wyrażenia w nawiasach, możesz wymusić to wyrażenie do obliczenia, niezależnie od tego, pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="f9c23-113">Aby wymusić w poprzednim przykładzie w celu dodawania, można przepisać go tak, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9c23-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="f9c23-114">W poprzednim przykładzie dodano `y` i `4`, następnie mnoży tej sumy przez `z`.</span><span class="sxs-lookup"><span data-stu-id="f9c23-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="f9c23-115">Zagnieżdżone wyrażenia w nawiasach</span><span class="sxs-lookup"><span data-stu-id="f9c23-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="f9c23-116">Można zagnieżdżać wyrażenia w nawiasy, aby zastąpić jeszcze bardziej priorytet na wielu poziomach.</span><span class="sxs-lookup"><span data-stu-id="f9c23-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="f9c23-117">Wyrażenia najgłębiej zagnieżdżony w nawiasach są obliczane najpierw następuje dalej, najgłębiej zagnieżdżony i tak dalej do najmniej głęboko zagnieżdżone, a na końcu wyrażeń poza nawiasów.</span><span class="sxs-lookup"><span data-stu-id="f9c23-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="f9c23-118">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="f9c23-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="f9c23-119">W powyższym przykładzie `z + 2` jest pierwszy ocenione, a następnie inne wyrażenia w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="f9c23-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="f9c23-120">Zapis wykładniczy, która zwykle ma wyższy priorytet niż dodawanie i mnożenie, jest oceniany w ostatniej w tym przykładzie, ponieważ inne wyrażenia są ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="f9c23-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c23-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9c23-121">See also</span></span>

- [<span data-ttu-id="f9c23-122">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9c23-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="f9c23-123">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9c23-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="f9c23-124">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9c23-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="f9c23-125">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9c23-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="f9c23-126">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="f9c23-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="f9c23-127">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="f9c23-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="f9c23-128">Instrukcje: Obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="f9c23-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="f9c23-129">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f9c23-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
