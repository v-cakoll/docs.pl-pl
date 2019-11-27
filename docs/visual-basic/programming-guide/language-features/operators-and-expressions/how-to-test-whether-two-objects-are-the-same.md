---
title: 'Porady: testowanie, czy dwa obiekty są takie same'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343620"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="a8bb2-102">Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8bb2-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="a8bb2-103">Jeśli istnieją dwie zmienne odwołujące się do obiektów, można użyć operatora `Is` lub `IsNot` lub obu, aby określić, czy odwołują się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="a8bb2-104">Aby sprawdzić, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="a8bb2-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="a8bb2-105">Użyj [operatora is](../../../../visual-basic/language-reference/operators/is-operator.md) lub [operatora IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) z dwiema zmiennymi jako operandami.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-105">Use the [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) or the [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="a8bb2-106">Możesz chcieć wykonać określoną akcję w zależności od tego, czy dwa obiekty odwołują się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="a8bb2-107">Poprzedni przykład porównuje `c` formantu z aktywną kontrolką w `f`formularza.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="a8bb2-108">Jeśli nie ma aktywnej kontrolki lub jeśli istnieje, ale nie jest to samo wystąpienie kontrolki co `c`, instrukcja `If` kończy się niepowodzeniem, a procedura zwróci wartość bez dalszej obróbki.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="a8bb2-109">Bez względu na to, czy korzystasz z `Is`, czy `IsNot`, to osobista wygoda użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="a8bb2-110">Jeden z nich może być łatwiejszy do odczytania w danym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a8bb2-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8bb2-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8bb2-111">See also</span></span>

- [<span data-ttu-id="a8bb2-112">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a8bb2-112">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
