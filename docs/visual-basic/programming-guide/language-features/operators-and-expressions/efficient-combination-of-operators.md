---
title: Skuteczna kombinacja operatorów
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
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348997"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="bc0ad-102">Skuteczna kombinacja operatorów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc0ad-102">Efficient Combination of Operators (Visual Basic)</span></span>
<span data-ttu-id="bc0ad-103">Wyrażenia złożone mogą zawierać wiele różnych operatorów.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-103">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="bc0ad-104">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-104">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="bc0ad-105">Tworzenie złożonych wyrażeń, takich jak jeden w poprzednim przykładzie, wymaga dokładnego poznania reguł pierwszeństwa operatorów.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-105">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="bc0ad-106">Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="bc0ad-106">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="bc0ad-107">Wyrażenia w nawiasach</span><span class="sxs-lookup"><span data-stu-id="bc0ad-107">Parenthetical Expressions</span></span>  
 <span data-ttu-id="bc0ad-108">Często operacje mają być wykonywane w innej kolejności niż określona przez pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-108">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="bc0ad-109">Rozważmy następujący przykład.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-109">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="bc0ad-110">Poprzedni przykład mnoży `z` przez `y`, a następnie dodaje wynik do `4`.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-110">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="bc0ad-111">Jeśli jednak chcesz dodać `y` i `4` przed pomnożeniem wyniku przez `z`, możesz przesłonić normalny priorytet operatorów przy użyciu nawiasów.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-111">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="bc0ad-112">Umieszczając wyrażenie w nawiasach, należy wymusić, aby wyrażenie było oceniane jako pierwsze, niezależnie od pierwszeństwa operatora.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-112">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="bc0ad-113">Aby wymusić powyższy przykład, aby najpierw wykonać dodanie, można napisać go ponownie tak, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-113">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="bc0ad-114">Powyższy przykład dodaje `y` i `4`, a następnie mnoży sumę według `z`.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-114">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="bc0ad-115">Zagnieżdżone wyrażenia ujęte w nawiasy</span><span class="sxs-lookup"><span data-stu-id="bc0ad-115">Nested Parenthetical Expressions</span></span>  
 <span data-ttu-id="bc0ad-116">Można zagnieżdżać wyrażenia na wielu poziomach nawiasów, aby jeszcze bardziej zastępować pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-116">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="bc0ad-117">Wyrażenia najbardziej głęboko zagnieżdżone w nawiasach są oceniane jako pierwsze, po których następuje następne przeważnie zagnieżdżone i tak dalej, jak najmniej głęboko zagnieżdżone, a wreszcie wyrażenia poza nawiasy.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-117">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="bc0ad-118">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-118">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="bc0ad-119">W poprzednim przykładzie `z + 2` jest oceniane jako pierwsze, a następnie inne wyrażenia ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-119">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="bc0ad-120">Potęga, która zwykle ma wyższy priorytet niż Dodawanie lub mnożenie, jest szacowana jako Ostatnia w tym przykładzie, ponieważ inne wyrażenia są ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="bc0ad-120">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc0ad-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bc0ad-121">See also</span></span>

- [<span data-ttu-id="bc0ad-122">Operatory arytmetyczne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc0ad-122">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="bc0ad-123">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc0ad-123">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="bc0ad-124">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc0ad-124">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="bc0ad-125">Operatory logiczne/bitowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bc0ad-125">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="bc0ad-126">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="bc0ad-126">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="bc0ad-127">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="bc0ad-127">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="bc0ad-128">Instrukcje: obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="bc0ad-128">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="bc0ad-129">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bc0ad-129">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
