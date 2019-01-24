---
title: '*= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 3aa1d563b9657d4e80425b8c2d29e069ca2ef06a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601886"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4920d-102">\*= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4920d-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="4920d-103">Mnoży wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="4920d-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4920d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4920d-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="4920d-105">Części</span><span class="sxs-lookup"><span data-stu-id="4920d-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4920d-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4920d-106">Required.</span></span> <span data-ttu-id="4920d-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="4920d-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="4920d-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="4920d-108">Required.</span></span> <span data-ttu-id="4920d-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="4920d-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4920d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4920d-110">Remarks</span></span>  
 <span data-ttu-id="4920d-111">Element w lewej części `*=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4920d-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4920d-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4920d-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="4920d-113">`*=` Operator najpierw Mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="4920d-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="4920d-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="4920d-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4920d-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="4920d-115">Overloading</span></span>  
 <span data-ttu-id="4920d-116">[\* — Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="4920d-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4920d-117">Przeciążanie `*` operator ma wpływ na zachowanie `*=` operatora.</span><span class="sxs-lookup"><span data-stu-id="4920d-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="4920d-118">Jeśli kod używa `*=` dla klasy lub struktury, która przeciążenia `*`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="4920d-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4920d-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4920d-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4920d-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="4920d-120">Example</span></span>  
 <span data-ttu-id="4920d-121">W poniższym przykładzie użyto `*=` operatora przez jeden `Integer` zmiennej przez drugi i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="4920d-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4920d-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4920d-122">See also</span></span>
- [<span data-ttu-id="4920d-123">\*, operator</span><span class="sxs-lookup"><span data-stu-id="4920d-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [<span data-ttu-id="4920d-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="4920d-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="4920d-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="4920d-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="4920d-126">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4920d-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4920d-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="4920d-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4920d-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="4920d-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
