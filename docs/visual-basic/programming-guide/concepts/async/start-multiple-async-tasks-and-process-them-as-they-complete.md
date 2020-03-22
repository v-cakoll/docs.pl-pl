---
title: Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b14171196a95e9a6a12f6b13f6f17d3cfe352bce
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266849"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Uruchamianie wielu zadań asynchronizowania i przetwarzanie ich po ich zakończeniu (visual basic)
Za <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>pomocą programu można uruchomić wiele zadań w tym samym czasie i przetwarzać je jeden po drugim, gdy są one wykonywane, a nie przetwarzać je w kolejności, w jakiej są uruchamiane.  
  
 W poniższym przykładzie użyto kwerendy do utworzenia kolekcji zadań. Każde zadanie pobiera zawartość określonej witryny sieci Web. W każdej iteracji while pętli oczekiwane `WhenAny` wywołanie zwraca zadanie w kolekcji zadań, która kończy pobieranie pierwszy. To zadanie jest usuwane z kolekcji i przetwarzane. Pętla powtarza się, dopóki kolekcja nie zawiera więcej zadań.  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać kompletny projekt Programu Windows Presentation Foundation (WPF) z [Async Sample: Fine Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonać następujące kroki.  
  
1. Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pozycję Plik**, **Otwórz,** **Projekt/Rozwiązanie**.  
  
3. W oknie dialogowym **Otwórz projekt** otwórz folder zawierający przykładowy kod, który został zdekonfekowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningVB.  
  
4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **ProcessTasksAsTheyFinish,** a następnie wybierz polecenie **Ustaw jako projekt startowy**.  
  
5. Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klawisze Ctrl+F5, aby uruchomić projekt bez debugowania.  
  
6. Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.  
  
 Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.  
  
## <a name="building-the-example"></a>Tworzenie przykładu  
 W tym przykładzie dodaje do kodu, który jest opracowany w [Anuluj pozostałe zadania asynchroniczne po zakończeniu one (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i używa tego samego interfejsu użytkownika.  
  
 Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz pozycję **CancelAfterOneTask** jako **projekt startowy**. Dodaj zmiany w tym `AccessTheWebAsync` temacie do metody w tym projekcie. Zmiany są oznaczone gwiazdkami.  
  
 Projekt **CancelAfterOneTask** zawiera już kwerendę, która po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w poniższym <xref:System.Threading.Tasks.Task%601> `TResult` kodzie zwraca gdzie jest całkowitej liczby.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 W pliku MainWindow.xaml.vb projektu należy wprowadzić następujące `AccessTheWebAsync` zmiany w metodzie.  
  
- Wykonaj kwerendę, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> stosując zamiast <xref:System.Linq.Enumerable.ToArray%2A>pliku .  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- Dodaj while pętli, która wykonuje następujące kroki dla każdego zadania w kolekcji.  
  
    1. Oczekuje na wywołanie, aby `WhenAny` zidentyfikować pierwsze zadanie w kolekcji, aby zakończyć jego pobieranie.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. Usuwa to zadanie z kolekcji.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. Oczekuje `firstFinishedTask`, który jest zwracany `ProcessURLAsync`przez wywołanie do . Zmienna `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> `TReturn` pewien gdzie jest pewien liczba całkowita. Zadanie jest już ukończone, ale czekasz na pobranie długości pobranej witryny sieci Web, jak pokazano w poniższym przykładzie.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Należy uruchomić projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.  
  
> [!CAUTION]
> Można użyć `WhenAny` w pętli, jak opisano w przykładzie, aby rozwiązać problemy, które obejmują niewielką liczbę zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań do przetworzenia. Aby uzyskać więcej informacji i przykładów, zobacz [Przetwarzanie zadań w miarę ich wykonywania](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełny tekst pliku MainWindow.xaml.vb dla przykładu. Gwiazdki oznaczyć elementy, które zostały dodane w tym przykładzie.  
  
 Należy zauważyć, że należy <xref:System.Net.Http>dodać odwołanie do .  
  
 Możesz pobrać projekt z [Async Sample: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronii (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z async i await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przykład asynchronii: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
