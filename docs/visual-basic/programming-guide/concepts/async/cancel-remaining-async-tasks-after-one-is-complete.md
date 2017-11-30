---
title: "Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 698ccf5901a77438368b9bf768b88ca6f90fdcbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a>Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (Visual Basic)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody razem z <xref:System.Threading.CancellationToken>, możesz anulować wszystkie pozostałe zadania po zakończeniu zadania. `WhenAny` Metoda przyjmuje argument, który jest kolekcji zadań. Metoda uruchamiania wszystkich zadań i zwraca jedno zadanie. Pojedyncze zadanie zakończeniu po ukończeniu zadań w kolekcji.  
  
 W tym przykładzie pokazano, jak używać w połączeniu z tokenem anulowania `WhenAny` do przechowywania na pierwszym zadaniem Zakończ z kolekcji zadań i anulowanie pozostałych zadań. Każde zadanie pobiera zawartość witryny sieci Web. W przykładzie wyświetla długość zawartości pierwsza z nich do wykonania i anuluje inne pliki do pobrania.  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046) , a następnie wykonaj następujące kroki.  
  
1.  Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningVB.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **CancelAfterOneTask** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
 Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.  
  
## <a name="building-the-example"></a>Tworzenie w przykładzie  
 W przykładzie w tym temacie jest dodawany do projektu, który został napisany w [anulowanie zadania asynchronicznego lub listy zadań](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) anulować listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używana jawnie.  
  
 Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.  
  
 W pliku MainWindow.xaml.vb **CancelAListOfTasks** projekt, uruchom przejście przez przeniesienie kroki przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do następującej metody asynchronicznej.  
  
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
  
 W `AccessTheWebAsync`, w tym przykładzie użyto kwerendy, <xref:System.Linq.Enumerable.ToArray%2A> metody i `WhenAny` metodę, aby utworzyć i uruchomić tablicy zadań. Stosowanie `WhenAny` do tablicy zwraca pojedyncze zadanie, gdy oczekiwane, daje w wyniku pierwszego zadania do wykonania w tablicy zadań.  
  
 Wprowadź następujące zmiany w `AccessTheWebAsync`. Gwiazdki oznaczyć zmiany w pliku kodu.  
  
1.  Komentarz lub usunąć pętli.  
  
2.  Utwórz kwerendę, która po wykonaniu tworzy kolekcję ogólnych zadań. Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  Wywołanie `ToArray` do wykonania zapytania i uruchamiania zadań. Stosowanie `WhenAny` metody w następnym kroku może wykonać zapytania i uruchomić zadania bez użycia `ToArray`, ale inne metody nie mogą. Najbezpieczniejszym rozwiązaniem jest jawnie wymusić wykonywania zapytania.  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Wywołanie `WhenAny` w kolekcji zadań. `WhenAny`Zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.  Oznacza to `WhenAny` zwraca zadanie, które ocenia pojedynczej `Task(Of Integer)` lub `Task<int>` po jest oczekiwane. Jednego zadania jest pierwszym zadaniem w kolekcji, aby zakończyć. Zadanie, które zostało zakończone najpierw jest przypisany do `firstFinishedTask`. Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą, ponieważ jest to typ zwracany `ProcessURLAsync`.  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  W tym przykładzie interesuje Cię tylko zadania, które kończy najpierw. Dlatego należy używać <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> na anulowanie pozostałych zadań.  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  Na koniec await `firstFinishedTask` można pobrać długości pobieranej zawartości.  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełny plik MainWindow.xaml.vb lub MainWindow.xaml.cs dla przykładu. Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.  
  
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
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
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
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
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
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Dostrajanie aplikacji Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](http://go.microsoft.com/fwlink/?LinkId=255046)
