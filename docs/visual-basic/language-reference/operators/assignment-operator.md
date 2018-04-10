---
title: = — Operator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="752ab-102">= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752ab-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="752ab-103">Przypisuje wartość do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="752ab-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="752ab-104">Syntax</span></span>  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="752ab-105">Części</span><span class="sxs-lookup"><span data-stu-id="752ab-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="752ab-106">Wszystkie zapisywalne zmiennej lub dowolną właściwość.</span><span class="sxs-lookup"><span data-stu-id="752ab-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="752ab-107">Wszelkie literal, stałej lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="752ab-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="752ab-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="752ab-108">Remarks</span></span>  
 <span data-ttu-id="752ab-109">Element po lewej stronie znaku równości (`=`) może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="752ab-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="752ab-110">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="752ab-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="752ab-111">`=` Operator przypisuje wartość jego prawej strony, aby zmienna lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="752ab-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="752ab-112">`=` Operator jest również używany jako operator porównania.</span><span class="sxs-lookup"><span data-stu-id="752ab-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="752ab-113">Aby uzyskać więcej informacji, zobacz [operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="752ab-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="752ab-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="752ab-114">Overloading</span></span>  
 <span data-ttu-id="752ab-115">`=` Operator może być przeciążona tylko jako operator porównania relacyjne, a nie jako operatora przypisania.</span><span class="sxs-lookup"><span data-stu-id="752ab-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="752ab-116">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="752ab-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="752ab-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="752ab-117">Example</span></span>  
 <span data-ttu-id="752ab-118">W poniższym przykładzie pokazano operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="752ab-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="752ab-119">Wartość po prawej stronie jest przypisany do zmiennej po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="752ab-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="752ab-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="752ab-120">See Also</span></span>  
 [<span data-ttu-id="752ab-121">& = — operator</span><span class="sxs-lookup"><span data-stu-id="752ab-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="752ab-122">\* = — Operator</span><span class="sxs-lookup"><span data-stu-id="752ab-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [<span data-ttu-id="752ab-123">+= — Operator</span><span class="sxs-lookup"><span data-stu-id="752ab-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [<span data-ttu-id="752ab-124">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752ab-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [<span data-ttu-id="752ab-125">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="752ab-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="752ab-126">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="752ab-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [<span data-ttu-id="752ab-127">^ = — Operator</span><span class="sxs-lookup"><span data-stu-id="752ab-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [<span data-ttu-id="752ab-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="752ab-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="752ab-129">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="752ab-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="752ab-130">Tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="752ab-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [<span data-ttu-id="752ab-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="752ab-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
