---
title: ^= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 73705df376284edd9d8f20baaf4306c41b1d3943
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699730"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="64b2a-102">^= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64b2a-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="64b2a-103">Podnosi wartość zmiennej lub właściwości do potęgi równej wyrażenia i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="64b2a-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64b2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="64b2a-104">Syntax</span></span>  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="64b2a-105">Części</span><span class="sxs-lookup"><span data-stu-id="64b2a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="64b2a-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="64b2a-106">Required.</span></span> <span data-ttu-id="64b2a-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="64b2a-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="64b2a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="64b2a-108">Required.</span></span> <span data-ttu-id="64b2a-109">Dowolne wyrażenie numeryczne.</span><span class="sxs-lookup"><span data-stu-id="64b2a-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64b2a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64b2a-110">Remarks</span></span>  
 <span data-ttu-id="64b2a-111">Element w lewej części `^=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="64b2a-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="64b2a-112">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="64b2a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="64b2a-113">`^=` Operator najpierw podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi równej wartości wyrażenia (po prawej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="64b2a-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="64b2a-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="64b2a-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="64b2a-115">Visual Basic zawsze wykonuje potęgowania w [typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="64b2a-115">Visual Basic always performs exponentiation in the [Double Data Type](../../../visual-basic/language-reference/data-types/double-data-type.md).</span></span> <span data-ttu-id="64b2a-116">Operandy dowolnego innego typu są konwertowane na `Double`, a wynik jest zawsze `Double`.</span><span class="sxs-lookup"><span data-stu-id="64b2a-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="64b2a-117">Wartość `expression` może być ułamkową ujemne lub obu.</span><span class="sxs-lookup"><span data-stu-id="64b2a-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="64b2a-118">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="64b2a-118">Overloading</span></span>  
 <span data-ttu-id="64b2a-119">[^ — Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="64b2a-119">The [^ Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="64b2a-120">Przeciążanie `^` operator ma wpływ na zachowanie `^=` operatora.</span><span class="sxs-lookup"><span data-stu-id="64b2a-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="64b2a-121">Jeśli kod używa `^=` dla klasy lub struktury, która przeciążenia `^`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="64b2a-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="64b2a-122">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="64b2a-122">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64b2a-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="64b2a-123">Example</span></span>  
 <span data-ttu-id="64b2a-124">W poniższym przykładzie użyto `^=` operator, aby zwiększyć wartość jednego `Integer` zmiennej do potęgi równej Druga zmienna i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="64b2a-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="64b2a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64b2a-125">See also</span></span>
- [<span data-ttu-id="64b2a-126">^, operator</span><span class="sxs-lookup"><span data-stu-id="64b2a-126">^ Operator</span></span>](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [<span data-ttu-id="64b2a-127">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="64b2a-127">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="64b2a-128">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="64b2a-128">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="64b2a-129">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64b2a-129">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="64b2a-130">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="64b2a-130">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="64b2a-131">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="64b2a-131">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
