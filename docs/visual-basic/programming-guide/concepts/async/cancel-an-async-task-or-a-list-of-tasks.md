---
title: Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 89a78e9e423ab4cce9fd3627ec433072ade238dc
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419867"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a>Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)

Można skonfigurować przycisk, którego można użyć do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na jej zakończenie. Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji pobierającej zawartość jednej witryny sieci Web lub listy witryn sieci Web.

W przykładach używany jest interfejs użytkownika, który opisuje [Dostosowywanie aplikacji asynchronicznej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) .

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="BKMK_CancelaTask"></a>Anulowanie zadania

Pierwszy przykład kojarzy przycisk **Anuluj** z pojedynczym zadaniem pobierania. Jeśli wybierzesz przycisk podczas pobierania zawartości przez aplikację, pobieranie zostanie anulowane.

### <a name="downloading-the-example"></a>Pobieranie przykładu

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningVB.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelATask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz F5, aby uruchomić projekt.

     Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.

 Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow. XAML. vb na końcu tego tematu.

### <a name="building-the-example"></a>Kompilowanie przykładu

Następujące zmiany umożliwiają dodanie przycisku **Anuluj** do aplikacji, która pobiera witrynę sieci Web. Jeśli nie chcesz pobierać ani kompilować przykładu, możesz przejrzeć końcowy produkt w sekcji "kompletne przykłady" na końcu tego tematu. Gwiazdki oznaczają zmiany w kodzie.

Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **StarterCode** jako **projekt startowy** , a nie **CancelATask**.

Następnie Dodaj następujące zmiany do pliku MainWindow. XAML. vb tego projektu.

1. Zadeklaruj zmienną `CancellationTokenSource`, `cts`, która znajduje się w zakresie dla wszystkich metod, które mają do niego dostęp.

    ```vb
    Class MainWindow

        ' ***Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. Dodaj następujący program obsługi zdarzeń dla przycisku **Anuluj** . Procedura obsługi zdarzeń używa metody <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> do powiadamiania `cts`, gdy użytkownik zażąda anulowania.

    ```vb
    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub
    ```

3. Wprowadź następujące zmiany w obsłudze zdarzeń dla przycisku **Start** `startButton_Click`.

    - Utwórz wystąpienie `CancellationTokenSource`, `cts`.

      ```vb
      ' ***Instantiate the CancellationTokenSource.
      cts = New CancellationTokenSource()
      ```

    - W wywołaniu do `AccessTheWebAsync`, które pobiera zawartość określonej witryny sieci Web, Wyślij Właściwość <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> `cts` jako argument. Właściwość `Token` propaguje komunikat w przypadku żądania anulowania. Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik zdecyduje się anulować operację pobierania. Poniższy kod przedstawia zmiany.

      ```vb
      Try
          ' ***Send a token to carry the message if cancellation is requested.
          Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

          resultsTextBox.Text &=
              vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

          ' *** If cancellation is requested, an OperationCanceledException results.
      Catch ex As OperationCanceledException
          resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

      Catch ex As Exception
          resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
      End Try
      ```

4. W `AccessTheWebAsync`należy użyć przeciążenia <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> metody `GetAsync` w typie <xref:System.Net.Http.HttpClient>, aby pobrać zawartość witryny sieci Web. Przekaż `ct`, parametr <xref:System.Threading.CancellationToken> `AccessTheWebAsync`jako drugi argument. Token przenosi komunikat, jeśli użytkownik wybierze przycisk **Anuluj** .

    Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.

    ```vb
    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &= vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
    ```

5. Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe:

    ```console
    Ready to download.
    Length of the downloaded string: 158125.
    ```

    Jeśli wybierzesz przycisk **Anuluj** , zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe:

    ```console
    Ready to download.
    Download canceled.
    ```

## <a name="BKMK_CancelaListofTasks"></a>Anulowanie listy zadań

Możesz poszerzyć poprzedni przykład, aby anulować wiele zadań, kojarząc to samo wystąpienie `CancellationTokenSource` z każdym zadaniem. Jeśli wybierzesz przycisk **Anuluj** , anulujesz wszystkie zadania, które nie zostały jeszcze ukończone.

### <a name="downloading-the-example"></a>Pobieranie przykładu

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningVB.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAListOfTasks** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz F5, aby uruchomić projekt.

     Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.

 Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow. XAML. vb na końcu tego tematu.

### <a name="building-the-example"></a>Kompilowanie przykładu

Aby poszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelATask** jako **projekt startowy**. Dodaj następujące zmiany do tego projektu. Gwiazdki oznaczają zmiany w programie.

1. Dodaj metodę, aby utworzyć listę adresów sieci Web.

    ```vb
    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function
    ```

2. Wywołaj metodę w `AccessTheWebAsync`.

    ```vb
    ' ***Call SetUpURLList to make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()
    ```

3. Dodaj następującą pętlę w `AccessTheWebAsync`, aby przetwarzać poszczególne adresy sieci Web na liście.

    ```vb
    ' ***Add a loop to process the list of web addresses.
    For Each url In urlList
        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' Argument ct carries the message if the Cancel button is chosen.
        ' ***Note that the Cancel button can cancel all remaining downloads.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        resultsTextBox.Text &=
            vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
    Next
    ```

4. Ponieważ `AccessTheWebAsync` wyświetla długości, metoda nie musi zwracać żadnych elementów. Usuń instrukcję return i Zmień zwracany typ metody na <xref:System.Threading.Tasks.Task>, a nie <xref:System.Threading.Tasks.Task%601>.

    ```vb
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task
    ```

    Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.

    ```vb
    Await AccessTheWebAsync(cts.Token)
    ```

5. Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe:

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

    Jeśli wybierzesz przycisk **Anuluj** przed ukończeniem pobierania, dane wyjściowe zawierają długości plików do pobrania, które zakończyły się przed anulowaniem.

    ```console
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="BKMK_CompleteExamples"></a>Kompletne przykłady

Poniższe sekcje zawierają kod dla każdego z powyższych przykładów. Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.

Możesz pobrać projekty z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="cancel-a-task-example"></a>Anulowanie zadania przykładowego

Poniższy kod jest pełnym plikiem MainWindow. XAML. vb dla przykładu, który anuluje pojedyncze zadanie.

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' ***Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)
        ' ***Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***Send a token to carry the message if cancellation is requested.
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {contentLength}." & vbCrLf

            ' *** If cancellation is requested, an OperationCanceledException results.
        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' ***Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' ***Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' ***Provide a parameter for the CancellationToken.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)

        Dim client As HttpClient = New HttpClient()

        resultsTextBox.Text &=
            vbCrLf & "Ready to download." & vbCrLf

        ' You might need to slow things down to have a chance to cancel.
        Await Task.Delay(250)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        ' ***The ct argument carries the message if the Cancel button is chosen.
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' The result of the method is the length of the downloaded website.
        Return urlContents.Length
    End Function
End Class

' Output for a successful download:

' Ready to download.

' Length of the downloaded string: 158125.

' Or, if you cancel:

' Ready to download.

' Download canceled.
```

### <a name="cancel-a-list-of-tasks-example"></a>Anuluj listę przykładowych zadań

Poniższy kod jest pełnym plikiem MainWindow. XAML. vb dla przykładu, który anuluje listę zadań.

```vb
' Add an Imports directive and a reference for System.Net.Http.
Imports System.Net.Http

' Add the following Imports directive for System.Threading.
Imports System.Threading

Class MainWindow

    ' Declare a System.Threading.CancellationTokenSource.
    Dim cts As CancellationTokenSource

    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)

        ' Instantiate the CancellationTokenSource.
        cts = New CancellationTokenSource()

        resultsTextBox.Clear()

        Try
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).
            Await AccessTheWebAsync(cts.Token)
            '  ***Small change in the display lines.
            resultsTextBox.Text &= vbCrLf & "Downloads complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' Add an event handler for the Cancel button.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' ***Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' ***Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        ' ***Add a loop to process the list of web addresses.
        For Each url In urlList
            ' GetAsync returns a Task(Of HttpResponseMessage).
            ' Argument ct carries the message if the Cancel button is chosen.
            ' ***Note that the Cancel button can cancel all remaining downloads.
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

            ' Retrieve the website contents from the HttpResponseMessage.
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

            resultsTextBox.Text &=
                vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        Next
    End Function

    ' ***Add a method that creates a list of web addresses.
    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

End Class

' Output if you do not choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Length of the downloaded string: 158124.

' Length of the downloaded string: 204890.

' Length of the downloaded string: 175488.

' Length of the downloaded string: 145790.

' Downloads complete.

'  Sample output if you choose to cancel:

' Length of the downloaded string: 35939.

' Length of the downloaded string: 237682.

' Length of the downloaded string: 128607.

' Downloads canceled.
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Dostrajanie aplikacji asynchronicznej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Próbka asynchroniczna: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
