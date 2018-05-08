---
title: Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 2de9c00e5094a1c40e64bdf5215157867372be8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="control-flow-in-async-programs-visual-basic"></a>Przepływ sterowania w aplikacjach asynchronicznych (Visual Basic)
Możesz wpisać i obsługa asynchroniczne programy łatwiej przy użyciu `Async` i `Await` słów kluczowych. Jednak wyniki, może Cię zaskoczył Jeśli nie znasz sposób działania programu. Ślady tego tematu, które przepływu sterowania za pośrednictwem programu async proste do wyświetlenia, gdy formant są przenoszone z jednej metody do innej i jakie informacje są przesyłane za każdym razem.  
  
> [!NOTE]
>  `Async` i `Await` słowa kluczowe wprowadzono w programie Visual Studio 2012.  
  
 Ogólnie rzecz biorąc, możesz oznaczyć metody, które zawierają asynchroniczne kodu za pomocą [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator. W przypadku metody oznaczonej za pomocą modyfikatora async służy [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operatora, aby określić, gdzie metoda wstrzymuje oczekiwania na ukończenie wywołanego procesu asynchronicznego. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 W poniższym przykładzie użyto metody asynchroniczne, aby pobrać zawartość z określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu. Przykład zawiera następujących dwóch metod.  
  
-   `startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetla wyniki.  
  
-   `AccessTheWebAsync`, która pobiera zawartość witryny sieci Web w postaci ciągu i zwraca długość ciągu. `AccessTheWebAsync` korzysta z asynchronicznego <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.  
  
 Numerowane wyświetlania wiersze pojawiają się w punktach strategicznych w programie, aby lepiej zrozumieć, jak program zostanie uruchomiony i wyjaśniający, co się stanie w każdym punkcie, który jest oznaczony jako. Wyświetlanie linii są oznaczone jako "Jeden"do "sześć." Etykiety opisania kolejności, w którym program osiągnie tych wierszy kodu.  
  
 Poniższy kod przedstawia konspektu programu.  
  
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
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
```  
  
 Każdej z etykietą lokalizacji, "ONE"do "6," Wyświetla informacje o bieżącym stanie programu. Są następujące wyniki.  
  
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
 Kod, który korzysta z tego tematu możesz pobrać z MSDN lub można utworzyć ją samodzielnie.  
  
> [!NOTE]
>  Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
### <a name="download-the-program"></a>Pobierz Program  
 Możesz pobrać aplikację dla tego tematu z [próbki Async: przepływ sterowania w aplikacjach asynchronicznych](http://go.microsoft.com/fwlink/?LinkId=255285). Poniższe kroki Otwórz i uruchom program.  
  
1.  Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  Przejdź do folderu, która przechowuje rozpakowane przykładowy kod, otwórz plik rozwiązania (sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.  
  
### <a name="build-the-program-yourself"></a>Samodzielnie kompilacji programu  
 Następujący projekt Windows Presentation Foundation (WPF) zawiera przykładowy kod dla tego tematu.  
  
 Aby uruchomić projekt, wykonaj następujące czynności:  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz **Visual Basic**, a następnie wybierz pozycję **aplikacji WPF** z listy typów projektów.  
  
4.  Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz pozycję **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
5.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
     Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.  
  
6.  W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.  
  
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
  
     Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.  
  
7.  Dodaj odwołanie do <xref:System.Net.Http>.  
  
8.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **kod widoku**.  
  
9. W MainWindow.xaml.vb Zastąp kod następującym kodem.  
  
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
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
     Następujące dane wyjściowe powinny być wyświetlane.  
  
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
 Wyświetlanie pierwszych dwóch linii śledzenia ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Poniższa ilustracja przedstawia wywołania metody metody.  
  
 ![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Zwracany typ `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>. Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą. Dla `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat asynchronicznej metody zwracane typy, zobacz [Async zwracać typów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
 Metody async umożliwiające zwracanie zadań Zwraca wystąpienie zadania podczas kontroli przewiduje się do obiektu wywołującego. Formant zwraca z metody asynchronicznej do swojego obiektu wywołującego albo gdy `Await` napotkano operator wywołaną metodę lub gdy kończy się wywołaną metodę. Wyświetlanie linii, które są oznaczone jako "Trzy"do "SZEŚCIU" śledzenia to część procesu.  
  
### <a name="step-three"></a>Krok 3  
 W `AccessTheWebAsync`, metod asynchronicznych <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości na docelowej stronie sieci Web. Zwraca kontroli z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.  
  
 `client.GetStringAsync` Metoda zwraca ciąg, który jest przypisany do zadania `getStringTask` zmiennej w `AccessTheWebAsync`. Następujący wiersz w programie przykład zawiera wywołanie `client.GetStringAsync` oraz przypisanie.  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
```  
  
 Można traktować jako promise przez zadania `client.GetStringAsync` do tworzenia rzeczywistych ciągu po pewnym czasie. W międzyczasie Jeśli `AccessTheWebAsync` ma pracy, który nie jest zależny od uzgodnionej ciąg, z `client.GetStringAsync`, aby kontynuować pracę podczas `client.GetStringAsync` oczekuje. W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują możliwość wykonywania pracy, niezależnie od  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Następująca instrukcja wstrzymuje postęp w `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 Na poniższej ilustracji przedstawiono przepływu sterowania z `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` zastosowanie operatora Await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")  
  
 Wyrażenie await zawiesi `AccessTheWebAsync` do momentu `client.GetStringAsync` zwraca. Tymczasem zwraca sterowania do wywołującego `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Zazwyczaj należy poczekać na wywołanie metody asynchronicznej natychmiast. Na przykład następujące przypisanie można zastąpić poprzedni kod, który tworzy, a następnie oczekiwanie `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`  
>   
>  W tym temacie operatora await jest stosowany później do uwzględnienia wiersze danych wyjściowych oznaczyć przepływu sterowania przez program.  
  
### <a name="step-four"></a>Krok 4  
 Zadeklarowany typ zwrotny `AccessTheWebAsync` jest `Task(Of Integer)`. W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej w celu `startButton_Click`. Należy pamiętać, że zwrócony zadań nie jest `getStringTask`. Zadanie zwracane jest nowe zadanie liczbę całkowitą reprezentującą, co ma odbywać się w metodzie wstrzymaną `AccessTheWebAsync`. Zadanie jest promise z `AccessTheWebAsync` wygenerowało całkowitą po zakończeniu zadania.  
  
 Następująca instrukcja przypisuje do tego zadania `getLengthTask` zmiennej.  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracy, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) do momentu zadania jest oczekiwane. Następujące wiersze danych wyjściowych reprezentują pracy.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 Postęp w `startButton_Click` zawieszone po `getLengthTask` jest oczekiwane. Następująca instrukcja przypisania wstrzymuje `startButton_Click` do momentu `AccessTheWebAsync` została ukończona.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Na poniższej ilustracji, strzałki oznaczają przepływu sterowania z wyrażenie await w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalnego przetwarzania w `startButton_Click` do momentu `getLengthTask` jest oczekiwane.  
  
 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "czterech AsyncTrace")  
  
### <a name="step-five"></a>Krok 5  
 Gdy `client.GetStringAsync` sygnały jest zakończone, przetwarzania w `AccessTheWebAsync` zwolnieniu od zawieszenie i można kontynuować mimo instrukcja await. Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Argument instrukcji return `urlContents.Length`, są przechowywane w zadaniu który `AccessTheWebAsync` zwraca. Wyrażenie await pobiera tej wartości od `getLengthTask` w `startButton_Click`.  
  
 Na poniższej ilustracji przedstawiono transfer kontroli po `client.GetStringAsync` (i `getStringTask`) są spełnione.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")  
  
 `AccessTheWebAsync` Zwraca używa do ukończenia i kontroli do `startButton_Click`, która oczekuje na zakończenie.  
  
### <a name="step-six"></a>Krok 6  
 Gdy `AccessTheWebAsync` sygnalizuje, że zakończeniu przetwarzania można kontynuować mimo instrukcja await w `startButton_Async`. W rzeczywistości program nie ma nic więcej robić.  
  
 Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania w `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Pobiera wyrażenie await z `getLengthTask` wartość całkowitą, która jest argument instrukcji return w `AccessTheWebAsync`. Następująca instrukcja przypisuje wartość tego `contentLength` zmiennej.  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 Na poniższej ilustracji przedstawiono zwracany formantu z `AccessTheWebAsync` do `startButton_Click`.  
  
 ![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace SZEŚCIU")  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Przykład Async: Przepływ sterowania w aplikacjach asynchronicznych (C# i Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)
