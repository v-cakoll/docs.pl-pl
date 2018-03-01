---
title: "Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0d0a5e7c50bacc657a3f54a7f08036ede59cbfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a>Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane do czasu ukończenia wywołania
Ponieważ to wywołanie nie jest oczekiwane, wykonywanie bieżącej metody będzie kontynuowane ukończenia wywołania. Należy rozważyć zastosowanie operatora "Await" do wyniku wywołania.  
  
 Bieżąca metoda wywołuje metody asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i nie ma zastosowania [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator do wyniku. Wywołanie metody asynchronicznej uruchamia zadanie asynchroniczne. Jednakże ponieważ nie `Await` zastosować operatora, program będzie kontynuowane bez oczekiwania na zakończenie zadania. W większości przypadków tego zachowania nie jest oczekiwany. Zazwyczaj inne aspekty wywołania metody są zależne od wyników wywołania, lub migrację wywołaną metodę oczekuje na ukończenie zwracany przez metodę, która zawiera wywołanie.  
  
 Problem równie ważne jest, co się dzieje z wyjątków, które są wywoływane w metodzie async o nazwie. Wyjątek jest zgłaszany w metodę, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> znajduje się w zwracanych zadań. Jeśli nie await zadania lub jawnie sprawdziła wyjątków, wyjątki zostaną utracone. Jeśli await zadania, jego wyjątku jest zgłoszony.  
  
 Najlepszym rozwiązaniem zawsze należy poczekać na wywołanie.  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC42358  
  
### <a name="to-address-this-warning"></a>W celu rozwiązania tego ostrzeżenia  
  
-   Należy rozważyć tylko wtedy, gdy wiesz, że nie chcesz czekać na wywołanie asynchroniczne do ukończenia i że wywołaną metodę nie będą zgłaszać wyjątki z pominięciem ostrzeżenia. W takim przypadku można pominąć to ostrzeżenie, przypisując wyniku zadania wywołania do zmiennej.  
  
     Poniższy przykład przedstawia sposób spowodować ostrzeżenia, sposób wyłączania go oraz sposobu await wywołania.  
  
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
  
     W tym przykładzie wybierz wywołać #1 lub wywołać #2 metody asynchronicznej unawaited (`CalledMethodAsync`) kończy się po obu wywołującego (`CallingMethodAsync`) i wywołującego wywołującego (`StartButton_Click`) są spełnione. W ostatnim wierszu następujących danych wyjściowych zawiera po zakończeniu wywołaną metodę. Wejście do i wyjście z obsługi zdarzeń, który wywołuje `CallingMethodAsync` w pełny przykład są oznaczone w danych wyjściowych.  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a>Przykład  
 Następującej aplikacji Windows Presentation Foundation (WPF) zawiera metody z poprzedniego przykładu. Poniższe kroki skonfigurować aplikację.  
  
1.  Tworzenie aplikacji WPF i nadaj mu nazwę `AsyncWarning`.  
  
2.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
     Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.  
  
3.  Zastąp kod w **XAML** widoku MainWindow.xaml następującym kodem.  
  
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
  
     Proste okna, który zawiera przycisk i pole tekstowe zostanie wyświetlony w **projekt** widoku MainWindow.xaml.  
  
     Aby uzyskać więcej informacji na temat projektanta XAML, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio). Aby dowiedzieć się, jak tworzyć własne prostego interfejsu użytkownika, zobacz "Aby utworzyć aplikację programu WPF" i "projektowania proste właściwości MainWindow WPF" sekcje [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).  
  
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
  
     Oczekiwane dane wyjściowe pojawia się na końcu kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Await — Operator](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Programowanie asynchroniczne z Async i Await](../../../visual-basic/programming-guide/concepts/async/index.md)
