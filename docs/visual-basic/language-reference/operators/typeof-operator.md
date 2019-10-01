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
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701285"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="afa5d-102">TypeOf — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="afa5d-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="afa5d-103">Sprawdza, czy typ środowiska uruchomieniowego wyniku wyrażenia jest zgodny z typem określonego typu.</span><span class="sxs-lookup"><span data-stu-id="afa5d-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="afa5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afa5d-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="afa5d-105">Części</span><span class="sxs-lookup"><span data-stu-id="afa5d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="afa5d-106">Zwracać.</span><span class="sxs-lookup"><span data-stu-id="afa5d-106">Returned.</span></span> <span data-ttu-id="afa5d-107">Wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="afa5d-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="afa5d-108">Required.</span></span> <span data-ttu-id="afa5d-109">Dowolne wyrażenie, którego wynikiem jest typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="afa5d-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="afa5d-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="afa5d-110">Required.</span></span> <span data-ttu-id="afa5d-111">Dowolna nazwa typu danych.</span><span class="sxs-lookup"><span data-stu-id="afa5d-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afa5d-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afa5d-112">Remarks</span></span>  
 <span data-ttu-id="afa5d-113">Operator `TypeOf` Określa, czy typ czasu wykonywania `objectexpression` jest zgodny z `typename`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="afa5d-114">Zgodność zależy od kategorii typu `typename`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="afa5d-115">W poniższej tabeli przedstawiono sposób określania zgodności.</span><span class="sxs-lookup"><span data-stu-id="afa5d-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="afa5d-116">Kategoria typu `typename`</span><span class="sxs-lookup"><span data-stu-id="afa5d-116">Type category of `typename`</span></span>|<span data-ttu-id="afa5d-117">Kryterium zgodności</span><span class="sxs-lookup"><span data-stu-id="afa5d-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="afa5d-118">Class</span><span class="sxs-lookup"><span data-stu-id="afa5d-118">Class</span></span>|<span data-ttu-id="afa5d-119">`objectexpression` jest typu `typename` lub dziedziczy po `typename`</span><span class="sxs-lookup"><span data-stu-id="afa5d-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="afa5d-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="afa5d-120">Structure</span></span>|<span data-ttu-id="afa5d-121">`objectexpression` jest typu `typename`</span><span class="sxs-lookup"><span data-stu-id="afa5d-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="afa5d-122">Interface</span><span class="sxs-lookup"><span data-stu-id="afa5d-122">Interface</span></span>|<span data-ttu-id="afa5d-123">`objectexpression` implementuje `typename` lub dziedziczy z klasy implementującej `typename`</span><span class="sxs-lookup"><span data-stu-id="afa5d-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="afa5d-124">Jeśli typ czasu wykonywania `objectexpression` spełnia kryteria zgodności, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="afa5d-125">W przeciwnym razie `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="afa5d-126">Jeśli `objectexpression` ma wartość null, wówczas `TypeOf`... `Is` zwraca `False`, i... `IsNot` zwraca `True`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="afa5d-127">`TypeOf` jest zawsze używana ze słowem kluczowym `Is` do konstruowania wyrażenia `TypeOf`... `Is` lub za pomocą słowa kluczowego `IsNot`, aby utworzyć `TypeOf`... `IsNot` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="afa5d-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="afa5d-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="afa5d-128">Example</span></span>  
 <span data-ttu-id="afa5d-129">W poniższym przykładzie są stosowane wyrażenia `TypeOf`... `Is` do testowania zgodności typów dwóch zmiennych odwołań do obiektów z różnymi typami danych.</span><span class="sxs-lookup"><span data-stu-id="afa5d-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="afa5d-130">Zmienna `refInteger` ma typ czasu wykonywania `Integer`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="afa5d-131">Jest on zgodny z `Integer`, ale nie z `Double`.</span><span class="sxs-lookup"><span data-stu-id="afa5d-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="afa5d-132">Zmienna `refForm` ma typ czasu wykonywania <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="afa5d-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="afa5d-133">Jest on zgodny z <xref:System.Windows.Forms.Form>, ponieważ jest to jego typ z <xref:System.Windows.Forms.Control>, ponieważ <xref:System.Windows.Forms.Form> dziedziczy z <xref:System.Windows.Forms.Control> i z <xref:System.ComponentModel.IComponent>, ponieważ <xref:System.ComponentModel.Component> dziedziczy z @no__t-, który implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="afa5d-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="afa5d-134">Jednak `refForm` nie jest zgodny z <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="afa5d-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afa5d-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afa5d-135">See also</span></span>

- [<span data-ttu-id="afa5d-136">Is, operator</span><span class="sxs-lookup"><span data-stu-id="afa5d-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="afa5d-137">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="afa5d-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="afa5d-138">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afa5d-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="afa5d-139">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afa5d-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="afa5d-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="afa5d-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="afa5d-141">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="afa5d-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
