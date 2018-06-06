---
title: 'Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 12d195caa11cd33b4e450e5a57699da4037ed4a2
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696354"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)
Może poprawić wydajność rozwiązania asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Ta metoda asynchronicznie oczekujące na wiele operacji asynchronicznych, które są reprezentowane jako kolekcji zadań.  
  
 Zwróć uwagę, w tym przewodnikiem czy witryn sieci Web Pobierz w różnym tempie. Czasami jednej z witryn sieci Web jest bardzo wolno, który wybrano opcję opóźnienia wszystkie pozostałe pliki do pobrania. Po uruchomieniu asynchroniczne rozwiązania, które można utworzyć w tym przewodnikiem, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby uruchomić wszystkie pobrane pliki w tym samym czasie i pozwól szybsze pobieranie kontynuować bez oczekiwania na to, że w  opóźnione.  
  
 Należy zastosować `Task.WhenAll` metody do kolekcji zadań. Stosowanie `WhenAll` zwraca pojedyncze zadanie, które nie są kompletne, do czasu ukończenia każdego zadania w kolekcji. Wyświetlanie zadań do uruchomienia równoległego, ale nie dodatkowe wątki są tworzone. Zadania można wykonać w dowolnej kolejności.  
  
> [!IMPORTANT]
>  Poniższe procedury opisują rozszerzeń aplikacji async, które są opracowywane w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Aplikacje można tworzyć spełniając wskazówki lub pobieranie kodu z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
>  Aby uruchomić przykład, musi mieć programu Visual Studio 2012 lub nowszy jest zainstalowany na tym komputerze.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać do rozwiązania GetURLContentsAsync Task.WhenAll  
  
1.  Dodaj `ProcessURLAsync` metody do pierwszej aplikacji, który został napisany w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.vb.  
  
    -   Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która obejmuje `GetURLContentsAsync` metody. Plik MainWindow.xaml.vb dla tej aplikacji jest pierwszym przykładzie w sekcji "Pełny kod przykłady z przewodnik".  
  
     `ProcessURLAsync` Metody konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym wskazówki. Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Komentarz lub usunąć `For Each` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.  
  
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
  
3.  Utwórz kolekcję zadań. Poniższy kod definiuje [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn. Zadania są uruchamiane podczas szacowania zapytania.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca. Wyrażenie do tablicy liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę obliczania sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać Task.WhenAll rozwiązania HttpClient.GetByteArrayAsync  
  
1.  Dodaj następujące wersję `ProcessURLAsync` do drugiego aplikacji utworzoną w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.vb.  
  
    -   Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która używa `HttpClient.GetByteArrayAsync` metody. Plik MainWindow.xaml.vb dla tej aplikacji jest drugi przykład w sekcji "Pełny kod przykłady z przewodnik".  
  
     `ProcessURLAsync` Metody konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym wskazówki. Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
     Jedyną różnicą z `ProcessURLAsync` metody w poprzedniej procedurze jest używana <xref:System.Net.Http.HttpClient> wystąpienia, `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Komentarz lub usunąć `For Each` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.  
  
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
  
3.  Zdefiniuj [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn. Zadania są uruchamiane podczas szacowania zapytania.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca. Po zakończeniu `Await` wyrażenie ma tablicę liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązań Task.WhenAll  
  
-   Dla obu rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku. Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Jednak zauważyć, że witryn sieci Web są wyświetlane w innej kolejności zawsze.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzeń w projekcie, który używa `GetURLContentsAsync` metodę, aby pobrać zawartość z sieci web.  
  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzenia do projektu, który używa metody `HttpClient.GetByteArrayAsync` na pobieranie zawartości z sieci web.  
  
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
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
