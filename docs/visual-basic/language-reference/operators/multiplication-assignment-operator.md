---
title: '*= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 47d3239af6ff24501e6babc23c0db4103c477796
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701067"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8c8b7-102">\*= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c8b7-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="8c8b7-103">Mnoży wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c8b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c8b7-104">Syntax</span></span>  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="8c8b7-105">Części</span><span class="sxs-lookup"><span data-stu-id="8c8b7-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8c8b7-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-106">Required.</span></span> <span data-ttu-id="8c8b7-107">Dowolna zmienna lub właściwość numeryczna.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="8c8b7-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-108">Required.</span></span> <span data-ttu-id="8c8b7-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8c8b7-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8c8b7-110">Remarks</span></span>  
 <span data-ttu-id="8c8b7-111">Element po lewej stronie operatora `*=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8c8b7-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8c8b7-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8c8b7-113">Operator `*=` w pierwszej kolejności mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora) ().</span><span class="sxs-lookup"><span data-stu-id="8c8b7-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="8c8b7-114">Następnie operator przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8c8b7-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="8c8b7-115">Overloading</span></span>  
 <span data-ttu-id="8c8b7-116">[Operator \*](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8c8b7-117">Przeciążanie operatora `*` wpływa na zachowanie operatora `*=`.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="8c8b7-118">Jeśli kod używa `*=` na klasie lub strukturze, która przeciąża `*`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8c8b7-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8c8b7-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c8b7-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8c8b7-120">Example</span></span>  
 <span data-ttu-id="8c8b7-121">Poniższy przykład używa operatora `*=` do mnożenia jednej zmiennej `Integer` przez sekundę i przypisze wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8c8b7-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8c8b7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c8b7-122">See also</span></span>

- [<span data-ttu-id="8c8b7-123">\*, operator</span><span class="sxs-lookup"><span data-stu-id="8c8b7-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="8c8b7-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="8c8b7-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8c8b7-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="8c8b7-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="8c8b7-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8c8b7-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8c8b7-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="8c8b7-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8c8b7-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="8c8b7-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
