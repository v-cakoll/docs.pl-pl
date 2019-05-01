---
title: Asynchroniczne typy zwracane (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: 227a187f7046d128a7170b272f90f77cfaac61c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022106"
---
# <a name="async-return-types-visual-basic"></a>Asynchroniczne typy zwracane (Visual Basic)
Metody asynchroniczne mają trzy możliwe zwracane typy: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>oraz typ void. W języku Visual Basic, zwrócony typ void jest napisany w postaci [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedury. Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Każdy typ zwracany jest badany w jednej z następujących sekcji, a można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tego tematu.  
  
> [!NOTE]
>  Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="BKMK_TaskTReturnType"></a> Zwracany typ Task(T)  
 <xref:System.Threading.Tasks.Task%601> Typ zwracany jest używany w metodzie asynchronicznej, która zawiera [zwracają](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcji, w której operator ma typ `TResult`.  
  
 W poniższym przykładzie `TaskOfT_MethodAsync` metoda asynchronicza zawiera instrukcję return, która zwraca liczbę całkowitą. Dlatego deklaracja metody musi określać typ zwracany `Task(Of Integer)`.  
  
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
  
 Gdy `TaskOfT_MethodAsync` jest wywoływana z poziomu wyrażenia await, wyrażenie await pobiera wartość całkowitą (wartość `leisureHours`) jest przechowywana w zadaniu, który jest zwracany przez `TaskOfT_MethodAsync`. Aby uzyskać więcej informacji dotyczących wyrażeń oczekiwania, zobacz [operatora Await](../../../../visual-basic/language-reference/operators/await-operator.md).  
  
 Poniższy kod wywołuje i czeka na metodę `TaskOfT_MethodAsync`. Wynik jest przypisany do `result1` zmiennej.  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 Można lepiej zrozumieć, jak to się dzieje oddzielając wywołanie `TaskOfT_MethodAsync` ze stosowania `Await`, jak pokazano w poniższym kodzie. Wywołanie metody `TaskOfT_MethodAsync` , która nie jest oczekiwana natychmiast zwraca `Task(Of Integer)`, jak można oczekiwać od deklaracji metody. Zadanie zostanie przypisane do `integerTask` zmiennej w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera on <xref:System.Threading.Tasks.Task%601.Result> właściwości typu `TResult`. W tym przypadku TResult reprezentuje typ liczby całkowitej. Gdy `Await` jest stosowany do `integerTask`, wyrażenie czekania zwraca wynik zawartość <xref:System.Threading.Tasks.Task%601.Result%2A> właściwość `integerTask`. Wartość jest przypisywana do `result2` zmiennej.  
  
> [!WARNING]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> Właściwość jest właściwością blokowania. Jeśli spróbujesz się do niej dostęp przed zakończeniem jej zadania, wątek, który jest obecnie aktywny jest zablokowany do momentu ukończenia zadania i wartość jest dostępna. W większości przypadków należy dostęp do wartości przy użyciu `Await` zamiast bezpośrednio dostęp do właściwości.  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 Instrukcje wyświetlania w poniższym kodzie upewnij się, że wartości `result1` zmiennej `result2` zmienną i `Result` właściwości są takie same. Należy pamiętać, że `Result` właściwość jest właściwością blokowania i nie powinna być dostępna zanim jej zadanie nie było oczekiwane.  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> Zwracany typ Task  
 Metody asynchroniczne, które nie zawierają instrukcji return lub zawierają instrukcję return, która nie zwraca operandu są zazwyczaj ma typ zwracany <xref:System.Threading.Tasks.Task>. Takie metody byłyby [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedur, gdyby były one napisane, aby były uruchamiane synchronicznie. Jeśli używasz `Task` zwracany typ metody asynchronicznej, wywoływania metody można użyć `Await` operator wstrzymania uzupełniania wywołującego do momentu zakończenia wywołanej metody asynchronicznej.  
  
 W poniższym przykładzie metoda asynchroniczna `Task_MethodAsync` nie zawiera instrukcji return. Dlatego należy określić typ zwracany `Task` dla metody, które umożliwia `Task_MethodAsync` oczekiwanie. Definicja `Task` nie zawiera typu `Result` właściwość do przechowywania wartości zwracanej.  
  
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
  
 `Task_MethodAsync` jest nazywana i oczekiwane za pomocą instrukcji await, a nie wyrażenia await, podobnie do instrukcji wywołujące synchronicznej procedury `Sub` lub metodę zwracającą typ void. Stosowanie `Await` operatora w tym przypadku nie zwraca wartości.  
  
 Poniższy kod wywołuje i czeka na metodę `Task_MethodAsync`.  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 Jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykład, można oddzielić wywołanie `Task_MethodAsync` ze stosowania `Await` operatora, co ilustruje poniższy kod. Jednak należy pamiętać, że `Task` nie ma `Result` właściwość i że wartość nie jest generowany, gdy await operator jest stosowany do `Task`.  
  
 Poniższy kod oddziela wywoływanie metody `Task_MethodAsync` od oczekiwania na zadanie, które `Task_MethodAsync` zwraca.  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> Typ zwracany void  
 Podstawowym zastosowaniem `Sub` procedury znajduje się w procedury obsługi zdarzeń, gdy istnieje bez zwrotu typu (nazywane zwracać typ void w innych językach). Zwracany typ void również mogą być używane do zastępowania metod zwracających wartość void lub dla metod, które wykonują czynności, które można skategoryzować jako "fire and forget." Jednak powinna zwrócić `Task` wszędzie tam, gdzie to możliwe, ponieważ metoda async zwraca void nie może być oczekiwany. Dowolny obiekt wywołujący taką metodę musi być w stanie kontynuować do zakończenia bez oczekiwania na zakończenie metody asynchronicznej, a obiekt wywołujący musi być niezależny od wartości lub wyjątków, które generuje metoda asynchroniczna.  
  
 Obiekt wywołujący metodę async zwraca void nie może przechwytywać wyjątków, które są generowane przez tę metodę, i takie nieobsłużone wyjątki mogą może spowodować awarię aplikacji. Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwróconym zadaniu i ponownie zgłaszany, gdy zadanie jest oczekiwane. Dlatego upewnij się, że każda metoda asynchroniczna, która może spowodować wyjątek ma typ zwracany <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że trwa oczekiwanie na wywołania metody.  
  
 Aby uzyskać więcej informacji dotyczących wyjątków CATCH w metodach asynchronicznych, zobacz [spróbuj... CATCH... Na koniec instrukcji](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
 Poniższy kod definiuje obsługę zdarzeń async.  
  
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
  
## <a name="BKMK_Example"></a> Kompletny przykład  
 Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykłady kodu z tego tematu.  
  
 Aby uruchomić projekt, należy wykonać następujące czynności:  
  
1. Uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3. W **zainstalowane**, **szablony** kategorii, wybierz **języka Visual Basic**, a następnie wybierz **Windows**. Wybierz **aplikacji WPF** z listy typów projektów.  
  
4. Wprowadź `AsyncReturnTypes` jako nazwę projektu, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
5. W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.  
  
     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Otwórz**.  
  
6. W **XAML** okna pliku mainwindow.XAML, Zastąp kod następującym kodem.  
  
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
  
     Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** okna MainWindow.xaml.  
  
7. W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **Wyświetl kod**.  
  
8. Zastąp kod w MainWindow.xaml.vb następującym kodem.  
  
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
  
     Powinien pojawić się następujące dane wyjściowe.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
