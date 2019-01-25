---
title: = — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 58dcdfd21fd8701c6ac391672e768819f696aab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643558"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="d6385-102">= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6385-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="d6385-103">Przypisuje wartość do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="d6385-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6385-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d6385-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="d6385-105">Części</span><span class="sxs-lookup"><span data-stu-id="d6385-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="d6385-106">Jakakolwiek zmienna zapisu lub dowolnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d6385-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="d6385-107">Wszelkie literał, — stała lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="d6385-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6385-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d6385-108">Remarks</span></span>  
 <span data-ttu-id="d6385-109">Element po lewej stronie znaku równości (`=`) może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d6385-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="d6385-110">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="d6385-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="d6385-111">`=` Operator przypisuje wartość do zmiennej po prawej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="d6385-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6385-112">`=` Operator jest również używany jako operator porównania.</span><span class="sxs-lookup"><span data-stu-id="d6385-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="d6385-113">Aby uzyskać więcej informacji, zobacz [operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="d6385-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d6385-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="d6385-114">Overloading</span></span>  
 <span data-ttu-id="d6385-115">`=` Operator może być przeciążona, tylko jako operator porównania relacyjnych, a nie jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="d6385-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="d6385-116">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d6385-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6385-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6385-117">Example</span></span>  
 <span data-ttu-id="d6385-118">W poniższym przykładzie pokazano operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="d6385-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="d6385-119">Wartość po prawej stronie jest przypisywana do zmiennej po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="d6385-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6385-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d6385-120">See also</span></span>
- [<span data-ttu-id="d6385-121">&=, operator</span><span class="sxs-lookup"><span data-stu-id="d6385-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="d6385-122">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="d6385-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="d6385-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="d6385-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="d6385-124">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6385-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="d6385-125">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6385-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="d6385-126">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="d6385-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="d6385-127">^=, operator</span><span class="sxs-lookup"><span data-stu-id="d6385-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="d6385-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="d6385-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="d6385-129">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="d6385-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="d6385-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="d6385-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="d6385-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="d6385-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
