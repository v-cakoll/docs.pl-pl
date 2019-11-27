---
title: = — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350200"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a4127-102">= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4127-102">= Operator (Visual Basic)</span></span>
<span data-ttu-id="a4127-103">Przypisuje wartość do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4127-103">Assigns a value to a variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4127-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a4127-104">Syntax</span></span>  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a><span data-ttu-id="a4127-105">Części</span><span class="sxs-lookup"><span data-stu-id="a4127-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="a4127-106">Dowolna zapisywalna zmienna lub Każda właściwość.</span><span class="sxs-lookup"><span data-stu-id="a4127-106">Any writable variable or any property.</span></span>  
  
 `value`  
 <span data-ttu-id="a4127-107">Dowolny literał, stała lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="a4127-107">Any literal, constant, or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4127-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a4127-108">Remarks</span></span>  
 <span data-ttu-id="a4127-109">Element po lewej stronie znaku równości (`=`) może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="a4127-109">The element on the left side of the equal sign (`=`) can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="a4127-110">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="a4127-110">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="a4127-111">Operator `=` przypisuje wartość po prawej stronie do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a4127-111">The `=` operator assigns the value on its right to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4127-112">Operator `=` jest również używany jako operator porównania.</span><span class="sxs-lookup"><span data-stu-id="a4127-112">The `=` operator is also used as a comparison operator.</span></span> <span data-ttu-id="a4127-113">Aby uzyskać szczegółowe informacje, zobacz [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).</span><span class="sxs-lookup"><span data-stu-id="a4127-113">For details, see [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a4127-114">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="a4127-114">Overloading</span></span>  
 <span data-ttu-id="a4127-115">Operator `=` może być przeciążony tylko jako operator porównania relacyjnego, a nie jako operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="a4127-115">The `=` operator can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span> <span data-ttu-id="a4127-116">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a4127-116">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4127-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="a4127-117">Example</span></span>  
 <span data-ttu-id="a4127-118">Poniższy przykład demonstruje operator przypisania.</span><span class="sxs-lookup"><span data-stu-id="a4127-118">The following example demonstrates the assignment operator.</span></span> <span data-ttu-id="a4127-119">Wartość po prawej stronie jest przypisana do zmiennej po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="a4127-119">The value on the right is assigned to the variable on the left.</span></span>  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="a4127-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4127-120">See also</span></span>

- [<span data-ttu-id="a4127-121">&=, operator</span><span class="sxs-lookup"><span data-stu-id="a4127-121">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="a4127-122">\*=, operator</span><span class="sxs-lookup"><span data-stu-id="a4127-122">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="a4127-123">+=, operator</span><span class="sxs-lookup"><span data-stu-id="a4127-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="a4127-124">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4127-124">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="a4127-125">Operator/= (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4127-125">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [<span data-ttu-id="a4127-126">\\= — operator</span><span class="sxs-lookup"><span data-stu-id="a4127-126">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="a4127-127">^=, operator</span><span class="sxs-lookup"><span data-stu-id="a4127-127">^= Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [<span data-ttu-id="a4127-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="a4127-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="a4127-129">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="a4127-129">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="a4127-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="a4127-130">ReadOnly</span></span>](../../../visual-basic/language-reference/modifiers/readonly.md)
- [<span data-ttu-id="a4127-131">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="a4127-131">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
