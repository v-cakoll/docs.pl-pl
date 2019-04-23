---
title: 'Instrukcje: Wywoływanie procedury zwracającej wartość (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59333889"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="0f738-102">Instrukcje: Wywoływanie procedury zwracającej wartość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f738-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="0f738-103">A `Function` procedury zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0f738-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="0f738-104">Zostanie ona wywołana przez dołączenie jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="0f738-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="0f738-105">Aby wywołać procedurę funkcji w wyrażeniu</span><span class="sxs-lookup"><span data-stu-id="0f738-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="0f738-106">Użyj `Function` procedury nazwij ten sam sposób, należy użyć zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0f738-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="0f738-107">Możesz użyć `Function` wywoływania gdziekolwiek w wyrażeniu można użyć zmiennej lub stała.</span><span class="sxs-lookup"><span data-stu-id="0f738-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="0f738-108">Postępuj zgodnie z nazwą procedury należy umieścić na liście argumentów za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0f738-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0f738-109">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0f738-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="0f738-110">Jednak przy użyciu nawiasów sprawia, że Twój kod łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="0f738-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="0f738-111">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0f738-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0f738-112">Należy podać argumenty w tej samej kolejności, `Function` procedura określa odpowiednich parametrów.</span><span class="sxs-lookup"><span data-stu-id="0f738-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="0f738-113">Możesz też przekazać jeden lub więcej argumentów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="0f738-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="0f738-114">Aby uzyskać więcej informacji, zobacz [przekazywanie argumentów według pozycji i według nazwy](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="0f738-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="0f738-115">Wartość zwracana z procedury uczestniczy w wyrażeniu, podobnie jak wartość zmiennej lub będzie stałą.</span><span class="sxs-lookup"><span data-stu-id="0f738-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="0f738-116">Aby wywołać procedurę Function w instrukcji przypisania</span><span class="sxs-lookup"><span data-stu-id="0f738-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="0f738-117">Użyj `Function` nazwy procedury po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="0f738-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="0f738-118">Postępuj zgodnie z nazwą procedury należy umieścić na liście argumentów za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0f738-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="0f738-119">Jeśli nie ma żadnych argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0f738-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="0f738-120">Jednak przy użyciu nawiasów sprawia, że Twój kod łatwiejsza do odczytania.</span><span class="sxs-lookup"><span data-stu-id="0f738-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="0f738-121">Argumenty należy umieścić na liście argumentów w nawiasie rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="0f738-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="0f738-122">Należy podać argumenty w tej samej kolejności, `Function` procedura określa odpowiednie parametry, chyba że przekazujesz je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="0f738-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="0f738-123">Wartość zwracana z procedury są przechowywane w zmiennej lub właściwość po lewej stronie w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="0f738-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f738-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f738-124">Example</span></span>  
 <span data-ttu-id="0f738-125">Poniższy przykład wywołuje Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> można pobrać wartości zmiennej środowiskowej systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="0f738-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="0f738-126">Pierwszy wiersz wywołania `Environ` w wyrażeniach, a drugi wiersz wywołuje on w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="0f738-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="0f738-127">`Environ` pobiera nazwę zmiennej, jako jedyny argument.</span><span class="sxs-lookup"><span data-stu-id="0f738-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="0f738-128">Zwraca wartość zmiennej do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="0f738-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="0f738-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f738-129">See also</span></span>

- [<span data-ttu-id="0f738-130">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="0f738-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="0f738-131">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="0f738-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="0f738-132">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="0f738-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="0f738-133">Instrukcje: Utwórz procedurę, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="0f738-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="0f738-134">Instrukcje: Zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="0f738-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="0f738-135">Instrukcje: Wywoływanie procedury, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="0f738-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
