---
title: "Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02083a93e63fe799f529776f777ca877d2d138b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a><span data-ttu-id="bb68d-102">Porady: określanie, czy dwa obiekty są jednakowe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb68d-102">How to: Determine Whether Two Objects Are Identical (Visual Basic)</span></span>
<span data-ttu-id="bb68d-103">W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], dwóch odwołań do zmiennych są traktowane jako identyczne, jeśli ich wskaźniki są takie same, to znaczy, jeśli obie zmienne wskazać to samo wystąpienie klasy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bb68d-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], two variable references are considered identical if their pointers are the same, that is, if both variables point to the same class instance in memory.</span></span> <span data-ttu-id="bb68d-104">Na przykład w aplikacji formularzy systemu Windows, można porównanie, aby określić, czy bieżące wystąpienie (`Me`) jest taka sama jak konkretnego wystąpienia, takich jak `Form2`.</span><span class="sxs-lookup"><span data-stu-id="bb68d-104">For example, in a Windows Forms application, you might want to make a comparison to determine whether the current instance (`Me`) is the same as a particular instance, such as `Form2`.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="bb68d-105">udostępnia dwa operatory porównanie wskaźników.</span><span class="sxs-lookup"><span data-stu-id="bb68d-105"> provides two operators to compare pointers.</span></span> <span data-ttu-id="bb68d-106">[Operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) zwraca `True` Jeśli obiekty są identyczne i [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) zwraca `True` Jeśli nie są one.</span><span class="sxs-lookup"><span data-stu-id="bb68d-106">The [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) returns `True` if the objects are identical, and the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) returns `True` if they are not.</span></span>  
  
## <a name="determining-if-two-objects-are-identical"></a><span data-ttu-id="bb68d-107">Określanie, czy dwa obiekty są jednakowe</span><span class="sxs-lookup"><span data-stu-id="bb68d-107">Determining if Two Objects Are Identical</span></span>  
  
#### <a name="to-determine-if-two-objects-are-identical"></a><span data-ttu-id="bb68d-108">Aby sprawdzić, czy dwa obiekty są identyczne</span><span class="sxs-lookup"><span data-stu-id="bb68d-108">To determine if two objects are identical</span></span>  
  
1.  <span data-ttu-id="bb68d-109">Konfigurowanie `Boolean` wyrażenia do testowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="bb68d-109">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="bb68d-110">W wyrażeniu testowania należy używać `Is` operatora z tymi dwoma obiektami jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb68d-110">In your testing expression, use the `Is` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="bb68d-111">`Is`Zwraca `True` Jeśli punkt obiekty do tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="bb68d-111">`Is` returns `True` if the objects point to the same class instance.</span></span>  
  
## <a name="determining-if-two-objects-are-not-identical"></a><span data-ttu-id="bb68d-112">Określanie, czy dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="bb68d-112">Determining if Two Objects Are Not Identical</span></span>  
 <span data-ttu-id="bb68d-113">Czasami chcesz wykonać akcję, jeśli dwa obiekty nie są identyczne, i można go połączyć nieodpowiednich `Not` i `Is`, na przykład `If Not obj1 Is obj2`.</span><span class="sxs-lookup"><span data-stu-id="bb68d-113">Sometimes you want to perform an action if the two objects are not identical, and it can be awkward to combine `Not` and `Is`, for example `If Not obj1 Is obj2`.</span></span> <span data-ttu-id="bb68d-114">W takim przypadku można użyć `IsNot` operatora.</span><span class="sxs-lookup"><span data-stu-id="bb68d-114">In such a case you can use the `IsNot` operator.</span></span>  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a><span data-ttu-id="bb68d-115">Aby określić, czy dwa obiekty nie są identyczne</span><span class="sxs-lookup"><span data-stu-id="bb68d-115">To determine if two objects are not identical</span></span>  
  
1.  <span data-ttu-id="bb68d-116">Konfigurowanie `Boolean` wyrażenia do testowania dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="bb68d-116">Set up a `Boolean` expression to test the two objects.</span></span>  
  
2.  <span data-ttu-id="bb68d-117">W wyrażeniu testowania należy używać `IsNot` operatora z tymi dwoma obiektami jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="bb68d-117">In your testing expression, use the `IsNot` operator with the two objects as operands.</span></span>  
  
     <span data-ttu-id="bb68d-118">`IsNot`Zwraca `True` Jeśli obiekty nie mogą wskazywać tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="bb68d-118">`IsNot` returns `True` if the objects do not point to the same class instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb68d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb68d-119">Example</span></span>  
 <span data-ttu-id="bb68d-120">Poniższy przykład testów pary `Object` zmienne, aby zobaczyć, jeśli one wskazywać tego samego wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="bb68d-120">The following example tests pairs of `Object` variables to see if they point to the same class instance.</span></span>  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 <span data-ttu-id="bb68d-121">W poprzednim przykładzie przedstawiono następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="bb68d-121">The preceding example displays the following output.</span></span>  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a><span data-ttu-id="bb68d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb68d-122">See Also</span></span>  
 [<span data-ttu-id="bb68d-123">Object — typ danych</span><span class="sxs-lookup"><span data-stu-id="bb68d-123">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="bb68d-124">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="bb68d-124">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="bb68d-125">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="bb68d-125">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [<span data-ttu-id="bb68d-126">Is — Operator</span><span class="sxs-lookup"><span data-stu-id="bb68d-126">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="bb68d-127">IsNot — Operator</span><span class="sxs-lookup"><span data-stu-id="bb68d-127">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="bb68d-128">Porady: Określanie, czy dwa obiekty są powiązane</span><span class="sxs-lookup"><span data-stu-id="bb68d-128">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="bb68d-129">Me, My, MyBase i MyClass</span><span class="sxs-lookup"><span data-stu-id="bb68d-129">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
