---
title: Operatory i wyrażenia w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dae47988e27ed4b1a714943ce1fbffe3b815066b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="a77c0-102">Operatory i wyrażenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a77c0-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="a77c0-103">*Operator* jest element kodu, który wykonuje operacje na elementy kodu, które zawierają wartości.</span><span class="sxs-lookup"><span data-stu-id="a77c0-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="a77c0-104">Wartość elementów obejmują zmienne, stałe, literały, właściwości, zwraca z `Function` i `Operator` procedur i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a77c0-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="a77c0-105">*Wyrażenie* jest szereg elementów wartość w połączeniu z operatorami, która daje w wyniku nową wartość.</span><span class="sxs-lookup"><span data-stu-id="a77c0-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="a77c0-106">Operatory działa w przypadku elementów wartość wykonując obliczenia, porównania lub innych operacji.</span><span class="sxs-lookup"><span data-stu-id="a77c0-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="a77c0-107">Typy operatorów</span><span class="sxs-lookup"><span data-stu-id="a77c0-107">Types of Operators</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="a77c0-108">udostępnia następujące operatory:</span><span class="sxs-lookup"><span data-stu-id="a77c0-108"> provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="a77c0-109">[Operatory arytmetyczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) obliczeń znanych na wartości liczbowe, łącznie z ich wzorców bitowe przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="a77c0-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="a77c0-110">[Operatory porównania](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porównać dwa wyrażenia i zwraca `Boolean` wartość reprezentująca wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="a77c0-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="a77c0-111">[Operatory łączenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) dołączyć wielu ciągów w jednym ciągu.</span><span class="sxs-lookup"><span data-stu-id="a77c0-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="a77c0-112">[Logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) połączyć `Boolean` lub alfanumeryczne wartości i zwraca wynik tego samego typu danych jako wartości.</span><span class="sxs-lookup"><span data-stu-id="a77c0-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="a77c0-113">Elementy wartości, które są łączone za pomocą operatora są nazywane *operandy* tego operatora.</span><span class="sxs-lookup"><span data-stu-id="a77c0-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="a77c0-114">Operatory w połączeniu z wartości wyrażenia formularza elementów, z wyjątkiem operatora przypisania który stanowi *instrukcji*.</span><span class="sxs-lookup"><span data-stu-id="a77c0-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="a77c0-115">Aby uzyskać więcej informacji, zobacz [instrukcje](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="a77c0-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="a77c0-116">Obliczanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="a77c0-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="a77c0-117">W rezultacie wyrażenie reprezentuje wartość, która jest zazwyczaj znanych danych typu, takich jak `Boolean`, `String`, lub typ liczbowy.</span><span class="sxs-lookup"><span data-stu-id="a77c0-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="a77c0-118">Poniżej przedstawiono przykłady wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a77c0-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="a77c0-119">Wiele operatorów dostępne akcje w jedno wyrażenie lub instrukcję, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a77c0-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 <span data-ttu-id="a77c0-120">W powyższym przykładzie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania (`=`), następnie przypisuje wynikowej wartości do zmiennej `x` po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a77c0-120">In the preceding example, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="a77c0-121">Nie ma żadnego limitu praktyczne liczby operatory, które mogą być połączone w wyrażeniu, ale zrozumienia [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) jest niezbędne mieć pewność, że wyniki spodziewasz się.</span><span class="sxs-lookup"><span data-stu-id="a77c0-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
 <span data-ttu-id="a77c0-122">Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="a77c0-122">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77c0-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a77c0-123">See Also</span></span>  
 [<span data-ttu-id="a77c0-124">Operatory</span><span class="sxs-lookup"><span data-stu-id="a77c0-124">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)  
 [<span data-ttu-id="a77c0-125">Skuteczna kombinacja operatorów</span><span class="sxs-lookup"><span data-stu-id="a77c0-125">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [<span data-ttu-id="a77c0-126">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="a77c0-126">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
