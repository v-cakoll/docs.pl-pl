---
title: '\=Operator'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a><span data-ttu-id="24dbb-102">\\= — Operator</span><span class="sxs-lookup"><span data-stu-id="24dbb-102">\\= Operator</span></span>
<span data-ttu-id="24dbb-103">Dzieli wartość zmiennej lub właściwość przez wartość wyrażenia i przypisuje całkowitą wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="24dbb-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24dbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24dbb-104">Syntax</span></span>  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="24dbb-105">Części</span><span class="sxs-lookup"><span data-stu-id="24dbb-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="24dbb-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="24dbb-106">Required.</span></span> <span data-ttu-id="24dbb-107">Zmienna numeryczna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="24dbb-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="24dbb-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="24dbb-108">Required.</span></span> <span data-ttu-id="24dbb-109">Dowolne wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="24dbb-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24dbb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24dbb-110">Remarks</span></span>  
 <span data-ttu-id="24dbb-111">Element po lewej stronie `\=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="24dbb-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="24dbb-112">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="24dbb-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="24dbb-113">`\=` Operator dzieli wartość zmiennej lub właściwość po lewej stronie przez wartość jego prawej stronie i przypisuje wynik całkowitą zmienna lub właściwość po lewej stronie</span><span class="sxs-lookup"><span data-stu-id="24dbb-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="24dbb-114">Aby uzyskać więcej informacji na dzielenie liczby całkowitej, zobacz [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="24dbb-114">For further information on integer division, see [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="24dbb-115">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="24dbb-115">Overloading</span></span>  
 <span data-ttu-id="24dbb-116">`\` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24dbb-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="24dbb-117">Przeciążanie `\` operator wpływa na działanie `\=` operatora.</span><span class="sxs-lookup"><span data-stu-id="24dbb-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="24dbb-118">Jeśli używa Twój kod `\=` na klasę lub strukturę, która overloads `\`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="24dbb-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="24dbb-119">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="24dbb-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24dbb-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="24dbb-120">Example</span></span>  
 <span data-ttu-id="24dbb-121">W poniższym przykładzie użyto `\=` operatora, aby podzielić jedną `Integer` zmiennej sekundę i Przypisz liczbę całkowitą wyniku do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="24dbb-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="24dbb-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24dbb-122">See Also</span></span>  
 [<span data-ttu-id="24dbb-123">\ — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24dbb-123">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [<span data-ttu-id="24dbb-124">/ = — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24dbb-124">/= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [<span data-ttu-id="24dbb-125">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="24dbb-125">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="24dbb-126">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="24dbb-126">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="24dbb-127">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24dbb-127">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="24dbb-128">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="24dbb-128">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="24dbb-129">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="24dbb-129">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
