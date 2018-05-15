---
title: Porównania wartości (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="0a725-102">Porównania wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a725-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="0a725-103">Operatory porównania może służyć do konstruowania wyrażeń, które porównanie wartości numerycznych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="0a725-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="0a725-104">Zwraca tych wyrażeń `Boolean` wartość oparta na czy wynik porównania ma wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="0a725-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="0a725-105">Przykłady takich wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0a725-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="0a725-106">Pierwsze wyrażenie daje w wyniku `True`, ponieważ jest większa niż 26 45.</span><span class="sxs-lookup"><span data-stu-id="0a725-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="0a725-107">Drugi przykład daje w wyniku `False`, ponieważ nie jest większa niż 45 26.</span><span class="sxs-lookup"><span data-stu-id="0a725-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="0a725-108">Wyrażenia liczbowe w ten sposób można także porównać.</span><span class="sxs-lookup"><span data-stu-id="0a725-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="0a725-109">Wyrażeń, które można porównać się być wyrażenia złożone, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a725-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="0a725-110">Poprzedniego wyrażenia złożone zawiera literały, zmienne i wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="0a725-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="0a725-111">Wyrażeń po obu stronach operatora porównania są obliczane, a wyniki są porównywane przy użyciu `>=` operator porównania.</span><span class="sxs-lookup"><span data-stu-id="0a725-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="0a725-112">Jeśli wartość wyrażenia z lewej strony jest większa lub równa wartości wyrażenie po prawej stronie, całe wyrażenie daje w wyniku `True`; w przeciwnym razie daje w wyniku `False`.</span><span class="sxs-lookup"><span data-stu-id="0a725-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="0a725-113">Wyrażeń, które umożliwia porównanie wartości są najczęściej używane w `If...Then` konstrukcje, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a725-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="0a725-114">`=` Znak jest operator porównania, a także operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="0a725-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="0a725-115">Gdy jest używany jako operator porównania, ocenia to, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a725-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="0a725-116">Można również użyć wyrażenia porównania dowolnym `Boolean` wartość jest wymagane, na przykład `If`, `While`, `Loop`, lub `ElseIf` instrukcji lub podczas przypisywania do lub przekazanie wartości do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a725-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="0a725-117">W poniższym przykładzie wartość zwrócona przez wyrażenie porównania jest przypisany do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a725-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0a725-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a725-118">See Also</span></span>  
 [<span data-ttu-id="0a725-119">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="0a725-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="0a725-120">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="0a725-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="0a725-121">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a725-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="0a725-122">Instrukcje: obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="0a725-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="0a725-123">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0a725-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
