---
title: 'Instrukcje: Sprawdź, czy dwa obiekty są tego samego (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: d13671f284863fa7bf56964c2b9b963c25e8ea52
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977451"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="06559-102">Instrukcje: Sprawdź, czy dwa obiekty są tego samego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06559-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="06559-103">Jeśli masz dwie zmienne odwołujące się do obiektów, można użyć albo `Is` lub `IsNot` operatora i / lub, aby ustalić, czy odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06559-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="06559-104">Aby sprawdzić, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="06559-104">To test whether two objects are the same</span></span>  
  
-   <span data-ttu-id="06559-105">Użyj [operatora Is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwoma zmiennymi argumentami operacji.</span><span class="sxs-lookup"><span data-stu-id="06559-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="06559-106">Możesz chcieć wykonać określone działanie w zależności od tego, czy dwa obiekty odnoszą się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="06559-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="06559-107">W poprzednim przykładzie porównano kontroli `c` względem aktywny formant w formularzu `f`.</span><span class="sxs-lookup"><span data-stu-id="06559-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="06559-108">Jeśli istnieje nie aktywną kontrolkę, lub jeżeli istnieje jeden, ale nie jest tego samego wystąpienia formantu, co `c`, a następnie `If` instrukcja kończy się niepowodzeniem i procedura jest zwracane bez dalszego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="06559-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="06559-109">Czy używać `Is` lub `IsNot` jest kwestią osobistych wygodę dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="06559-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="06559-110">Jeden może być łatwiejsza do odczytania niż ten drugi z danego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="06559-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06559-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="06559-111">See also</span></span>
- [<span data-ttu-id="06559-112">Operatory porównania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="06559-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
