---
title: "Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76f5c19386cce84207f80d217326d2e3babf4e44
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="b7c69-102">Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7c69-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="b7c69-103">Jeśli masz dwie zmienne odwołujące się do obiektów, możesz użyć albo `Is` lub `IsNot` operatora i/lub do określenia, czy odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b7c69-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="b7c69-104">Aby sprawdzić, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="b7c69-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="b7c69-105">Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwie zmienne jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="b7c69-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="b7c69-106">Warto podjąć pewne akcję w zależności od tego, czy dwa obiekty odwoływać się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b7c69-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="b7c69-107">Powyższy przykład porównuje kontroli `c` przed aktywną kontrolkę w formularzu `f`.</span><span class="sxs-lookup"><span data-stu-id="b7c69-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="b7c69-108">Jeśli wystąpi nie aktywny formant, lub jeśli istnieje jeden, ale nie jest to samo wystąpienie formantu jako `c`, a następnie `If` instrukcja nie powiedzie się i procedury zwraca bez dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="b7c69-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="b7c69-109">Określa, czy używasz `Is` lub `IsNot` polega na wygodę osobistych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b7c69-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="b7c69-110">Co może być bardziej czytelny niż w podane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="b7c69-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c69-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7c69-111">See Also</span></span>  
 [<span data-ttu-id="b7c69-112">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b7c69-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
