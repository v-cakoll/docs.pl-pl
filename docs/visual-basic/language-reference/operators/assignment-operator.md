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
ms.openlocfilehash: ad74e3ebc947af4f36022be838b69df6ce24997a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608280"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="653f6-102">= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="653f6-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="653f6-103">Przypisuje wartość do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="653f6-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="653f6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="653f6-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="653f6-105">Części</span><span class="sxs-lookup"><span data-stu-id="653f6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="653f6-106">Jakakolwiek zmienna zapisu lub dowolnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="653f6-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="653f6-107">Wszelkie literał, — stała lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="653f6-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="653f6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="653f6-108">Remarks</span></span>  
 <span data-ttu-id="653f6-109">Element po lewej stronie znaku równości (`=`) może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="653f6-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="653f6-110">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="653f6-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="653f6-111">`=` Operator przypisuje wartość do zmiennej po prawej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="653f6-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="653f6-112">`=` Operator jest również używany jako operator porównania.</span><span class="sxs-lookup"><span data-stu-id="653f6-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="653f6-113">Aby uzyskać więcej informacji, zobacz [operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="653f6-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="653f6-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="653f6-114">Overloading</span></span>  
 <span data-ttu-id="653f6-115">`=` Operator może być przeciążona, tylko jako operator porównania relacyjnych, a nie jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="653f6-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="653f6-116">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="653f6-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="653f6-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="653f6-117">Example</span></span>  
 <span data-ttu-id="653f6-118">W poniższym przykładzie pokazano operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="653f6-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="653f6-119">Wartość po prawej stronie jest przypisywana do zmiennej po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="653f6-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="653f6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="653f6-120">See also</span></span>

- [<span data-ttu-id="653f6-121">&=, operator</span><span class="sxs-lookup"><span data-stu-id="653f6-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="653f6-122">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="653f6-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="653f6-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="653f6-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="653f6-124">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="653f6-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="653f6-125">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="653f6-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="653f6-126">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="653f6-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="653f6-127">^=, operator</span><span class="sxs-lookup"><span data-stu-id="653f6-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="653f6-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="653f6-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="653f6-129">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="653f6-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="653f6-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="653f6-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="653f6-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="653f6-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
