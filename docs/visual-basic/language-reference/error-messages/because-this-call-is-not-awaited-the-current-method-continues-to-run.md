---
title: Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: fe820b9d2157c09428903a36427d3ff5e4c0045b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45619178"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="5e4f1-102">Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania</span><span class="sxs-lookup"><span data-stu-id="5e4f1-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="5e4f1-103">Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane bez oczekiwania na ukończenie wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="5e4f1-104">Należy rozważyć zastosowanie operatora "Await" do wyniku wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="5e4f1-105">Bieżąca metoda wywołuje metody asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i nie ma zastosowania [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora do wyniku.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="5e4f1-106">Wywołanie metody asynchronicznej uruchamia zadanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="5e4f1-107">Jednakże ponieważ nie `Await` jest stosowany operator, działanie programu jest kontynuowane bez oczekiwania na zakończenie zadania.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="5e4f1-108">W większości przypadków to zachowanie nie jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="5e4f1-109">Zazwyczaj inne aspekty wywoływania metody są zależne od wyników wywołania, lub co najmniej wywoływana metoda oczekuje na ukończenie powrocie z metody, która zawiera wywołanie.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="5e4f1-110">Równie ważne problem polega na tym, co się dzieje z wyjątków, które są wywoływane w wywołanej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="5e4f1-111">Wyjątek, który jest wywoływany w metodzie, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> jest przechowywany w zwróconym zadaniu.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="5e4f1-112">Jeśli nie poczekać na zadanie, lub jawnie szukać wyjątków, wyjątki zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="5e4f1-113">Jeśli włączysz zadania, jego wyjątek jest zgłaszany ponownie.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="5e4f1-114">Najlepszym rozwiązaniem jest zawsze należy poczekać na wywołanie.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="5e4f1-115">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-115">By default, this message is a warning.</span></span> <span data-ttu-id="5e4f1-116">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5e4f1-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5e4f1-117">**Identyfikator błędu:** BC42358</span><span class="sxs-lookup"><span data-stu-id="5e4f1-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="5e4f1-118">Aby rozwiązać tego ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="5e4f1-118">To address this warning</span></span>  
  
-   <span data-ttu-id="5e4f1-119">Należy rozważyć pominięcie ostrzeżenia, tylko wtedy, gdy wiesz, że nie chcesz czekać na ukończenie asynchronicznego wywołania i czy wywoływanej metody nie będzie zgłaszać żadnych wyjątków.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="5e4f1-120">W takim przypadku można pominąć to ostrzeżenie, przypisując wynik zadania wywołania ze zmienną.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="5e4f1-121">Poniższy przykład pokazuje, jak spowodować, że to ostrzeżenie, jak pomijanie go i instrukcje await wywołania.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
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
  
     <span data-ttu-id="5e4f1-122">W przykładzie, jeśli wybierzesz wywołać #1 lub wywołać nr 2, metoda unawaited async (`CalledMethodAsync`) kończy się po obu obiektu wywołującego (`CallingMethodAsync`) i element wywołujący wywołującego (`StartButton_Click`) są kompletne.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="5e4f1-123">W ostatnim wierszu następujące dane wyjściowe pokazuje, po zakończeniu wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="5e4f1-124">Wpisu i wyjścia z programu obsługi zdarzeń, który wywołuje `CallingMethodAsync` w pełnym przykładzie są oznaczone w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="5e4f1-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e4f1-125">Example</span></span>  
 <span data-ttu-id="5e4f1-126">Następującej aplikacji Windows Presentation Foundation (WPF) zawiera metody z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="5e4f1-127">Poniższe kroki. Konfigurowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="5e4f1-128">Tworzenie aplikacji WPF i nadaj mu nazwę `AsyncWarning`.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="5e4f1-129">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="5e4f1-130">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="5e4f1-131">Zastąp kod w **XAML** widok pliku MainWindow.xaml w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
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
  
     <span data-ttu-id="5e4f1-132">Proste okno, która zawiera przycisk i pole tekstowe, pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="5e4f1-133">Aby uzyskać więcej informacji dotyczących projektanta XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5e4f1-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="5e4f1-134">Aby uzyskać informacje dotyczące sposobu tworzenia własnych prostego interfejsu użytkownika, zobacz "Aby utworzyć aplikację programu WPF" i "projektowania proste MainWindow WPF" sekcje [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5e4f1-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
4.  <span data-ttu-id="5e4f1-135">Zastąp kod w MainWindow.xaml.vb następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
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
  
5.  <span data-ttu-id="5e4f1-136">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="5e4f1-137">Oczekiwane dane wyjściowe pojawia się na końcu kod.</span><span class="sxs-lookup"><span data-stu-id="5e4f1-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e4f1-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e4f1-138">See also</span></span>

- [<span data-ttu-id="5e4f1-139">Await, operator</span><span class="sxs-lookup"><span data-stu-id="5e4f1-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
- [<span data-ttu-id="5e4f1-140">Programowanie asynchroniczne z Async i Await</span><span class="sxs-lookup"><span data-stu-id="5e4f1-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
