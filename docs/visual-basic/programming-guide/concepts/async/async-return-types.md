---
title: Asynchroniczne typy zwracane (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: a5553070dd68a0bc3eaad1c5e8c000f7a31f8783
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423969"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="7042e-102">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7042e-102">Async Return Types (Visual Basic)</span></span>

<span data-ttu-id="7042e-103">Metody asynchroniczne mają trzy możliwe typy zwracane: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>i void.</span><span class="sxs-lookup"><span data-stu-id="7042e-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="7042e-104">W Visual Basic typ zwracany void jest zapisywana jako procedura [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) .</span><span class="sxs-lookup"><span data-stu-id="7042e-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="7042e-105">Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7042e-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="7042e-106">Każdy typ zwracany jest badany w jednej z poniższych sekcji i można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tematu.</span><span class="sxs-lookup"><span data-stu-id="7042e-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>

> [!NOTE]
> <span data-ttu-id="7042e-107">Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="7042e-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_TaskTReturnType"></a><span data-ttu-id="7042e-108">Typ zwracany zadania (T)</span><span class="sxs-lookup"><span data-stu-id="7042e-108">Task(T) Return Type</span></span>

<span data-ttu-id="7042e-109">Typ zwracany <xref:System.Threading.Tasks.Task%601> jest używany dla metody asynchronicznej, która zawiera instrukcję [Return](../../../../visual-basic/language-reference/statements/return-statement.md) , w której operand ma typ `TResult`.</span><span class="sxs-lookup"><span data-stu-id="7042e-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>

<span data-ttu-id="7042e-110">W poniższym przykładzie metoda async `TaskOfT_MethodAsync` zawiera instrukcję return, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="7042e-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="7042e-111">W związku z tym Deklaracja metody musi określać zwracany typ `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="7042e-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>

```vb
' TASK(OF T) EXAMPLE
Async Function TaskOfT_MethodAsync() As Task(Of Integer)

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.FromResult is a placeholder for actual work that returns a string.
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

    ' The method then can process the result in some way.
    Dim leisureHours As Integer
    If today.First() = "S" Then
        leisureHours = 16
    Else
        leisureHours = 5
    End If

    ' Because the return statement specifies an operand of type Integer, the
    ' method must have a return type of Task(Of Integer).
    Return leisureHours
End Function
```

<span data-ttu-id="7042e-112">Gdy `TaskOfT_MethodAsync` jest wywoływana z w wyrażeniu await, wyrażenie await Pobiera wartość całkowitą (wartość `leisureHours`) przechowywaną w zadaniu, które jest zwracane przez `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="7042e-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="7042e-113">Aby uzyskać więcej informacji na temat wyrażeń await, zobacz [operator await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="7042e-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>

<span data-ttu-id="7042e-114">Poniższy kod wywołuje i czeka na metodę `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="7042e-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="7042e-115">Wynik jest przypisywany do zmiennej `result1`.</span><span class="sxs-lookup"><span data-stu-id="7042e-115">The result is assigned to the `result1` variable.</span></span>

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

<span data-ttu-id="7042e-116">Można lepiej zrozumieć, jak to się dzieje, oddzielając wywołanie do `TaskOfT_MethodAsync` z aplikacji `Await`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7042e-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="7042e-117">Wywołanie metody `TaskOfT_MethodAsync`, która nie oczekuje od razu, zwraca `Task(Of Integer)`, jak oczekiwano od deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="7042e-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="7042e-118">Zadanie jest przypisane do zmiennej `integerTask` w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="7042e-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="7042e-119">Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera właściwość <xref:System.Threading.Tasks.Task%601.Result> typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="7042e-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="7042e-120">W tym przypadku TResult reprezentuje typ Integer.</span><span class="sxs-lookup"><span data-stu-id="7042e-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="7042e-121">Gdy `Await` jest stosowany do `integerTask`, wyrażenie await zwróci zawartość właściwości <xref:System.Threading.Tasks.Task%601.Result%2A> `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="7042e-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="7042e-122">Wartość jest przypisana do zmiennej `result2`.</span><span class="sxs-lookup"><span data-stu-id="7042e-122">The value is assigned to the `result2` variable.</span></span>

> [!WARNING]
> <span data-ttu-id="7042e-123">Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> jest właściwością blokującą.</span><span class="sxs-lookup"><span data-stu-id="7042e-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="7042e-124">Jeśli spróbujesz uzyskać dostęp do niego przed ukończeniem zadania, wątek, który jest obecnie aktywny, jest blokowany do momentu zakończenia zadania, a wartość jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="7042e-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="7042e-125">W większości przypadków należy uzyskać dostęp do wartości przy użyciu `Await` zamiast bezpośrednio uzyskać dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="7042e-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

Dim result2 As Integer = Await integerTask
```

<span data-ttu-id="7042e-126">Instrukcje Display w poniższym kodzie weryfikują, że wartości zmiennej `result1`, zmiennej `result2` i właściwości `Result` są takie same.</span><span class="sxs-lookup"><span data-stu-id="7042e-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="7042e-127">Należy pamiętać, że właściwość `Result` jest właściwością blokującą i nie należy uzyskać do niej dostępu, zanim jej zadanie nie zostanie oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="7042e-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf
```

## <a name="BKMK_TaskReturnType"></a><span data-ttu-id="7042e-128">Typ zwracany zadania</span><span class="sxs-lookup"><span data-stu-id="7042e-128">Task Return Type</span></span>

<span data-ttu-id="7042e-129">Metody asynchroniczne, które nie zawierają instrukcji return lub zawierające instrukcję return, która nie zwraca operandu, zwykle mają zwracany typ <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="7042e-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="7042e-130">Takie metody byłyby procedurami [podrzędnymi](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , jeśli zostały wykonane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="7042e-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="7042e-131">Jeśli używasz `Task` zwracanego typu dla metody asynchronicznej, Metoda wywołująca może użyć operatora `Await`, aby zawiesić zakończenie procesu wywołującego do momentu zakończenia wywołanej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="7042e-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>

<span data-ttu-id="7042e-132">W poniższym przykładzie metoda async `Task_MethodAsync` nie zawiera instrukcji return.</span><span class="sxs-lookup"><span data-stu-id="7042e-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="7042e-133">W związku z tym należy określić zwracany typ `Task` dla metody, która umożliwia `Task_MethodAsync` oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="7042e-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="7042e-134">Definicja typu `Task` nie zawiera właściwości `Result` do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="7042e-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>

```vb
' TASK EXAMPLE
Async Function Task_MethodAsync() As Task

    ' The body of an async method is expected to contain an awaited
    ' asynchronous call.
    ' Task.Delay is a placeholder for actual work.
    Await Task.Delay(2000)
    textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

    ' This method has no return statement, so its return type is Task.
End Function
```

<span data-ttu-id="7042e-135">`Task_MethodAsync` jest wywoływana i oczekiwana przy użyciu instrukcji Await zamiast wyrażenia await, podobnie jak instrukcja wywołująca dla metody synchronicznej `Sub` lub void-zwracającej.</span><span class="sxs-lookup"><span data-stu-id="7042e-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="7042e-136">W tym przypadku aplikacja operatora `Await` nie tworzy wartości.</span><span class="sxs-lookup"><span data-stu-id="7042e-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>

<span data-ttu-id="7042e-137">Poniższy kod wywołuje i czeka na metodę `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="7042e-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

<span data-ttu-id="7042e-138">Tak jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykładzie, można oddzielić wywołanie `Task_MethodAsync` z aplikacji operatora `Await`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="7042e-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="7042e-139">Należy jednak pamiętać, że `Task` nie ma właściwości `Result` i żadna wartość nie jest generowana, gdy operator await jest stosowany do `Task`.</span><span class="sxs-lookup"><span data-stu-id="7042e-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>

<span data-ttu-id="7042e-140">Poniższy kod oddziela wywoływanie `Task_MethodAsync` od oczekiwania na zadanie, które `Task_MethodAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="7042e-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a><span data-ttu-id="7042e-141">Typ zwracany void</span><span class="sxs-lookup"><span data-stu-id="7042e-141">Void Return Type</span></span>

<span data-ttu-id="7042e-142">Podstawowe użycie procedur `Sub` znajduje się w obsłudze zdarzeń, gdzie nie ma żadnego typu zwracanego (nazywanego typem zwracanym void w innych językach).</span><span class="sxs-lookup"><span data-stu-id="7042e-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="7042e-143">Zwracanego typu void można użyć do przesłaniania metod typu void lub dla metod wykonujących działania, które można podzielić na kategorie jako "pożar i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="7042e-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="7042e-144">Należy jednak zwrócić `Task`, wszędzie tam, gdzie jest to możliwe, ponieważ nie można oczekiwać metody asynchronicznej zwracającej wartość void.</span><span class="sxs-lookup"><span data-stu-id="7042e-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="7042e-145">Każdy obiekt wywołujący taką metodę musi być w stanie kontynuować ukończenie bez oczekiwania na zakończenie wywołanej metody asynchronicznej, a obiekt wywołujący musi być niezależny od wartości lub wyjątków, które generuje Metoda asynchroniczna.</span><span class="sxs-lookup"><span data-stu-id="7042e-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>

<span data-ttu-id="7042e-146">Obiekt wywołujący metodę asynchroniczną zwracającą wartość void nie może przechwytywać wyjątków, które są generowane przez metodę, a takie Nieobsłużone wyjątki mogą spowodować niepowodzenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7042e-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="7042e-147">Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwracanym zadaniu i ponownie zgłaszany po oczekiwaniu na zadanie.</span><span class="sxs-lookup"><span data-stu-id="7042e-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="7042e-148">W związku z tym upewnij się, że każda Metoda asynchroniczna, która może generować wyjątek, ma zwracany typ <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="7042e-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>

<span data-ttu-id="7042e-149">Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7042e-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>

<span data-ttu-id="7042e-150">Poniższy kod definiuje procedurę obsługi zdarzeń asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="7042e-150">The following code defines an async event handler.</span></span>

```vb
' SUB EXAMPLE
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

    textBox1.Clear()

    ' Start the process and await its completion. DriverAsync is a
    ' Task-returning async method.
    Await DriverAsync()

    ' Say goodbye.
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
End Sub
```

## <a name="BKMK_Example"></a><span data-ttu-id="7042e-151">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="7042e-151">Complete Example</span></span>

<span data-ttu-id="7042e-152">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykłady kodu z tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7042e-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>

 <span data-ttu-id="7042e-153">Aby uruchomić projekt, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7042e-153">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="7042e-154">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7042e-154">Start Visual Studio.</span></span>

2. <span data-ttu-id="7042e-155">Na pasku menu wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="7042e-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="7042e-156">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="7042e-156">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="7042e-157">W kategorii **zainstalowane**, **szablony** wybierz pozycję **Visual Basic**, a następnie wybierz pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="7042e-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="7042e-158">Wybierz **aplikację WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="7042e-158">Choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="7042e-159">Wprowadź `AsyncReturnTypes` jako nazwę projektu, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="7042e-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="7042e-160">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="7042e-160">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="7042e-161">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="7042e-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="7042e-162">Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="7042e-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>

6. <span data-ttu-id="7042e-163">W oknie **XAML** MainWindow. XAML Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="7042e-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window x:Class="MainWindow"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            Title="MainWindow" Height="350" Width="525">
        <Grid>
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>

        </Grid>
    </Window>
    ```

     <span data-ttu-id="7042e-164">Proste okno zawierające pole tekstowe i przycisk pojawia się w oknie **projekt** MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="7042e-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>

7. <span data-ttu-id="7042e-165">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="7042e-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

8. <span data-ttu-id="7042e-166">Zastąp kod w MainWindow. XAML. vb następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="7042e-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>

    ```vb
    Class MainWindow

        ' SUB EXAMPLE
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click

            textBox1.Clear()

            ' Start the process and await its completion. DriverAsync is a
            ' Task-returning async method.
            Await DriverAsync()

            ' Say goodbye.
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."
        End Sub

        Async Function DriverAsync() As Task

            ' Task(Of T)
            ' Call and await the Task(Of T)-returning async method in the same statement.
            Dim result1 As Integer = Await TaskOfT_MethodAsync()

            ' Call and await in separate statements.
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

            ' You can do other work that does not rely on resultTask before awaiting.
            textBox1.Text &= "Application can continue working while the Task(Of T) runs. . . . " & vbCrLf

            Dim result2 As Integer = Await integerTask

            ' Display the values of the result1 variable, the result2 variable, and
            ' the resultTask.Result property.
            textBox1.Text &= vbCrLf & $"Value of result1 variable:   {result1}" & vbCrLf
            textBox1.Text &= $"Value of result2 variable:   {result2}" & vbCrLf
            textBox1.Text &= $"Value of resultTask.Result:  {integerTask.Result}" & vbCrLf

            ' Task
            ' Call and await the Task-returning async method in the same statement.
            Await Task_MethodAsync()

            ' Call and await in separate statements.
            Dim simpleTask As Task = Task_MethodAsync()

            ' You can do other work that does not rely on simpleTask before awaiting.
            textBox1.Text &= vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf

            Await simpleTask
        End Function

        ' TASK(OF T) EXAMPLE
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.FromResult is a placeholder for actual work that returns a string.
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())

            ' The method then can process the result in some way.
            Dim leisureHours As Integer
            If today.First() = "S" Then
                leisureHours = 16
            Else
                leisureHours = 5
            End If

            ' Because the return statement specifies an operand of type Integer, the
            ' method must have a return type of Task(Of Integer).
            Return leisureHours
        End Function

        ' TASK EXAMPLE
        Async Function Task_MethodAsync() As Task

            ' The body of an async method is expected to contain an awaited
            ' asynchronous call.
            ' Task.Delay is a placeholder for actual work.
            Await Task.Delay(2000)
            textBox1.Text &= vbCrLf & "Sorry for the delay. . . ." & vbCrLf

            ' This method has no return statement, so its return type is Task.
        End Function

    End Class
    ```

9. <span data-ttu-id="7042e-167">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="7042e-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="7042e-168">Powinny pojawić się następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7042e-168">The following output should appear:</span></span>

    ```console
    Application can continue working while the Task<T> runs. . . .

    Value of result1 variable:   5
    Value of result2 variable:   5
    Value of integerTask.Result: 5

    Sorry for the delay. . . .

    Application can continue working while the Task runs. . . .

    Sorry for the delay. . . .

    All done, exiting button-click event handler.
    ```

## <a name="see-also"></a><span data-ttu-id="7042e-169">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7042e-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="7042e-170">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7042e-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="7042e-171">Przepływ sterowania w programach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7042e-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="7042e-172">Async</span><span class="sxs-lookup"><span data-stu-id="7042e-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="7042e-173">Await, operator</span><span class="sxs-lookup"><span data-stu-id="7042e-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
