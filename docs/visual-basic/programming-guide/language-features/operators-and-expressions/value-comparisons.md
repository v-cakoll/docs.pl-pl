---
title: "Porównania wartości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c11f12bbaf261c0853e96802f03322c5e7fdc706
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="value-comparisons-visual-basic"></a><span data-ttu-id="d9fab-102">Porównania wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9fab-102">Value Comparisons (Visual Basic)</span></span>
<span data-ttu-id="d9fab-103">Operatory porównania może służyć do konstruowania wyrażeń, które porównanie wartości numerycznych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d9fab-103">Comparison operators can be used to construct expressions that compare the values of numeric variables.</span></span> <span data-ttu-id="d9fab-104">Zwraca tych wyrażeń `Boolean` wartość oparta na czy wynik porównania ma wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="d9fab-104">These expressions return a `Boolean` value based on whether the comparison is true or false.</span></span> <span data-ttu-id="d9fab-105">Przykłady takich wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d9fab-105">Examples of such an expression are as follows.</span></span>  
  
 `45 > 26`  
  
 `26 > 45`  
  
 <span data-ttu-id="d9fab-106">Pierwsze wyrażenie daje w wyniku `True`, ponieważ jest większa niż 26 45.</span><span class="sxs-lookup"><span data-stu-id="d9fab-106">The first expression evaluates to `True`, because 45 is greater than 26.</span></span> <span data-ttu-id="d9fab-107">Drugi przykład daje w wyniku `False`, ponieważ nie jest większa niż 45 26.</span><span class="sxs-lookup"><span data-stu-id="d9fab-107">The second example evaluates to `False`, because 26 is not greater than 45.</span></span>  
  
 <span data-ttu-id="d9fab-108">Wyrażenia liczbowe w ten sposób można także porównać.</span><span class="sxs-lookup"><span data-stu-id="d9fab-108">You can also compare numeric expressions in this fashion.</span></span> <span data-ttu-id="d9fab-109">Wyrażeń, które można porównać się być wyrażenia złożone, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d9fab-109">The expressions you compare can themselves be complex expressions, as in the following example.</span></span>  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 <span data-ttu-id="d9fab-110">Poprzedniego wyrażenia złożone zawiera literały, zmienne i wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d9fab-110">The preceding complex expression includes literals, variables, and function calls.</span></span> <span data-ttu-id="d9fab-111">Wyrażeń po obu stronach operatora porównania są obliczane, a wyniki są porównywane przy użyciu `>=` operator porównania.</span><span class="sxs-lookup"><span data-stu-id="d9fab-111">The expressions on both sides of the comparison operator are evaluated, and the resulting values are then compared using the `>=` comparison operator.</span></span> <span data-ttu-id="d9fab-112">Jeśli wartość wyrażenia z lewej strony jest większa lub równa wartości wyrażenie po prawej stronie, całe wyrażenie daje w wyniku `True`; w przeciwnym razie daje w wyniku `False`.</span><span class="sxs-lookup"><span data-stu-id="d9fab-112">If the value of the expression on the left side is greater than or equal to the value of the expression on the right, the entire expression evaluates to `True`; otherwise, it evaluates to `False`.</span></span>  
  
 <span data-ttu-id="d9fab-113">Wyrażeń, które umożliwia porównanie wartości są najczęściej używane w `If...Then` konstrukcje, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d9fab-113">Expressions that compare values are most commonly used in `If...Then` constructions, as in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 <span data-ttu-id="d9fab-114">`=` Znak jest operator porównania, a także operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="d9fab-114">The `=` sign is a comparison operator as well as an assignment operator.</span></span> <span data-ttu-id="d9fab-115">Gdy jest używany jako operator porównania, ocenia to, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d9fab-115">When used as a comparison operator, it evaluates whether the value on the left is equal to the value on the right, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 <span data-ttu-id="d9fab-116">Można również użyć wyrażenia porównania dowolnym `Boolean` wartość jest wymagane, na przykład `If`, `While`, `Loop`, lub `ElseIf` instrukcji lub podczas przypisywania do lub przekazanie wartości do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d9fab-116">You can also use a comparison expression anywhere a `Boolean` value is needed, such as in an `If`, `While`, `Loop`, or `ElseIf` statement, or when assigning to or passing a value to a `Boolean` variable.</span></span> <span data-ttu-id="d9fab-117">W poniższym przykładzie wartość zwrócona przez wyrażenie porównania jest przypisany do `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d9fab-117">In the following example, the value returned by the comparison expression is assigned to a `Boolean` variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d9fab-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9fab-118">See Also</span></span>  
 [<span data-ttu-id="d9fab-119">Wyrażenia logiczne</span><span class="sxs-lookup"><span data-stu-id="d9fab-119">Boolean Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="d9fab-120">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="d9fab-120">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="d9fab-121">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9fab-121">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="d9fab-122">Porady: obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="d9fab-122">How to: Calculate Numeric Values</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [<span data-ttu-id="d9fab-123">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d9fab-123">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)
