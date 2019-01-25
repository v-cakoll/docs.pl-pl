---
title: Operatory i wyrażenia w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: 9badc41a97043b6e32da4dd93834770f871261c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498534"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="190a5-102">Operatory i wyrażenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="190a5-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="190a5-103">*Operator* jest element kodu, który wykonuje operację na elementy kodu, które zawierają wartości.</span><span class="sxs-lookup"><span data-stu-id="190a5-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="190a5-104">Elementy wartości obejmują zmienne, stałe, literały, właściwości, zwraca z `Function` i `Operator` procedur i wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="190a5-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="190a5-105">*Wyrażenie* jest serią wartości elementów w połączeniu z operatorami, która daje w wyniku nową wartość.</span><span class="sxs-lookup"><span data-stu-id="190a5-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="190a5-106">Operatory działają w przypadku elementów wartość, wykonując obliczenia, porównania lub innych operacji.</span><span class="sxs-lookup"><span data-stu-id="190a5-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="190a5-107">Typy operatorów</span><span class="sxs-lookup"><span data-stu-id="190a5-107">Types of Operators</span></span>  
 <span data-ttu-id="190a5-108">Visual Basic oferuje następujące operatory:</span><span class="sxs-lookup"><span data-stu-id="190a5-108">Visual Basic provides the following types of operators:</span></span>  
  
-   <span data-ttu-id="190a5-109">[Operatory arytmetyczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) wykonywanie obliczeń dobrze znanych na wartości liczbowe, łącznie z ich wzorców bitowe przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="190a5-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
-   <span data-ttu-id="190a5-110">[Operatory porównania](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) porównać dwa wyrażenia i zwraca `Boolean` wartość reprezentująca wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="190a5-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
-   <span data-ttu-id="190a5-111">[Concatenation — operatory](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) Dołącz do wielu ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="190a5-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
-   <span data-ttu-id="190a5-112">[Logiczne i bitowe operatory w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) połączyć `Boolean` lub wartości liczbowych i zwracają wynik o ten sam typ danych jako wartości.</span><span class="sxs-lookup"><span data-stu-id="190a5-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="190a5-113">Elementy wartości, które są połączone z operatorem są nazywane *operandy* tego operatora.</span><span class="sxs-lookup"><span data-stu-id="190a5-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="190a5-114">Operatory w połączeniu z wyrażenia formularza elementów wartości, z wyjątkiem operatora przypisania, który stanowi *instrukcji*.</span><span class="sxs-lookup"><span data-stu-id="190a5-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="190a5-115">Aby uzyskać więcej informacji, zobacz [instrukcji](../../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="190a5-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="190a5-116">Obliczanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="190a5-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="190a5-117">Wynik końcowy wyrażenie reprezentuje wartość, która jest zazwyczaj dobrze znanych danych typu, takich jak `Boolean`, `String`, lub typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="190a5-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="190a5-118">Poniżej przedstawiono przykłady wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="190a5-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="190a5-119">Wiele operatorów może wykonywać akcje w pojedyncze wyrażenie lub instrukcję, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="190a5-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/index_1.vb)]  
  
 <span data-ttu-id="190a5-120">W powyższym przykładzie Visual Basic wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania (`=`), następnie przypisuje wynikowej wartości do zmiennej `x` po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="190a5-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="190a5-121">Nie ma żadnego limitu praktyczne liczby operatorów, które mogą być połączone w wyrażeniu, ale zrozumienie [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) jest niezbędne do zapewnienia, że otrzymujesz oczekiwanych wyników.</span><span class="sxs-lookup"><span data-stu-id="190a5-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  
  
 <span data-ttu-id="190a5-122">Aby uzyskać więcej informacji i przykładów, zobacz [przeciążania operatora w języku Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span><span class="sxs-lookup"><span data-stu-id="190a5-122">For more information and examples, see [Operator Overloading in Visual Basic 2005](https://msdn.microsoft.com/library/ms379613(v=vs.80).aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190a5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="190a5-123">See also</span></span>
- [<span data-ttu-id="190a5-124">Operatory</span><span class="sxs-lookup"><span data-stu-id="190a5-124">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="190a5-125">Skuteczna kombinacja operatorów</span><span class="sxs-lookup"><span data-stu-id="190a5-125">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="190a5-126">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="190a5-126">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
