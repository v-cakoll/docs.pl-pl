---
title: Is — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349533"
---
# <a name="is-operator-visual-basic"></a><span data-ttu-id="be7eb-102">Is — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be7eb-102">Is Operator (Visual Basic)</span></span>
<span data-ttu-id="be7eb-103">Porównuje dwie zmienne odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="be7eb-103">Compares two object reference variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be7eb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be7eb-104">Syntax</span></span>  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a><span data-ttu-id="be7eb-105">Części</span><span class="sxs-lookup"><span data-stu-id="be7eb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="be7eb-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="be7eb-106">Required.</span></span> <span data-ttu-id="be7eb-107">Dowolna wartość `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="be7eb-107">Any `Boolean` value.</span></span>  
  
 `object1`  
 <span data-ttu-id="be7eb-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="be7eb-108">Required.</span></span> <span data-ttu-id="be7eb-109">Dowolna nazwa `Object`.</span><span class="sxs-lookup"><span data-stu-id="be7eb-109">Any `Object` name.</span></span>  
  
 `object2`  
 <span data-ttu-id="be7eb-110">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="be7eb-110">Required.</span></span> <span data-ttu-id="be7eb-111">Dowolna nazwa `Object`.</span><span class="sxs-lookup"><span data-stu-id="be7eb-111">Any `Object` name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be7eb-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be7eb-112">Remarks</span></span>  
 <span data-ttu-id="be7eb-113">Operator `Is` określa, czy dwa odwołania do obiektów odwołują się do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="be7eb-113">The `Is` operator determines if two object references refer to the same object.</span></span> <span data-ttu-id="be7eb-114">Jednak nie wykonuje porównania wartości.</span><span class="sxs-lookup"><span data-stu-id="be7eb-114">However, it does not perform value comparisons.</span></span> <span data-ttu-id="be7eb-115">Jeśli `object1` i `object2` oba odnoszą się do tego samego wystąpienia obiektu, `result` jest `True`; Jeśli tak nie jest, `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="be7eb-115">If `object1` and `object2` both refer to the exact same object instance, `result` is `True`; if they do not, `result` is `False`.</span></span>  
  
 <span data-ttu-id="be7eb-116">`Is` można również użyć ze słowem kluczowym `TypeOf`, aby utworzyć wyrażenie `TypeOf`...`Is`, które sprawdza, czy zmienna obiektu jest zgodna z typem danych.</span><span class="sxs-lookup"><span data-stu-id="be7eb-116">`Is` can also be used with the `TypeOf` keyword to make a `TypeOf`...`Is` expression, which tests whether an object variable is compatible with a data type.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be7eb-117">Słowo kluczowe `Is` jest również używane w [SELECT... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="be7eb-117">The `Is` keyword is also used in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be7eb-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="be7eb-118">Example</span></span>  
 <span data-ttu-id="be7eb-119">Poniższy przykład używa operatora `Is` do porównywania par odwołań do obiektów.</span><span class="sxs-lookup"><span data-stu-id="be7eb-119">The following example uses the `Is` operator to compare pairs of object references.</span></span> <span data-ttu-id="be7eb-120">Wyniki są przypisane do `Boolean` wartości, co oznacza, czy dwa obiekty są identyczne.</span><span class="sxs-lookup"><span data-stu-id="be7eb-120">The results are assigned to a `Boolean` value representing whether the two objects are identical.</span></span>  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 <span data-ttu-id="be7eb-121">Jak pokazano w powyższym przykładzie, można użyć operatora `Is` do przetestowania zarówno obiektów wczesnych, jak i późnych powiązań.</span><span class="sxs-lookup"><span data-stu-id="be7eb-121">As the preceding example demonstrates, you can use the `Is` operator to test both early bound and late bound objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be7eb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be7eb-122">See also</span></span>

- [<span data-ttu-id="be7eb-123">TypeOf, operator</span><span class="sxs-lookup"><span data-stu-id="be7eb-123">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="be7eb-124">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="be7eb-124">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="be7eb-125">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be7eb-125">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="be7eb-126">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="be7eb-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="be7eb-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="be7eb-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="be7eb-128">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="be7eb-128">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
