---
title: 'Porady: wywoływanie procedury operatora'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340245"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="630b1-102">Porady: wywoływanie procedury operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="630b1-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="630b1-103">You call an operator procedure by using the operator symbol in an expression.</span><span class="sxs-lookup"><span data-stu-id="630b1-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="630b1-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span><span class="sxs-lookup"><span data-stu-id="630b1-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="630b1-105">You do not call operator procedures explicitly.</span><span class="sxs-lookup"><span data-stu-id="630b1-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="630b1-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span><span class="sxs-lookup"><span data-stu-id="630b1-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="630b1-107">Visual Basic makes the call to the operator procedure.</span><span class="sxs-lookup"><span data-stu-id="630b1-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="630b1-108">Defining an operator on a class or structure is also called *overloading* the operator.</span><span class="sxs-lookup"><span data-stu-id="630b1-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="630b1-109">To call an operator procedure</span><span class="sxs-lookup"><span data-stu-id="630b1-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="630b1-110">Use the operator symbol in an expression in the ordinary way.</span><span class="sxs-lookup"><span data-stu-id="630b1-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="630b1-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span><span class="sxs-lookup"><span data-stu-id="630b1-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="630b1-112">The operator contributes to the value of the expression as expected.</span><span class="sxs-lookup"><span data-stu-id="630b1-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="630b1-113">To call a conversion operator procedure</span><span class="sxs-lookup"><span data-stu-id="630b1-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="630b1-114">Use `CType` inside an expression.</span><span class="sxs-lookup"><span data-stu-id="630b1-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="630b1-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span><span class="sxs-lookup"><span data-stu-id="630b1-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="630b1-116">`CType` calls the conversion operator procedure and returns the converted value.</span><span class="sxs-lookup"><span data-stu-id="630b1-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="630b1-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="630b1-117">Example</span></span>  
 <span data-ttu-id="630b1-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span><span class="sxs-lookup"><span data-stu-id="630b1-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="630b1-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span><span class="sxs-lookup"><span data-stu-id="630b1-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="630b1-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="630b1-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="630b1-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="630b1-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="630b1-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="630b1-122">Compiling the Code</span></span>  
 <span data-ttu-id="630b1-123">Be sure the class or structure you are using defines the operator you want to use.</span><span class="sxs-lookup"><span data-stu-id="630b1-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630b1-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="630b1-124">See also</span></span>

- [<span data-ttu-id="630b1-125">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="630b1-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="630b1-126">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="630b1-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="630b1-127">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="630b1-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="630b1-128">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="630b1-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="630b1-129">Widening</span><span class="sxs-lookup"><span data-stu-id="630b1-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="630b1-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="630b1-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="630b1-131">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="630b1-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="630b1-132">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="630b1-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="630b1-133">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="630b1-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="630b1-134">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="630b1-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
