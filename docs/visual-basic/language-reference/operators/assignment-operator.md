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
ms.openlocfilehash: 5e6d34802f5f82373d0e8176f3b732a327c55d01
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964997"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="9220f-102">= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9220f-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="9220f-103">Przypisuje wartość do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="9220f-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9220f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9220f-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="9220f-105">Części</span><span class="sxs-lookup"><span data-stu-id="9220f-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="9220f-106">Jakakolwiek zmienna zapisu lub dowolnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="9220f-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="9220f-107">Wszelkie literał, — stała lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="9220f-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9220f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9220f-108">Remarks</span></span>  
 <span data-ttu-id="9220f-109">Element po lewej stronie znaku równości (`=`) może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="9220f-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="9220f-110">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="9220f-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="9220f-111">`=` Operator przypisuje wartość do zmiennej po prawej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="9220f-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9220f-112">`=` Operator jest również używany jako operator porównania.</span><span class="sxs-lookup"><span data-stu-id="9220f-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="9220f-113">Aby uzyskać więcej informacji, zobacz [operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="9220f-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="9220f-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="9220f-114">Overloading</span></span>  
 <span data-ttu-id="9220f-115">`=` Operator może być przeciążona, tylko jako operator porównania relacyjnych, a nie jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="9220f-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="9220f-116">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9220f-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9220f-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="9220f-117">Example</span></span>  
 <span data-ttu-id="9220f-118">W poniższym przykładzie pokazano operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="9220f-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="9220f-119">Wartość po prawej stronie jest przypisywana do zmiennej po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="9220f-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="9220f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9220f-120">See also</span></span>
- [<span data-ttu-id="9220f-121">&=, operator</span><span class="sxs-lookup"><span data-stu-id="9220f-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="9220f-122">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="9220f-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="9220f-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="9220f-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="9220f-124">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9220f-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="9220f-125">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9220f-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="9220f-126">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="9220f-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="9220f-127">^=, operator</span><span class="sxs-lookup"><span data-stu-id="9220f-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="9220f-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="9220f-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="9220f-129">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="9220f-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="9220f-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="9220f-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="9220f-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="9220f-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
