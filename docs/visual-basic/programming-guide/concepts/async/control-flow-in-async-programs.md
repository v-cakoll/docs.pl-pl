---
title: Przepływ sterowania w programach asynchronicznych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 265efde93cec87594a0407309b58b6bdf11817af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630598"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Przepływ sterowania w programach asynchronicznych (Visual Basic)

Można łatwiej pisać i konserwować programy asynchroniczne przy użyciu `Async` słów kluczowych i. `Await` Jednak wyniki mogą być niewidoczne, jeśli nie zrozumiesz, jak działa program. Ten temat śledzi przepływ kontroli za pośrednictwem prostego programu asynchronicznego, aby pokazać, gdy kontrolka przechodzi z jednej metody do innej i jakie informacje są przesyłane za każdym razem.

> [!NOTE]
> Słowa kluczowe `Await` i zostały wprowadzone w programie Visual Studio 2012. `Async`

Ogólnie rzecz biorąc, należy oznaczyć metody, które zawierają kod asynchroniczny z modyfikatorem [asynchronicznym](../../../../visual-basic/language-reference/modifiers/async.md) . W metodzie, która jest oznaczona za pomocą modyfikatora asynchronicznego, można użyć operatora [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) , aby określić miejsce wstrzymania metody do oczekiwania na zakończenie wywołanego procesu asynchronicznego. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

W poniższym przykładzie zastosowano metody asynchroniczne, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu. Przykład zawiera poniższe dwie metody.

- `startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetlają wynik.

- `AccessTheWebAsync`, która pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu. `AccessTheWebAsync`używa metody asynchronicznej <xref:System.Net.Http.HttpClient> , <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>aby pobrać zawartość.

Numerowane linie wyświetlania pojawiają się w punktach strategicznych w całym programie, aby pomóc zrozumieć, jak działa program, i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony. Linie wyświetlania są oznaczone jako "ONE" do "SZÓSTe". Etykiety reprezentują kolejność, w której program osiągnie te wiersze kodu.

Poniższy kod przedstawia kontur programu.

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

Każda z oznaczonych lokalizacji "jeden" do "SZÓSTy" wyświetla informacje o bieżącym stanie programu. Generowane są następujące dane wyjściowe.

```
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a>Konfigurowanie programu

Możesz pobrać kod, który jest wykorzystywany przez ten temat w witrynie MSDN, lub możesz utworzyć go samodzielnie.

> [!NOTE]
> Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

### <a name="download-the-program"></a>Pobierz program

Możesz pobrać aplikację dla tego tematu z [przykładu asynchronicznego: Przepływ sterowania w programach](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)asynchronicznych. Poniższe kroki otwierają i uruchamiają program.

1. Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

3. Przejdź do folderu, który zawiera niespakowany przykładowy kod, Otwórz plik rozwiązania (. sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.

### <a name="build-the-program-yourself"></a>Kompiluj program samodzielnie

Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu dla tego tematu.

Aby uruchomić projekt, wykonaj następujące czynności:

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku**, **New**, **projektu**.

    **Nowy projekt** zostanie otwarte okno dialogowe.

3. W okienku **zainstalowane szablony** wybierz pozycję **Visual Basic**, a następnie wybierz pozycję **Aplikacja WPF** z listy typów projektów.

4. Wprowadź `AsyncTracer` nazwę projektu, a następnie wybierz przycisk **OK** .

    Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

5. W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .

    Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.

6. W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    Proste okno zawierające pole tekstowe i przycisk pojawia się w widoku **projekt** MainWindow. XAML.

7. Dodaj odwołanie do <xref:System.Net.Http>.

8. W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.

9. W MainWindow. XAML. vb Zastąp kod następującym kodem.

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

    Powinny pojawić się następujące dane wyjściowe.

    ```
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a>Śledzenie programu

### <a name="steps-one-and-two"></a>Kroki jeden i dwa

Pierwsze dwa wyświetlane wiersze `startButton_Click` śledzą ścieżkę jako wywołania `AccessTheWebAsync`i `AccessTheWebAsync` wywołania metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>asynchronicznej <xref:System.Net.Http.HttpClient> . Na poniższej ilustracji przedstawiono wywołania metody do metody.

![Kroki jeden i dwa](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace — ONETWO")

Zwracany typ obu `AccessTheWebAsync` i `client.GetStringAsync` to <xref:System.Threading.Tasks.Task%601>. Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą. Dla `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat typów zwracanych metody asynchronicznej, zobacz [asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

Metoda asynchroniczna zwracająca zadanie zwraca wystąpienie zadania, gdy kontrolka przesunie się z powrotem do obiektu wywołującego. Kontrolka zwraca z metody asynchronicznej do obiektu wywołującego, `Await` gdy w wywołanej metodzie zostanie napotkany operator lub gdy wywołana metoda zostanie zakończona. Linie wyświetlania oznaczone etykietą "trzy" do "sześć" śledzą tę część procesu.

### <a name="step-three"></a>Krok trzeci

W `AccessTheWebAsync`programie wywoływana jest metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> asynchroniczna, aby pobrać zawartość docelowej strony sieci Web. Kontrolka zwraca `client.GetStringAsync` z `AccessTheWebAsync` do `client.GetStringAsync` , gdy zwraca.

Metoda zwraca zadanie ciągu, który jest przypisany `getStringTask` do zmiennej w `AccessTheWebAsync`. `client.GetStringAsync` Poniższy wiersz w przykładowym programie pokazuje wywołanie `client.GetStringAsync` i przypisanie.

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

Możesz traktować zadanie jako obietnicę, `client.GetStringAsync` aby utworzyć rzeczywisty ciąg ostatecznie. W międzyczasie, jeśli `AccessTheWebAsync` program ma pracę, która nie jest zależna od uzgodnionego ciągu z `client.GetStringAsync`, to działanie może być `client.GetStringAsync` kontynuowane podczas oczekiwania. W przykładzie następujące wiersze danych wyjściowych, które są oznaczone etykietą "trzy", reprezentują możliwość wykonania niezależnej pracy

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Poniższa instrukcja zawiesza postęp w `AccessTheWebAsync` czasie `getStringTask` oczekiwania.

```vb
Dim urlContents As String = Await getStringTask
```

Na poniższej ilustracji przedstawiono przepływ sterowania z `client.GetStringAsync` do `getStringTask` przypisania do `getStringTask` i od tworzenia do aplikacji operatora await.

![Krok trzeci](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace — trzy")

Wyrażenie await zawiesza `AccessTheWebAsync` się do momentu `client.GetStringAsync` powracania. W międzyczasie sterowanie powraca do obiektu wywołującego `AccessTheWebAsync`,. `startButton_Click`

> [!NOTE]
> Zwykle oczekujesz natychmiastowego wywołania metody asynchronicznej. Na przykład następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka `getStringTask`na:`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`
>
> W tym temacie operator await jest stosowany później, aby pomieścić linie wyjściowe, które oznaczają przepływ sterowania przez program.

### <a name="step-four"></a>Krok 4

Zadeklarowany zwracany typ `AccessTheWebAsync` to `Task(Of Integer)`. W związku z `AccessTheWebAsync` tym, gdy zostanie zawieszone, zwraca zadanie z `startButton_Click`liczbą całkowitą do. Należy pamiętać, że zwrócone zadanie nie jest `getStringTask`. Zwrócone zadanie to nowe zadanie liczb całkowitych, które reprezentuje, `AccessTheWebAsync`co pozostało do wykonania w metodzie zawieszonej. Zadanie jest obietnicą `AccessTheWebAsync` do wygenerowania liczby całkowitej po zakończeniu zadania.

Poniższa instrukcja przypisuje to zadanie do `getLengthTask` zmiennej.

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

Jak w `AccessTheWebAsync`programie `startButton_Click` , program może kontynuować pracę, która nie zależy od wyników zadania asynchronicznego (`getLengthTask`), dopóki zadanie nie zostanie oczekiwane. Poniższe wiersze danych wyjściowych przedstawiają tę działanie.

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

Postęp w `startButton_Click` programie jest zawieszony `getLengthTask` , gdy jest oczekiwany. Następująca instrukcja przypisania zawiesza `startButton_Click` się do momentu `AccessTheWebAsync` ukończenia.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Na poniższej ilustracji strzałki pokazują przepływ sterowania z wyrażenia await `AccessTheWebAsync` w do przypisywania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` do momentu `getLengthTask` oczekiwania.

![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace — cztery")

### <a name="step-five"></a>Krok 5

Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest uwalniane z zawieszenia i może być kontynuowane za pomocą instrukcji Await. Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

Operand instrukcji `urlContents.Length`Return jest przechowywany w zadaniu, które `AccessTheWebAsync` zwraca. Wyrażenie await pobiera tę wartość z `getLengthTask`. `startButton_Click`

Na poniższej ilustracji przedstawiono transfer kontroli po `client.GetStringAsync` zakończeniu (i `getStringTask`).

![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace — pięć")

`AccessTheWebAsync`działa do ukończenia, a sterowanie powraca `startButton_Click`do, który oczekuje na ukończenie.

### <a name="step-six"></a>Krok SZÓSTy

Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie może być kontynuowane po instrukcji Await w. `startButton_Async` W rzeczywistości program nie ma niczego więcej.

Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w `startButton_Async`:

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

Wyrażenie await pobiera z `getLengthTask` wartości całkowitej, która jest argumentem instrukcji return w. `AccessTheWebAsync` Poniższa instrukcja przypisuje tę wartość do `contentLength` zmiennej.

```vb
Dim contentLength As Integer = Await getLengthTask
```

Na poniższej ilustracji przedstawiono powrót sterowania z `AccessTheWebAsync` do. `startButton_Click`

![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przykład asynchroniczny: Przepływ sterowania w programach asynchronicznychC# (i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
