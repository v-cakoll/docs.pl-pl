---
title: 'Porady: wywoływanie procedury zwracającej wartość (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbaaa5ed17845a7ac8847786fb10111c724015ba
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="566b1-102">Porady: wywoływanie procedury zwracającej wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="566b1-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="566b1-103">A `Function` procedury zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="566b1-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="566b1-104">Należy wywołać go przez dołączenie jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="566b1-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="566b1-105">Aby wywołać procedurę Function w wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="566b1-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="566b1-106">Użyj `Function` taki sam sposób, należy użyć zmiennej Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="566b1-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="566b1-107">Można użyć `Function` wywoływanie procedury, można użyć zmiennej lub stałą w wyrażeniu dowolnego miejsca.</span><span class="sxs-lookup"><span data-stu-id="566b1-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="566b1-108">Po nazwie procedury nawiasami ujmij listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="566b1-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="566b1-109">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="566b1-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="566b1-110">Jednak za pomocą nawiasów ułatwia kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="566b1-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="566b1-111">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="566b1-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="566b1-112">Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="566b1-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="566b1-113">Alternatywnie można przekazać co najmniej jeden z argumentów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="566b1-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="566b1-114">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="566b1-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="566b1-115">Wartość zwracana z procedury uczestniczy w wyrażeniu podobnie jak wartość zmiennej lub czy stała.</span><span class="sxs-lookup"><span data-stu-id="566b1-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="566b1-116">Aby wywołać procedurę Function w instrukcji przypisania</span><span class="sxs-lookup"><span data-stu-id="566b1-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="566b1-117">Użyj `Function` nazwę procedury po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="566b1-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="566b1-118">Po nazwie procedury nawiasami ujmij listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="566b1-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="566b1-119">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="566b1-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="566b1-120">Jednak za pomocą nawiasów ułatwia kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="566b1-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="566b1-121">Umieść listy argumentów w nawiasie rozdzielone przecinkami argumenty.</span><span class="sxs-lookup"><span data-stu-id="566b1-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="566b1-122">Należy podać argumenty w tej samej kolejności, która `Function` procedury definiuje odpowiednie parametry, chyba że przekazaniem ich według nazwy.</span><span class="sxs-lookup"><span data-stu-id="566b1-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="566b1-123">Wartość zwracana z procedury są przechowywane w zmiennej lub właściwości po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="566b1-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="566b1-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="566b1-124">Example</span></span>  
 <span data-ttu-id="566b1-125">Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> można pobrać wartości zmiennej środowiskowej systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="566b1-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="566b1-126">Pierwsze wywołania wiersza `Environ` w wyrażeniu, a drugi wiersz wywołuje ona w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="566b1-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="566b1-127">`Environ` pobiera nazwę zmiennej jako jedynego argumentu.</span><span class="sxs-lookup"><span data-stu-id="566b1-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="566b1-128">Zwraca wartość zmiennej do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="566b1-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="566b1-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="566b1-129">See Also</span></span>  
 [<span data-ttu-id="566b1-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="566b1-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="566b1-131">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="566b1-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="566b1-132">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="566b1-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="566b1-133">Instrukcje: tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="566b1-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="566b1-134">Instrukcje: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="566b1-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="566b1-135">Instrukcje: wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="566b1-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
