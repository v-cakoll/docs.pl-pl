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
ms.openlocfilehash: 50054b9e32f4d49a34c1bb1a5c79129662019aee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965914"
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="645ad-102">Porównania wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="645ad-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="645ad-103">Operatory porównania może służyć do konstruowania wyrażeń, które Porównaj wartości liczbowe zmiennych.</span><span class="sxs-lookup"><span data-stu-id="645ad-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="645ad-104">Zwraca te wyrażenia `Boolean` wartość oparta na czy wynik porównania ma wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="645ad-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="645ad-105">Przykłady takich wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="645ad-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="645ad-106">Pierwsze wyrażenie, które daje w wyniku `True`, ponieważ 45 jest większa od 26.</span><span class="sxs-lookup"><span data-stu-id="645ad-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="645ad-107">Drugi przykład daje w wyniku `False`, ponieważ nie jest większa niż 45 26.</span><span class="sxs-lookup"><span data-stu-id="645ad-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="645ad-108">Można również porównać wyrażeń liczbowych w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="645ad-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="645ad-109">Same wyrażeń, które można porównać mogą być złożone wyrażenia, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="645ad-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="645ad-110">Poprzedni złożone wyrażenie zawiera literały, zmienne i wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="645ad-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="645ad-111">Wyrażenia po obu stronach operatora porównania są obliczane i wynikające z tego wartości są porównywane za pomocą `>=` operator porównania.</span><span class="sxs-lookup"><span data-stu-id="645ad-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="645ad-112">Jeśli wartość wyrażenia po lewej stronie jest większa lub równa wartości wyrażenia po prawej stronie, całe wyrażenie daje w wyniku `True`; w przeciwnym razie daje w wyniku `False`.</span><span class="sxs-lookup"><span data-stu-id="645ad-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="645ad-113">Wyrażeń, Porównaj wartości, które są najczęściej używane w `If...Then` konstrukcje, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="645ad-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 <span data-ttu-id="645ad-114">`=` Znak jest operator porównania, a także operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="645ad-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="645ad-115">Gdy jest używana jako operator porównania, ocenia to, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="645ad-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 <span data-ttu-id="645ad-116">Umożliwia także wyrażenia porównania dowolnym `Boolean` wartość jest wymagane, na przykład `If`, `While`, `Loop`, lub `ElseIf` instrukcji, lub podczas przypisywania do lub przekazanie wartości do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="645ad-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="645ad-117">W poniższym przykładzie przypisano wartości zwracanych przez wyrażenie porównania `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="645ad-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a><span data-ttu-id="645ad-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="645ad-118">See also</span></span>
- [<span data-ttu-id="645ad-119">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="645ad-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="645ad-120">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="645ad-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="645ad-121">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="645ad-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="645ad-122">Instrukcje: Obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="645ad-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [<span data-ttu-id="645ad-123">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="645ad-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
