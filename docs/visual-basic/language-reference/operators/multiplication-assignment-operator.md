---
title: "*= — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0a2c638f3faaf20fadb745ef437941ee29d4f6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="84686-102">\*= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84686-102">\*= Operator (Visual Basic)</span></span>
<span data-ttu-id="84686-103">Mnoży wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="84686-103">Multiplies the value of a variable or property by the value of an expression and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84686-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84686-104">Syntax</span></span>  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="84686-105">Części</span><span class="sxs-lookup"><span data-stu-id="84686-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="84686-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="84686-106">Required.</span></span> <span data-ttu-id="84686-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="84686-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="84686-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="84686-108">Required.</span></span> <span data-ttu-id="84686-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="84686-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84686-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84686-110">Remarks</span></span>  
 <span data-ttu-id="84686-111">Element po lewej stronie `*=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="84686-111">The element on the left side of the `*=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="84686-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="84686-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="84686-113">`*=` Operator najpierw Mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora).</span><span class="sxs-lookup"><span data-stu-id="84686-113">The `*=` operator first multiplies the value of the expression (on the right-hand side of the operator) by the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="84686-114">Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="84686-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="84686-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="84686-115">Overloading</span></span>  
 <span data-ttu-id="84686-116">[\* — Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="84686-116">The [\* Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="84686-117">Przeciążanie `*` operator wpływa na działanie `*=` operatora.</span><span class="sxs-lookup"><span data-stu-id="84686-117">Overloading the `*` operator affects the behavior of the `*=` operator.</span></span> <span data-ttu-id="84686-118">Jeśli używa Twój kod `*=` na klasę lub strukturę, która overloads `*`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="84686-118">If your code uses `*=` on a class or structure that overloads `*`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="84686-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="84686-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="84686-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="84686-120">Example</span></span>  
 <span data-ttu-id="84686-121">W poniższym przykładzie użyto `*=` operatora, aby pomnożyć jedną `Integer` zmiennej sekundę i przypisz wynik do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="84686-121">The following example uses the `*=` operator to multiply one `Integer` variable by a second and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="84686-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="84686-122">See Also</span></span>  
 [<span data-ttu-id="84686-123">\* — Operator</span><span class="sxs-lookup"><span data-stu-id="84686-123">\* Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-operator.md)  
 [<span data-ttu-id="84686-124">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="84686-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="84686-125">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="84686-125">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="84686-126">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84686-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="84686-127">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="84686-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="84686-128">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="84686-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
