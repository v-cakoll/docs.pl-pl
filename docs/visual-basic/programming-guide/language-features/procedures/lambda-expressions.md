---
title: Wyrażenia lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 54a9c0cf275a67c77748c32771c3c5dcbdb916d7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406706"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="42421-102">Lambda — Wyrażenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42421-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="42421-103">*Wyrażenie lambda* jest funkcją lub podprocedurą bez nazwy, która może być używana wszędzie tam, gdzie delegat jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="42421-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="42421-104">Wyrażenia lambda mogą być funkcjami lub procedurami i mogą być jednowierszowe lub wielowierszowe.</span><span class="sxs-lookup"><span data-stu-id="42421-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="42421-105">Można przekazać wartości z bieżącego zakresu do wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="42421-106">`RemoveHandler`Instrukcja to wyjątek.</span><span class="sxs-lookup"><span data-stu-id="42421-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="42421-107">W parametrze delegata elementu nie można przekazać wyrażenia lambda `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="42421-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="42421-108">Wyrażenia lambda można tworzyć za pomocą `Function` `Sub` słowa kluczowego or, tak jak w przypadku tworzenia standardowej funkcji lub procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="42421-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="42421-109">Jednak wyrażenia lambda są zawarte w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="42421-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="42421-110">Poniższy przykład jest wyrażeniem lambda, które zwiększa jego argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="42421-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="42421-111">W przykładzie pokazano zarówno jednowierszowy, jak i wielowierszową składnię wyrażenia lambda dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="42421-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="42421-112">Poniższy przykład jest wyrażeniem lambda, które zapisuje wartość w konsoli.</span><span class="sxs-lookup"><span data-stu-id="42421-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="42421-113">W przykładzie pokazano zarówno jednowierszowe, jak i wielowierszowa składnia wyrażenia lambda dla procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="42421-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="42421-114">Zwróć uwagę, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="42421-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="42421-115">Za każdym razem, gdy odwołujesz się do zmiennej, wywołaj wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="42421-116">Można również zadeklarować i wywołać wyrażenie lambda w tym samym czasie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42421-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="42421-117">Wyrażenie lambda może być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w sekcji [kontekstu](#context) w dalszej części tego tematu) lub przekazana jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42421-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="42421-118">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="42421-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="42421-119">Składnia wyrażenia lambda jest podobna do standardowej funkcji lub procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="42421-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="42421-120">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="42421-120">The differences are as follows:</span></span>

- <span data-ttu-id="42421-121">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="42421-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="42421-122">Wyrażenia lambda nie mogą mieć modyfikatorów, takich jak `Overloads` lub `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="42421-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="42421-123">Jednowierszowe funkcje lambda nie używają `As` klauzuli do wyznaczania typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="42421-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="42421-124">Zamiast tego, typ jest wywnioskowany na podstawie wartości, do której szacuje się treść wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="42421-125">Na przykład jeśli treść wyrażenia lambda jest `cust.City = "London"` , jego typem zwracanym jest `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="42421-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="42421-126">W wielowierszowych funkcjach lambda można określić typ zwracany przy użyciu `As` klauzuli lub pominąć `As` klauzulę, tak aby typ zwracany został wywnioskowany.</span><span class="sxs-lookup"><span data-stu-id="42421-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="42421-127">Gdy `As` klauzula jest pomijana dla wielowierszowej funkcji lambda, zwracany typ jest wywnioskowany jako typ dominujący ze wszystkich `Return` instrukcji w wielowierszowej funkcji lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="42421-128">*Typ dominujący* jest typem unikatowym, do którego można rozszerzyć wszystkie inne typy.</span><span class="sxs-lookup"><span data-stu-id="42421-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="42421-129">Jeśli nie można określić tego unikatowego typu, typ dominujący jest typem unikatowym, do którego można zawęzić wszystkie inne typy w tablicy.</span><span class="sxs-lookup"><span data-stu-id="42421-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="42421-130">Jeśli nie można określić żadnego z tych unikatowych typów, typ dominujący to `Object` .</span><span class="sxs-lookup"><span data-stu-id="42421-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="42421-131">W tym przypadku, jeśli `Option Strict` jest ustawiona na `On` , wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="42421-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="42421-132">Na przykład, jeśli wyrażenia dostarczone do `Return` instrukcji zawierają wartości typu `Integer` , `Long` , i `Double` , Tablica wyników jest typu `Double` .</span><span class="sxs-lookup"><span data-stu-id="42421-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="42421-133">Obie `Integer` i `Long` rozszerzają się `Double` tylko do i `Double` .</span><span class="sxs-lookup"><span data-stu-id="42421-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="42421-134">W związku `Double` z tym jest typem dominującym.</span><span class="sxs-lookup"><span data-stu-id="42421-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="42421-135">Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="42421-135">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="42421-136">Treść funkcji jednowierszowej musi być wyrażeniem zwracającym wartość, a nie instrukcją.</span><span class="sxs-lookup"><span data-stu-id="42421-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="42421-137">Brak `Return` instrukcji dla funkcji jednowierszowych.</span><span class="sxs-lookup"><span data-stu-id="42421-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="42421-138">Wartość zwracana przez funkcję jednowierszową jest wartością wyrażenia w treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="42421-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="42421-139">Treść podprocedury jednowierszowej musi być instrukcją jednowierszową.</span><span class="sxs-lookup"><span data-stu-id="42421-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="42421-140">Funkcje jednowierszowe i podprocedury nie zawierają `End Function` `End Sub` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="42421-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="42421-141">Można określić typ danych parametru wyrażenia lambda za pomocą `As` słowa kluczowego lub można wywnioskować typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="42421-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="42421-142">Wszystkie parametry muszą mieć określone typy danych lub muszą zostać wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="42421-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="42421-143">`Optional``Paramarray`Parametry i są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="42421-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="42421-144">Parametry ogólne są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="42421-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="42421-145">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="42421-145">Async Lambdas</span></span>

<span data-ttu-id="42421-146">Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych operatora [Async](../../../language-reference/modifiers/async.md) i [await](../../../language-reference/operators/await-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="42421-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../language-reference/modifiers/async.md) and [Await Operator](../../../language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="42421-147">Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="42421-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="42421-148">Tę samą procedurę obsługi zdarzeń można dodać przy użyciu asynchronicznego wyrażenia lambda w [instrukcji AddHandler](../../../language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="42421-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="42421-149">Aby dodać tę procedurę obsługi, Dodaj `Async` modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42421-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="42421-150">Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i await](../../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="42421-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="42421-151">Kontekst</span><span class="sxs-lookup"><span data-stu-id="42421-151">Context</span></span>

<span data-ttu-id="42421-152">Wyrażenie lambda udostępnia swój kontekst z zakresem, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="42421-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="42421-153">Ma takie same prawa dostępu jak każdy kod zapisany w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="42421-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="42421-154">Obejmuje to dostęp do zmiennych składowych, funkcji i `Me` parametrów, a także zmiennych lokalnych w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="42421-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="42421-155">Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym może wykraczać poza okres istnienia tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="42421-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="42421-156">Tak długo, jak delegat odwołujący się do wyrażenia lambda nie jest dostępny do wyrzucania elementów bezużytecznych, zostanie zachowany dostęp do zmiennych w oryginalnym środowisku.</span><span class="sxs-lookup"><span data-stu-id="42421-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="42421-157">W poniższym przykładzie zmienna `target` jest lokalna do `makeTheGame` , metoda, w której `playTheGame` jest zdefiniowane wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="42421-158">Zwróć uwagę, że zwrócone wyrażenie lambda przypisane do `takeAGuess` w `Main` , nadal ma dostęp do zmiennej lokalnej `target` .</span><span class="sxs-lookup"><span data-stu-id="42421-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="42421-159">Poniższy przykład demonstruje szeroki zakres praw dostępu zagnieżdżonego wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="42421-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="42421-160">Gdy zwrócone wyrażenie lambda jest wykonywane z `Main` AS `aDel` , uzyskuje dostęp do następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="42421-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="42421-161">Pole klasy, w której jest zdefiniowany:`aField`</span><span class="sxs-lookup"><span data-stu-id="42421-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="42421-162">Właściwość klasy, w której jest zdefiniowana:`aProp`</span><span class="sxs-lookup"><span data-stu-id="42421-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="42421-163">Parametr metody `functionWithNestedLambda` , w której jest zdefiniowany:`level1`</span><span class="sxs-lookup"><span data-stu-id="42421-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="42421-164">Zmienna lokalna `functionWithNestedLambda` :`localVar`</span><span class="sxs-lookup"><span data-stu-id="42421-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="42421-165">Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`</span><span class="sxs-lookup"><span data-stu-id="42421-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="42421-166">Konwertowanie na typ delegata</span><span class="sxs-lookup"><span data-stu-id="42421-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="42421-167">Wyrażenie lambda może być niejawnie konwertowane na zgodny typ delegata.</span><span class="sxs-lookup"><span data-stu-id="42421-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="42421-168">Aby uzyskać informacje o ogólnych wymaganiach dotyczących zgodności, zobacz [swobodne przekształcenie delegata](../delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="42421-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="42421-169">Na przykład poniższy kod ilustruje wyrażenie lambda, które niejawnie konwertuje do `Func(Of Integer, Boolean)` lub pasujący podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="42421-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="42421-170">Poniższy przykład kodu przedstawia wyrażenie lambda, które niejawnie konwertuje do `Sub(Of Double, String, Double)` lub pasujący podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="42421-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="42421-171">W przypadku przypisywania wyrażeń lambda do delegatów lub przekazywania ich jako argumentów do procedur, można określić nazwy parametrów, ale pomijać ich typy danych, dzięki czemu typy mają być pobierane z delegata.</span><span class="sxs-lookup"><span data-stu-id="42421-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="42421-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="42421-172">Examples</span></span>

- <span data-ttu-id="42421-173">W poniższym przykładzie zdefiniowano wyrażenie lambda, które zwraca `True` , jeśli argument typu wartości null ma przypisaną wartość i `False` jeśli jego wartość to `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="42421-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="42421-174">Poniższy przykład definiuje wyrażenie lambda zwracające indeks ostatniego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="42421-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="42421-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42421-175">See also</span></span>

- [<span data-ttu-id="42421-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="42421-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="42421-177">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42421-177">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="42421-178">Delegaci</span><span class="sxs-lookup"><span data-stu-id="42421-178">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="42421-179">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="42421-179">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="42421-180">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="42421-180">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="42421-181">Typy wartości null</span><span class="sxs-lookup"><span data-stu-id="42421-181">Nullable Value Types</span></span>](../data-types/nullable-value-types.md)
- [<span data-ttu-id="42421-182">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42421-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="42421-183">Porady: tworzenie wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="42421-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="42421-184">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="42421-184">Relaxed Delegate Conversion</span></span>](../delegates/relaxed-delegate-conversion.md)
