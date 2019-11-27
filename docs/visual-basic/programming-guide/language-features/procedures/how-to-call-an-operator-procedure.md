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
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="c44cd-102">Porady: wywoływanie procedury operatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c44cd-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="c44cd-103">Wywoływanie procedury operatora przy użyciu symbolu operatora w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="c44cd-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="c44cd-104">W przypadku operatora konwersji należy wywołać [funkcję CType](../../../../visual-basic/language-reference/functions/ctype-function.md) , aby przekonwertować wartość z jednego typu danych na inny.</span><span class="sxs-lookup"><span data-stu-id="c44cd-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="c44cd-105">Procedury operatorów nie są jawnie wywoływane.</span><span class="sxs-lookup"><span data-stu-id="c44cd-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="c44cd-106">Wystarczy użyć operatora lub funkcji `CType` w instrukcji przypisania lub wyrażeniu, tak samo jak zwykle korzystasz z operatora.</span><span class="sxs-lookup"><span data-stu-id="c44cd-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="c44cd-107">Visual Basic wykonuje wywołanie procedury operatora.</span><span class="sxs-lookup"><span data-stu-id="c44cd-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="c44cd-108">Definiowanie operatora w klasie lub strukturze jest również nazywane *przeciążeniem* operatora.</span><span class="sxs-lookup"><span data-stu-id="c44cd-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="c44cd-109">Aby wywołać procedurę operatora</span><span class="sxs-lookup"><span data-stu-id="c44cd-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="c44cd-110">Użyj symbolu operatora w wyrażeniu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="c44cd-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="c44cd-111">Upewnij się, że typy danych argumentów operacji są odpowiednie dla operatora i w prawidłowej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c44cd-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="c44cd-112">Operator uczestniczy w wartości wyrażenia zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="c44cd-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="c44cd-113">Aby wywołać procedurę operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="c44cd-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="c44cd-114">Użyj `CType` wewnątrz wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="c44cd-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="c44cd-115">Upewnij się, że typy danych argumentów operacji są odpowiednie dla konwersji, i w odpowiedniej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c44cd-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="c44cd-116">`CType` wywołuje procedurę operatora konwersji i zwraca przekonwertowaną wartość.</span><span class="sxs-lookup"><span data-stu-id="c44cd-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c44cd-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="c44cd-117">Example</span></span>  
 <span data-ttu-id="c44cd-118">Poniższy przykład tworzy dwie <xref:System.TimeSpan> struktur, dodaje je razem i zapisuje wynik w trzeciej strukturze <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="c44cd-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="c44cd-119">Struktura <xref:System.TimeSpan> definiuje procedury operatora, aby przeciążać kilka standardowych operatorów.</span><span class="sxs-lookup"><span data-stu-id="c44cd-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="c44cd-120">Ponieważ <xref:System.TimeSpan> przeciążać standardowego operatora `+`, poprzedni przykład wywołuje procedurę operatora podczas obliczania wartości `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="c44cd-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="c44cd-121">Aby zapoznać się z przykładem wywoływania procedury operatora konwersacji, zobacz [How to: use a Class, który definiuje operatory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c44cd-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c44cd-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c44cd-122">Compiling the Code</span></span>  
 <span data-ttu-id="c44cd-123">Upewnij się, że używana Klasa lub struktura definiuje operatora, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="c44cd-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c44cd-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c44cd-124">See also</span></span>

- [<span data-ttu-id="c44cd-125">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="c44cd-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c44cd-126">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="c44cd-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="c44cd-127">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="c44cd-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="c44cd-128">Operator, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c44cd-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c44cd-129">Widening</span><span class="sxs-lookup"><span data-stu-id="c44cd-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="c44cd-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="c44cd-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="c44cd-131">Structure, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c44cd-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c44cd-132">Instrukcje: deklarowanie struktury</span><span class="sxs-lookup"><span data-stu-id="c44cd-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="c44cd-133">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="c44cd-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c44cd-134">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="c44cd-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
