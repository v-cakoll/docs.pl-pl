---
title: 'Porady: wywoływanie procedury operatora (Visual Basic)'
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
ms.openlocfilehash: b1dc4477daa4ceb9dfc6a9a6ab3f041e68011acd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649971"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="29893-102">Porady: wywoływanie procedury operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29893-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="29893-103">Za pomocą symbol operatora w wyrażeniu jest wywoływanie procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="29893-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="29893-104">W przypadku operatora konwersji, należy wywołać [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) można przekonwertować wartości z jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="29893-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="29893-105">Procedury operatorów nie zostanie jawnie wywołana.</span><span class="sxs-lookup"><span data-stu-id="29893-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="29893-106">Po prostu użyć operatora, lub `CType` funkcji w instrukcji przypisania lub wyrażenie, tak samo zwykle użycie operatora.</span><span class="sxs-lookup"><span data-stu-id="29893-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="29893-107">Visual Basic sprawia, że wywołanie procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="29893-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="29893-108">Definiowanie operatora w klasie lub strukturze jest również nazywany *przeładowanie* operatora.</span><span class="sxs-lookup"><span data-stu-id="29893-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="29893-109">Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="29893-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="29893-110">Symbol operatora należy używać w wyrażeniach w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="29893-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="29893-111">Upewnij się, że typy danych argumenty operacji są odpowiednie dla operatora i we właściwej kolejności.</span><span class="sxs-lookup"><span data-stu-id="29893-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="29893-112">Operator przyczynia się do wartości wyrażenia zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="29893-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="29893-113">Wywoływanie procedury operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="29893-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="29893-114">Użyj `CType` wewnątrz wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="29893-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="29893-115">Upewnij się, że typy danych argumenty operacji są odpowiednie do konwersji, a w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="29893-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="29893-116">`CType` wywołuje procedurę operatora konwersji i zwraca wartość przekonwertowana.</span><span class="sxs-lookup"><span data-stu-id="29893-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29893-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="29893-117">Example</span></span>  
 <span data-ttu-id="29893-118">Poniższy przykład tworzy dwa <xref:System.TimeSpan> struktury, dodaje je ze sobą i zapisuje wynik w innej <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="29893-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="29893-119"><xref:System.TimeSpan> Struktury definiuje operator procedury przeciążenia kilka standardowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="29893-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="29893-120">Ponieważ <xref:System.TimeSpan> overloads standardowego `+` operatora, poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="29893-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="29893-121">Przykład wywoływanie procedury operatora konwersacji, zobacz [porady: używanie klasy tego definiuje operatory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="29893-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="29893-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="29893-122">Compiling the Code</span></span>  
 <span data-ttu-id="29893-123">Upewnij się, że klasy lub struktury, którego używasz definiuje operator, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="29893-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29893-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29893-124">See Also</span></span>  
 [<span data-ttu-id="29893-125">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="29893-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="29893-126">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="29893-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="29893-127">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="29893-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="29893-128">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29893-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="29893-129">Widening</span><span class="sxs-lookup"><span data-stu-id="29893-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="29893-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="29893-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="29893-131">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="29893-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="29893-132">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="29893-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="29893-133">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="29893-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="29893-134">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="29893-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
