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
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249672"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="789ea-102">Lambda — Wyrażenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="789ea-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="789ea-103">Wyrażenie *lambda* jest funkcją lub podprocedury bez nazwy, która może być używana wszędzie tam, gdzie delegat jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="789ea-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="789ea-104">Wyrażenia Lambda mogą być funkcjami lub podprocedury i mogą być jednowierszowe lub wieloliniowe.</span><span class="sxs-lookup"><span data-stu-id="789ea-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="789ea-105">Wartości z bieżącego zakresu można przekazać do wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="789ea-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="789ea-106">Instrukcja `RemoveHandler` jest wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="789ea-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="789ea-107">Nie można przekazać wyrażenia lambda dla `RemoveHandler`parametru delegata .</span><span class="sxs-lookup"><span data-stu-id="789ea-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="789ea-108">Wyrażenia lambda można tworzyć `Function` przy `Sub` użyciu słowa kluczowego lub, tak jak tworzysz standardową funkcję lub podprocedury.</span><span class="sxs-lookup"><span data-stu-id="789ea-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="789ea-109">Jednak wyrażenia lambda są uwzględniane w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="789ea-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="789ea-110">Poniższy przykład jest wyrażenie lambda, który zwiększa jego argument i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="789ea-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="789ea-111">W przykładzie przedstawiono składnię wyrażenia lambda jedno- i wielowierszowego dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="789ea-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="789ea-112">Poniższy przykład jest wyrażenie lambda, który zapisuje wartość do konsoli.</span><span class="sxs-lookup"><span data-stu-id="789ea-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="789ea-113">W przykładzie przedstawiono składnię wyrażenia lambda jedno- i wielowierszowego dla podprocedury.</span><span class="sxs-lookup"><span data-stu-id="789ea-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="789ea-114">Należy zauważyć, że w poprzednich przykładach wyrażenia lambda są przypisane do nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="789ea-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="789ea-115">Za każdym razem, gdy odwołujesz się do zmiennej, wywołujesz wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="789ea-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="789ea-116">Można również zadeklarować i wywołać wyrażenie lambda w tym samym czasie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="789ea-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="789ea-117">Wyrażenie lambda może być zwracane jako wartość wywołania funkcji (jak pokazano w przykładzie w sekcji Kontekst w dalszej części tego [tematu)](#context) lub przekazywane jako argument do parametru, który przyjmuje typ delegata, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="789ea-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="789ea-118">Składnia wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="789ea-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="789ea-119">Składnia wyrażenia lambda przypomina składność funkcji standardowej lub podprocedury.</span><span class="sxs-lookup"><span data-stu-id="789ea-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="789ea-120">Różnice są następujące:</span><span class="sxs-lookup"><span data-stu-id="789ea-120">The differences are as follows:</span></span>

- <span data-ttu-id="789ea-121">Wyrażenie lambda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="789ea-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="789ea-122">Wyrażenia Lambda nie mogą mieć `Overloads` modyfikatorów, takich jak lub `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="789ea-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="789ea-123">Funkcje lambda jednowierszowe `As` nie używają klauzuli do wyznaczenia typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="789ea-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="789ea-124">Zamiast tego typ jest wywnioskowany z wartości, która jest oceniana przez obiekt wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="789ea-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="789ea-125">Na przykład, jeśli treść wyrażenia lambda jest `cust.City = "London"`, `Boolean`jego typem zwracany jest .</span><span class="sxs-lookup"><span data-stu-id="789ea-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="789ea-126">W wielowierszowych funkcjach lambda można określić typ `As` zwracany przy `As` użyciu klauzuli lub pominąć klauzulę, tak aby wywnioskować typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="789ea-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="789ea-127">Gdy `As` klauzula jest pominięta dla funkcji lambda wielowierszowej, typ zwracany jest `Return` wnioskowany jako typ dominujący ze wszystkich instrukcji w funkcji lambda wielowierszowej.</span><span class="sxs-lookup"><span data-stu-id="789ea-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="789ea-128">*Typ dominujący* jest typem unikatowym, do który można poszerzyć wszystkie inne typy.</span><span class="sxs-lookup"><span data-stu-id="789ea-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="789ea-129">Jeśli nie można określić tego typu unikatowego, typ dominujący jest typem unikatowym, do który można zawęzić wszystkie inne typy w tablicy.</span><span class="sxs-lookup"><span data-stu-id="789ea-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="789ea-130">Jeśli żaden z tych unikatowych typów nie `Object`może być określony, typem dominującym jest .</span><span class="sxs-lookup"><span data-stu-id="789ea-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="789ea-131">W takim przypadku, `Option Strict` jeśli `On`jest ustawiona na , występuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="789ea-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="789ea-132">Na przykład, jeśli wyrażenia dostarczone `Return` do instrukcji `Integer`zawierają `Long`wartości `Double`typu , i , `Double`wynikowa tablica jest typu .</span><span class="sxs-lookup"><span data-stu-id="789ea-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="789ea-133">Zarówno `Integer` `Long` i `Double` poszerzyć `Double`do i tylko .</span><span class="sxs-lookup"><span data-stu-id="789ea-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="789ea-134">W związku `Double` z tym jest typem dominującym.</span><span class="sxs-lookup"><span data-stu-id="789ea-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="789ea-135">Aby uzyskać więcej informacji, zobacz [Rozszerzanie i zawężanie konwersji](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="789ea-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="789ea-136">Treść funkcji jednowierszowej musi być wyrażeniem, które zwraca wartość, a nie instrukcją.</span><span class="sxs-lookup"><span data-stu-id="789ea-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="789ea-137">Nie ma `Return` instrukcji dla funkcji jednowierszowych.</span><span class="sxs-lookup"><span data-stu-id="789ea-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="789ea-138">Wartość zwracana przez funkcję jednowierszową jest wartością wyrażenia w treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="789ea-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="789ea-139">Treść podprocedury jednowierszowej musi być instrukcją jednowierszową.</span><span class="sxs-lookup"><span data-stu-id="789ea-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="789ea-140">Funkcje jednowierszowe i podprocedury nie zawierają `End Function` instrukcji ani `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="789ea-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="789ea-141">Można określić typ danych parametru wyrażenia lambda za pomocą `As` słowa kluczowego lub typ danych parametru można wywnioskować.</span><span class="sxs-lookup"><span data-stu-id="789ea-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="789ea-142">Wszystkie parametry muszą mieć określone typy danych lub wszystkie muszą być wywnioskowane.</span><span class="sxs-lookup"><span data-stu-id="789ea-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="789ea-143">`Optional`i `Paramarray` parametry nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="789ea-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="789ea-144">Parametry ogólne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="789ea-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="789ea-145">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="789ea-145">Async Lambdas</span></span>

<span data-ttu-id="789ea-146">Można łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [async](../../../../visual-basic/language-reference/modifiers/async.md) i [await operator](../../../../visual-basic/language-reference/operators/await-operator.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="789ea-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="789ea-147">Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje metodę asynchronizową i oczekuje na metodę asynchronizowania. `ExampleMethodAsync`</span><span class="sxs-lookup"><span data-stu-id="789ea-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="789ea-148">Ten sam program obsługi zdarzeń można dodać przy użyciu lambda asynchronii w [Instrukcji AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="789ea-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="789ea-149">Aby dodać ten program `Async` obsługi, dodaj modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="789ea-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="789ea-150">Aby uzyskać więcej informacji na temat tworzenia i używania metod [asynchronicznych, zobacz Programowanie asynchroniczne za pomocą asynchronii i Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="789ea-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="789ea-151">Kontekst</span><span class="sxs-lookup"><span data-stu-id="789ea-151">Context</span></span>

<span data-ttu-id="789ea-152">Wyrażenie lambda udostępnia swój kontekst z zakresem, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="789ea-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="789ea-153">Ma takie same prawa dostępu, jak każdy kod napisany w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="789ea-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="789ea-154">Obejmuje to dostęp do zmiennych członkowskich, funkcji i subs oraz `Me`parametrów i zmiennych lokalnych w zakresie zawierającym.</span><span class="sxs-lookup"><span data-stu-id="789ea-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="789ea-155">Dostęp do zmiennych lokalnych i parametrów w zakresie zawierającym może wykraczać poza okres istnienia tego zakresu.</span><span class="sxs-lookup"><span data-stu-id="789ea-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="789ea-156">Tak długo, jak delegat odnoszący się do wyrażenia lambda nie jest dostępny do wyrzucania elementów bezużytecznych, dostęp do zmiennych w środowisku oryginalnym jest zachowywany.</span><span class="sxs-lookup"><span data-stu-id="789ea-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="789ea-157">W poniższym przykładzie zmienna `target` jest lokalna do `makeTheGame`, `playTheGame` metoda, w której wyrażenie lambda jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="789ea-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="789ea-158">Należy zauważyć, że zwrócone wyrażenie `takeAGuess` lambda, przypisane do w `Main`programie , nadal ma dostęp do zmiennej `target`lokalnej .</span><span class="sxs-lookup"><span data-stu-id="789ea-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="789ea-159">W poniższym przykładzie przedstawiono szeroki zakres praw dostępu wyrażenia lambda zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="789ea-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="789ea-160">Gdy zwrócone wyrażenie lambda `Main` `aDel`jest wykonywane z as , uzyskuje dostęp do tych elementów:</span><span class="sxs-lookup"><span data-stu-id="789ea-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="789ea-161">Pole klasy, w której jest zdefiniowane:`aField`</span><span class="sxs-lookup"><span data-stu-id="789ea-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="789ea-162">Właściwość klasy, w której jest zdefiniowana:`aProp`</span><span class="sxs-lookup"><span data-stu-id="789ea-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="789ea-163">Parametr metody, `functionWithNestedLambda`w którym jest zdefiniowany:`level1`</span><span class="sxs-lookup"><span data-stu-id="789ea-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="789ea-164">Zmienna lokalna: `functionWithNestedLambda``localVar`</span><span class="sxs-lookup"><span data-stu-id="789ea-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="789ea-165">Parametr wyrażenia lambda, w którym jest zagnieżdżony:`level2`</span><span class="sxs-lookup"><span data-stu-id="789ea-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="789ea-166">Konwertowanie na typ delegata</span><span class="sxs-lookup"><span data-stu-id="789ea-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="789ea-167">Wyrażenie lambda można niejawnie przekonwertować na zgodny typ delegata.</span><span class="sxs-lookup"><span data-stu-id="789ea-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="789ea-168">Aby uzyskać informacje na temat ogólnych wymagań dotyczących zgodności, zobacz [Zrelaksowana konwersja delegata](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="789ea-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="789ea-169">Na przykład w poniższym przykładzie kodu pokazano wyrażenie lambda, które niejawnie konwertuje do `Func(Of Integer, Boolean)` lub pasujące podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="789ea-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="789ea-170">Poniższy przykład kodu pokazuje wyrażenie lambda, `Sub(Of Double, String, Double)` które niejawnie konwertuje do lub pasujące podpis delegata.</span><span class="sxs-lookup"><span data-stu-id="789ea-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="789ea-171">Po przypisaniu wyrażeń lambda do delegatów lub przekazać je jako argumenty do procedur, można określić nazwy parametrów, ale pominąć ich typy danych, pozwalając typy być pobierane od pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="789ea-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="789ea-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="789ea-172">Examples</span></span>

- <span data-ttu-id="789ea-173">Poniższy przykład definiuje wyrażenie lambda, które zwraca, `True` jeśli argument typu wartości `False` nullable `Nothing`ma przypisaną wartość, a jeśli jego wartość jest .</span><span class="sxs-lookup"><span data-stu-id="789ea-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="789ea-174">Poniższy przykład definiuje wyrażenie lambda, który zwraca indeks ostatniego elementu w tablicy.</span><span class="sxs-lookup"><span data-stu-id="789ea-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="789ea-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="789ea-175">See also</span></span>

- [<span data-ttu-id="789ea-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="789ea-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="789ea-177">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="789ea-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="789ea-178">Delegaty</span><span class="sxs-lookup"><span data-stu-id="789ea-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="789ea-179">Instrukcja funkcji</span><span class="sxs-lookup"><span data-stu-id="789ea-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="789ea-180">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="789ea-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="789ea-181">Typy o wartości zerowalnej</span><span class="sxs-lookup"><span data-stu-id="789ea-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="789ea-182">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="789ea-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="789ea-183">Porady: tworzenie wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="789ea-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="789ea-184">Swobodna konwersja delegatów</span><span class="sxs-lookup"><span data-stu-id="789ea-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
