---
title: '\=, operator'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: 600acf9b41b63358da245fe602595fee4093b15b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330944"
---
# <a name="-operator"></a><span data-ttu-id="ea2f8-102">\\= — operator</span><span class="sxs-lookup"><span data-stu-id="ea2f8-102">\\= Operator</span></span>
<span data-ttu-id="ea2f8-103">Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik całkowity do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea2f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea2f8-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ea2f8-105">Części</span><span class="sxs-lookup"><span data-stu-id="ea2f8-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ea2f8-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-106">Required.</span></span> <span data-ttu-id="ea2f8-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ea2f8-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-108">Required.</span></span> <span data-ttu-id="ea2f8-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea2f8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea2f8-110">Remarks</span></span>  
 <span data-ttu-id="ea2f8-111">Element po lewej stronie operatora `\=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ea2f8-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ea2f8-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ea2f8-113">Operator `\=` dzieli wartość zmiennej lub właściwości po lewej stronie przez wartość po prawej stronie, a następnie przypisuje wynik całkowity do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="ea2f8-114">Aby uzyskać więcej informacji na temat dzielenia liczb całkowitych, zobacz element [\ operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="ea2f8-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ea2f8-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="ea2f8-115">Overloading</span></span>  
 <span data-ttu-id="ea2f8-116">Operator `\` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ea2f8-117">Przeciążanie operatora `\` ma wpływ na zachowanie operatora `\=`.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="ea2f8-118">Jeśli kod używa `\=` na klasie lub strukturze, która przeciąża `\`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ea2f8-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ea2f8-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea2f8-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ea2f8-120">Example</span></span>  
 <span data-ttu-id="ea2f8-121">Poniższy przykład używa operatora `\=`, aby podzielić jedną zmienną `Integer` przez sekundę i przypisać wynik całkowity do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ea2f8-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="ea2f8-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ea2f8-122">See also</span></span>

- [<span data-ttu-id="ea2f8-123">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea2f8-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [<span data-ttu-id="ea2f8-124">Operator/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea2f8-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="ea2f8-125">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="ea2f8-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="ea2f8-126">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="ea2f8-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="ea2f8-127">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea2f8-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ea2f8-128">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="ea2f8-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ea2f8-129">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="ea2f8-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
