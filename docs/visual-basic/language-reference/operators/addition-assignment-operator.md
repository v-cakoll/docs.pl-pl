---
title: += — Operator
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
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372210"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f7542-102">+= — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7542-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="f7542-103">Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7542-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="f7542-104">Można również użyć do łączenia `String` wyrażenia z `String` zmienną lub właściwością i przypisywać wynik do zmiennej lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="f7542-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7542-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7542-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="f7542-106">Części</span><span class="sxs-lookup"><span data-stu-id="f7542-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f7542-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f7542-107">Required.</span></span> <span data-ttu-id="f7542-108">Dowolna wartość liczbowa lub `String` zmienna lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="f7542-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="f7542-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f7542-109">Required.</span></span> <span data-ttu-id="f7542-110">Wszystkie wartości liczbowe lub `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f7542-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7542-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f7542-111">Remarks</span></span>  
 <span data-ttu-id="f7542-112">Element po lewej stronie `+=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy.</span><span class="sxs-lookup"><span data-stu-id="f7542-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f7542-113">Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f7542-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f7542-114">`+=`Operator dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="f7542-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="f7542-115">`+=`Operatora można także użyć do łączenia `String` wyrażenia po prawej stronie ze `String` zmienną lub właściwości po lewej stronie, a następnie przypisywać wynik do zmiennej lub właściwości po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="f7542-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7542-116">Gdy używasz `+=` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów.</span><span class="sxs-lookup"><span data-stu-id="f7542-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="f7542-117">Użyj `&=` operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.</span><span class="sxs-lookup"><span data-stu-id="f7542-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="f7542-118">Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę.</span><span class="sxs-lookup"><span data-stu-id="f7542-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="f7542-119">Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="f7542-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="f7542-120">Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f7542-120">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="f7542-121">Jeśli dozwolone jest semantyka ograniczająca, `+=` operator niejawnie wykonuje szereg konwersji ciągów i liczb, identycznych z tymi wykonywanymi przez `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="f7542-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="f7542-122">Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f7542-122">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f7542-123">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="f7542-123">Overloading</span></span>  
 <span data-ttu-id="f7542-124">`+`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f7542-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f7542-125">Przeciążanie `+` operatora ma wpływ na zachowanie `+=` operatora.</span><span class="sxs-lookup"><span data-stu-id="f7542-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="f7542-126">Jeśli kod korzysta z `+=` klasy lub struktury, która przeciążania `+` , należy poznać jej ponownie zdefiniowane zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f7542-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f7542-127">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f7542-127">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7542-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="f7542-128">Example</span></span>  
 <span data-ttu-id="f7542-129">Poniższy przykład używa operatora, `+=` Aby połączyć wartość jednej zmiennej z inną.</span><span class="sxs-lookup"><span data-stu-id="f7542-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="f7542-130">Pierwsza część używa `+=` ze zmiennymi liczbowymi, aby dodać jedną wartość do innej.</span><span class="sxs-lookup"><span data-stu-id="f7542-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="f7542-131">Druga część używa `+=` ze `String` zmiennymi do łączenia jednej wartości z inną.</span><span class="sxs-lookup"><span data-stu-id="f7542-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="f7542-132">W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f7542-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="f7542-133">Wartość `num1` to teraz 13, a wartość `str1` to teraz "103".</span><span class="sxs-lookup"><span data-stu-id="f7542-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7542-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7542-134">See also</span></span>

- [<span data-ttu-id="f7542-135">+ — Operator</span><span class="sxs-lookup"><span data-stu-id="f7542-135">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="f7542-136">Operatory przypisania</span><span class="sxs-lookup"><span data-stu-id="f7542-136">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="f7542-137">Operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="f7542-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="f7542-138">Concatenation — Operatory</span><span class="sxs-lookup"><span data-stu-id="f7542-138">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="f7542-139">Kolejność wykonywania działań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7542-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="f7542-140">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="f7542-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="f7542-141">Instrukcje</span><span class="sxs-lookup"><span data-stu-id="f7542-141">Statements</span></span>](../../programming-guide/language-features/statements.md)
