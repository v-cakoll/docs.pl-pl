---
title: Operatory i wyrażenia
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
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403436"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="1488d-102">Operatory i wyrażenia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1488d-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="1488d-103">*Operator* jest elementem kodu, który wykonuje operację na jednym lub większej liczbie elementów kodu, które przechowują wartości.</span><span class="sxs-lookup"><span data-stu-id="1488d-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="1488d-104">Elementy wartości to zmienne, stałe, literały, właściwości, zwracane z `Function` i `Operator` procedury i wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1488d-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="1488d-105">*Wyrażenie* jest serią elementów wartości połączonych z operatorami, które dają nową wartość.</span><span class="sxs-lookup"><span data-stu-id="1488d-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="1488d-106">Operatory działają na elementach wartości przez wykonywanie obliczeń, porównań lub innych operacji.</span><span class="sxs-lookup"><span data-stu-id="1488d-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="1488d-107">Typy operatorów</span><span class="sxs-lookup"><span data-stu-id="1488d-107">Types of Operators</span></span>  
 <span data-ttu-id="1488d-108">Visual Basic udostępnia następujące typy operatorów:</span><span class="sxs-lookup"><span data-stu-id="1488d-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="1488d-109">[Operatory arytmetyczne](arithmetic-operators.md) wykonują znane obliczenia na wartościach liczbowych, w tym przesunięcie ich wzorców bitowych.</span><span class="sxs-lookup"><span data-stu-id="1488d-109">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="1488d-110">[Operatory porównania](comparison-operators.md) porównują dwa wyrażenia i zwracają `Boolean` wartość reprezentującą wynik porównania.</span><span class="sxs-lookup"><span data-stu-id="1488d-110">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="1488d-111">[Operatory łączenia](concatenation-operators.md) sprzęga wiele ciągów w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="1488d-111">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="1488d-112">[Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md) łączenia `Boolean` lub wartości liczbowych i zwracają wynik tego samego typu danych co wartości.</span><span class="sxs-lookup"><span data-stu-id="1488d-112">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="1488d-113">Elementy wartości, które są połączone z operatorem, są nazywane *operandami* tego operatora.</span><span class="sxs-lookup"><span data-stu-id="1488d-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="1488d-114">Operatory połączone z wyrażeniami elementów wartości, z wyjątkiem operatora przypisania, który tworzy *instrukcję*.</span><span class="sxs-lookup"><span data-stu-id="1488d-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="1488d-115">Aby uzyskać więcej informacji, zobacz [instrukcje](../statements.md).</span><span class="sxs-lookup"><span data-stu-id="1488d-115">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="1488d-116">Obliczanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1488d-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="1488d-117">Wynik końcowy wyrażenia reprezentuje wartość, która jest zazwyczaj znanym typem danych, takim jak `Boolean` , `String` lub typu liczbowego.</span><span class="sxs-lookup"><span data-stu-id="1488d-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="1488d-118">Poniżej przedstawiono przykłady wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1488d-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="1488d-119">Kilka operatorów może wykonywać akcje w pojedynczym wyrażeniu lub instrukcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1488d-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="1488d-120">W poprzednim przykładzie Visual Basic wykonuje operacje w wyrażeniu po prawej stronie operatora przypisania ( `=` ), a następnie przypisuje wartość wyniki do zmiennej `x` po lewej.</span><span class="sxs-lookup"><span data-stu-id="1488d-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="1488d-121">Nie ma praktycznego limitu liczby operatorów, które mogą być połączone w wyrażeniu, ale w celu uzyskania oczekiwanych wyników należy zrozumieć [pierwszeństwo operatorów w Visual Basic](../../../language-reference/operators/operator-precedence.md) .</span><span class="sxs-lookup"><span data-stu-id="1488d-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="1488d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1488d-122">See also</span></span>

- [<span data-ttu-id="1488d-123">Operatory</span><span class="sxs-lookup"><span data-stu-id="1488d-123">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="1488d-124">Skuteczna kombinacja operatorów</span><span class="sxs-lookup"><span data-stu-id="1488d-124">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="1488d-125">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="1488d-125">Statements</span></span>](../../../language-reference/statements/index.md)
