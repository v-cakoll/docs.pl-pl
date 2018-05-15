---
title: Procedury funkcji (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 887c930cb757b012542c97d64a57a62882a2eed3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="e6b50-102">Procedury funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b50-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="e6b50-103">A `Function` procedura jest serię instrukcji języka Visual Basic otoczony `Function` i `End Function` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="e6b50-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="e6b50-104">`Function` Procedury wykonuje zadanie, a następnie zwraca sterowania do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e6b50-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="e6b50-105">Zwraca kontroli, również zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e6b50-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="e6b50-106">Zawsze procedura jest wywoływana, jego instrukcje uruchamiania, zaczynając od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończąc pierwszy `End Function`, `Exit Function`, lub `Return` Napotkano instrukcję.</span><span class="sxs-lookup"><span data-stu-id="e6b50-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="e6b50-107">Można zdefiniować `Function` procedury w module, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="e6b50-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="e6b50-108">Jest `Public` domyślnie oznacza wywołać ją z dowolnego miejsca w aplikacji, który ma dostęp do modułu, klasy lub struktury ona zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="e6b50-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="e6b50-109">A `Function` może potrwać argumenty, takie jak stałe, zmiennych lub wyrażeń, które są przekazywane do niej przez kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="e6b50-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="e6b50-110">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="e6b50-110">Declaration Syntax</span></span>  
 <span data-ttu-id="e6b50-111">Składnia deklaracji `Function` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e6b50-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="e6b50-112">*Modyfikatory* można określić poziom dostępu i informacji dotyczących przeładowanie, zastępowanie udostępniania i przesłanianie.</span><span class="sxs-lookup"><span data-stu-id="e6b50-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="e6b50-113">Aby uzyskać więcej informacji, zobacz [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e6b50-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="e6b50-114">Deklarowanie tak samo jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e6b50-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="e6b50-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="e6b50-115">Data Type</span></span>  
 <span data-ttu-id="e6b50-116">Każdy `Function` procedura ma typ danych, jest tylko każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e6b50-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="e6b50-117">Ten typ danych jest określony przez `As` w klauzuli `Function` instrukcji która określa typ danych wartości, funkcja zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="e6b50-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="e6b50-118">Następujące przykładowe deklaracje ilustrację.</span><span class="sxs-lookup"><span data-stu-id="e6b50-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="e6b50-119">Aby uzyskać więcej informacji, zobacz "Części" w [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e6b50-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="e6b50-120">Zwracanie wartości</span><span class="sxs-lookup"><span data-stu-id="e6b50-120">Returning Values</span></span>  
 <span data-ttu-id="e6b50-121">Wartość `Function` procedury wysyła Wstecz, aby kod wywołujący nosi nazwę swojej zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="e6b50-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="e6b50-122">Procedura zwraca tę wartość w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="e6b50-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="e6b50-123">Używa `Return` instrukcji, aby określić zwracanej wartości i zwraca kontrolować natychmiast do wywoływania programu.</span><span class="sxs-lookup"><span data-stu-id="e6b50-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="e6b50-124">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e6b50-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="e6b50-125">Przypisuje wartość do jego własnej nazwy funkcji w jedną lub więcej instrukcji procedury.</span><span class="sxs-lookup"><span data-stu-id="e6b50-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="e6b50-126">Formant nie powróci do wywoływania programu do `Exit Function` lub `End Function` instrukcja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="e6b50-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="e6b50-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="e6b50-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="e6b50-128">Zaletą przypisywanie wartości zwracanej nazwa funkcji jest, że formant nie zwraca z procedury aż do napotkania `Exit Function` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e6b50-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="e6b50-129">Dzięki temu można przypisać wartości wstępny i dostosowanie go później, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="e6b50-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="e6b50-130">Aby uzyskać więcej informacji na temat zwracanie wartości, zobacz [instrukcji Function](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e6b50-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="e6b50-131">Informacje dotyczące zwracania tablic, zobacz [tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="e6b50-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="e6b50-132">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="e6b50-132">Calling Syntax</span></span>  
 <span data-ttu-id="e6b50-133">Wywołuje się `Function` procedury w tym jego nazwa i argumenty albo po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="e6b50-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="e6b50-134">Należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias.</span><span class="sxs-lookup"><span data-stu-id="e6b50-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="e6b50-135">Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="e6b50-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="e6b50-136">Składnia wywołania `Function` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="e6b50-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="e6b50-137">*l-wartością*`=`*functionname* `[(` *listaargumentów*  `)]`</span><span class="sxs-lookup"><span data-stu-id="e6b50-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="e6b50-138">`If ((` *FunctionName* `[(` *listaargumentów* `)] / 3) <=` *wyrażenia*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="e6b50-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="e6b50-139">Podczas wywoływania `Function` procedury, nie trzeba używać jej zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="e6b50-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="e6b50-140">Jeśli nie chcesz, wykonywane są wszystkie akcje funkcji, ale wartość zwracana jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="e6b50-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="e6b50-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> jest często nazywana w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="e6b50-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="e6b50-142">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="e6b50-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="e6b50-143">Następujące `Function` procedury oblicza najdłuższego boku lub przeciwprostokątnej trójkąta prawo podanych wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="e6b50-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](./codesnippet/VisualBasic/function-procedures_1.vb)]  
  
 <span data-ttu-id="e6b50-144">W poniższym przykładzie przedstawiono typowe wywołania `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="e6b50-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](./codesnippet/VisualBasic/function-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b50-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e6b50-145">See Also</span></span>  
 [<span data-ttu-id="e6b50-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="e6b50-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="e6b50-147">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="e6b50-147">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="e6b50-148">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="e6b50-148">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="e6b50-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="e6b50-149">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="e6b50-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="e6b50-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e6b50-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e6b50-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e6b50-152">Instrukcje: tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="e6b50-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="e6b50-153">Instrukcje: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="e6b50-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="e6b50-154">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="e6b50-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
