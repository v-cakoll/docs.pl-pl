---
title: "IsFalse — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d85fc51a75f82c65cf226b8239a8eee6585bd18a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="be929-102">IsFalse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be929-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="be929-103">Określa, czy wyrażenie jest `False`.</span><span class="sxs-lookup"><span data-stu-id="be929-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="be929-104">Nie można wywołać `IsFalse` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `AndAlso` klauzul.</span><span class="sxs-lookup"><span data-stu-id="be929-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="be929-105">Jeśli można zdefiniować klasy lub struktury, a następnie użyć zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="be929-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="be929-106">Kompilator uwzględnia `IsFalse` i `IsTrue` operatorów jako *dopasowane pary*.</span><span class="sxs-lookup"><span data-stu-id="be929-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="be929-107">Oznacza to, że jeśli jedna z nich zostanie zdefiniowana, należy także zdefiniować innego.</span><span class="sxs-lookup"><span data-stu-id="be929-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="be929-108">`IsFalse` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowania podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="be929-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="be929-109">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="be929-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="be929-110">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="be929-110">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be929-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="be929-111">Example</span></span>  
 <span data-ttu-id="be929-112">Poniższy przykładowy kod definiuje konturu struktury, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="be929-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isfalse-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="be929-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be929-113">See Also</span></span>  
 [<span data-ttu-id="be929-114">IsTrue — Operator</span><span class="sxs-lookup"><span data-stu-id="be929-114">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)  
 [<span data-ttu-id="be929-115">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="be929-115">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="be929-116">AndAlso — Operator</span><span class="sxs-lookup"><span data-stu-id="be929-116">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
