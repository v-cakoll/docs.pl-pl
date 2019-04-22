---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: e07a775eec003a3e488f6909181aed3f742b4b91
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833519"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="e1824-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1824-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="e1824-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1824-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1824-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1824-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="e1824-105">Części</span><span class="sxs-lookup"><span data-stu-id="e1824-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e1824-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e1824-106">Required.</span></span> <span data-ttu-id="e1824-107">A `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="e1824-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="e1824-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e1824-108">Required.</span></span> <span data-ttu-id="e1824-109">Wszelkie `Object` zmiennej lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e1824-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="e1824-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="e1824-110">Required.</span></span> <span data-ttu-id="e1824-111">Wszelkie `Object` zmiennej lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e1824-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1824-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1824-112">Remarks</span></span>  
 <span data-ttu-id="e1824-113">`IsNot` Określa operator, jeśli dwa odwołania do obiektu odnoszą się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="e1824-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="e1824-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="e1824-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="e1824-115">Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `False`; Jeśli nie, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="e1824-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="e1824-116">`IsNot` jest to odwrotność `Is` operatora.</span><span class="sxs-lookup"><span data-stu-id="e1824-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="e1824-117">Zaletą `IsNot` jest uniknięcie niewygodna składni `Not` i `Is`, który może być trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="e1824-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="e1824-118">Możesz użyć `Is` i `IsNot` operatorów, aby przetestować obiekty z wczesnym wiązaniem i z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="e1824-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1824-119">`IsNot` Operator nie może służyć do porównywania zwrócone w wyniku wyrażenia `TypeOf` operatora.</span><span class="sxs-lookup"><span data-stu-id="e1824-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="e1824-120">Zamiast tego należy użyć `Not` i `Is` operatorów.</span><span class="sxs-lookup"><span data-stu-id="e1824-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1824-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e1824-121">Example</span></span>  
 <span data-ttu-id="e1824-122">W poniższym przykładzie kodu użyto obu `Is` operatora i `IsNot` operatora, aby osiągnąć ten sam porównania.</span><span class="sxs-lookup"><span data-stu-id="e1824-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="e1824-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e1824-123">See also</span></span>

- [<span data-ttu-id="e1824-124">Is, operator</span><span class="sxs-lookup"><span data-stu-id="e1824-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="e1824-125">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="e1824-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="e1824-126">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1824-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e1824-127">Instrukcje: Sprawdź, czy dwa obiekty są takie Same</span><span class="sxs-lookup"><span data-stu-id="e1824-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
