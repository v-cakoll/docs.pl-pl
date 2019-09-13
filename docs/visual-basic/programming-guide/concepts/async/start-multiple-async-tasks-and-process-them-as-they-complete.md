---
title: Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b103f385c804061c4df99dc9d1fdd54c7876151a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928458"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (Visual Basic)
Korzystając z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>programu, można uruchomić wiele zadań w tym samym czasie i przetworzyć je w taki sposób, aby były wykonywane, a nie przetwarzane w kolejności, w której są uruchamiane.  
  
 Poniższy przykład używa zapytania, aby utworzyć kolekcję zadań. Każde zadanie pobiera zawartość określonej witryny sieci Web. W każdej iteracji pętli while oczekiwane wywołanie `WhenAny` zwraca zadanie w kolekcji zadań, które kończą najpierw pobieranie. To zadanie jest usuwane z kolekcji i przetwarzane. Pętla powtarza się, dopóki kolekcja nie będzie zawierać żadnych zadań.  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.  
  
1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.  
  
3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningVB.  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProcessTasksAsTheyFinish** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.  
  
5. Wybierz klawisz F5, aby uruchomić projekt.  
  
     Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.  
  
6. Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.  
  
 Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow. XAML. vb na końcu tego tematu.  
  
## <a name="building-the-example"></a>Kompilowanie przykładu  
 Ten przykład dodaje do kodu, który został opracowany w polu [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i używa tego samego interfejsu użytkownika.  
  
 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAfterOneTask** jako **projekt startowy**. Dodaj zmiany w tym temacie do `AccessTheWebAsync` metody w tym projekcie. Zmiany są oznaczone gwiazdkami.  
  
 Projekt **CancelAfterOneTask** zawiera już zapytanie, które po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca, <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 W pliku MainWindow. XAML. vb projektu wprowadź następujące zmiany `AccessTheWebAsync` w metodzie.  
  
- Wykonaj zapytanie, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToArray%2A>zamiast.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- Dodaj pętlę while, która wykonuje następujące kroki dla każdego zadania w kolekcji.  
  
    1. Oczekuje na wywołanie `WhenAny` do zidentyfikowania pierwszego zadania w kolekcji, aby zakończyć jego pobieranie.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. Usuwa to zadanie z kolekcji.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. Czeka, który jest zwracany przez `ProcessURLAsync`wywołanie metody. `firstFinishedTask` `firstFinishedTask` Zmienna togdzie`TReturn`jestliczbącałkowitą. <xref:System.Threading.Tasks.Task%601> Zadanie zostało już ukończone, ale czeka na pobranie długości pobranej witryny sieci Web, jak pokazano w poniższym przykładzie.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Należy uruchomić projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.  
  
> [!CAUTION]
> Można użyć `WhenAny` w pętli, jak opisano w przykładzie, w celu rozwiązania problemów obejmujących niewielką liczbę zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań do przetworzenia. Aby uzyskać więcej informacji i przykładów, zobacz [Przetwarzanie zadań po ich zakończeniu](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełnym tekstem pliku MainWindow. XAML. vb dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.  
  
 Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.  
  
 Możesz pobrać projekt z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronicznej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Przykład asynchroniczny: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
