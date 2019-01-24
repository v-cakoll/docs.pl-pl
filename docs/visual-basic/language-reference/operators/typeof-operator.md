---
title: TypeOf — Operator (Visual Basic)
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
ms.openlocfilehash: 2695f517c42fb944d21f57aec829bbf8a864af17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596738"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="1cf59-102">TypeOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1cf59-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="1cf59-103">Porównuje zmienną obiektu odwołania do typu danych.</span><span class="sxs-lookup"><span data-stu-id="1cf59-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1cf59-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="1cf59-105">Części</span><span class="sxs-lookup"><span data-stu-id="1cf59-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1cf59-106">Zwracane.</span><span class="sxs-lookup"><span data-stu-id="1cf59-106">Returned.</span></span> <span data-ttu-id="1cf59-107">A `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="1cf59-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="1cf59-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1cf59-108">Required.</span></span> <span data-ttu-id="1cf59-109">Dowolne wyrażenie, którego wynikiem jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="1cf59-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="1cf59-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1cf59-110">Required.</span></span> <span data-ttu-id="1cf59-111">Nazwa typu żadnych danych.</span><span class="sxs-lookup"><span data-stu-id="1cf59-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cf59-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1cf59-112">Remarks</span></span>  
 <span data-ttu-id="1cf59-113">`TypeOf` Operator określa, czy środowiska wykonawczego typu `objectexpression` jest zgodny z `typename`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="1cf59-114">Zgodność jest zależna od typu kategorii `typename`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="1cf59-115">W poniższej tabeli przedstawiono, jak jest określana zgodność.</span><span class="sxs-lookup"><span data-stu-id="1cf59-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="1cf59-116">Typ kategorii `typename`</span><span class="sxs-lookup"><span data-stu-id="1cf59-116">Type category of `typename`</span></span>|<span data-ttu-id="1cf59-117">Kryterium zgodności</span><span class="sxs-lookup"><span data-stu-id="1cf59-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="1cf59-118">Class</span><span class="sxs-lookup"><span data-stu-id="1cf59-118">Class</span></span>|<span data-ttu-id="1cf59-119">`objectexpression` Typ jest `typename` lub dziedziczy z `typename`</span><span class="sxs-lookup"><span data-stu-id="1cf59-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="1cf59-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="1cf59-120">Structure</span></span>|<span data-ttu-id="1cf59-121">`objectexpression` jest typu `typename`</span><span class="sxs-lookup"><span data-stu-id="1cf59-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="1cf59-122">Interface</span><span class="sxs-lookup"><span data-stu-id="1cf59-122">Interface</span></span>|<span data-ttu-id="1cf59-123">`objectexpression` implementuje `typename` lub dziedziczy z klasy, która implementuje `typename`</span><span class="sxs-lookup"><span data-stu-id="1cf59-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="1cf59-124">Jeśli typ środowiska wykonawczego `objectexpression` spełnia kryterium zgodności `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="1cf59-125">W przeciwnym razie `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="1cf59-126">Jeśli `objectexpression` ma wartość null, następnie `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="1cf59-127">`TypeOf` zawsze jest używana z `Is` — słowo kluczowe do konstruowania `TypeOf`... `Is` wyrażenie, lub za pomocą `IsNot` — słowo kluczowe do konstruowania `TypeOf`... `IsNot` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1cf59-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cf59-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="1cf59-128">Example</span></span>  
 <span data-ttu-id="1cf59-129">W poniższym przykładzie użyto `TypeOf`... `Is` wyrażeń, które umożliwiają przetestowanie zgodności typu dwóch obiektów zmienne odwołania z różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="1cf59-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 <span data-ttu-id="1cf59-130">Zmienna `refInteger` ma typ środowiska wykonawczego `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="1cf59-131">Jest to zgodne z `Integer` , ale nie z `Double`.</span><span class="sxs-lookup"><span data-stu-id="1cf59-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="1cf59-132">Zmienna `refForm` ma typ środowiska wykonawczego <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="1cf59-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="1cf59-133">Jest to zgodne z <xref:System.Windows.Forms.Form> , ponieważ jego typ, jest z <xref:System.Windows.Forms.Control> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.Windows.Forms.Control>i <xref:System.ComponentModel.IComponent> ponieważ <xref:System.Windows.Forms.Form> dziedziczy <xref:System.ComponentModel.Component>, który implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="1cf59-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="1cf59-134">Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="1cf59-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf59-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1cf59-135">See also</span></span>
- [<span data-ttu-id="1cf59-136">Is, operator</span><span class="sxs-lookup"><span data-stu-id="1cf59-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1cf59-137">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="1cf59-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="1cf59-138">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cf59-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="1cf59-139">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1cf59-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1cf59-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="1cf59-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1cf59-141">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1cf59-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
