---
title: Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 754fc6750e63f6d9f39da94041fc452829bca46d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591437"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="f0fd4-102">Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania</span><span class="sxs-lookup"><span data-stu-id="f0fd4-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="f0fd4-103">Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane ukończenia wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="f0fd4-104">Należy rozważyć zastosowanie operatora "Await" do wyniku wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="f0fd4-105">Bieżąca metoda wywołuje metody asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i nie ma zastosowania [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator do wyniku.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="f0fd4-106">Wywołanie metody asynchronicznej uruchamia zadanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="f0fd4-107">Jednakże ponieważ nie `Await` zastosować operatora, program będzie kontynuowane bez oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="f0fd4-108">W większości przypadków tego zachowania nie jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="f0fd4-109">Zazwyczaj inne aspekty wywołania metody są zależne od wyników wywołania, lub migrację wywołaną metodę oczekuje na ukończenie zwracany przez metodę, która zawiera wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="f0fd4-110">Problem równie ważne jest, co się dzieje z wyjątków, które są wywoływane w metodzie async o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="f0fd4-111">Wyjątek jest zgłaszany w metodę, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> znajduje się w zwracanych zadań.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="f0fd4-112">Jeśli nie await zadania lub jawnie sprawdziła wyjątków, wyjątki zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="f0fd4-113">Jeśli await zadania, jego wyjątku jest zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="f0fd4-114">Najlepszym rozwiązaniem zawsze należy poczekać na wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="f0fd4-115">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-115">By default, this message is a warning.</span></span> <span data-ttu-id="f0fd4-116">Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f0fd4-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f0fd4-117">**Identyfikator błędu:** BC42358</span><span class="sxs-lookup"><span data-stu-id="f0fd4-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="f0fd4-118">W celu rozwiązania tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="f0fd4-118">To address this warning</span></span>  
  
-   <span data-ttu-id="f0fd4-119">Należy rozważyć tylko wtedy, gdy wiesz, że nie chcesz czekać na wywołanie asynchroniczne do ukończenia i że wywołaną metodę nie będą zgłaszać wyjątki z pominięciem ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="f0fd4-120">W takim przypadku można pominąć to ostrzeżenie, przypisując wyniku zadania wywołania do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="f0fd4-121">Poniższy przykład przedstawia sposób spowodować ostrzeżenia, sposób wyłączania go oraz sposobu await wywołania.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
    ```vb  
    Async Function CallingMethodAsync() As Task  
  
        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
        ' Variable delay is used to slow down the called method so that you  
        ' can distinguish between awaiting and not awaiting in the program's output.   
        ' You can adjust the value to produce the output that this topic shows   
        ' after the code.  
        Dim delay = 5000  
  
        ' Call #1.  
        ' Call an async method. Because you don't await it, its completion isn't   
        ' coordinated with the current method, CallingMethodAsync.  
        ' The following line causes the warning.  
        CalledMethodAsync(delay)  
  
        ' Call #2.  
        ' To suppress the warning without awaiting, you can assign the   
        ' returned task to a variable. The assignment doesn't change how  
        ' the program runs. However, the recommended practice is always to  
        ' await a call to an async method.  
        ' Replace Call #1 with the following line.  
        'Task delayTask = CalledMethodAsync(delay)  
  
        ' Call #3  
        ' To contrast with an awaited call, replace the unawaited call   
        ' (Call #1 or Call #2) with the following awaited call. The best   
        ' practice is to await the call.  
  
        'Await CalledMethodAsync(delay)  
  
        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
        ' continues to run and, in this example, finishes its work and returns  
        ' to its caller.  
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
    End Function  
  
    Async Function CalledMethodAsync(howLong As Integer) As Task  
  
        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
        ' Slow the process down a little so you can distinguish between awaiting  
        ' and not awaiting. Adjust the value for howLong if necessary.  
        Await Task.Delay(howLong)  
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
    End Function  
    ```  
  
     <span data-ttu-id="f0fd4-122">W tym przykładzie wybierz wywołać #1 lub wywołać #2 metody asynchronicznej unawaited (`CalledMethodAsync`) kończy się po obu wywołującego (`CallingMethodAsync`) i wywołującego wywołującego (`StartButton_Click`) są spełnione.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="f0fd4-123">W ostatnim wierszu następujących danych wyjściowych zawiera po zakończeniu wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="f0fd4-124">Wejście do i wyjście z obsługi zdarzeń, który wywołuje `CallingMethodAsync` w pełny przykład są oznaczone w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="f0fd4-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0fd4-125">Example</span></span>  
 <span data-ttu-id="f0fd4-126">Następującej aplikacji Windows Presentation Foundation (WPF) zawiera metody z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="f0fd4-127">Poniższe kroki skonfigurować aplikację.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="f0fd4-128">Tworzenie aplikacji WPF i nadaj mu nazwę `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="f0fd4-129">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="f0fd4-130">Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="f0fd4-131">Zastąp kod w **XAML** widoku MainWindow.xaml następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />  
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="f0fd4-132">Proste okna, który zawiera przycisk i pole tekstowe zostanie wyświetlony w **projekt** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="f0fd4-133">Aby uzyskać więcej informacji na temat projektanta XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f0fd4-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="f0fd4-134">Aby dowiedzieć się, jak tworzyć własne prostego interfejsu użytkownika, zobacz "Aby utworzyć aplikację programu WPF" i "projektowania proste właściwości MainWindow WPF" sekcje [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span><span class="sxs-lookup"><span data-stu-id="f0fd4-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="f0fd4-135">Zastąp kod w MainWindow.xaml.vb następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow   
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."  
            Await CallingMethodAsync()  
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."  
        End Sub  
  
        Async Function CallingMethodAsync() As Task  
  
            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
            ' Variable delay is used to slow down the called method so that you  
            ' can distinguish between awaiting and not awaiting in the program's output.   
            ' You can adjust the value to produce the output that this topic shows   
            ' after the code.  
            Dim delay = 5000  
  
            ' Call #1.  
            ' Call an async method. Because you don't await it, its completion isn't   
            ' coordinated with the current method, CallingMethodAsync.  
            ' The following line causes the warning.  
            CalledMethodAsync(delay)  
  
            ' Call #2.  
            ' To suppress the warning without awaiting, you can assign the   
            ' returned task to a variable. The assignment doesn't change how  
            ' the program runs. However, the recommended practice is always to  
            ' await a call to an async method.  
  
            ' Replace Call #1 with the following line.  
            'Task delayTask = CalledMethodAsync(delay)  
  
            ' Call #3  
            ' To contrast with an awaited call, replace the unawaited call   
            ' (Call #1 or Call #2) with the following awaited call. The best   
            ' practice is to await the call.  
  
            'Await CalledMethodAsync(delay)  
  
            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
            ' continues to run and, in this example, finishes its work and returns  
            ' to its caller.  
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
        End Function  
  
        Async Function CalledMethodAsync(howLong As Integer) As Task  
  
            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
            ' Slow the process down a little so you can distinguish between awaiting  
            ' and not awaiting. Adjust the value for howLong if necessary.  
            Await Task.Delay(howLong)  
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
        End Function  
  
    End Class  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    '     Task.Delay is finished--returning from called method.  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '     Task.Delay is finished--returning from called method.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    ```  
  
5.  <span data-ttu-id="f0fd4-136">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="f0fd4-137">Oczekiwane dane wyjściowe pojawia się na końcu kodu.</span><span class="sxs-lookup"><span data-stu-id="f0fd4-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fd4-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0fd4-138">See Also</span></span>  
 [<span data-ttu-id="f0fd4-139">Await, operator</span><span class="sxs-lookup"><span data-stu-id="f0fd4-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="f0fd4-140">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="f0fd4-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
