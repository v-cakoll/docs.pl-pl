---
title: Is — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="d4897-102">Is — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4897-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="d4897-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4897-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4897-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4897-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="d4897-105">Części</span><span class="sxs-lookup"><span data-stu-id="d4897-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="d4897-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d4897-106">Required.</span></span> <span data-ttu-id="d4897-107">Wszelkie `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="d4897-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="d4897-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d4897-108">Required.</span></span> <span data-ttu-id="d4897-109">Wszelkie `Object` nazwy.</span><span class="sxs-lookup"><span data-stu-id="d4897-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="d4897-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d4897-110">Required.</span></span> <span data-ttu-id="d4897-111">Wszelkie `Object` nazwy.</span><span class="sxs-lookup"><span data-stu-id="d4897-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4897-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4897-112">Remarks</span></span>  
 <span data-ttu-id="d4897-113">`Is` Operator określa, czy dwa odwołania do obiektów odwoływać się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="d4897-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="d4897-114">Porównania wartości nie są jednak wykonać.</span><span class="sxs-lookup"><span data-stu-id="d4897-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="d4897-115">Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `True`; Jeśli nie, `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="d4897-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="d4897-116">`Is` można również używać razem `TypeOf` — słowo kluczowe, aby `TypeOf`... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest niezgodny z typem danych.</span><span class="sxs-lookup"><span data-stu-id="d4897-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4897-117">`Is` — Słowo kluczowe jest również używana w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d4897-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4897-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4897-118">Example</span></span>  
 <span data-ttu-id="d4897-119">W poniższym przykładzie użyto `Is` operatora, aby porównać pary odwołania do obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4897-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="d4897-120">Wyniki są przypisane do `Boolean` wartość reprezentującą informację, czy dwa obiekty są identyczne.</span><span class="sxs-lookup"><span data-stu-id="d4897-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 <span data-ttu-id="d4897-121">Jak pokazano w powyższym przykładzie, można użyć `Is` operatora, aby sprawdzić zarówno z wczesnym wiązaniem i rozpoznanie późnego wiązania obiektów.</span><span class="sxs-lookup"><span data-stu-id="d4897-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4897-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4897-122">See Also</span></span>  
 [<span data-ttu-id="d4897-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="d4897-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [<span data-ttu-id="d4897-124">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="d4897-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="d4897-125">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4897-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="d4897-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4897-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="d4897-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="d4897-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="d4897-128">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="d4897-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
