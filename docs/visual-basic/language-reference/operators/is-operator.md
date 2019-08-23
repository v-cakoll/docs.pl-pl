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
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917216"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="e3a33-102">Is — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3a33-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="e3a33-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="e3a33-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3a33-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3a33-104">Syntax</span></span>  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="e3a33-105">Części</span><span class="sxs-lookup"><span data-stu-id="e3a33-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e3a33-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e3a33-106">Required.</span></span> <span data-ttu-id="e3a33-107">Dowolna `Boolean` wartość.</span><span class="sxs-lookup"><span data-stu-id="e3a33-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="e3a33-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e3a33-108">Required.</span></span> <span data-ttu-id="e3a33-109">Dowolna `Object` nazwa.</span><span class="sxs-lookup"><span data-stu-id="e3a33-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="e3a33-110">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="e3a33-110">Required.</span></span> <span data-ttu-id="e3a33-111">Dowolna `Object` nazwa.</span><span class="sxs-lookup"><span data-stu-id="e3a33-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3a33-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3a33-112">Remarks</span></span>  
 <span data-ttu-id="e3a33-113">`Is` Operator określa, czy dwa odwołania do obiektów odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3a33-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="e3a33-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="e3a33-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="e3a33-115">Jeśli `object1` i `True` `result` `result` `False`oba odnoszą się do dokładnie tego samego wystąpienia obiektu, to; jeśli nie, to. `object2`</span><span class="sxs-lookup"><span data-stu-id="e3a33-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="e3a33-116">`Is`można go również użyć ze słowem kluczowym `TypeOf` , `TypeOf`aby utworzyć... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest zgodna z typem danych.</span><span class="sxs-lookup"><span data-stu-id="e3a33-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3a33-117">`Is` Słowo kluczowe jest również używane w [SELECT... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3a33-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3a33-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3a33-118">Example</span></span>  
 <span data-ttu-id="e3a33-119">Poniższy przykład używa `Is` operatora do porównywania par odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="e3a33-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="e3a33-120">Wyniki są przypisane do `Boolean` wartości reprezentującej, czy dwa obiekty są identyczne.</span><span class="sxs-lookup"><span data-stu-id="e3a33-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="e3a33-121">Jak pokazano w powyższym przykładzie, można użyć `Is` operatora do przetestowania zarówno obiektów wczesnych, jak i późnych powiązań.</span><span class="sxs-lookup"><span data-stu-id="e3a33-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3a33-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3a33-122">See also</span></span>

- [<span data-ttu-id="e3a33-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="e3a33-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="e3a33-124">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="e3a33-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="e3a33-125">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a33-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="e3a33-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3a33-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="e3a33-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="e3a33-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="e3a33-128">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e3a33-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
