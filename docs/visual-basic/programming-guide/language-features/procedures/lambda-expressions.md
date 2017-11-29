---
title: "Lambda — Wyrażenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: "52"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 69ac88d295420277e99058d0f80a5ae1c2ce2e39
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="85267-102">Lambda — Wyrażenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85267-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="85267-103">A *wyrażenia lambda* jest funkcją lub podprocedury bez nazwy, który może służyć wszędzie tam, gdzie delegata jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="85267-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="85267-104">Wyrażenia lambda można używać funkcji lub procedury i może być jednym lub wielu linii.</span><span class="sxs-lookup"><span data-stu-id="85267-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="85267-105">Wyrażenie lambda, można przekazać wartości z bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="85267-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85267-106">`RemoveHandler` Instrukcja jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="85267-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="85267-107">Nie można przekazać wyrażenia lambda w dla parametru delegowanego `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="85267-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="85267-108">Tworzenie wyrażenia lambda za pomocą `Function` lub `Sub` — słowo kluczowe, tak samo jak tworzenie standardowych funkcji lub procedury.</span><span class="sxs-lookup"><span data-stu-id="85267-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="85267-109">Jednak wyrażenia lambda znajdują się w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="85267-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="85267-110">Poniższy przykład jest zwiększa jej argument, który zwraca wartość wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="85267-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="85267-111">W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="85267-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="85267-112">Poniższy przykład jest wyrażenie lambda, które zapisuje wartość do konsoli.</span><span class="sxs-lookup"><span data-stu-id="85267-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="85267-113">W przykładzie zarówno jeden wiersz i wielowierszowe składnia wyrażenia lambda dla procedury.</span><span class="sxs-lookup"><span data-stu-id="85267-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="85267-114">Zwróć uwagę, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="85267-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="85267-115">Odwołując się do zmiennej, można wywołać wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="85267-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="85267-116">Można również deklarować i wywołać wyrażenia lambda w tym samym czasie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85267-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="85267-117">Wyrażenia lambda, może być zwracany jako wartość wywołania funkcji (jak to pokazano w przykładzie w [kontekstu](#context) później w tym temacie), lub przekazany jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykład.</span><span class="sxs-lookup"><span data-stu-id="85267-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="85267-118">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="85267-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="85267-119">Składnia wyrażenia lambda jest podobny do standardowych funkcji lub procedury.</span><span class="sxs-lookup"><span data-stu-id="85267-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="85267-120">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="85267-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="85267-121">Wyrażenia lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="85267-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="85267-122">Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="85267-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="85267-123">Nie używaj funkcji lambda jednowierszowego `As` klauzuli, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="85267-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="85267-124">Zamiast tego typu jest wywnioskowany na podstawie wartości, która daje w wyniku treści wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="85267-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="85267-125">Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, jego typem zwracanym jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="85267-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="85267-126">W wielowierszowym lambda funkcji, można określić zwracanego typu przy użyciu `As` klauzuli lub Pomiń `As` klauzuli tak, aby zwracany typ jest wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="85267-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="85267-127">Gdy `As` klauzuli pominięto dla funkcji lambda wiele wierszy, zwracany typ jest wywnioskowany dominującą typem ze wszystkich `Return` instrukcje w funkcji lambda wiele wierszy.</span><span class="sxs-lookup"><span data-stu-id="85267-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="85267-128">*Typu dominującą* jest typem unikatowy poszerzyć do innych typów.</span><span class="sxs-lookup"><span data-stu-id="85267-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="85267-129">Nie można określić tego typu unikatowy, ten typ dominującej nie jest unikatowy typ, który wszystkie typy w tablicy można ograniczyć do.</span><span class="sxs-lookup"><span data-stu-id="85267-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="85267-130">Jeśli żadna z tych typów unikatowy nie można ustalić, jest typu dominującą `Object`.</span><span class="sxs-lookup"><span data-stu-id="85267-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="85267-131">W tym przypadku jeśli `Option Strict` ma ustawioną wartość `On`, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="85267-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="85267-132">Na przykład, jeśli wyrażenia dostarczony do `Return` instrukcji zawierają wartości typu `Integer`, `Long`, i `Double`, wynikowy tablicy jest typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="85267-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="85267-133">Zarówno `Integer` i `Long` rozszerzane `Double` i tylko `Double`.</span><span class="sxs-lookup"><span data-stu-id="85267-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="85267-134">W związku z tym `Double` jest dominującą typu.</span><span class="sxs-lookup"><span data-stu-id="85267-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="85267-135">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="85267-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="85267-136">Treść funkcji pojedynczej linii musi być wyrażenie zwracające wartość, nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="85267-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="85267-137">Brak nie `Return` instrukcji dla funkcji jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="85267-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="85267-138">Wartość zwrócona przez funkcję jeden wiersz jest wartość wyrażenia w treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="85267-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="85267-139">Treść podprocedury jeden wiersz musi być instrukcją jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="85267-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="85267-140">Nie dołączaj jednowierszowego funkcje i podprocedury `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="85267-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="85267-141">Można określić typ danych parametru wyrażenia lambda za pomocą `As` można wywnioskować — słowo kluczowe lub typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="85267-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="85267-142">Albo wszystkie parametry muszą określono można wywnioskować typów danych lub wszystkich.</span><span class="sxs-lookup"><span data-stu-id="85267-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="85267-143">`Optional`i `Paramarray` parametry są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="85267-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="85267-144">Parametry ogólne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="85267-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="85267-145">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="85267-145">Async Lambdas</span></span>  
 <span data-ttu-id="85267-146">Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="85267-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="85267-147">Na przykład w poniższym przykładzie formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekujące na metody asynchronicznej `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="85267-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="85267-148">Można dodać tej procedury obsługi zdarzeń za pomocą asynchroniczne lambda w [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="85267-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="85267-149">Aby dodać ten program obsługi, Dodaj `Async` modyfikator przed listy parametrów lambda, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="85267-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="85267-150">Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z Async i Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="85267-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <span data-ttu-id="85267-151"><a name="context"></a>Kontekst</span><span class="sxs-lookup"><span data-stu-id="85267-151"><a name="context"></a> Context</span></span>  
 <span data-ttu-id="85267-152">Wyrażenia lambda udostępnia kontekst zakresu, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="85267-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="85267-153">Ma te same prawa dostępu jako dowolny kod napisany w zawierający zakres.</span><span class="sxs-lookup"><span data-stu-id="85267-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="85267-154">Obejmuje to dostęp do zmiennych Członkowskich, funkcje i subskrypcji, `Me`i parametrów i zmiennych lokalnych w zawierającym zasięgu.</span><span class="sxs-lookup"><span data-stu-id="85267-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="85267-155">Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym mogą wykraczać poza okres istnienia tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="85267-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="85267-156">Tak długo, jak delegata odwołujących się do wyrażenia lambda nie jest dostępny dla wyrzucanie elementów bezużytecznych, dostęp do zmiennych w oryginalne środowisko jest przechowywane.</span><span class="sxs-lookup"><span data-stu-id="85267-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="85267-157">W poniższym przykładzie zmienna `target` jest lokalny dla `makeTheGame`, metody, w którym wyrażenie lambda `playTheGame` jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="85267-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="85267-158">Należy pamiętać, że wyrażenie lambda zwrócony przypisane do `takeAGuess` w `Main`, ma nadal dostęp do zmiennej lokalnej `target`.</span><span class="sxs-lookup"><span data-stu-id="85267-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="85267-159">W poniższym przykładzie pokazano szeroką gamę praw dostępu wyrażenia lambda zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="85267-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="85267-160">Po wykonaniu wyrażenia lambda zwrócony z `Main` jako `aDel`, uzyskuje dostęp do tych elementów:</span><span class="sxs-lookup"><span data-stu-id="85267-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="85267-161">To pole klasy, w którym jest zdefiniowany:`aField`</span><span class="sxs-lookup"><span data-stu-id="85267-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="85267-162">Właściwość klasy, w którym jest zdefiniowana:`aProp`</span><span class="sxs-lookup"><span data-stu-id="85267-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="85267-163">Parametr metody `functionWithNestedLambda`, w którym jest zdefiniowana:`level1`</span><span class="sxs-lookup"><span data-stu-id="85267-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="85267-164">Zmienna lokalna o `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="85267-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="85267-165">Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`</span><span class="sxs-lookup"><span data-stu-id="85267-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="85267-166">Konwertowanie na typ delegowany</span><span class="sxs-lookup"><span data-stu-id="85267-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="85267-167">Wyrażenia lambda można niejawnie przekonwertować na typ delegata zgodne.</span><span class="sxs-lookup"><span data-stu-id="85267-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="85267-168">Aby uzyskać informacje ogólne wymagania dotyczące zgodności, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="85267-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="85267-169">Na przykład poniższy przykładowy kod przedstawia wyrażenie lambda, które jawnie konwertuje `Func(Of Integer, Boolean)` lub zgodnego podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="85267-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="85267-170">Poniższy przykład kodu pokazuje Wyrażenie lambda, które jawnie konwertuje `Sub(Of Double, String, Double)` lub zgodnego podpisu delegata.</span><span class="sxs-lookup"><span data-stu-id="85267-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="85267-171">Podczas przypisywania do delegatów wyrażenia lambda lub przekazywane jako argumenty do procedur można określić nazwy parametrów, ale pominąć typy danych, umożliwiając typy pobrane z obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="85267-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="85267-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="85267-172">Examples</span></span>  
  
-   <span data-ttu-id="85267-173">W poniższym przykładzie zdefiniowano wyrażenia lambda, która zwraca `True` Jeśli argument NULL ma przypisaną wartość i `False` jeśli jego wartość wynosi `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="85267-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="85267-174">Poniższy przykład definiuje wyrażenie lambda, które zwraca indeks ostatniego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="85267-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="85267-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85267-175">See Also</span></span>  
 [<span data-ttu-id="85267-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="85267-176">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="85267-177">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85267-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="85267-178">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="85267-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="85267-179">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="85267-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="85267-180">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="85267-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="85267-181">Typy dopuszczające wartości zerowe wartości</span><span class="sxs-lookup"><span data-stu-id="85267-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="85267-182">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85267-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="85267-183">Porady: Tworzenie wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="85267-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)  
 [<span data-ttu-id="85267-184">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="85267-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
