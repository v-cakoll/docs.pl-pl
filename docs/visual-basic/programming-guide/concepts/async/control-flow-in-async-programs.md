---
title: Przepływ sterowania w programach Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: c6afd7e166e08ea30637bd3f05026ef71d781ab6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624760"
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Przepływ sterowania w programach Async (Visual Basic)
Pozwala pisać i łatwiej utrzymać asynchroniczne programy za pomocą `Async` i `Await` słów kluczowych. Jednak wyniki mogą Cię zaskoczyć, jeśli nie rozumiesz sposobu działania programu. W tym temacie omówiono, którą przepływ sterowania za pośrednictwem prostego programu asynchronicznego aby pokazać, kiedy sterowania przechodzi od jednej metody do innej i jakie informacje są przesyłane za każdym razem.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012.  
  
 Ogólnie rzecz biorąc Oznacz metody, które zawierają kod asynchroniczny [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator. W metodzie, która jest oznaczona modyfikatorem asynchronicznym, można użyć [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operatora, aby określić, gdzie metoda wstrzymuje się oczekiwania wywołany proces asynchroniczny zakończyć. Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 W poniższym przykładzie użyto metody asynchronicznej, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu. Przykład zawiera następujących dwóch metod.  
  
- `startButton_Click`, która wywołuje metodę `AccessTheWebAsync` i wyświetla wynik.  
  
- `AccessTheWebAsync`, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu. `AccessTheWebAsync` używa asynchronicznej <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.  
  
 Ponumerowane wyświetlanych wierszy pojawiających się w strategiczny punktach w całym programie, aby lepiej zrozumieć, jak działa program i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony. Wyświetlane wiersze są oznaczone etykietami od "ONE"do "sześć." Etykiety reprezentują kolejność, w jakiej program osiąga te wiersze kodu.  
  
 Poniższy kod przedstawia zarys programu.  
  
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
  
 Każda z etykietami lokalizacje "ONE"do "6," Wyświetla informacje dotyczące bieżącego stanu programu. Następujące dane wyjściowe są generowane.  
  
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
 Kod, który używa tego tematu możesz pobrać z witryny MSDN lub tworzyć je samodzielnie.  
  
> [!NOTE]
>  Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
### <a name="download-the-program"></a>Pobierz Program  
 Możesz pobrać aplikację dotyczącą tego tematu z [próbka asynchroniczna: Kontrolowanie Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Poniższe kroki, Otwórz i uruchom program.  
  
1. Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.  
  
3. Przejdź do folderu, który posiada rozpakowany przykładowego kodu, otwórz plik rozwiązania (.sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.  
  
### <a name="build-the-program-yourself"></a>Sam Zbuduj Program  
 Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu, w tym temacie.  
  
 Aby uruchomić projekt, należy wykonać następujące czynności:  
  
1. Uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3. W **zainstalowane szablony** okienku wybierz **języka Visual Basic**, a następnie wybierz **aplikacji WPF** z listy typów projektów.  
  
4. Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
5. W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.  
  
     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.  
  
6. W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.  
  
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
  
     Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.  
  
7. Dodaj odwołanie do <xref:System.Net.Http>.  
  
8. W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **Wyświetl kod**.  
  
9. W pliku MainWindow.xaml.vb Zastąp kod następującym kodem.  
  
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
  
10. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Powinien pojawić się następujące dane wyjściowe.  
  
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
  
### <a name="steps-one-and-two"></a>Kroki 1 i 2  
 Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Poniższa ilustracja przedstawia wywołania z metody do metody.  
  
 ![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Zwracanym typem obu metod `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>. Aby uzyskać `AccessTheWebAsync`, TResult jest liczbą całkowitą. Aby uzyskać `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat typów zwracanych w metodach asynchronicznych, zobacz [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Asynchroniczna metoda zwracania zadania Zwraca wystąpienie zadania Jeśli kontrola przechodzi do obiektu wywołującego. Formant powraca z metody asynchronicznej do obiektu wywołującego gdy `Await` operator zostanie napotkany w metodzie wywoływanej, lub gdy metoda wywoływana się zakończy. Wyświetlane wiersze, które są oznaczone jako "Trzy"do "6" śledzą tę część procesu.  
  
### <a name="step-three"></a>Krok 3  
 W `AccessTheWebAsync`, metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web. Formant powraca z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.  
  
 `client.GetStringAsync` Metoda zwraca zadanie ciągu, która jest przypisana do `getStringTask` zmienną `AccessTheWebAsync`. Następujący wiersz w programie przykładowym pokazuje wywołanie `client.GetStringAsync` i przypisania.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 Można traktować zadanie jako zapowiedź `client.GetStringAsync` do produkcji rzeczywistego ciągu po pewnym czasie. W międzyczasie Jeśli `AccessTheWebAsync` ma robić prace, które nie są zależne od uzgodnionego ciągu z `client.GetStringAsync`, można kontynuować pracę podczas `client.GetStringAsync` oczekuje. W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują okazję do samodzielnej pracy  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Poniższa instrukcja wstrzymuje `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Na poniższej ilustracji przedstawiono przepływ sterowania od `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` do zastosowania operatora Await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")  
  
 Wyrażenie await wstrzymuje `AccessTheWebAsync` aż `client.GetStringAsync` zwraca. W międzyczasie formant powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Zazwyczaj można oczekiwać wywołania metody asynchronicznej natychmiast. Na przykład, następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`  
>   
>  W tym temacie await operator jest stosowany później, aby pomieścić linie wyjściowych, oznaczające przepływ sterowania za pośrednictwem programu.  
  
### <a name="step-four"></a>Krok czwarty  
 Deklarowanym typem zwracanym metody `AccessTheWebAsync` jest `Task(Of Integer)`. W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej do `startButton_Click`. Należy zrozumieć, że zwracane zadanie nie jest `getStringTask`. Zwracane zadanie jest nowym zadaniem liczby całkowitej określającej, co jeszcze pozostało do zrobienia WE wstrzymanej metodzie, `AccessTheWebAsync`. Zadanie jest obietnicą ze `AccessTheWebAsync` do utworzenia typu integer, po ukończeniu zadania.  
  
 Poniższa instrukcja przypisuje to zadanie `getLengthTask` zmiennej.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) dopóki trwa oczekiwanie na zadanie. Poniższe wiersze danych wyjściowych przedstawiają tę pracę.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 Postęp w `startButton_Click` jest zawieszony gdy `getLengthTask` jest oczekiwane. Poniższa instrukcja przypisania wstrzymuje `startButton_Click` aż `AccessTheWebAsync` zostało zakończone.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Na poniższej ilustracji, strzałki pokazują przepływ sterowania z wyrażenia oczekującego w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` aż `getLengthTask` jest oczekiwane.  
  
 ![Krok czwarty](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 4")  
  
### <a name="step-five"></a>Krok piąty  
 Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest zwalniane z zawieszenia i można kontynuować po instrukcji czekania. Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Argument instrukcji return `urlContents.Length`, jest zapisywany w zadaniu, `AccessTheWebAsync` zwraca. Wyrażenie await pobiera tę wartość ze `getLengthTask` w `startButton_Click`.  
  
 Poniższa ilustracja przedstawia przekazanie sterowania po `client.GetStringAsync` (i `getStringTask`) są kompletne.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")  
  
 `AccessTheWebAsync` przebieg do ukończenia, a formant powraca do `startButton_Click`, która oczekuje na zakończenie.  
  
### <a name="step-six"></a>Krok SZÓSTY  
 Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie można kontynuować po instrukcji czekania w `startButton_Async`. W rzeczywistości program nie ma nic więcej do zrobienia.  
  
 Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w metodzie `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Wyrażenie await pobiera ze `getLengthTask` wartość całkowitą, która jest argumentem instrukcji return w `AccessTheWebAsync`. Poniższa instrukcja przypisuje wartość do `contentLength` zmiennej.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Poniższa ilustracja przedstawia powrót sterowania z `AccessTheWebAsync` do `startButton_Click`.  
  
 ![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Próbka asynchroniczna: Kontrolowanie Flow in Async Programs (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
