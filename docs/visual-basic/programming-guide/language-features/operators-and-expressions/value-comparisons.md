---
title: Porównania wartości
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
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346287"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="ebe6b-102">Porównania wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ebe6b-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="ebe6b-103">Operatory porównania mogą służyć do konstruowania wyrażeń, które porównują wartości zmiennych liczbowych.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="ebe6b-104">Te wyrażenia zwracają wartość `Boolean` na podstawie tego, czy porównanie ma wartość PRAWDA, czy fałsz.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="ebe6b-105">Przykłady takiego wyrażenia są następujące.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="ebe6b-106">Pierwsze wyrażenie szacuje `True`, ponieważ 45 jest większe niż 26.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="ebe6b-107">Drugi przykład jest obliczany `False`, ponieważ 26 nie jest większy niż 45.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="ebe6b-108">Możesz również porównać wyrażenia liczbowe w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="ebe6b-109">Porównywane wyrażenia mogą same być wyrażeniami złożonymi, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="ebe6b-110">Poprzednie wyrażenie złożone zawiera literały, zmienne i wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="ebe6b-111">Wyrażenia po obu stronach operatora porównania są oceniane, a wynikowe wartości są porównywane przy użyciu operatora porównania `>=`.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="ebe6b-112">Jeśli wartość wyrażenia po lewej stronie jest większa lub równa wartości wyrażenia z prawej strony, całe wyrażenie szacuje się `True`; w przeciwnym razie szacuje się `False`.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="ebe6b-113">Wyrażenia, które porównują wartości są najczęściej używane w konstrukcjach `If...Then`, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="ebe6b-114">Znak `=` jest operatorem porównania, a także operatorem przypisania.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="ebe6b-115">Gdy jest używany jako operator porównania, sprawdza, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="ebe6b-116">Można również użyć wyrażenia porównania w dowolnym miejscu, `Boolean` jest wymagana wartość, na przykład w `If`, `While`, `Loop`lub instrukcji `ElseIf` lub po przypisaniu lub przekazaniu wartości do zmiennej `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="ebe6b-117">W poniższym przykładzie wartość zwracana przez wyrażenie porównania jest przypisana do zmiennej `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ebe6b-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="ebe6b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebe6b-118">See also</span></span>

- [<span data-ttu-id="ebe6b-119">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="ebe6b-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="ebe6b-120">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ebe6b-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="ebe6b-121">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebe6b-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="ebe6b-122">Instrukcje: obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="ebe6b-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="ebe6b-123">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebe6b-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
