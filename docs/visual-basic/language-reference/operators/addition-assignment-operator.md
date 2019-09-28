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
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591647"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="431d5-102">+= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="431d5-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="431d5-103">Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="431d5-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="431d5-104">Można również użyć do łączenia wyrażenia `String` z zmienną lub właściwością `String` i przypisywać wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="431d5-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="431d5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="431d5-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="431d5-106">Części</span><span class="sxs-lookup"><span data-stu-id="431d5-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="431d5-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="431d5-107">Required.</span></span> <span data-ttu-id="431d5-108">Każda zmienna lub właściwość o wartości liczbowej lub `String`.</span><span class="sxs-lookup"><span data-stu-id="431d5-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="431d5-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="431d5-109">Required.</span></span> <span data-ttu-id="431d5-110">Dowolne wyrażenie liczbowe lub `String`.</span><span class="sxs-lookup"><span data-stu-id="431d5-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="431d5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="431d5-111">Remarks</span></span>  
 <span data-ttu-id="431d5-112">Element po lewej stronie operatora `+=` może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="431d5-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="431d5-113">Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="431d5-114">Operator `+=` dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="431d5-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="431d5-115">Operatora `+=` można także użyć do łączenia wyrażenia `String` po prawej stronie ze zmienną `String` lub właściwością po lewej stronie i przypisywać wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="431d5-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="431d5-116">Gdy używasz operatora `+=`, możesz nie być w stanie określić, czy zostanie wykonane Dodawanie lub łączenie ciągów.</span><span class="sxs-lookup"><span data-stu-id="431d5-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="431d5-117">Użyj operatora `&=` do łączenia, aby wyeliminować niejednoznaczność i wprowadzić kod do samoobsługowego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="431d5-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="431d5-118">Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę.</span><span class="sxs-lookup"><span data-stu-id="431d5-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="431d5-119">Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="431d5-120">Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="431d5-121">Jeśli dozwolone są semantyki ograniczającej, operator `+=` niejawnie wykonuje szereg konwersji ciągów i liczb identycznych z tymi wykonywanymi przez operator `+`.</span><span class="sxs-lookup"><span data-stu-id="431d5-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="431d5-122">Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="431d5-123">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="431d5-123">Overloading</span></span>  
 <span data-ttu-id="431d5-124">Operator `+` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="431d5-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="431d5-125">Przeciążanie operatora `+` wpływa na zachowanie operatora `+=`.</span><span class="sxs-lookup"><span data-stu-id="431d5-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="431d5-126">Jeśli kod używa `+=` na klasie lub strukturze, która przeciąża `+`, należy zrozumieć jego ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="431d5-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="431d5-127">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="431d5-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="431d5-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="431d5-128">Example</span></span>  
 <span data-ttu-id="431d5-129">Poniższy przykład używa operatora `+=` do łączenia wartości jednej zmiennej z inną.</span><span class="sxs-lookup"><span data-stu-id="431d5-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="431d5-130">Pierwsza część używa `+=` z zmiennymi numerycznymi w celu dodania jednej wartości do innej.</span><span class="sxs-lookup"><span data-stu-id="431d5-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="431d5-131">Druga część używa `+=` ze zmiennymi `String` do łączenia jednej wartości z inną.</span><span class="sxs-lookup"><span data-stu-id="431d5-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="431d5-132">W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="431d5-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="431d5-133">Wartość `num1` to teraz 13, a wartość `str1` to teraz "103".</span><span class="sxs-lookup"><span data-stu-id="431d5-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="431d5-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="431d5-134">See also</span></span>

- [<span data-ttu-id="431d5-135">+, operator</span><span class="sxs-lookup"><span data-stu-id="431d5-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="431d5-136">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="431d5-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="431d5-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="431d5-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="431d5-138">Operatory łączenia</span><span class="sxs-lookup"><span data-stu-id="431d5-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="431d5-139">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="431d5-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="431d5-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="431d5-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="431d5-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="431d5-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
