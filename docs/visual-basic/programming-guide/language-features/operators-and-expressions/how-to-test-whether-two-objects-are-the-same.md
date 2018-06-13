---
title: 'Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 005c91e6f4ec556a7e1bf255b47c8276a5d3d185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647608"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="63b84-102">Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63b84-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="63b84-103">Jeśli masz dwie zmienne odwołujące się do obiektów, możesz użyć albo `Is` lub `IsNot` operatora i/lub do określenia, czy odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="63b84-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="63b84-104">Aby sprawdzić, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="63b84-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="63b84-105">Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwie zmienne jako argumentów.</span><span class="sxs-lookup"><span data-stu-id="63b84-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-test-whether-two-objects-are-the-same_1.vb)]  
  
 <span data-ttu-id="63b84-106">Warto podjąć pewne akcję w zależności od tego, czy dwa obiekty odwoływać się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="63b84-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="63b84-107">Powyższy przykład porównuje kontroli `c` przed aktywną kontrolkę w formularzu `f`.</span><span class="sxs-lookup"><span data-stu-id="63b84-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="63b84-108">Jeśli wystąpi nie aktywny formant, lub jeśli istnieje jeden, ale nie jest to samo wystąpienie formantu jako `c`, a następnie `If` instrukcja nie powiedzie się i procedury zwraca bez dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="63b84-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="63b84-109">Określa, czy używasz `Is` lub `IsNot` polega na wygodę osobistych użytkownika.</span><span class="sxs-lookup"><span data-stu-id="63b84-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="63b84-110">Co może być bardziej czytelny niż w podane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="63b84-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b84-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63b84-111">See Also</span></span>  
 [<span data-ttu-id="63b84-112">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63b84-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
