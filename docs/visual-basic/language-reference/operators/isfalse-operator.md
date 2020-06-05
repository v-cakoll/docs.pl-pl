---
title: IsFalse, operator
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 7c5ad5fa0b72370eeb19fbaced88807570467552
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370677"
---
# <a name="isfalse-operator-visual-basic"></a><span data-ttu-id="98293-102">IsFalse — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98293-102">IsFalse Operator (Visual Basic)</span></span>
<span data-ttu-id="98293-103">Określa, czy wyrażenie jest `False` .</span><span class="sxs-lookup"><span data-stu-id="98293-103">Determines whether an expression is `False`.</span></span>  
  
 <span data-ttu-id="98293-104">Nie można `IsFalse` jawnie wywołać w kodzie, ale kompilator Visual Basic może użyć go do wygenerowania kodu z `AndAlso` klauzul.</span><span class="sxs-lookup"><span data-stu-id="98293-104">You cannot call `IsFalse` explicitly in your code, but the Visual Basic compiler can use it to generate code from `AndAlso` clauses.</span></span> <span data-ttu-id="98293-105">W przypadku zdefiniowania klasy lub struktury, a następnie użycia zmiennej tego typu w `AndAlso` klauzuli, należy zdefiniować `IsFalse` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="98293-105">If you define a class or structure and then use a variable of that type in an `AndAlso` clause, you must define `IsFalse` on that class or structure.</span></span>  
  
 <span data-ttu-id="98293-106">Kompilator traktuje `IsFalse` Operatory i `IsTrue` jako *pasującą parę*.</span><span class="sxs-lookup"><span data-stu-id="98293-106">The compiler considers the `IsFalse` and `IsTrue` operators as a *matched pair*.</span></span> <span data-ttu-id="98293-107">Oznacza to, że w przypadku zdefiniowania jednego z nich należy również zdefiniować drugi.</span><span class="sxs-lookup"><span data-stu-id="98293-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98293-108">`IsFalse`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może zmienić jego zachowanie, gdy jego operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="98293-108">The `IsFalse` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="98293-109">Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="98293-109">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="98293-110">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="98293-110">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98293-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="98293-111">Example</span></span>  
 <span data-ttu-id="98293-112">Poniższy przykład kodu definiuje kontur struktury, która zawiera definicje `IsFalse` `IsTrue` operatorów i.</span><span class="sxs-lookup"><span data-stu-id="98293-112">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a><span data-ttu-id="98293-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="98293-113">See also</span></span>

- [<span data-ttu-id="98293-114">IsTrue, operator</span><span class="sxs-lookup"><span data-stu-id="98293-114">IsTrue Operator</span></span>](istrue-operator.md)
- [<span data-ttu-id="98293-115">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="98293-115">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="98293-116">AndAlso, operator</span><span class="sxs-lookup"><span data-stu-id="98293-116">AndAlso Operator</span></span>](andalso-operator.md)
