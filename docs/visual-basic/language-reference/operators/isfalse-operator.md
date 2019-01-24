---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: ec8d7bcd2f4ca3fb1c74f4edcf6ec8af78fd144d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740439"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="59a26-102">IsFalse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59a26-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="59a26-103">Określa, czy wyrażenie jest `False`.</span><span class="sxs-lookup"><span data-stu-id="59a26-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="59a26-104">Nie można wywołać `IsFalse` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `AndAlso` klauzul.</span><span class="sxs-lookup"><span data-stu-id="59a26-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="59a26-105">Jeśli zdefiniowano klasy lub struktury, a następnie użyć zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="59a26-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="59a26-106">Kompilator traktuje `IsFalse` i `IsTrue` operatorów jako *dopasowane pary*.</span><span class="sxs-lookup"><span data-stu-id="59a26-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="59a26-107">Oznacza to, że jeśli zdefiniujesz jednego z nich, musisz również zdefiniować innego.</span><span class="sxs-lookup"><span data-stu-id="59a26-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="59a26-108">`IsFalse` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="59a26-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="59a26-109">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="59a26-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="59a26-110">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="59a26-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="59a26-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="59a26-111">Example</span></span>  
 <span data-ttu-id="59a26-112">Poniższy przykład kodu przedstawia zarys to struktura, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="59a26-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="59a26-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59a26-113">See also</span></span>
- [<span data-ttu-id="59a26-114">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="59a26-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="59a26-115">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="59a26-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="59a26-116">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="59a26-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
