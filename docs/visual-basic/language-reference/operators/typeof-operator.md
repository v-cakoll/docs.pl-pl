---
title: "TypeOf — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="cae46-102">TypeOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cae46-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="cae46-103">Porównuje zmiennej odwołania do obiektu z typem danych.</span><span class="sxs-lookup"><span data-stu-id="cae46-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cae46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cae46-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="cae46-105">Części</span><span class="sxs-lookup"><span data-stu-id="cae46-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="cae46-106">Zwracane.</span><span class="sxs-lookup"><span data-stu-id="cae46-106">Returned.</span></span> <span data-ttu-id="cae46-107">A `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="cae46-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="cae46-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cae46-108">Required.</span></span> <span data-ttu-id="cae46-109">Wyrażenie, którego wynikiem jest typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="cae46-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="cae46-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cae46-110">Required.</span></span> <span data-ttu-id="cae46-111">Nazwa typu żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="cae46-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cae46-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cae46-112">Remarks</span></span>  
 <span data-ttu-id="cae46-113">`TypeOf` Operator określa, czy typ środowiska wykonawczego `objectexpression` jest zgodny z `typename`.</span><span class="sxs-lookup"><span data-stu-id="cae46-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="cae46-114">Zgodność zależy od typu kategorii `typename`.</span><span class="sxs-lookup"><span data-stu-id="cae46-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="cae46-115">W poniższej tabeli przedstawiono, jak ustalona zgodności.</span><span class="sxs-lookup"><span data-stu-id="cae46-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="cae46-116">Typ kategorii`typename`</span><span class="sxs-lookup"><span data-stu-id="cae46-116">Type category of `typename`</span></span>|<span data-ttu-id="cae46-117">Kryterium zgodności</span><span class="sxs-lookup"><span data-stu-id="cae46-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="cae46-118">Class</span><span class="sxs-lookup"><span data-stu-id="cae46-118">Class</span></span>|<span data-ttu-id="cae46-119">`objectexpression`jest typu `typename` lub dziedziczy`typename`</span><span class="sxs-lookup"><span data-stu-id="cae46-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="cae46-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="cae46-120">Structure</span></span>|<span data-ttu-id="cae46-121">`objectexpression`jest typu`typename`</span><span class="sxs-lookup"><span data-stu-id="cae46-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="cae46-122">Interface</span><span class="sxs-lookup"><span data-stu-id="cae46-122">Interface</span></span>|<span data-ttu-id="cae46-123">`objectexpression`implementuje `typename` lub dziedziczy z klasy, która implementuje`typename`</span><span class="sxs-lookup"><span data-stu-id="cae46-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="cae46-124">Jeśli typ środowiska wykonawczego `objectexpression` spełnia kryterium zgodności `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="cae46-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="cae46-125">W przeciwnym razie `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="cae46-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="cae46-126">Jeśli `objectexpression` ma wartość null, następnie `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="cae46-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="cae46-127">`TypeOf`zawsze jest używany z `Is` — słowo kluczowe do skonstruowania `TypeOf`... `Is` wyrażenia, lub z `IsNot` — słowo kluczowe do skonstruowania `TypeOf`... `IsNot` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="cae46-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cae46-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="cae46-128">Example</span></span>  
 <span data-ttu-id="cae46-129">W poniższym przykładzie użyto `TypeOf`... `Is` wyrażenia do testowania zgodności typu dwóch obiektów zmienne odwołujące się przy użyciu różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="cae46-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 <span data-ttu-id="cae46-130">Zmienna `refInteger` ma typ środowiska wykonawczego `Integer`.</span><span class="sxs-lookup"><span data-stu-id="cae46-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="cae46-131">Jest on zgodny z `Integer` , lecz nie `Double`.</span><span class="sxs-lookup"><span data-stu-id="cae46-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="cae46-132">Zmienna `refForm` ma typ środowiska wykonawczego <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="cae46-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="cae46-133">Jest on zgodny z <xref:System.Windows.Forms.Form> , ponieważ jego typ, który jest z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.Windows.Forms.Control>i z <xref:System.ComponentModel.IComponent> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="cae46-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="cae46-134">Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="cae46-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cae46-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cae46-135">See Also</span></span>  
 [<span data-ttu-id="cae46-136">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="cae46-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="cae46-137">IsNot — Operator</span><span class="sxs-lookup"><span data-stu-id="cae46-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="cae46-138">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cae46-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="cae46-139">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cae46-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="cae46-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="cae46-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="cae46-141">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cae46-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
