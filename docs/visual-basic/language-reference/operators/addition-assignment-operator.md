---
title: "+= — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ac8f5679aa90c50c15c33a957cfc75d9ccecde6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c4b9c-102">+= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4b9c-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="c4b9c-103">Dodaje wartość wyrażenia liczbowego wartość liczbowa zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="c4b9c-104">Może również służyć do łączenia `String` wyrażenie `String` zmienna lub właściwość i przypisz wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b9c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4b9c-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c4b9c-106">Części</span><span class="sxs-lookup"><span data-stu-id="c4b9c-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c4b9c-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-107">Required.</span></span> <span data-ttu-id="c4b9c-108">Wszelkie liczbowe lub `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c4b9c-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-109">Required.</span></span> <span data-ttu-id="c4b9c-110">Wszelkie liczbowe lub `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4b9c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4b9c-111">Remarks</span></span>  
 <span data-ttu-id="c4b9c-112">Element po lewej stronie `+=` operator może być zmienną skalarną proste, właściwością lub element tablicy.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c4b9c-113">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c4b9c-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="c4b9c-114">`+=` Operator dodaje wartość jego prawej strony, aby zmienna lub właściwość po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="c4b9c-115">`+=` Operator może także służyć do łączenia `String` wyrażenie jego prawej strony, aby `String` zmienna lub właściwość w lewo i przypisz wynik do zmiennej lub po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4b9c-116">Jeśli używasz `+=` operatora, może nie można ustalić, czy nastąpi dodanie lub ciąg łączenia.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="c4b9c-117">Użyj `&=` operatora łączenia wyeliminować niejednoznaczności oraz zapewnienia automatycznie dokumentowane kodu.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="c4b9c-118">Ten operator przypisania wykonuje niejawnie rozszerzanie, ale nie zawężanie konwersji, jeśli w środowisku kompilacji wymusza semantykę strict.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="c4b9c-119">Aby uzyskać więcej informacji o tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c4b9c-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="c4b9c-120">Aby uzyskać więcej informacji na semantykę ograniczeniami i ograniczająca, zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c4b9c-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="c4b9c-121">Jeśli dozwolone ograniczająca semantyki, `+=` operator niejawnie wykonuje szereg konwersji ciągu i liczbowe identyczne jak wykonywane przez `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="c4b9c-122">Aby uzyskać więcej informacji o tych konwersji, zobacz [operatora +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c4b9c-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c4b9c-123">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="c4b9c-123">Overloading</span></span>  
 <span data-ttu-id="c4b9c-124">`+` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c4b9c-125">Przeciążanie `+` operator wpływa na działanie `+=` operatora.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="c4b9c-126">Jeśli używa Twój kod `+=` na klasę lub strukturę, która overloads `+`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c4b9c-127">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c4b9c-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b9c-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4b9c-128">Example</span></span>  
 <span data-ttu-id="c4b9c-129">W poniższym przykładzie użyto `+=` operatora, aby połączyć z inną wartość jednej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="c4b9c-130">Pierwsza część używa `+=` się liczbowych zmienne Dodaj jedną wartość na inny.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="c4b9c-131">Druga część używa `+=` z `String` zmienne do łączenia jedną wartość na inną.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="c4b9c-132">W obu przypadkach wynik jest przypisany do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="c4b9c-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="c4b9c-133">Wartość `num1` jest teraz 13 i wartość `str1` jest teraz "103".</span><span class="sxs-lookup"><span data-stu-id="c4b9c-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b9c-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4b9c-134">See Also</span></span>  
 [<span data-ttu-id="c4b9c-135">+ — Operator</span><span class="sxs-lookup"><span data-stu-id="c4b9c-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [<span data-ttu-id="c4b9c-136">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="c4b9c-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="c4b9c-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="c4b9c-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [<span data-ttu-id="c4b9c-138">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="c4b9c-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="c4b9c-139">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4b9c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="c4b9c-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="c4b9c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="c4b9c-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="c4b9c-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
