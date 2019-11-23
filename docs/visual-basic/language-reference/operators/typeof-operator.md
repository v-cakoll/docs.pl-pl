---
title: TypeOf — Operator
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350891"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="ac67a-102">TypeOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac67a-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="ac67a-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span><span class="sxs-lookup"><span data-stu-id="ac67a-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="ac67a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ac67a-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="ac67a-105">Części</span><span class="sxs-lookup"><span data-stu-id="ac67a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ac67a-106">Returned.</span><span class="sxs-lookup"><span data-stu-id="ac67a-106">Returned.</span></span> <span data-ttu-id="ac67a-107">A `Boolean` value.</span><span class="sxs-lookup"><span data-stu-id="ac67a-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="ac67a-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ac67a-108">Required.</span></span> <span data-ttu-id="ac67a-109">Any expression that evaluates to a reference type.</span><span class="sxs-lookup"><span data-stu-id="ac67a-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="ac67a-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="ac67a-110">Required.</span></span> <span data-ttu-id="ac67a-111">Any data type name.</span><span class="sxs-lookup"><span data-stu-id="ac67a-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac67a-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ac67a-112">Remarks</span></span>  
 <span data-ttu-id="ac67a-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="ac67a-114">The compatibility depends on the type category of `typename`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="ac67a-115">The following table shows how compatibility is determined.</span><span class="sxs-lookup"><span data-stu-id="ac67a-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="ac67a-116">Type category of `typename`</span><span class="sxs-lookup"><span data-stu-id="ac67a-116">Type category of `typename`</span></span>|<span data-ttu-id="ac67a-117">Compatibility criterion</span><span class="sxs-lookup"><span data-stu-id="ac67a-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="ac67a-118">Class</span><span class="sxs-lookup"><span data-stu-id="ac67a-118">Class</span></span>|<span data-ttu-id="ac67a-119">`objectexpression` is of type `typename` or inherits from `typename`</span><span class="sxs-lookup"><span data-stu-id="ac67a-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="ac67a-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="ac67a-120">Structure</span></span>|<span data-ttu-id="ac67a-121">`objectexpression` is of type `typename`</span><span class="sxs-lookup"><span data-stu-id="ac67a-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="ac67a-122">Interface</span><span class="sxs-lookup"><span data-stu-id="ac67a-122">Interface</span></span>|<span data-ttu-id="ac67a-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span><span class="sxs-lookup"><span data-stu-id="ac67a-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="ac67a-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="ac67a-125">Otherwise, `result` is `False`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="ac67a-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="ac67a-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span><span class="sxs-lookup"><span data-stu-id="ac67a-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac67a-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="ac67a-128">Example</span></span>  
 <span data-ttu-id="ac67a-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span><span class="sxs-lookup"><span data-stu-id="ac67a-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="ac67a-130">The variable `refInteger` has a run-time type of `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="ac67a-131">It is compatible with `Integer` but not with `Double`.</span><span class="sxs-lookup"><span data-stu-id="ac67a-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="ac67a-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="ac67a-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="ac67a-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="ac67a-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="ac67a-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="ac67a-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac67a-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac67a-135">See also</span></span>

- [<span data-ttu-id="ac67a-136">Is, operator</span><span class="sxs-lookup"><span data-stu-id="ac67a-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="ac67a-137">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="ac67a-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="ac67a-138">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac67a-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="ac67a-139">Operator Precedence in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac67a-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="ac67a-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="ac67a-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="ac67a-141">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ac67a-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
