---
title: "Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dfabe4619e5d73b554d91edb137ae1ce7d34b5ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a>Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (Visual Basic)
Przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, można uruchomić wielu zadań jednocześnie i je jeden po drugim Przetwarzaj one jest ukończona, a nie ich przetworzyć w kolejności, w którym jest uruchomiona.  
  
 W poniższym przykładzie użyto zapytania, aby utworzyć kolekcję zadań. Każde zadanie pobiera zawartość z określonej witryny sieci Web. W każdej iteracji chwilę pętli, oczekiwano wywołania `WhenAny` zwraca zadanie w kolekcji zadań najpierw zakończy jej pobierania. To zadanie jest usunięty z kolekcji i przetwarzane. Pętla jest powtarzany do momentu Kolekcja nie zawiera więcej zadań.  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046) , a następnie wykonaj następujące kroki.  
  
1.  Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningVB.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProcessTasksAsTheyFinish** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.  
  
 Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.  
  
## <a name="building-the-example"></a>Tworzenie w przykładzie  
 W tym przykładzie dodaje kod, który został napisany w [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) i używa tego samego interfejsu użytkownika.  
  
 Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAfterOneTask** jako **projekt startowy**. Dodaj zmiany w tym temacie umożliwiają `AccessTheWebAsync` metody w tym projekcie. Zmiany są oznaczone gwiazdki.  
  
 **CancelAfterOneTask** Projekt już zawiera zapytanie, które po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 W pliku MainWindow.xaml.vb projektu, wprowadź następujące zmiany do `AccessTheWebAsync` metody.  
  
-   Wykonanie kwerendy, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
-   Dodaj chwilę pętli, które wykonuje następujące czynności dla każdego zadania w kolekcji.  
  
    1.  Oczekujące na wywołanie `WhenAny` do identyfikowania pierwszego zadania w kolekcji, aby zakończyć jej pobierania.  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2.  To zadanie usuwa z kolekcji.  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3.  Oczekujące na `firstFinishedTask`, który jest zwracany przez wywołanie do `ProcessURLAsync`. `firstFinishedTask` Zmienna jest <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą. Zadanie zostało już ukończone, ale należy poczekać na można pobrać długości pobrany witryny sieci Web, jak przedstawiono na poniższym przykładzie.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności należy uruchomić kilka razy projektu.  
  
> [!CAUTION]
>  Można użyć `WhenAny` w pętli, zgodnie z opisem w tym przykładzie, aby rozwiązać problemy z działaniem niewielkiej liczby zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań w celu przetworzenia. Aby uzyskać dodatkowe informacje i przykłady, zobacz [przetwarzania zadań jako zakończenie](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## <a name="complete-example"></a>Kompletny przykład  
 Następujący kod jest pełny tekst pliku MainWindow.xaml.vb dla przykładu. Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.  
  
 Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.  
  
 Można pobrać projektu z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Dostrajanie aplikacji Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](http://go.microsoft.com/fwlink/?LinkId=255046)
