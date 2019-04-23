---
title: 'Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 7ad2d9cdd85a7bdb67bbf091a38274fd20e5a66f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331887"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)
Może poprawić wydajność rozwiązania asynchronicznego w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Ta metoda asynchronicznie czeka na wiele operacji asynchronicznych, które są reprezentowane jako kolekcję zadań.  
  
 Można zauważyć w instruktażu, witryn sieci Web pobierane w różnym tempie. Czasami jednej z witryn sieci Web działa bardzo powoli, co opóźnia wszystkie pozostałe pobrania. Po uruchomieniu asynchronicznych rozwiązań, które kompilujesz w instruktażu, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby Uruchom wszystkie akcje pobierania w tym samym czasie i umożliwiają szybsze pobieranie bez oczekiwania na tym, który firmy  opóźnione.  
  
 Należy zastosować `Task.WhenAll` metodę do kolekcji zadań. Stosowanie `WhenAll` zwrócenie pojedynczego zadania, które nie zostało zakończone, aż do zakończenia wszystkich zadań w kolekcji. Zadania wydają się być uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone. Zadania można wykonywać w dowolnej kolejności.  
  
> [!IMPORTANT]
>  Poniższe procedury opisują rozszerzenia aplikacji asynchronicznych, które są opracowywane w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Można opracować aplikacje przez wykonanie kroków przewodnika lub ściągając kod z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Aby uruchomić przykład, jest posiadanie programu Visual Studio 2012 lub nowszy jest zainstalowany na tym komputerze.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać Task.WhenAll do rozwiązania GetURLContentsAsync  
  
1. Dodaj `ProcessURLAsync` metody do pierwszego wniosku opracowywanego w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod ze [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough, a następnie dodaj `ProcessURLAsync` w pliku MainWindow.xaml.vb.  
  
    -   Jeśli kod jest opracowany przez wykonanie kroków przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która obejmuje `GetURLContentsAsync` metody. Plik MainWindow.xaml.vb dla tej aplikacji to pierwszy przykład w sekcji "Przykłady pełnego kodu z przewodnika".  
  
     `ProcessURLAsync` Metoda konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym przewodniku. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów i następnie wyświetla i zwraca długość tablicy bajtów.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Skomentuj lub usuń `For Each` pętli w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3. Utwórz kolekcję zadań. Poniższy kod definiuje [zapytania](../../../../visual-basic/programming-guide/concepts/linq/index.md) , podczas wykonywania przez <xref:System.Linq.Enumerable.ToArray%2A> metody, tworzy kolekcję zadań pobierających zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest obliczane.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po zadeklarowaniu `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` Zwraca pojedyncze zadanie, który kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie czeka na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, zaraz za kodem dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metody w celu obliczenia sumy długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać Task.WhenAll do rozwiązania HttpClient.GetByteArrayAsync  
  
1. Dodaj następującą wersję `ProcessURLAsync` do drugiej aplikacji opracowywanej w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod ze [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` w pliku MainWindow.xaml.vb.  
  
    -   Jeśli kod jest opracowany przez wykonanie kroków przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która używa `HttpClient.GetByteArrayAsync` metody. Plik MainWindow.xaml.vb dla tej aplikacji to drugi przykład w sekcji "Przykłady pełnego kodu z przewodnika".  
  
     `ProcessURLAsync` Metoda konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym przewodniku. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów i następnie wyświetla i zwraca długość tablicy bajtów.  
  
     Jedyną różnicą między `ProcessURLAsync` metoda w poprzedniej procedurze jest użycie <xref:System.Net.Http.HttpClient> wypadku `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Skomentuj lub usuń `For Each` pętli w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
    ```  
  
3. Zdefiniuj [zapytania](../../../../visual-basic/programming-guide/concepts/linq/index.md) , podczas wykonywania przez <xref:System.Linq.Enumerable.ToArray%2A> metody, tworzy kolekcję zadań pobierających zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest obliczane.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po zadeklarowaniu `client` i `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` Zwraca pojedyncze zadanie, który kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie czeka na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Po zakończeniu `Await` wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, zaraz za kodem dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metody w celu uzyskania sumy długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązania Task.WhenAll  
  
-   Dla dowolnego z rozwiązań, wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku. Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchronicznych w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Jednak należy zauważyć, że witryny sieci Web są wyświetlane w innej kolejności każdorazowo.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzenia projektu, który używa `GetURLContentsAsync` metody do pobierania zawartości z sieci web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzenia projektu, który używa metody `HttpClient.GetByteArrayAsync` można pobrać zawartości z sieci web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://www.msdn.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
