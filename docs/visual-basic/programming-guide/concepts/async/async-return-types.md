---
title: Asynchroniczne typy zwracane (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: f85b3ec536033fd6d3cdec8f5a6ac4f9f66077f3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524331"
---
# <a name="async-return-types-visual-basic"></a>Asynchroniczne typy zwracane (Visual Basic)

Metody asynchroniczne mają trzy możliwe typy zwracane: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> i void. W Visual Basic typ zwracany void jest zapisywana jako procedura [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) . Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Każdy typ zwracany jest badany w jednej z poniższych sekcji i można znaleźć pełny przykład, który używa wszystkich trzech typów na końcu tematu.

> [!NOTE]
> Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="BKMK_TaskTReturnType"></a>Typ zwracany zadania (T)

Typ zwracany <xref:System.Threading.Tasks.Task%601> jest używany dla metody asynchronicznej, która zawiera instrukcję [Return](../../../../visual-basic/language-reference/statements/return-statement.md) , w której operand ma typ `TResult`.

W poniższym przykładzie metoda async `TaskOfT_MethodAsync` zawiera instrukcję return, która zwraca liczbę całkowitą. W związku z tym Deklaracja metody musi określać zwracany typ `Task(Of Integer)`.

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

Gdy `TaskOfT_MethodAsync` jest wywoływana z w wyrażeniu await, wyrażenie await Pobiera wartość całkowitą (wartość `leisureHours`) przechowywaną w zadaniu, które jest zwracane przez `TaskOfT_MethodAsync`. Aby uzyskać więcej informacji na temat wyrażeń await, zobacz [operator await](../../../../visual-basic/language-reference/operators/await-operator.md).

Poniższy kod wywołuje i czeka na metodę `TaskOfT_MethodAsync`. Wynik jest przypisywany do zmiennej `result1`.

```vb
' Call and await the Task(Of T)-returning async method in the same statement.
Dim result1 As Integer = Await TaskOfT_MethodAsync()
```

Można lepiej zrozumieć, jak to się dzieje, oddzielając wywołanie do `TaskOfT_MethodAsync` z aplikacji `Await`, jak pokazano w poniższym kodzie. Wywołanie metody `TaskOfT_MethodAsync`, która nie oczekuje od razu, zwraca `Task(Of Integer)`, jak oczekiwano od deklaracji metody. Zadanie jest przypisane do zmiennej `integerTask` w przykładzie. Ponieważ `integerTask` jest <xref:System.Threading.Tasks.Task%601>, zawiera właściwość <xref:System.Threading.Tasks.Task%601.Result> typu `TResult`. W tym przypadku TResult reprezentuje typ Integer. Gdy `Await` jest stosowany do `integerTask`, wyrażenie await zwróci zawartość właściwości <xref:System.Threading.Tasks.Task%601.Result%2A> `integerTask`. Wartość jest przypisana do zmiennej `result2`.

> [!WARNING]
> Właściwość <xref:System.Threading.Tasks.Task%601.Result%2A> jest właściwością blokującą. Jeśli spróbujesz uzyskać dostęp do niego przed ukończeniem zadania, wątek, który jest obecnie aktywny, jest blokowany do momentu zakończenia zadania, a wartość jest dostępna. W większości przypadków należy uzyskać dostęp do wartości przy użyciu `Await` zamiast bezpośrednio uzyskać dostęp do właściwości.

```vb
' Call and await in separate statements.
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()

' You can do other work that does not rely on resultTask before awaiting.
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)

Dim result2 As Integer = Await integerTask
```

Instrukcje Display w poniższym kodzie weryfikują, że wartości zmiennej `result1`, zmiennej `result2` i właściwości `Result` są takie same. Należy pamiętać, że właściwość `Result` jest właściwością blokującą i nie należy uzyskać do niej dostępu, zanim jej zadanie nie zostanie oczekiwane.

```vb
' Display the values of the result1 variable, the result2 variable, and
' the resultTask.Result property.
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)
```

## <a name="BKMK_TaskReturnType"></a>Typ zwracany zadania

Metody asynchroniczne, które nie zawierają instrukcji return lub zawierające instrukcję return, która nie zwraca operandu, zwykle mają zwracany typ <xref:System.Threading.Tasks.Task>. Takie metody byłyby procedurami [podrzędnymi](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , jeśli zostały wykonane synchronicznie. Jeśli używasz `Task` zwracanego typu dla metody asynchronicznej, Metoda wywołująca może użyć operatora `Await`, aby zawiesić zakończenie procesu wywołującego do momentu zakończenia wywołanej metody asynchronicznej.

W poniższym przykładzie metoda async `Task_MethodAsync` nie zawiera instrukcji return. W związku z tym należy określić zwracany typ `Task` dla metody, która umożliwia `Task_MethodAsync` oczekiwać. Definicja typu `Task` nie zawiera właściwości `Result` do przechowywania wartości zwracanej.

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

`Task_MethodAsync` jest wywoływana i oczekiwana przy użyciu instrukcji Await zamiast wyrażenia await, podobnie jak instrukcja wywołująca dla metody synchronicznej `Sub` lub void-zwracającej. W tym przypadku aplikacja operatora `Await` nie tworzy wartości.

Poniższy kod wywołuje i czeka na metodę `Task_MethodAsync`.

```vb
' Call and await the Task-returning async method in the same statement.
Await Task_MethodAsync()
```

Tak jak w poprzednim <xref:System.Threading.Tasks.Task%601> przykładzie, można oddzielić wywołanie `Task_MethodAsync` z aplikacji operatora `Await`, jak pokazano w poniższym kodzie. Należy jednak pamiętać, że `Task` nie ma właściwości `Result` i żadna wartość nie jest generowana, gdy operator await jest stosowany do `Task`.

Poniższy kod oddziela wywoływanie `Task_MethodAsync` od oczekiwania na zadanie, które `Task_MethodAsync` zwraca.

```vb
' Call and await in separate statements.
Dim simpleTask As Task = Task_MethodAsync()

' You can do other work that does not rely on simpleTask before awaiting.
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)

Await simpleTask
```

## <a name="BKMK_VoidReturnType"></a>Typ zwracany void

Podstawowe użycie procedur `Sub` znajduje się w obsłudze zdarzeń, gdzie nie ma żadnego typu zwracanego (nazywanego typem zwracanym void w innych językach). Zwracanego typu void można użyć do przesłaniania metod typu void lub dla metod wykonujących działania, które można podzielić na kategorie jako "pożar i zapomnij". Należy jednak zwrócić `Task`, wszędzie tam, gdzie jest to możliwe, ponieważ nie można oczekiwać metody asynchronicznej zwracającej wartość void. Każdy obiekt wywołujący taką metodę musi być w stanie kontynuować ukończenie bez oczekiwania na zakończenie wywołanej metody asynchronicznej, a obiekt wywołujący musi być niezależny od wartości lub wyjątków, które generuje Metoda asynchroniczna.

Obiekt wywołujący metodę asynchroniczną zwracającą wartość void nie może przechwytywać wyjątków, które są generowane przez metodę, a takie Nieobsłużone wyjątki mogą spowodować niepowodzenie działania aplikacji. Jeśli wystąpi wyjątek w metodzie asynchronicznej, która zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>, wyjątek jest przechowywany w zwracanym zadaniu i ponownie zgłaszany po oczekiwaniu na zadanie. W związku z tym upewnij się, że każda Metoda asynchroniczna, która może generować wyjątek, ma zwracany typ <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601> i że wywołania metody są oczekiwane.

Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz [try... Catch... Finally — instrukcja](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).

Poniższy kod definiuje procedurę obsługi zdarzeń asynchronicznych.

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

## <a name="BKMK_Example"></a>Pełny przykład

Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykłady kodu z tego tematu.

 Aby uruchomić projekt, wykonaj następujące czynności:

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W kategorii **zainstalowane**, **szablony** wybierz pozycję **Visual Basic**, a następnie wybierz pozycję **Windows**. Wybierz **aplikację WPF** z listy typów projektów.

4. Wprowadź `AsyncReturnTypes` jako nazwę projektu, a następnie wybierz przycisk **OK** .

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

5. W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .

     Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Otwórz**.

6. W oknie **XAML** MainWindow. XAML Zastąp kod następującym kodem.

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

     Proste okno zawierające pole tekstowe i przycisk pojawia się w oknie **projekt** MainWindow. XAML.

7. W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.

8. Zastąp kod w MainWindow. XAML. vb następującym kodem.

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

9. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

     Powinny pojawić się następujące dane wyjściowe:

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przepływ sterowania w programach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
