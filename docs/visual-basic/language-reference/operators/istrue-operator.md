---
title: IsTrue — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: bf81384b0cecfd1ee3d438e4463949381279a181
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254882"
---
# <a name="istrue-operator-visual-basic"></a><span data-ttu-id="5d90f-102">IsTrue — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d90f-102">IsTrue Operator (Visual Basic)</span></span>
<span data-ttu-id="5d90f-103">Określa, czy wyrażenie jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5d90f-103">Determines whether an expression is `True`.</span></span>  
  
 <span data-ttu-id="5d90f-104">Nie można wywołać `IsTrue` jawnie w kodzie, ale Visual Basic kompilatora służy do generowania kodu z `OrElse` klauzul.</span><span class="sxs-lookup"><span data-stu-id="5d90f-104">You cannot call `IsTrue` explicitly in your code, but the Visual Basic compiler can use it to generate code from `OrElse` clauses.</span></span> <span data-ttu-id="5d90f-105">Jeśli zdefiniowano klasy lub struktury, a następnie użyć zmiennej tego typu w `OrElse` klauzuli, należy zdefiniować `IsTrue` dla tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5d90f-105">If you define a class or structure and then use a variable of that type in an `OrElse` clause, you must define `IsTrue` on that class or structure.</span></span>  
  
 <span data-ttu-id="5d90f-106">Kompilator traktuje `IsTrue` i `IsFalse` operatorów jako *dopasowane pary*.</span><span class="sxs-lookup"><span data-stu-id="5d90f-106">The compiler considers the `IsTrue` and `IsFalse` operators as a *matched pair*.</span></span> <span data-ttu-id="5d90f-107">Oznacza to, że jeśli zdefiniujesz jednego z nich, musisz również zdefiniować innego.</span><span class="sxs-lookup"><span data-stu-id="5d90f-107">This means that if you define one of them, you must also define the other one.</span></span>  
  
## <a name="compiler-use-of-istrue"></a><span data-ttu-id="5d90f-108">Używanie kompilatora IsTrue</span><span class="sxs-lookup"><span data-stu-id="5d90f-108">Compiler Use of IsTrue</span></span>  
 <span data-ttu-id="5d90f-109">Po zdefiniowaniu klasy lub struktury, można użyć zmiennej tego typu w `For`, `If`, `Else If`, lub `While` instrukcji lub `When` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="5d90f-109">When you have defined a class or structure, you can use a variable of that type in a `For`, `If`, `Else If`, or `While` statement, or in a `When` clause.</span></span> <span data-ttu-id="5d90f-110">Jeśli to zrobisz, kompilator wymaga operatora, który konwertuje danego typu w `Boolean` wartość, aby ją przetestować warunku.</span><span class="sxs-lookup"><span data-stu-id="5d90f-110">If you do this, the compiler requires an operator that converts your type into a `Boolean` value so it can test a condition.</span></span> <span data-ttu-id="5d90f-111">Wyszukuje odpowiedniego operatora w następującej kolejności:</span><span class="sxs-lookup"><span data-stu-id="5d90f-111">It searches for a suitable operator in the following order:</span></span>  
  
1.  <span data-ttu-id="5d90f-112">Operatora konwersji rozszerzającej od klasy lub struktury do `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5d90f-112">A widening conversion operator from your class or structure to `Boolean`.</span></span>  
  
2.  <span data-ttu-id="5d90f-113">Operatora konwersji rozszerzającej od klasy lub struktury do `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="5d90f-113">A widening conversion operator from your class or structure to `Boolean?`.</span></span>  
  
3.  <span data-ttu-id="5d90f-114">`IsTrue` Operator dla swojej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5d90f-114">The `IsTrue` operator on your class or structure.</span></span>  
  
4.  <span data-ttu-id="5d90f-115">Konwersja zawężająca do `Boolean?` nie wymaga konwersji `Boolean` do `Boolean?`.</span><span class="sxs-lookup"><span data-stu-id="5d90f-115">A narrowing conversion to `Boolean?` that does not involve a conversion from `Boolean` to `Boolean?`.</span></span>  
  
5.  <span data-ttu-id="5d90f-116">Operatora konwersji zawężającej od klasy lub struktury do `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5d90f-116">A narrowing conversion operator from your class or structure to `Boolean`.</span></span>  
  
 <span data-ttu-id="5d90f-117">Jeśli nie zdefiniowano żadnych konwersji na `Boolean` lub `IsTrue` operatora, kompilator sygnalizuje błąd.</span><span class="sxs-lookup"><span data-stu-id="5d90f-117">If you have not defined any conversion to `Boolean` or an `IsTrue` operator, the compiler signals an error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d90f-118">`IsTrue` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie podczas jej argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5d90f-118">The `IsTrue` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure.</span></span> <span data-ttu-id="5d90f-119">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5d90f-119">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5d90f-120">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5d90f-120">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d90f-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d90f-121">Example</span></span>  
 <span data-ttu-id="5d90f-122">Poniższy przykład kodu przedstawia zarys to struktura, która zawiera definicje dla `IsFalse` i `IsTrue` operatorów.</span><span class="sxs-lookup"><span data-stu-id="5d90f-122">The following code example defines the outline of a structure that includes definitions for the `IsFalse` and `IsTrue` operators.</span></span>  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5d90f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d90f-123">See Also</span></span>  
 [<span data-ttu-id="5d90f-124">IsFalse, operator</span><span class="sxs-lookup"><span data-stu-id="5d90f-124">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)  
 [<span data-ttu-id="5d90f-125">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="5d90f-125">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="5d90f-126">OrElse, operator</span><span class="sxs-lookup"><span data-stu-id="5d90f-126">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)
