---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966936"
---
# <a name="isnot-operator-visual-basic"></a><span data-ttu-id="1ed14-102">IsNot — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ed14-102">IsNot Operator (Visual Basic)</span></span>
<span data-ttu-id="1ed14-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="1ed14-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed14-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ed14-104">Syntax</span></span>  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a><span data-ttu-id="1ed14-105">Części</span><span class="sxs-lookup"><span data-stu-id="1ed14-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="1ed14-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1ed14-106">Required.</span></span> <span data-ttu-id="1ed14-107">`Boolean` Wartość.</span><span class="sxs-lookup"><span data-stu-id="1ed14-107">A `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="1ed14-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1ed14-108">Required.</span></span> <span data-ttu-id="1ed14-109">Dowolna `Object` zmienna lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1ed14-109">Any `Object` variable or expression.</span></span>  
  
 `object2`  
 <span data-ttu-id="1ed14-110">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="1ed14-110">Required.</span></span> <span data-ttu-id="1ed14-111">Dowolna `Object` zmienna lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1ed14-111">Any `Object` variable or expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ed14-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ed14-112">Remarks</span></span>  
 <span data-ttu-id="1ed14-113">Operator `IsNot` określa, czy dwa odwołania do obiektów odwołują się do różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="1ed14-113">The `IsNot` operator determines if two object references refer to different objects.</span></span> <span data-ttu-id="1ed14-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="1ed14-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="1ed14-115">Jeśli `object1` i `False` `result` `result` `True`oba odnoszą się do dokładnie tego samego wystąpienia obiektu, to; jeśli nie, to. `object2`</span><span class="sxs-lookup"><span data-stu-id="1ed14-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `False`; if they do not, `result` is `True`.</span></span>  
  
 <span data-ttu-id="1ed14-116">`IsNot`jest przeciwieństwem `Is` operatora.</span><span class="sxs-lookup"><span data-stu-id="1ed14-116">`IsNot` is the opposite of the `Is` operator.</span></span> <span data-ttu-id="1ed14-117">Zaletą `IsNot` jest to, że można uniknąć niewygodna składni z `Not` i `Is`, co może być trudne do odczytania.</span><span class="sxs-lookup"><span data-stu-id="1ed14-117">The advantage of `IsNot` is that you can avoid awkward syntax with `Not` and `Is`, which can be difficult to read.</span></span>  
  
 <span data-ttu-id="1ed14-118">Operatory `Is` i`IsNot` służą do testowania zarówno obiektów wczesnych, jak i z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="1ed14-118">You can use the `Is` and `IsNot` operators to test both early-bound and late-bound objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ed14-119">Nie można użyć `TypeOf` operatoradoporównaniawyrażeńzwracanych`IsNot` z operatora.</span><span class="sxs-lookup"><span data-stu-id="1ed14-119">The `IsNot` operator cannot be used to compare expressions returned from the `TypeOf` operator.</span></span> <span data-ttu-id="1ed14-120">Zamiast tego należy użyć `Not` operatorów i. `Is`</span><span class="sxs-lookup"><span data-stu-id="1ed14-120">Instead, you must use the `Not` and `Is` operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ed14-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ed14-121">Example</span></span>  
 <span data-ttu-id="1ed14-122">Poniższy przykład kodu używa `Is` operatora `IsNot` i operatora, aby wykonać to samo porównanie.</span><span class="sxs-lookup"><span data-stu-id="1ed14-122">The following code example uses both the `Is` operator and the `IsNot` operator to accomplish the same comparison.</span></span>  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a><span data-ttu-id="1ed14-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ed14-123">See also</span></span>

- [<span data-ttu-id="1ed14-124">Is, operator</span><span class="sxs-lookup"><span data-stu-id="1ed14-124">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="1ed14-125">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="1ed14-125">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="1ed14-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ed14-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1ed14-127">Instrukcje: Sprawdź, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="1ed14-127">How to: Test Whether Two Objects Are the Same</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
