---
title: IsFalse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 9f25c406038486224c2c4708c86ef86889c44c15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818491"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="2df17-102">IsFalse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2df17-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="2df17-103">Określa, czy wyrażenie jest `False`.</span><span class="sxs-lookup"><span data-stu-id="2df17-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="2df17-104">Nie można wywołać `IsFalse` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `AndAlso` klauzul.</span><span class="sxs-lookup"><span data-stu-id="2df17-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="2df17-105">Jeśli zdefiniowano klasy lub struktury, a następnie użyć zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2df17-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="2df17-106">Kompilator traktuje `IsFalse` i `IsTrue` operatorów jako *dopasowane pary*.</span><span class="sxs-lookup"><span data-stu-id="2df17-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="2df17-107">Oznacza to, że jeśli zdefiniujesz jednego z nich, musisz również zdefiniować innego.</span><span class="sxs-lookup"><span data-stu-id="2df17-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2df17-108">`IsFalse` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="2df17-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="2df17-109">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="2df17-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2df17-110">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2df17-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2df17-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="2df17-111">Example</span></span>  
 <span data-ttu-id="2df17-112">Poniższy przykład kodu przedstawia zarys to struktura, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="2df17-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="2df17-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2df17-113">See also</span></span>

- [<span data-ttu-id="2df17-114">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="2df17-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="2df17-115">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="2df17-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="2df17-116">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="2df17-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
