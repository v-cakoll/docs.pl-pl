---
title: Asynchroniczne typy zwracane (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="6b498-102">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b498-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="6b498-103">Metody asynchroniczne ma trzy możliwe typy zwracane: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, a typ void.</span><span class="sxs-lookup"><span data-stu-id="6b498-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="6b498-104">W języku Visual Basic zwrócony typ void jest zapisywany jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury.</span><span class="sxs-lookup"><span data-stu-id="6b498-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="6b498-105">Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6b498-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="6b498-106">Każdy typ zwracany jest sprawdzany w jednej z następujących sekcji, a znajduje się pełny przykład, który używa wszystkich trzech typów na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6b498-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b498-107">Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6b498-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="6b498-108">Zwracany typ Task(T)</span><span class="sxs-lookup"><span data-stu-id="6b498-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="6b498-109"><xref:System.Threading.Tasks.Task%601> Zwracany typ jest używany dla metody asynchronicznej, który zawiera [zwracać](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcji, w którym argument operacji ma typ `TResult`.</span><span class="sxs-lookup"><span data-stu-id="6b498-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="6b498-110">W poniższym przykładzie `TaskOfT_MethodAsync` metody asynchronicznej zawiera instrukcję return, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="6b498-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="6b498-111">W związku z tym deklaracji metody należy określić typ zwracany `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="6b498-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
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
  
 <span data-ttu-id="6b498-112">Gdy `TaskOfT_MethodAsync` jest wywoływana z wewnątrz wyrażenie await wyrażenie await pobiera wartość całkowita (wartość `leisureHours`) przechowywanego w zadaniu, który jest zwracany przez `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b498-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6b498-113">Aby uzyskać więcej informacji na temat await wyrażeń, zobacz [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md).</span><span class="sxs-lookup"><span data-stu-id="6b498-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="6b498-114">Poniższy kod wywołuje i oczekujące na metodę `TaskOfT_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b498-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6b498-115">Wynik jest przypisany do `result1` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6b498-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="6b498-116">Lepiej zrozumieć, jak dzieje się tak, dzieląc wywołanie `TaskOfT_MethodAsync` ze stosowania `Await`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6b498-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="6b498-117">Wywołanie metody `TaskOfT_MethodAsync` , która nie jest od razu oczekiwano zwraca `Task(Of Integer)`, jak można oczekiwać od deklaracji metody.</span><span class="sxs-lookup"><span data-stu-id="6b498-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="6b498-118">Zadanie jest przypisany do `integerTask` zmiennej w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6b498-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="6b498-119">Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera <xref:System.Threading.Tasks.Task%601.Result> właściwości typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="6b498-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="6b498-120">W takim przypadku TResult reprezentuje typu integer.</span><span class="sxs-lookup"><span data-stu-id="6b498-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="6b498-121">Gdy `Await` jest stosowany do `integerTask`, wyrażenie await ma zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość `integerTask`.</span><span class="sxs-lookup"><span data-stu-id="6b498-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="6b498-122">Wartość jest przypisywana do `result2` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6b498-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="6b498-123"><xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokowania.</span><span class="sxs-lookup"><span data-stu-id="6b498-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="6b498-124">Jeśli spróbujesz się do niego dostęp, przed jego zadanie jest zakończone, wątku, który jest obecnie aktywny jest zablokowany, dopiero po zakończeniu zadania i wartość jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="6b498-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="6b498-125">W większości przypadków, uzyskaniu dostępu wartość w przy użyciu `Await` zamiast bezpośrednie uzyskiwanie dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b498-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="6b498-126">Instrukcje wyświetlania w poniższym kodzie upewnij się, że wartości `result1` zmiennej `result2` zmienną i `Result` właściwości są takie same.</span><span class="sxs-lookup"><span data-stu-id="6b498-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="6b498-127">Należy pamiętać, że `Result` właściwość jest właściwością blokowania i nie można uzyskać dostępu do przed jego zadania zostały oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6b498-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="6b498-128">Zwracany typ zadania</span><span class="sxs-lookup"><span data-stu-id="6b498-128">Task Return Type</span></span>  
 <span data-ttu-id="6b498-129">Metody asynchroniczne, które nie zawierają instrukcji return lub zawierają instrukcji return, która nie zwraca zwykle argumentu operacji ma typ zwracany <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="6b498-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6b498-130">Takie metody są [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury, jeśli zostały one zapisane uruchamiane synchronicznie.</span><span class="sxs-lookup"><span data-stu-id="6b498-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="6b498-131">Jeśli używasz `Task` typ zwracany dla metody asynchronicznej metody wywołującej można użyć `Await` operatora, aby wstrzymać ukończenia wywołującego przed zakończeniem metody asynchronicznej o nazwie.</span><span class="sxs-lookup"><span data-stu-id="6b498-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="6b498-132">W poniższym przykładzie metoda asynchroniczna `Task_MethodAsync` nie zawiera instrukcji return.</span><span class="sxs-lookup"><span data-stu-id="6b498-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="6b498-133">W związku z tym, określ typ zwracany `Task` metody, które umożliwia `Task_MethodAsync` do można zdefiniować dla niego oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="6b498-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="6b498-134">Definicja `Task` nie zawiera typu `Result` właściwości do przechowywania wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="6b498-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="6b498-135">`Task_MethodAsync` jest nazywane i oczekiwane przy użyciu instrukcji await zamiast wyrażenie await, podobna do instrukcji wywoływania dla synchronicznego `Sub` lub metody zwracające typ void.</span><span class="sxs-lookup"><span data-stu-id="6b498-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="6b498-136">Stosowanie `Await` operatora w takim przypadku nie tworzy wartości.</span><span class="sxs-lookup"><span data-stu-id="6b498-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="6b498-137">Poniższy kod wywołuje i oczekujące na metodę `Task_MethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="6b498-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="6b498-138">Jak w poprzedniej <xref:System.Threading.Tasks.Task%601> przykładzie można oddzielić wywołanie `Task_MethodAsync` ze stosowania `Await` operatora, jak przedstawiono na poniższym kodem.</span><span class="sxs-lookup"><span data-stu-id="6b498-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="6b498-139">Należy jednak pamiętać, że `Task` nie ma `Result` właściwości i że żadna wartość jest generowany po zastosowaniu operatora await do `Task`.</span><span class="sxs-lookup"><span data-stu-id="6b498-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="6b498-140">Poniższy kod oddziela wywoływania `Task_MethodAsync` z oczekiwanie na zadanie który `Task_MethodAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="6b498-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="6b498-141">Zwrócony typ void</span><span class="sxs-lookup"><span data-stu-id="6b498-141">Void Return Type</span></span>  
 <span data-ttu-id="6b498-142">Podstawowym zastosowaniem `Sub` jest procedury obsługi zdarzeń w przypadku, gdy nie ma zwracanego typu (nazywane zwrócony typ void w innych językach).</span><span class="sxs-lookup"><span data-stu-id="6b498-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="6b498-143">Zwracany typ void można również zastąpić metody zwracające typ void lub dla metod, które wykonują działania, które mogą być podzielone jako "wyzwalać i zapomnij."</span><span class="sxs-lookup"><span data-stu-id="6b498-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="6b498-144">Należy jednak zwrócić `Task` wszędzie tam, gdzie to możliwe, ponieważ nie może być oczekiwane asynchronicznej metody zwracające typ void.</span><span class="sxs-lookup"><span data-stu-id="6b498-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="6b498-145">Wszelkie wywołującego taka metoda musi mieć możliwość nadal ukończenia bez oczekiwania na metody asynchronicznej wywołany zakończyć, a obiekt wywołujący musi być niezależne od dowolnej wartości lub wyjątki, które generuje metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="6b498-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="6b498-146">Obiekt wywołujący metody asynchronicznej zwracające typ void nie może przechwycić wyjątki, które są generowane przez metodę i takich nieobsługiwanych wyjątków są może spowodować awarię aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6b498-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="6b498-147">Jeśli wystąpi wyjątek w to metoda asynchroniczna, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, przechowywane w zadaniu zwrócony wyjątek i zgłoszony, gdy zadanie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6b498-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="6b498-148">W związku z tym, upewnij się, że wszystkie metoda asynchroniczna, która może spowodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6b498-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="6b498-149">Aby uzyskać więcej informacji o sposobie przechwytywanie wyjątków w metodach asynchronicznych, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6b498-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="6b498-150">Poniższy kod definiuje asynchronicznej obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6b498-150">The following code defines an async event handler.</span></span>  
  
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
  
##  <a name="BKMK_Example"></a> <span data-ttu-id="6b498-151">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="6b498-151">Complete Example</span></span>  
 <span data-ttu-id="6b498-152">Następujący projekt Windows Presentation Foundation (WPF) zawiera przykładowy kod z tego tematu.</span><span class="sxs-lookup"><span data-stu-id="6b498-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="6b498-153">Aby uruchomić projekt, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6b498-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="6b498-154">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6b498-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6b498-155">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6b498-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="6b498-156">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6b498-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6b498-157">W **zainstalowana**, **szablony** kategorii, wybierz **Visual Basic**, a następnie wybierz pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="6b498-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="6b498-158">Wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="6b498-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="6b498-159">Wprowadź `AsyncReturnTypes` jako nazwę projektu, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="6b498-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="6b498-160">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="6b498-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="6b498-161">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="6b498-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="6b498-162">Jeśli karta nie jest widoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="6b498-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="6b498-163">W **XAML** okna MainWindow.xaml, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6b498-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="6b498-164">Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** okna MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="6b498-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="6b498-165">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="6b498-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="6b498-166">Zastąp kod w MainWindow.xaml.vb następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6b498-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
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
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="6b498-167">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="6b498-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="6b498-168">Następujące dane wyjściowe powinny być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="6b498-168">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6b498-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b498-169">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [<span data-ttu-id="6b498-170">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b498-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="6b498-171">Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b498-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [<span data-ttu-id="6b498-172">Async</span><span class="sxs-lookup"><span data-stu-id="6b498-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="6b498-173">Await, operator</span><span class="sxs-lookup"><span data-stu-id="6b498-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
