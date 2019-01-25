---
title: Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania
ms.date: 07/20/2015
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
ms.openlocfilehash: 5c8767db154c79d9e3b37a22410ac1e4705b7a44
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609802"
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania
Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane bez oczekiwania na ukończenie wywołania. Należy rozważyć zastosowanie operatora "Await" do wyniku wywołania.  
  
 Bieżąca metoda wywołuje metody asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i nie ma zastosowania [Await](../../../visual-basic/language-reference/operators/await-operator.md) operatora do wyniku. Wywołanie metody asynchronicznej uruchamia zadanie asynchroniczne. Jednakże ponieważ nie `Await` jest stosowany operator, działanie programu jest kontynuowane bez oczekiwania na zakończenie zadania. W większości przypadków to zachowanie nie jest oczekiwany. Zazwyczaj inne aspekty wywoływania metody są zależne od wyników wywołania, lub co najmniej wywoływana metoda oczekuje na ukończenie powrocie z metody, która zawiera wywołanie.  
  
 Równie ważne problem polega na tym, co się dzieje z wyjątków, które są wywoływane w wywołanej metody asynchronicznej. Wyjątek, który jest wywoływany w metodzie, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> jest przechowywany w zwróconym zadaniu. Jeśli nie poczekać na zadanie, lub jawnie szukać wyjątków, wyjątki zostaną utracone. Jeśli włączysz zadania, jego wyjątek jest zgłaszany ponownie.  
  
 Najlepszym rozwiązaniem jest zawsze należy poczekać na wywołanie.  
  
 Domyślnie ta wiadomość jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42358  
  
### <a name="to-address-this-warning"></a>Aby rozwiązać tego ostrzeżenia  
  
-   Należy rozważyć pominięcie ostrzeżenia, tylko wtedy, gdy wiesz, że nie chcesz czekać na ukończenie asynchronicznego wywołania i czy wywoływanej metody nie będzie zgłaszać żadnych wyjątków. W takim przypadku można pominąć to ostrzeżenie, przypisując wynik zadania wywołania ze zmienną.  
  
     Poniższy przykład pokazuje, jak spowodować, że to ostrzeżenie, jak pomijanie go i instrukcje await wywołania.  
  
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
  
     W przykładzie, jeśli wybierzesz wywołać #1 lub wywołać nr 2, metoda unawaited async (`CalledMethodAsync`) kończy się po obu obiektu wywołującego (`CallingMethodAsync`) i element wywołujący wywołującego (`StartButton_Click`) są kompletne. W ostatnim wierszu następujące dane wyjściowe pokazuje, po zakończeniu wywoływanej metody. Wpisu i wyjścia z programu obsługi zdarzeń, który wywołuje `CallingMethodAsync` w pełnym przykładzie są oznaczone w danych wyjściowych.  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji Windows Presentation Foundation (WPF) zawiera metody z poprzedniego przykładu. Poniższe kroki. Konfigurowanie aplikacji.  
  
1.  Tworzenie aplikacji WPF i nadaj mu nazwę `AsyncWarning`.  
  
2.  W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.  
  
     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.  
  
3.  Zastąp kod w **XAML** widok pliku MainWindow.xaml w następującym kodem.  
  
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
  
     Proste okno, która zawiera przycisk i pole tekstowe, pojawia się w **projektowania** widoku MainWindow.xaml.  
  
     Aby uzyskać więcej informacji dotyczących projektanta XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Aby uzyskać informacje dotyczące sposobu tworzenia własnych prostego interfejsu użytkownika, zobacz "Aby utworzyć aplikację programu WPF" i "projektowania proste MainWindow WPF" sekcje [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
4.  Zastąp kod w MainWindow.xaml.vb następującym kodem.  
  
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
  
5.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Oczekiwane dane wyjściowe pojawia się na końcu kod.  
  
## <a name="see-also"></a>Zobacz także

- [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)
