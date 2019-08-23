---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917153"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="090cb-102">IsFalse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="090cb-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="090cb-103">Określa, czy wyrażenie jest `False`.</span><span class="sxs-lookup"><span data-stu-id="090cb-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="090cb-104">Nie można jawnie `IsFalse` wywołać w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z `AndAlso` klauzul.</span><span class="sxs-lookup"><span data-stu-id="090cb-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="090cb-105">W przypadku zdefiniowania klasy lub struktury, a następnie użycia zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="090cb-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="090cb-106">Kompilator traktuje `IsFalse` operatory i `IsTrue` jako pasującą *parę*.</span><span class="sxs-lookup"><span data-stu-id="090cb-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="090cb-107">Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.</span><span class="sxs-lookup"><span data-stu-id="090cb-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="090cb-108">Operator może być przeciążony, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury. `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="090cb-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="090cb-109">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="090cb-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="090cb-110">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="090cb-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="090cb-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="090cb-111">Example</span></span>  
 <span data-ttu-id="090cb-112">Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje `IsFalse` operatorów i. `IsTrue`</span><span class="sxs-lookup"><span data-stu-id="090cb-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="090cb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="090cb-113">See also</span></span>

- [<span data-ttu-id="090cb-114">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="090cb-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="090cb-115">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="090cb-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="090cb-116">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="090cb-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
