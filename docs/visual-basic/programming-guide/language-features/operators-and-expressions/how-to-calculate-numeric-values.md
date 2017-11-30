---
title: "Porady: obliczanie wartości liczbowych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a><span data-ttu-id="77bdf-102">Porady: obliczanie wartości liczbowych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77bdf-102">How to: Calculate Numeric Values (Visual Basic)</span></span>
<span data-ttu-id="77bdf-103">Można obliczyć wartości liczbowych za pomocą wyrażeń liczbowych.</span><span class="sxs-lookup"><span data-stu-id="77bdf-103">You can calculate numeric values through the use of numeric expressions.</span></span> <span data-ttu-id="77bdf-104">A *wyrażenia liczbowego* jest wyrażenie, które zawiera literały, stałe i zmienne reprezentujący wartości liczbowych i operatory, które działają na tych wartości.</span><span class="sxs-lookup"><span data-stu-id="77bdf-104">A *numeric expression* is an expression that contains literals, constants, and variables representing numeric values, and operators that act on those values.</span></span>  
  
## <a name="calculating-numeric-values"></a><span data-ttu-id="77bdf-105">Obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="77bdf-105">Calculating Numeric Values</span></span>  
  
#### <a name="to-calculate-a-numeric-value"></a><span data-ttu-id="77bdf-106">Obliczanie wartości liczbowych</span><span class="sxs-lookup"><span data-stu-id="77bdf-106">To calculate a numeric value</span></span>  
  
-   <span data-ttu-id="77bdf-107">Łączenie co najmniej jeden literały numeryczne, stałe i zmienne w wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="77bdf-107">Combine one or more numeric literals, constants, and variables into a numeric expression.</span></span> <span data-ttu-id="77bdf-108">W poniższym przykładzie przedstawiono niektóre prawidłowe wyrażenia liczbowego.</span><span class="sxs-lookup"><span data-stu-id="77bdf-108">The following example shows some valid numeric expressions.</span></span>  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     <span data-ttu-id="77bdf-109">Pierwsze trzy wiersze zawierają literałem stałej i zmiennej.</span><span class="sxs-lookup"><span data-stu-id="77bdf-109">The first three lines show a literal, a constant, and a variable.</span></span> <span data-ttu-id="77bdf-110">Każda z nich stanowi prawidłowe wyrażenie liczbowe samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="77bdf-110">Each one forms a valid numeric expression by itself.</span></span> <span data-ttu-id="77bdf-111">Końcowe wiersz zawiera kombinację zmiennej z dwóch literały.</span><span class="sxs-lookup"><span data-stu-id="77bdf-111">The final line shows a combination of a variable with two literals.</span></span>  
  
     <span data-ttu-id="77bdf-112">Należy pamiętać, że wyrażenie liczbowe nie tworzą pełnego [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instrukcji samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="77bdf-112">Note that a numeric expression does not form a complete [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statement by itself.</span></span> <span data-ttu-id="77bdf-113">Należy użyć wyrażenia jako część pełną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="77bdf-113">You must use the expression as part of a complete statement.</span></span>  
  
#### <a name="to-store-a-numeric-value"></a><span data-ttu-id="77bdf-114">Do przechowywania wartości numerycznej</span><span class="sxs-lookup"><span data-stu-id="77bdf-114">To store a numeric value</span></span>  
  
-   <span data-ttu-id="77bdf-115">Aby przypisać wartość reprezentowanego przez wyrażenie liczbowe do zmiennej, jak w poniższym przykładzie pokazano służy instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="77bdf-115">You can use an assignment statement to assign the value represented by a numeric expression to a variable, as the following example demonstrates.</span></span>  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     <span data-ttu-id="77bdf-116">W powyższym przykładzie wartość wyrażenie po prawej stronie operatora równa (`=`) jest przypisany do zmiennej `j` po lewej stronie operatora, więc `j` daje w wyniku 276.</span><span class="sxs-lookup"><span data-stu-id="77bdf-116">In the preceding example, the value of the expression on the right side of the equal operator (`=`) is assigned to the variable `j` on the left side of the operator, so `j` evaluates to 276.</span></span>  
  
     <span data-ttu-id="77bdf-117">Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="77bdf-117">For more information, see [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="multiple-operators"></a><span data-ttu-id="77bdf-118">Wiele operatorów</span><span class="sxs-lookup"><span data-stu-id="77bdf-118">Multiple Operators</span></span>  
 <span data-ttu-id="77bdf-119">Jeśli wyrażenie liczbowe zawiera więcej niż jeden operator, kolejność, w jakiej są oceniane jest określana przez reguły pierwszeństwo operatorów.</span><span class="sxs-lookup"><span data-stu-id="77bdf-119">If the numeric expression contains more than one operator, the order in which they are evaluated is determined by the rules of operator precedence.</span></span> <span data-ttu-id="77bdf-120">Aby zastąpić reguły pierwszeństwa operatora, ujmij wyrażenia w nawiasach, tak jak w powyższym przykładzie; zamknięte wyrażenia są sprawdzane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="77bdf-120">To override the rules of operator precedence, you enclose expressions in parentheses, as in the above example; the enclosed expressions are evaluated first.</span></span>  
  
#### <a name="to-override-normal-operator-precedence"></a><span data-ttu-id="77bdf-121">Aby zastąpić normalne kolejność wykonywania działań</span><span class="sxs-lookup"><span data-stu-id="77bdf-121">To override normal operator precedence</span></span>  
  
-   <span data-ttu-id="77bdf-122">Umieść nawiasy operacje, które można wykonać pierwsze.</span><span class="sxs-lookup"><span data-stu-id="77bdf-122">Use parentheses to enclose the operations you want to be performed first.</span></span> <span data-ttu-id="77bdf-123">W poniższym przykładzie pokazano dwa różne wyniki z tej samej argumenty i operatory.</span><span class="sxs-lookup"><span data-stu-id="77bdf-123">The following example shows two different results with the same operands and operators.</span></span>  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     <span data-ttu-id="77bdf-124">W powyższym przykładzie obliczeń dla `j` wykonuje operator dodawania (`+`) pierwszego ponieważ nawiasy, `(67 + i)` zastąpienia normalnym priorytecie, a wartość przypisana do `j` jest 276 (4 razy 69).</span><span class="sxs-lookup"><span data-stu-id="77bdf-124">In the preceding example, the calculation for `j` performs the addition operator (`+`) first because the parentheses around `(67 + i)` override normal precedence, and the value assigned to `j` is 276 (4 times 69).</span></span> <span data-ttu-id="77bdf-125">Obliczanie dla `k` wykonuje operatorów w ich normalnym pierwszeństwa (`*` przed `+`) i wartość przypisana do `k` jest 270 (268 plus 2).</span><span class="sxs-lookup"><span data-stu-id="77bdf-125">The calculation for `k` performs the operators in their normal precedence (`*` before `+`), and the value assigned to `k` is 270 (268 plus 2).</span></span>  
  
     <span data-ttu-id="77bdf-126">Aby uzyskać więcej informacji, zobacz [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="77bdf-126">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77bdf-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77bdf-127">See Also</span></span>  
 [<span data-ttu-id="77bdf-128">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="77bdf-128">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="77bdf-129">Porównania wartości</span><span class="sxs-lookup"><span data-stu-id="77bdf-129">Value Comparisons</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="77bdf-130">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="77bdf-130">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="77bdf-131">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="77bdf-131">Operator Precedence in Visual Basic</span></span>](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="77bdf-132">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="77bdf-132">Arithmetic Operators</span></span>](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="77bdf-133">Skuteczna kombinacja operatorów</span><span class="sxs-lookup"><span data-stu-id="77bdf-133">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
