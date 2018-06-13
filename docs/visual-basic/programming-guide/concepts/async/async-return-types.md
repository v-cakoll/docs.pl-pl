---
title: Asynchroniczne typy zwracane (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 0c6c02efd282f8581f3dc85905149acf7b3ea6ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644085"
---
# <a name="async-return-types-visual-basic"></a>Asynchroniczne typy zwracane (Visual Basic)
Metody asynchroniczne ma trzy możliwe typy zwracane: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, a typ void. W języku Visual Basic zwrócony typ void jest zapisywany jako [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury. Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Każdy typ zwracany jest sprawdzany w jednej z następujących sekcji, a znajduje się pełny przykład, który używa wszystkich trzech typów na końcu tego tematu.  
  
> [!NOTE]
>  Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
##  <a name="BKMK_TaskTReturnType"></a> Zwracany typ Task(T)  
 <xref:System.Threading.Tasks.Task%601> Zwracany typ jest używany dla metody asynchronicznej, który zawiera [zwracać](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcji, w którym argument operacji ma typ `TResult`.  
  
 W poniższym przykładzie `TaskOfT_MethodAsync` metody asynchronicznej zawiera instrukcję return, która zwraca liczbę całkowitą. W związku z tym deklaracji metody należy określić typ zwracany `Task(Of Integer)`.  
  
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
  
 Gdy `TaskOfT_MethodAsync` jest wywoływana z wewnątrz wyrażenie await wyrażenie await pobiera wartość całkowita (wartość `leisureHours`) przechowywanego w zadaniu, który jest zwracany przez `TaskOfT_MethodAsync`. Aby uzyskać więcej informacji na temat await wyrażeń, zobacz [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Poniższy kod wywołuje i oczekujące na metodę `TaskOfT_MethodAsync`. Wynik jest przypisany do `result1` zmiennej.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Lepiej zrozumieć, jak dzieje się tak, dzieląc wywołanie `TaskOfT_MethodAsync` ze stosowania `Await`, jak pokazano w następującym kodem. Wywołanie metody `TaskOfT_MethodAsync` , która nie jest od razu oczekiwano zwraca `Task(Of Integer)`, jak można oczekiwać od deklaracji metody. Zadanie jest przypisany do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera <xref:System.Threading.Tasks.Task%601.Result> właściwości typu `TResult`. W takim przypadku TResult reprezentuje typu integer. Gdy `Await` jest stosowany do `integerTask`, wyrażenie await ma zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość `integerTask`. Wartość jest przypisywana do `result2` zmiennej.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokowania. Jeśli spróbujesz się do niego dostęp, przed jego zadanie jest zakończone, wątku, który jest obecnie aktywny jest zablokowany, dopiero po zakończeniu zadania i wartość jest dostępna. W większości przypadków, uzyskaniu dostępu wartość w przy użyciu `Await` zamiast bezpośrednie uzyskiwanie dostępu do właściwości.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Instrukcje wyświetlania w poniższym kodzie upewnij się, że wartości `result1` zmiennej `result2` zmienną i `Result` właściwości są takie same. Należy pamiętać, że `Result` właściwość jest właściwością blokowania i nie można uzyskać dostępu do przed jego zadania zostały oczekiwane.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Zwracany typ zadania  
 Metody asynchroniczne, które nie zawierają instrukcji return lub zawierają instrukcji return, która nie zwraca zwykle argumentu operacji ma typ zwracany <xref:System.Threading.Tasks.Task>. Takie metody są [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury, jeśli zostały one zapisane uruchamiane synchronicznie. Jeśli używasz `Task` typ zwracany dla metody asynchronicznej metody wywołującej można użyć `Await` operatora, aby wstrzymać ukończenia wywołującego przed zakończeniem metody asynchronicznej o nazwie.  
  
 W poniższym przykładzie metoda asynchroniczna `Task_MethodAsync` nie zawiera instrukcji return. W związku z tym, określ typ zwracany `Task` metody, które umożliwia `Task_MethodAsync` do można zdefiniować dla niego oczekiwania. Definicja `Task` nie zawiera typu `Result` właściwości do przechowywania wartości zwracanej.  
  
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
  
 `Task_MethodAsync` jest nazywane i oczekiwane przy użyciu instrukcji await zamiast wyrażenie await, podobna do instrukcji wywoływania dla synchronicznego `Sub` lub metody zwracające typ void. Stosowanie `Await` operatora w takim przypadku nie tworzy wartości.  
  
 Poniższy kod wywołuje i oczekujące na metodę `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Jak w poprzedniej <xref:System.Threading.Tasks.Task%601> przykładzie można oddzielić wywołanie `Task_MethodAsync` ze stosowania `Await` operatora, jak przedstawiono na poniższym kodem. Należy jednak pamiętać, że `Task` nie ma `Result` właściwości i że żadna wartość jest generowany po zastosowaniu operatora await do `Task`.  
  
 Poniższy kod oddziela wywoływania `Task_MethodAsync` z oczekiwanie na zadanie który `Task_MethodAsync` zwraca.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
##  <a name="BKMK_VoidReturnType"></a> Zwrócony typ void  
 Podstawowym zastosowaniem `Sub` jest procedury obsługi zdarzeń w przypadku, gdy nie ma zwracanego typu (nazywane zwrócony typ void w innych językach). Zwracany typ void można również zastąpić metody zwracające typ void lub dla metod, które wykonują działania, które mogą być podzielone jako "wyzwalać i zapomnij." Należy jednak zwrócić `Task` wszędzie tam, gdzie to możliwe, ponieważ nie może być oczekiwane asynchronicznej metody zwracające typ void. Wszelkie wywołującego taka metoda musi mieć możliwość nadal ukończenia bez oczekiwania na metody asynchronicznej wywołany zakończyć, a obiekt wywołujący musi być niezależne od dowolnej wartości lub wyjątki, które generuje metody asynchronicznej.  
  
 Obiekt wywołujący metody asynchronicznej zwracające typ void nie może przechwycić wyjątki, które są generowane przez metodę i takich nieobsługiwanych wyjątków są może spowodować awarię aplikacji. Jeśli wystąpi wyjątek w to metoda asynchroniczna, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, przechowywane w zadaniu zwrócony wyjątek i zgłoszony, gdy zadanie jest oczekiwane. W związku z tym, upewnij się, że wszystkie metoda asynchroniczna, która może spowodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.  
  
 Aby uzyskać więcej informacji o sposobie przechwytywanie wyjątków w metodach asynchronicznych, zobacz [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Poniższy kod definiuje asynchronicznej obsługi zdarzeń.  
  
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
  
##  <a name="BKMK_Example"></a> Pełny przykład  
 Następujący projekt Windows Presentation Foundation (WPF) zawiera przykładowy kod z tego tematu.  
  
 Aby uruchomić projekt, wykonaj następujące czynności:  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowana**, **szablony** kategorii, wybierz **Visual Basic**, a następnie wybierz pozycję **Windows**. Wybierz **aplikacji WPF** z listy typów projektów.  
  
4.  Wprowadź `AsyncReturnTypes` jako nazwę projektu, a następnie wybierz pozycję **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
5.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
     Jeśli karta nie jest widoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **Otwórz**.  
  
6.  W **XAML** okna MainWindow.xaml, Zastąp kod następującym kodem.  
  
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
  
     Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** okna MainWindow.xaml.  
  
7.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **kod widoku**.  
  
8.  Zastąp kod w MainWindow.xaml.vb następującym kodem.  
  
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
  
9. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Następujące dane wyjściowe powinny być wyświetlane.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task.FromResult%2A>  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)  
 [Async](../../../../visual-basic/language-reference/modifiers/async.md)  
 [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
