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
ms.openlocfilehash: b215225dbc2d8c0d2bdfe2206e5d4a4f1faa6d0c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403424"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a><span data-ttu-id="92e4b-102">Porady: testowanie, czy dwa obiekty są takie same (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92e4b-102">How to: Test Whether Two Objects Are the Same (Visual Basic)</span></span>
<span data-ttu-id="92e4b-103">Jeśli istnieją dwie zmienne odwołujące się do obiektów, można użyć `Is` operatora OR lub `IsNot` obu, aby określić, czy odwołują się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="92e4b-103">If you have two variables that refer to objects, you can use either the `Is` or `IsNot` operator, or both, to determine whether they refer to the same instance.</span></span>  
  
### <a name="to-test-whether-two-objects-are-the-same"></a><span data-ttu-id="92e4b-104">Aby sprawdzić, czy dwa obiekty są takie same</span><span class="sxs-lookup"><span data-stu-id="92e4b-104">To test whether two objects are the same</span></span>  
  
- <span data-ttu-id="92e4b-105">Użyj [operatora is](../../../language-reference/operators/is-operator.md) lub [operatora IsNot](../../../language-reference/operators/isnot-operator.md) z dwiema zmiennymi jako operandami.</span><span class="sxs-lookup"><span data-stu-id="92e4b-105">Use the [Is Operator](../../../language-reference/operators/is-operator.md) or the [IsNot Operator](../../../language-reference/operators/isnot-operator.md) with the two variables as operands.</span></span>  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 <span data-ttu-id="92e4b-106">Możesz chcieć wykonać określoną akcję w zależności od tego, czy dwa obiekty odwołują się do tego samego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="92e4b-106">You might want to take a certain action depending on whether two objects refer to the same instance.</span></span> <span data-ttu-id="92e4b-107">Poprzedni przykład porównuje kontrolę `c` z aktywną kontrolką w formularzu `f` .</span><span class="sxs-lookup"><span data-stu-id="92e4b-107">The preceding example compares control `c` against the active control on form `f`.</span></span> <span data-ttu-id="92e4b-108">Jeśli nie ma aktywnej kontrolki lub jeśli istnieje, ale nie jest to samo wystąpienie formantu co `c` , `If` instrukcja kończy się niepowodzeniem, a procedura zwróci wartość bez dalszej obróbki.</span><span class="sxs-lookup"><span data-stu-id="92e4b-108">If there is no active control, or if there is one but it is not the same control instance as `c`, then the `If` statement fails and the procedure returns without further processing.</span></span>  
  
 <span data-ttu-id="92e4b-109">Bez względu na to, czy korzystasz z możliwości użytkownika, czy `Is` też `IsNot` jest to osobna wygoda.</span><span class="sxs-lookup"><span data-stu-id="92e4b-109">Whether you use `Is` or `IsNot` is a matter of personal convenience to you.</span></span> <span data-ttu-id="92e4b-110">Jeden z nich może być łatwiejszy do odczytania w danym wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="92e4b-110">One might be easier to read than the other in a given expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92e4b-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92e4b-111">See also</span></span>

- [<span data-ttu-id="92e4b-112">Operatory porównania w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="92e4b-112">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
