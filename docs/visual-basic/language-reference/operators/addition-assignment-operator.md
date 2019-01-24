---
title: += — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: cfe987929099fc73ba3af9fe92b5871275c5396e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54617554"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="3178c-102">+= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3178c-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="3178c-103">Dodaje wartość wyrażenia liczbowego wartość liczbową zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3178c-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="3178c-104">Może również służyć do łączenia `String` wyrażenie `String` zmiennej lub właściwości i przypisz wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3178c-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3178c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3178c-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="3178c-106">Części</span><span class="sxs-lookup"><span data-stu-id="3178c-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="3178c-107">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="3178c-107">Required.</span></span> <span data-ttu-id="3178c-108">Wszelkie wartości numeryczne lub `String` zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="3178c-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="3178c-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="3178c-109">Required.</span></span> <span data-ttu-id="3178c-110">Wszelkie wartości numeryczne lub `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3178c-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3178c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3178c-111">Remarks</span></span>  
 <span data-ttu-id="3178c-112">Element w lewej części `+=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3178c-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="3178c-113">Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="3178c-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="3178c-114">`+=` Operator dodaje wartość jego prawej strony do zmiennej lub właściwość po lewej stronie i przypisuje wynik do zmiennej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3178c-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="3178c-115">`+=` Operator może również służyć do łączenia `String` wyrażenie po jego prawej stronie, aby `String` zmiennej lub właściwość po lewej stronie i przypisz wynik do zmiennej lub właściwość po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="3178c-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3178c-116">Kiedy używasz `+=` operatora, może nie można określić, czy dodanie lub ciąg łączenie wystąpi.</span><span class="sxs-lookup"><span data-stu-id="3178c-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="3178c-117">Użyj `&=` operatora łączenia, aby wyeliminować niejednoznaczności i zapewnienie automatycznie dokumentowane kodu.</span><span class="sxs-lookup"><span data-stu-id="3178c-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="3178c-118">Ten operator przypisania niejawnie wykonuje rozszerzenia, ale nie zawężających, jeśli środowisko kompilacji Wymusza ścisłą semantykę.</span><span class="sxs-lookup"><span data-stu-id="3178c-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="3178c-119">Aby uzyskać więcej informacji na temat takiej konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="3178c-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="3178c-120">Aby uzyskać więcej informacji na semantyce ograniczeniami i ograniczające, zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3178c-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="3178c-121">Jeśli mogą ograniczająca semantyki `+=` operator niejawnie wykonuje szereg konwersji ciągu i liczbowe identyczne z tymi wykonywane przez `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="3178c-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="3178c-122">Szczegółowe informacje na temat takiej konwersji, [+ — Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="3178c-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="3178c-123">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="3178c-123">Overloading</span></span>  
 <span data-ttu-id="3178c-124">`+` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="3178c-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="3178c-125">Przeciążanie `+` operator ma wpływ na zachowanie `+=` operatora.</span><span class="sxs-lookup"><span data-stu-id="3178c-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="3178c-126">Jeśli kod używa `+=` dla klasy lub struktury, która przeciążenia `+`, należy zrozumieć zachowanie zmieniony.</span><span class="sxs-lookup"><span data-stu-id="3178c-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="3178c-127">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3178c-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3178c-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="3178c-128">Example</span></span>  
 <span data-ttu-id="3178c-129">W poniższym przykładzie użyto `+=` operatora łączenia wartości jednej zmiennej z inną.</span><span class="sxs-lookup"><span data-stu-id="3178c-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="3178c-130">Pierwsza część używa `+=` z Zmienne liczbowe, aby dodać jedną wartość na inny.</span><span class="sxs-lookup"><span data-stu-id="3178c-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="3178c-131">Druga część używa `+=` z `String` zmienne do łączenia jednej wartości z inną.</span><span class="sxs-lookup"><span data-stu-id="3178c-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="3178c-132">W obu przypadkach wynik jest przypisany do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3178c-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 <span data-ttu-id="3178c-133">Wartość `num1` jest teraz 13 i wartość `str1` jest teraz "103".</span><span class="sxs-lookup"><span data-stu-id="3178c-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3178c-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3178c-134">See also</span></span>
- [<span data-ttu-id="3178c-135">+, operator</span><span class="sxs-lookup"><span data-stu-id="3178c-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="3178c-136">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="3178c-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="3178c-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="3178c-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="3178c-138">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="3178c-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="3178c-139">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3178c-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="3178c-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="3178c-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="3178c-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="3178c-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
