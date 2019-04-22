---
title: -= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: be1ff4f10f6b30d8448d2441ee3ad2c1e2f80e2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815904"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="5c432-102">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c432-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="5c432-103">Odejmuje wartość wyrażenia z wartości zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c432-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c432-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c432-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5c432-105">Części</span><span class="sxs-lookup"><span data-stu-id="5c432-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="5c432-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5c432-106">Required.</span></span> <span data-ttu-id="5c432-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="5c432-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="5c432-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5c432-108">Required.</span></span> <span data-ttu-id="5c432-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="5c432-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c432-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c432-110">Remarks</span></span>  
 <span data-ttu-id="5c432-111">Element w lewej części `-=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5c432-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="5c432-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="5c432-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="5c432-113">`-=` Operator najpierw odejmuje wartość wyrażenia (po prawej stronie operatora) z wartości zmiennej lub właściwości (po lewej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="5c432-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="5c432-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="5c432-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5c432-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="5c432-115">Overloading</span></span>  
 <span data-ttu-id="5c432-116">[-— Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5c432-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5c432-117">Przeciążanie `-` operator ma wpływ na zachowanie `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="5c432-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="5c432-118">Jeśli kod używa `-=` dla klasy lub struktury, która przeciążenia `-`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="5c432-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5c432-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5c432-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c432-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c432-120">Example</span></span>  
 <span data-ttu-id="5c432-121">W poniższym przykładzie użyto `-=` operatora, aby odjąć jedną `Integer` zmiennej z innego i przypisz wynik do zmiennej ostatnie.</span><span class="sxs-lookup"><span data-stu-id="5c432-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="5c432-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c432-122">See also</span></span>

- [<span data-ttu-id="5c432-123">-— Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c432-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="5c432-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="5c432-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="5c432-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="5c432-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="5c432-126">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c432-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5c432-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5c432-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5c432-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="5c432-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
