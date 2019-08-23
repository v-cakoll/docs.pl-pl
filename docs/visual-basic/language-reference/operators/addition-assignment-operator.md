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
ms.openlocfilehash: f615df50643912beb12eb89d80b922fc30a3e6df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944471"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2cbfe-102">+= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cbfe-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="2cbfe-103">Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="2cbfe-104">Można również użyć do łączenia `String` wyrażenia `String` z zmienną lub właściwością i przypisywać wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cbfe-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cbfe-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2cbfe-106">Części</span><span class="sxs-lookup"><span data-stu-id="2cbfe-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2cbfe-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-107">Required.</span></span> <span data-ttu-id="2cbfe-108">Dowolna wartość `String` liczbowa lub zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2cbfe-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-109">Required.</span></span> <span data-ttu-id="2cbfe-110">Wszystkie wartości liczbowe `String` lub wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cbfe-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cbfe-111">Remarks</span></span>  
 <span data-ttu-id="2cbfe-112">Element po lewej stronie `+=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2cbfe-113">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2cbfe-114">`+=` Operator dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="2cbfe-115">Operatora można także użyć do łączenia `String` wyrażenia `String` po prawej stronie ze zmienną lub właściwości po lewej stronie, a następnie przypisywać wynik do zmiennej lub właściwości po lewej stronie. `+=`</span><span class="sxs-lookup"><span data-stu-id="2cbfe-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cbfe-116">Gdy używasz `+=` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="2cbfe-117">`&=` Użyj operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="2cbfe-118">Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="2cbfe-119">Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="2cbfe-120">Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="2cbfe-121">Jeśli dozwolone jest semantyka ograniczająca, `+=` operator niejawnie wykonuje szereg konwersji ciągów i liczb, identycznych z tymi wykonywanymi `+` przez operatora.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="2cbfe-122">Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2cbfe-123">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="2cbfe-123">Overloading</span></span>  
 <span data-ttu-id="2cbfe-124">Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `+`</span><span class="sxs-lookup"><span data-stu-id="2cbfe-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2cbfe-125">Przeciążanie `+` operatora ma wpływ na zachowanie `+=` operatora.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="2cbfe-126">Jeśli kod korzysta `+=` z klasy lub struktury, która przeciążania `+`, należy poznać jej ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2cbfe-127">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2cbfe-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cbfe-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="2cbfe-128">Example</span></span>  
 <span data-ttu-id="2cbfe-129">Poniższy przykład używa operatora, `+=` aby połączyć wartość jednej zmiennej z inną.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="2cbfe-130">Pierwsza część używa `+=` ze zmiennymi liczbowymi, aby dodać jedną wartość do innej.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="2cbfe-131">Druga część używa `+=` ze `String` zmiennymi do łączenia jednej wartości z inną.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="2cbfe-132">W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2cbfe-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2cbfe-133">Wartość `num1` to teraz 13, a `str1` wartość to teraz "103".</span><span class="sxs-lookup"><span data-stu-id="2cbfe-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cbfe-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cbfe-134">See also</span></span>

- [<span data-ttu-id="2cbfe-135">+, operator</span><span class="sxs-lookup"><span data-stu-id="2cbfe-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="2cbfe-136">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="2cbfe-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="2cbfe-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="2cbfe-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="2cbfe-138">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="2cbfe-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="2cbfe-139">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2cbfe-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2cbfe-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="2cbfe-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2cbfe-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="2cbfe-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
