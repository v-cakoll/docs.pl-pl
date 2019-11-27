---
title: Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: e6747f35e665611ac7a48a87f955c8b893ee2b99
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347924"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)

Korzystając z metody <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> wraz z <xref:System.Threading.CancellationToken>, można anulować wszystkie pozostałe zadania po zakończeniu jednego zadania. Metoda `WhenAny` przyjmuje argument, który jest kolekcją zadań. Metoda uruchamia wszystkie zadania i zwraca pojedyncze zadanie. Pojedyncze zadanie zostanie ukończone, gdy dowolne zadanie w kolekcji zostanie zakończone.

W tym przykładzie pokazano, jak używać tokenu anulowania w połączeniu z `WhenAny` do pierwszego zadania, aby zakończyć z kolekcji zadań i anulować pozostałe zadania. Każde zadanie pobiera zawartość witryny sieci Web. W przykładzie jest wyświetlana długość zawartości pierwszego pobrania, która zostanie zakończona, a pozostałe pliki do pobrania zostaną anulowane.

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="downloading-the-example"></a>Pobieranie przykładu

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningVB.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterOneTask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz F5, aby uruchomić projekt.

    Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.

6. Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.

Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow. XAML. vb na końcu tego tematu.

## <a name="building-the-example"></a>Kompilowanie przykładu

Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) , aby anulować listę zadań. W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.

Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.

W pliku MainWindow. XAML. vb projektu **CancelAListOfTasks** Rozpocznij przejście, przenosząc kroki przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do poniższej metody asynchronicznej.

```vb
' ***Bundle the processing steps for a website into one async method.
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

    ' GetAsync returns a Task(Of HttpResponseMessage).
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

    ' Retrieve the website contents from the HttpResponseMessage.
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

    Return urlContents.Length
End Function
```

W `AccessTheWebAsync`w tym przykładzie używa się zapytania, metody <xref:System.Linq.Enumerable.ToArray%2A> i metody `WhenAny` do tworzenia i uruchamiania tablicy zadań. Zastosowanie `WhenAny` do tablicy zwraca pojedyncze zadanie, które w oczekiwany sposób oblicza pierwsze zadanie, aby osiągnąć ukończenie w tablicy zadań.

Wprowadź następujące zmiany w `AccessTheWebAsync`. Gwiazdki oznaczają zmiany w pliku kodu.

1. Skomentuj lub Usuń pętlę.

2. Utwórz zapytanie, które po wykonaniu tworzy kolekcję zadań ogólnych. Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą.

    ```vb
    ' ***Create a query that, when executed, returns a collection of tasks.
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
        From url In urlList Select ProcessURLAsync(url, client, ct)
    ```

3. Wywołaj `ToArray`, aby wykonać zapytanie i uruchomić zadania. Zastosowanie metody `WhenAny` w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez użycia `ToArray`, ale inne metody mogą nie być. Najbezpieczniejszym sposobem jest wymuszenie jawnie wykonywania zapytania.

    ```vb
    ' ***Use ToArray to execute the query and start the download tasks.
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()
    ```

4. Wywołaj `WhenAny` w kolekcji zadań. `WhenAny` zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.  Oznacza to, że `WhenAny` zwraca zadanie, które zostanie obliczone do pojedynczego `Task(Of Integer)` lub `Task<int>`, gdy jest oczekiwane. To pojedyncze zadanie to pierwsze zadanie w kolekcji, które ma zostać zakończone. Zadanie, które zostało zakończone, zostało przypisane do `firstFinishedTask`. Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą, ponieważ jest typem zwracanym `ProcessURLAsync`.

    ```vb
    ' ***Call WhenAny and then await the result. The task that finishes
    ' first is assigned to firstFinishedTask.
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)
    ```

5. W tym przykładzie interesuje Cię tylko zadanie, które zakończy się w pierwszej kolejności. W związku z tym Użyj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType>, aby anulować pozostałe zadania.

    ```vb
    ' ***Cancel the rest of the downloads. You just want the first one.
    cts.Cancel()
    ```

6. Na koniec oczekujemy, `firstFinishedTask` pobrać długość pobranej zawartości.

    ```vb
    Dim length = Await firstFinishedTask
    resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    ```

Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.

## <a name="complete-example"></a>Kompletny przykład

Poniższy kod jest pełnym plikiem MainWindow. XAML. vb lub MainWindow.xaml.cs dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.

Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.

Możesz pobrać projekt z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
            Await AccessTheWebAsync(cts.Token)
            resultsTextBox.Text &= vbCrLf & "Download complete."

        Catch ex As OperationCanceledException
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

        Catch ex As Exception
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf
        End Try

        ' Set the CancellationTokenSource to Nothing when the download is complete.
        cts = Nothing
    End Sub

    ' You can still include a Cancel button if you want to.
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)

        If cts IsNot Nothing Then
            cts.Cancel()
        End If
    End Sub

    ' Provide a parameter for the CancellationToken.
    ' Change the return type to Task because the method has no return statement.
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task

        Dim client As HttpClient = New HttpClient()

        ' Call SetUpURLList to make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        '' Comment out or delete the loop.
        ''For Each url In urlList
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).
        ''    ' Argument ct carries the message if the Cancel button is chosen.
        ''    ' Note that the Cancel button can cancel all remaining downloads.
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ''    ' Retrieve the website contents from the HttpResponseMessage.
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ''    resultsTextBox.Text &=
        ''        vbCrLf & $"Length of the downloaded string: {urlContents.Length}." & vbCrLf
        ''Next

        ' ***Create a query that, when executed, returns a collection of tasks.
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =
            From url In urlList Select ProcessURLAsync(url, client, ct)

        ' ***Use ToArray to execute the query and start the download tasks.
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()

        ' ***Call WhenAny and then await the result. The task that finishes
        ' first is assigned to firstFinishedTask.
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)

        ' ***Cancel the rest of the downloads. You just want the first one.
        cts.Cancel()

        ' ***Await the first completed task and display the results
        ' Run the program several times to demonstrate that different
        ' websites can finish first.
        Dim length = Await firstFinishedTask
        resultsTextBox.Text &= vbCrLf & $"Length of the downloaded website:  {length}" & vbCrLf
    End Function

    ' ***Bundle the processing steps for a website into one async method.
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)

        ' GetAsync returns a Task(Of HttpResponseMessage).
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        Return urlContents.Length
    End Function

    ' Add a method that creates a list of web addresses.
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

' Sample output:

' Length of the downloaded website:  158856

' Download complete.
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronicznej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Próbka asynchroniczna: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
