---
title: -= — Operator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="68b1c-102">-= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68b1c-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="68b1c-103">Odejmuje wartość wyrażenia z wartości zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="68b1c-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68b1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68b1c-104">Syntax</span></span>  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="68b1c-105">Części</span><span class="sxs-lookup"><span data-stu-id="68b1c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="68b1c-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="68b1c-106">Required.</span></span> <span data-ttu-id="68b1c-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="68b1c-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="68b1c-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="68b1c-108">Required.</span></span> <span data-ttu-id="68b1c-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="68b1c-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b1c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68b1c-110">Remarks</span></span>  
 <span data-ttu-id="68b1c-111">Element po lewej stronie `-=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="68b1c-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="68b1c-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="68b1c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="68b1c-113">`-=` Operator najpierw odejmuje wartość wyrażenia (po prawej stronie operatora) z wartością zmiennej lub właściwości (po lewej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="68b1c-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="68b1c-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="68b1c-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="68b1c-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="68b1c-115">Overloading</span></span>  
 <span data-ttu-id="68b1c-116">[-— Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="68b1c-116">The [- Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="68b1c-117">Przeciążanie `-` operator wpływa na działanie `-=` operatora.</span><span class="sxs-lookup"><span data-stu-id="68b1c-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="68b1c-118">Jeśli używa Twój kod `-=` na klasę lub strukturę, która overloads `-`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="68b1c-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="68b1c-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="68b1c-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b1c-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="68b1c-120">Example</span></span>  
 <span data-ttu-id="68b1c-121">W poniższym przykładzie użyto `-=` operator do odjęcia jedną `Integer` zmiennej z innego i przypisz wynik do zmiennej ostatnie.</span><span class="sxs-lookup"><span data-stu-id="68b1c-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="68b1c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68b1c-122">See Also</span></span>  
 [<span data-ttu-id="68b1c-123">-— Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68b1c-123">- Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [<span data-ttu-id="68b1c-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="68b1c-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="68b1c-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="68b1c-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="68b1c-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68b1c-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="68b1c-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="68b1c-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="68b1c-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="68b1c-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
