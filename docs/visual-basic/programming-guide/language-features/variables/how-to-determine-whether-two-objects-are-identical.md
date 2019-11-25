---
title: 'Porady: określanie, czy dwa obiekty są jednakowe'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348597"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="083d4-102">Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="083d4-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="083d4-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span><span class="sxs-lookup"><span data-stu-id="083d4-103">In Visual Basic, two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="083d4-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span><span class="sxs-lookup"><span data-stu-id="083d4-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 <span data-ttu-id="083d4-105">Visual Basic provides two operators to compare pointers.</span><span class="sxs-lookup"><span data-stu-id="083d4-105">Visual Basic provides two operators to compare pointers.</span></span> <span data-ttu-id="083d4-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span><span class="sxs-lookup"><span data-stu-id="083d4-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="083d4-107">Determining if Two Objects Are Identical</span><span class="sxs-lookup"><span data-stu-id="083d4-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="083d4-108">To determine if two objects are identical</span><span class="sxs-lookup"><span data-stu-id="083d4-108">To determine if two objects are identical</span></span>  
  
1. <span data-ttu-id="083d4-109">Set up a `Boolean` expression to test the two objects.</span><span class="sxs-lookup"><span data-stu-id="083d4-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="083d4-110">In your testing expression, use the `Is` operator with the two objects as operands.</span><span class="sxs-lookup"><span data-stu-id="083d4-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="083d4-111">`Is` returns `True` if the objects point to the same class instance.</span><span class="sxs-lookup"><span data-stu-id="083d4-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="083d4-112">Determining if Two Objects Are Not Identical</span><span class="sxs-lookup"><span data-stu-id="083d4-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="083d4-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="083d4-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="083d4-114">In such a case you can use the `IsNot` operator.</span><span class="sxs-lookup"><span data-stu-id="083d4-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="083d4-115">To determine if two objects are not identical</span><span class="sxs-lookup"><span data-stu-id="083d4-115">To determine if two objects are not identical</span></span>  
  
1. <span data-ttu-id="083d4-116">Set up a `Boolean` expression to test the two objects.</span><span class="sxs-lookup"><span data-stu-id="083d4-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2. <span data-ttu-id="083d4-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span><span class="sxs-lookup"><span data-stu-id="083d4-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="083d4-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span><span class="sxs-lookup"><span data-stu-id="083d4-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="083d4-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="083d4-119">Example</span></span>  
 <span data-ttu-id="083d4-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span><span class="sxs-lookup"><span data-stu-id="083d4-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 <span data-ttu-id="083d4-121">The preceding example displays the following output.</span><span class="sxs-lookup"><span data-stu-id="083d4-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="083d4-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="083d4-122">See also</span></span>

- [<span data-ttu-id="083d4-123">Object, typ danych</span><span class="sxs-lookup"><span data-stu-id="083d4-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="083d4-124">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="083d4-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="083d4-125">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="083d4-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [<span data-ttu-id="083d4-126">Is, operator</span><span class="sxs-lookup"><span data-stu-id="083d4-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="083d4-127">IsNot, operator</span><span class="sxs-lookup"><span data-stu-id="083d4-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="083d4-128">Instrukcje: określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="083d4-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="083d4-129">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="083d4-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
