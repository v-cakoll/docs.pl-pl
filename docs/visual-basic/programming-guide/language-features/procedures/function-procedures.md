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
ms.openlocfilehash: 568489d6034316e895cd999801241fa995aadefa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834247"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="36585-102">Procedury funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36585-102">Function Procedures (Visual Basic)</span></span>
<span data-ttu-id="36585-103">A `Function` procedura jest szereg instrukcji ujęta w `Function` i `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="36585-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="36585-104">`Function` Procedura wykonuje zadanie, a następnie przekazuje sterowanie do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="36585-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="36585-105">Przekazuje sterowanie, również zwraca wartość do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="36585-105">When it returns control, it also returns a value to the calling code.</span></span>  
  
 <span data-ttu-id="36585-106">Każdorazowo, procedura jest wywoływana, jego instrukcje uruchamiania, począwszy od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończącą pierwszy `End Function`, `Exit Function`, lub `Return` instrukcji napotkany.</span><span class="sxs-lookup"><span data-stu-id="36585-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="36585-107">Można zdefiniować `Function` procedury w module, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="36585-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="36585-108">Jest `Public` domyślnie, co oznacza, że można ją wywołać z dowolnego miejsca w aplikacji, które ma dostęp do modułu, klasy lub struktury on zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="36585-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>  
  
 <span data-ttu-id="36585-109">A `Function` procedurę można wykonać argumentów, takich jak stałe, zmienne lub wyrażeń, które są przekazywane do niej przez kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="36585-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="36585-110">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="36585-110">Declaration Syntax</span></span>  
 <span data-ttu-id="36585-111">Składnia do deklarowania `Function` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="36585-111">The syntax for declaring a `Function` procedure is as follows:</span></span>  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 <span data-ttu-id="36585-112">*Modyfikatory* można określić poziom dostępu i informacji dotyczących przeciążenia, zastępowanie, udostępnianie i cieniowania.</span><span class="sxs-lookup"><span data-stu-id="36585-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="36585-113">Aby uzyskać więcej informacji, zobacz [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36585-113">For more information, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="36585-114">Zadeklaruj taki sam sposób jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="36585-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="36585-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="36585-115">Data Type</span></span>  
 <span data-ttu-id="36585-116">Każdy `Function` procedura ma typ danych, jest po prostu każdej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="36585-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="36585-117">Ten typ danych jest określony przez `As` w klauzuli `Function` instrukcji która określa typ danych wartości, funkcja zwraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="36585-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="36585-118">Następujące deklaracje przykładowe przedstawiają to.</span><span class="sxs-lookup"><span data-stu-id="36585-118">The following sample declarations illustrate this.</span></span>  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 <span data-ttu-id="36585-119">Aby uzyskać więcej informacji, zobacz "Części" w [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36585-119">For more information, see "Parts" in [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
## <a name="returning-values"></a><span data-ttu-id="36585-120">Zwracanie wartości</span><span class="sxs-lookup"><span data-stu-id="36585-120">Returning Values</span></span>  
 <span data-ttu-id="36585-121">Wartość `Function` procedury wysyła Wstecz, aby kod wywołujący nosi nazwę wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="36585-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="36585-122">Procedura zwraca tę wartość w jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="36585-122">The procedure returns this value in one of two ways:</span></span>  
  
-   <span data-ttu-id="36585-123">Używa ona `Return` instrukcję, aby określić wartości zwracanej i zwraca kontrolę natychmiast program wywołujący.</span><span class="sxs-lookup"><span data-stu-id="36585-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="36585-124">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="36585-124">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   <span data-ttu-id="36585-125">Przypisuje wartość do jego własnej nazwy funkcji w jedną lub więcej instrukcji procedury.</span><span class="sxs-lookup"><span data-stu-id="36585-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="36585-126">Formant powraca do program wywołujący, aż do `Exit Function` lub `End Function` instrukcja jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="36585-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="36585-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="36585-127">The following example illustrates this.</span></span>  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 <span data-ttu-id="36585-128">Zaletą przypisywanie wartości zwracanej do nazwy funkcji jest, że kontrolka nie zwraca z procedury aż do napotkania `Exit Function` lub `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="36585-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="36585-129">Dzięki temu można przypisać wartości wstępny i dostosować go później, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="36585-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>  
  
 <span data-ttu-id="36585-130">Aby uzyskać więcej informacji na temat zwracanie wartości zobacz [Function — instrukcja](../../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="36585-130">For more information about returning values, see [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="36585-131">Aby uzyskać informacje dotyczące zwracania tablic, zobacz [tablic](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="36585-131">For information about returning arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="36585-132">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="36585-132">Calling Syntax</span></span>  
 <span data-ttu-id="36585-133">Wywołuje się `Function` procedury, takie jak jego nazwa i argumentów, albo po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="36585-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="36585-134">Należy podać wartości w argumentach, które nie są opcjonalne, a na liście argumentów należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="36585-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="36585-135">Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="36585-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="36585-136">Składnia służąca do wywołania `Function` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="36585-136">The syntax for a call to a `Function` procedure is as follows:</span></span>  
  
 <span data-ttu-id="36585-137">*l-wartości*`=`*functionname* `[(` *listaargumentów* `)]`</span><span class="sxs-lookup"><span data-stu-id="36585-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="36585-138">`If ((` *FunctionName* `[(` *listaargumentów* `)] / 3) <=` *wyrażenia* `) Then`</span><span class="sxs-lookup"><span data-stu-id="36585-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>  
  
 <span data-ttu-id="36585-139">Gdy wywołujesz `Function` procedury, trzeba użyć jego zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="36585-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="36585-140">Jeśli tego nie zrobisz, wykonywane są wszystkie akcje funkcji, ale zwracana wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="36585-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="36585-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> jest często nazywana w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="36585-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="36585-142">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="36585-142">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="36585-143">Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="36585-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 <span data-ttu-id="36585-144">W poniższym przykładzie przedstawiono typowe wywołanie `hypotenuse`.</span><span class="sxs-lookup"><span data-stu-id="36585-144">The following example shows a typical call to `hypotenuse`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="36585-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36585-145">See also</span></span>

- [<span data-ttu-id="36585-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="36585-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="36585-147">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="36585-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="36585-148">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="36585-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="36585-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="36585-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="36585-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="36585-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="36585-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="36585-151">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="36585-152">Instrukcje: Utwórz procedurę, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="36585-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="36585-153">Instrukcje: Zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="36585-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="36585-154">Instrukcje: Wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="36585-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
