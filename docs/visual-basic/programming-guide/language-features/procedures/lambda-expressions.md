---
title: Lambda — Wyrażenia (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 3d2cab1c40b1a84e9a3b6bed885b2a0020e53f01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529479"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="84d2c-102">Lambda — Wyrażenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84d2c-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="84d2c-103">A *wyrażenia lambda* jest funkcji lub podprocedury bez nazwy, który może służyć wszędzie tam, gdzie obiekt delegowany jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="84d2c-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="84d2c-104">Wyrażenia lambda może być funkcji lub podprocedury i może być w jednym lub wielu linii.</span><span class="sxs-lookup"><span data-stu-id="84d2c-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="84d2c-105">Wyrażenie lambda można przekazać wartości z bieżącego zakresu.</span><span class="sxs-lookup"><span data-stu-id="84d2c-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d2c-106">`RemoveHandler` Instrukcja jest wyjątek.</span><span class="sxs-lookup"><span data-stu-id="84d2c-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="84d2c-107">Nie można przekazać wyrażenia lambda w parametrze delegata `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="84d2c-108">Tworzenie wyrażenia lambda przy użyciu `Function` lub `Sub` — słowo kluczowe, podobnie jak tworzenie standardowej funkcji lub podprocedury.</span><span class="sxs-lookup"><span data-stu-id="84d2c-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="84d2c-109">Jednak wyrażenia lambda są uwzględnione w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="84d2c-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="84d2c-110">Poniższy przykład jest wyrażenie lambda, która zwiększa jej argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="84d2c-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="84d2c-111">W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="84d2c-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="84d2c-112">Poniższy przykład jest wyrażenie lambda, która zapisuje wartości do konsoli.</span><span class="sxs-lookup"><span data-stu-id="84d2c-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="84d2c-113">W przykładzie pokazano oba jeden wiersz i wielowierszowe składnia wyrażenia lambda do procedurę.</span><span class="sxs-lookup"><span data-stu-id="84d2c-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="84d2c-114">Należy zauważyć, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="84d2c-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="84d2c-115">Zawsze, gdy odwołujesz się do zmiennej, można wywołać wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="84d2c-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="84d2c-116">Można również zadeklarować i wywołać Wyrażenie lambda, w tym samym czasie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="84d2c-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="84d2c-117">Wyrażenia lambda mogą być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w [kontekstu](#context) w dalszej części tego tematu), lub przekazany jako argument do parametru, która przyjmuje typ delegata, jak pokazano w poniższym przykład.</span><span class="sxs-lookup"><span data-stu-id="84d2c-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="84d2c-118">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="84d2c-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="84d2c-119">Składnia wyrażenia lambda przypomina standardowej funkcji lub podprocedury.</span><span class="sxs-lookup"><span data-stu-id="84d2c-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="84d2c-120">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="84d2c-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="84d2c-121">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="84d2c-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="84d2c-122">Wyrażenia lambda nie może mieć modyfikatorów, takich jak `Overloads` lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="84d2c-123">Nie należy używać funkcji lambda jednowierszowego `As` klauzuli, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="84d2c-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="84d2c-124">Zamiast tego typ jest wnioskowany z wartości, która daje w wyniku treść wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="84d2c-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="84d2c-125">Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, jego typem zwracanym jest `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="84d2c-126">W przypadku funkcji lambda wielowierszowe można określić typ zwracany za pomocą `As` klauzuli lub Pomiń `As` klauzuli tak, aby zwracany typ jest wnioskowany.</span><span class="sxs-lookup"><span data-stu-id="84d2c-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="84d2c-127">Gdy `As` klauzuli zostanie pominięty dla funkcji lambda wielowierszowego, zwracany typ jest wnioskowany jako typ dominujący ze wszystkich `Return` instrukcji w funkcji lambda wiele wierszy.</span><span class="sxs-lookup"><span data-stu-id="84d2c-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="84d2c-128">*Typ dominujący* to unikatowy typ, który poszerzyć do innych typów.</span><span class="sxs-lookup"><span data-stu-id="84d2c-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="84d2c-129">Jeżeli nie można ustalić tego typu unikatowego, Typ dominujący to unikatowy typ, który można zawęzić wszystkie typy w tablicy.</span><span class="sxs-lookup"><span data-stu-id="84d2c-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="84d2c-130">Jeśli żadna z tych typów unikatowych nie można ustalić, typem dominującym jest `Object`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="84d2c-131">W takim przypadku `Option Strict` ustawiono `On`, występuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="84d2c-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="84d2c-132">Na przykład, jeśli wyrażenie dostarczone do `Return` instrukcji zawierają wartości typu `Integer`, `Long`, i `Double`, tablica wynikowa jest typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="84d2c-133">Zarówno `Integer` i `Long` mogą zostać poszerzone do `Double` i tylko `Double`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="84d2c-134">W związku z tym `Double` jest typem dominującym.</span><span class="sxs-lookup"><span data-stu-id="84d2c-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="84d2c-135">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="84d2c-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="84d2c-136">Treść funkcji pojedynczej linii musi być wyrażenie zwracające wartość nie instrukcję.</span><span class="sxs-lookup"><span data-stu-id="84d2c-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="84d2c-137">Istnieje nie `Return` poufności informacji dla funkcji pojedynczej linii.</span><span class="sxs-lookup"><span data-stu-id="84d2c-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="84d2c-138">Wartość zwrócona przez funkcję jednowierszowego jest wartość wyrażenia w treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="84d2c-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="84d2c-139">Treść procedury jeden wiersz musi być instrukcją jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="84d2c-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="84d2c-140">Nie dołączaj jednowierszowego, funkcje i procedur `End Function` lub `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="84d2c-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="84d2c-141">Typ danych parametru wyrażenia lambda można określić za pomocą `As` można wywnioskować — słowo kluczowe lub typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="84d2c-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="84d2c-142">Musi mieć określony albo wszystkie parametry można wywnioskować typów danych lub wszystkich.</span><span class="sxs-lookup"><span data-stu-id="84d2c-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="84d2c-143">`Optional` i `Paramarray` parametry nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="84d2c-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="84d2c-144">Parametry ogólne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="84d2c-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="84d2c-145">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="84d2c-145">Async Lambdas</span></span>  
 <span data-ttu-id="84d2c-146">Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [Async](../../../../visual-basic/language-reference/modifiers/async.md) i [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="84d2c-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="84d2c-147">Na przykład, poniższy przykład Windows Forms zawiera program obsługi zdarzeń, który wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="84d2c-148">Można dodać tę samą procedurę obsługi zdarzeń, używając lambdy asynchronicznej w [AddHandler — instrukcja](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="84d2c-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="84d2c-149">Aby dodać ten program obsługi `Async` modyfikator przed listą parametrów lambda, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="84d2c-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="84d2c-150">Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="84d2c-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a> <span data-ttu-id="84d2c-151">Kontekst</span><span class="sxs-lookup"><span data-stu-id="84d2c-151">Context</span></span>  
 <span data-ttu-id="84d2c-152">Wyrażenie lambda udostępnia kontekst zakresu, w którym jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="84d2c-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="84d2c-153">Ma on te same prawa dostępu, jak każdy kod napisany w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="84d2c-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="84d2c-154">Obejmuje to dostęp do zmiennych składowych, funkcje i subskrypcji, `Me`oraz parametry i zmienne lokalne w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="84d2c-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="84d2c-155">Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym mogą wykraczać poza okres istnienia tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="84d2c-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="84d2c-156">Tak długo, jak obiekt delegowany odwołujące się do wyrażenia lambda nie jest dostępna dla wyrzucania elementów bezużytecznych, dostęp do zmiennych w środowisku, oryginalnym są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="84d2c-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="84d2c-157">W poniższym przykładzie zmienna `target` jest lokalną grupą `makeTheGame`, metody, w którym wyrażenie lambda `playTheGame` jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="84d2c-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="84d2c-158">Należy zauważyć, że wyrażenie lambda zwrócone przypisane do `takeAGuess` w `Main`, wciąż ma dostęp do zmiennej lokalnej `target`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="84d2c-159">W poniższym przykładzie pokazano szeroką gamę prawa dostępu zagnieżdżonym wyrażeniem lambda.</span><span class="sxs-lookup"><span data-stu-id="84d2c-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="84d2c-160">Gdy wyrażenie lambda zwracany jest wykonywany z `Main` jako `aDel`, uzyskuje dostęp do tych elementów:</span><span class="sxs-lookup"><span data-stu-id="84d2c-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="84d2c-161">Pole klasy, w którym jest zdefiniowany: `aField`</span><span class="sxs-lookup"><span data-stu-id="84d2c-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="84d2c-162">Właściwość klasy, w którym jest zdefiniowany: `aProp`</span><span class="sxs-lookup"><span data-stu-id="84d2c-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="84d2c-163">Parametr metody `functionWithNestedLambda`, w którym jest zdefiniowana: `level1`</span><span class="sxs-lookup"><span data-stu-id="84d2c-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="84d2c-164">Zmienna lokalna o `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="84d2c-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="84d2c-165">Parametr wyrażenia lambda, w którym jest zagnieżdżona: `level2`</span><span class="sxs-lookup"><span data-stu-id="84d2c-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="84d2c-166">Konwertowanie do typu delegata</span><span class="sxs-lookup"><span data-stu-id="84d2c-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="84d2c-167">Wyrażenia lambda mogą być niejawnie konwertowane na typ delegata zgodne.</span><span class="sxs-lookup"><span data-stu-id="84d2c-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="84d2c-168">Aby uzyskać informacje na temat ogólnych wymagań dotyczących zgodności, zobacz [swobodna konwersja delegatów](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="84d2c-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="84d2c-169">Na przykład, poniższy przykład kodu pokazuje Wyrażenie lambda, która niejawnie konwertuje `Func(Of Integer, Boolean)` lub pasujący podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="84d2c-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="84d2c-170">Poniższy przykład kodu pokazuje Wyrażenie lambda, która niejawnie konwertuje `Sub(Of Double, String, Double)` lub pasujący podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="84d2c-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="84d2c-171">Podczas przypisywania wyrażenia lambda do delegatów i przekazywane jako argumenty do procedur, można określić nazwy parametrów, ale Pomiń typy danych, umożliwiając typy podejmowane na podstawie obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="84d2c-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="84d2c-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="84d2c-172">Examples</span></span>  
  
-   <span data-ttu-id="84d2c-173">W poniższym przykładzie zdefiniowano Wyrażenie lambda, które zwraca `True` Jeśli przypisaną wartością argumentu dopuszcza wartości null i `False` gdy jego wartość jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="84d2c-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="84d2c-174">W poniższym przykładzie zdefiniowano Wyrażenie lambda, które zwraca indeks ostatniego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="84d2c-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="84d2c-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84d2c-175">See also</span></span>
- [<span data-ttu-id="84d2c-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="84d2c-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="84d2c-177">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84d2c-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="84d2c-178">Delegaty</span><span class="sxs-lookup"><span data-stu-id="84d2c-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="84d2c-179">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="84d2c-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="84d2c-180">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="84d2c-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="84d2c-181">Typy wartości dopuszczających wartości null</span><span class="sxs-lookup"><span data-stu-id="84d2c-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="84d2c-182">Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84d2c-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="84d2c-183">Instrukcje: Tworzenie wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="84d2c-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="84d2c-184">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="84d2c-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
