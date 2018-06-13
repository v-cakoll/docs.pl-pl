---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603317"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="10ef9-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="10ef9-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="10ef9-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="10ef9-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10ef9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="10ef9-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="10ef9-105">Części</span><span class="sxs-lookup"><span data-stu-id="10ef9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="10ef9-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="10ef9-106">Required.</span></span> <span data-ttu-id="10ef9-107">A `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="10ef9-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="10ef9-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="10ef9-108">Required.</span></span> <span data-ttu-id="10ef9-109">Wszelkie `Object` zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="10ef9-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="10ef9-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="10ef9-110">Required.</span></span> <span data-ttu-id="10ef9-111">Wszelkie `Object` zmiennej lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="10ef9-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="10ef9-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="10ef9-112">Remarks</span></span>  
 <span data-ttu-id="10ef9-113">`IsNot` Operator określa, czy dwa odwołania do obiektów odwoływać się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="10ef9-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="10ef9-114">Porównania wartości nie są jednak wykonać.</span><span class="sxs-lookup"><span data-stu-id="10ef9-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="10ef9-115">Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `False`; Jeśli nie, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="10ef9-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="10ef9-116">`IsNot` jest to odwrotność wzorca `Is` operatora.</span><span class="sxs-lookup"><span data-stu-id="10ef9-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="10ef9-117">Zaletą `IsNot` jest uniknięcie nieodpowiednich składni `Not` i `Is`, które mogą być trudny do odczytania.</span><span class="sxs-lookup"><span data-stu-id="10ef9-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="10ef9-118">Można użyć `Is` i `IsNot` operatory do testowania obiektów zarówno z wczesnym wiązaniem i późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="10ef9-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="10ef9-119">`IsNot` Nie można używać operatora porównywanie wyrażeń zwrócony z `TypeOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="10ef9-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="10ef9-120">Zamiast tego należy użyć `Not` i `Is` operatorów.</span><span class="sxs-lookup"><span data-stu-id="10ef9-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ef9-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="10ef9-121">Example</span></span>  
 <span data-ttu-id="10ef9-122">Poniższy przykład kodu wykorzystuje zarówno `Is` operatora i `IsNot` operatora, aby osiągnąć tego samego porównania.</span><span class="sxs-lookup"><span data-stu-id="10ef9-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="10ef9-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10ef9-123">See Also</span></span>  
 [<span data-ttu-id="10ef9-124">Is, operator</span><span class="sxs-lookup"><span data-stu-id="10ef9-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="10ef9-125">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="10ef9-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="10ef9-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="10ef9-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="10ef9-127">Instrukcje: testowanie, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="10ef9-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
