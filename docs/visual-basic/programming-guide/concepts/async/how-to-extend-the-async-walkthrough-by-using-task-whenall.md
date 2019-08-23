---
title: 'Instrukcje: Rozwiń Przewodnik asynchroniczny za pomocą polecenia Task. WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 8b88c51955a11a428e01f059cae2d7a6dd829300
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958064"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a>Instrukcje: Rozwiń Przewodnik asynchroniczny za pomocą polecenia Task. WhenAll (Visual Basic)
Wydajność rozwiązania asynchronicznego można poprawić w [przewodniku: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) (Visual Basic) <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> za pomocą metody. Ta metoda asynchronicznie czeka na wiele operacji asynchronicznych, które są reprezentowane jako kolekcja zadań.  
  
 W instruktażu można zauważyć, że witryny sieci Web pobierają różne stawki. Czasami jedna z witryn sieci Web działa bardzo wolno, co opóźnia wszystkie pozostałe pliki do pobrania. Po uruchomieniu rozwiązań asynchronicznych, które można skompilować w przewodniku, można łatwo zakończyć działanie programu, jeśli nie chcesz czekać, ale lepszym rozwiązaniem jest uruchomienie wszystkich pobrań w tym samym czasie i szybsze pobieranie będzie kontynuowane bez czekania na ten  Wydłuż.  
  
 `Task.WhenAll` Metoda zostanie zastosowana do kolekcji zadań. Aplikacja `WhenAll` zwraca pojedyncze zadanie, które nie zostanie ukończone, dopóki każde zadanie w kolekcji nie zostanie ukończone. Zadania są uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone. Zadania można wykonać w dowolnej kolejności.  
  
> [!IMPORTANT]
> Poniższe procedury opisują rozszerzenia dla aplikacji asynchronicznych, które są opracowywane w [przewodniku: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)(Visual Basic). Aplikacje można opracowywać, wykonując Instruktaż lub pobierając kod z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
>   
> Aby uruchomić ten przykład, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać zadanie. WhenAll do rozwiązania GetURLContentsAsync  
  
1. Dodaj metodę do pierwszej aplikacji, która została opracowana w [przewodniku: `ProcessURLAsync` Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)(Visual Basic).  
  
    - Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), Otwórz projekt AsyncWalkthrough, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow. XAML. vb.  
  
    - Jeśli kod został opracowany przez wypełnienie przewodnika, należy dodać `ProcessURLAsync` do aplikacji, która `GetURLContentsAsync` zawiera metodę. Plik MainWindow. XAML. vb dla tej aplikacji to pierwszy przykład w sekcji "pełne przykłady kodu z przewodnika".  
  
     Metoda konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` pierwotnym instruktażu. `ProcessURLAsync` Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Skomentuj lub Usuń `For Each` pętlę w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.  
  
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
  
3. Utwórz kolekcję zadań. Poniższy kod definiuje [zapytanie](../../../../visual-basic/programming-guide/concepts/linq/index.md) , które podczas wykonywania przez <xref:System.Linq.Enumerable.ToArray%2A> metodę, tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest oceniane.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po `urlList`deklaracji.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll`zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tuż po kodzie dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Na koniec Użyj <xref:System.Linq.Enumerable.Sum%2A> metody, aby obliczyć sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać zadanie. WhenAll do rozwiązania HttpClient. GetByteArrayAsync  
  
1. Dodaj następującą wersję programu `ProcessURLAsync` do drugiej aplikacji, która została opracowana w [przewodniku: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)(Visual Basic).  
  
    - Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), Otwórz projekt AsyncWalkthrough_HttpClient, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow. XAML. vb.  
  
    - Jeśli kod został opracowany przez wypełnienie przewodnika, należy dodać `ProcessURLAsync` do aplikacji `HttpClient.GetByteArrayAsync` używającej metody. Plik MainWindow. XAML. vb dla tej aplikacji to drugi przykład w sekcji "pełne przykłady kodu z przewodnika".  
  
     Metoda konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` pierwotnym instruktażu. `ProcessURLAsync` Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
     Jedyną różnicą z `ProcessURLAsync` metody opisanej w poprzedniej procedurze jest użycie <xref:System.Net.Http.HttpClient> wystąpienia, `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2. Skomentuj lub Usuń `For Each` pętlę w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.  
  
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
  
3. Zdefiniuj [zapytanie](../../../../visual-basic/programming-guide/concepts/linq/index.md) , które po wykonaniu przez <xref:System.Linq.Enumerable.ToArray%2A> metodę tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest oceniane.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po `client` deklaracji i `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4. Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll`zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `Await` wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Po zakończeniu `Await` wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tuż po kodzie dodanym w poprzednim kroku.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5. Na koniec Użyj <xref:System.Linq.Enumerable.Sum%2A> metody, aby uzyskać sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązania Task. WhenAll  
  
- Dla dowolnego rozwiązania wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** . Dane wyjściowe powinny wyglądać podobnie do danych wyjściowych z rozwiązań asynchronicznych w [przewodniku: Uzyskiwanie dostępu do sieci Web za pomocą Async i await](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)(Visual Basic). Należy jednak zauważyć, że witryny sieci Web są wyświetlane w innej kolejności za każdym razem.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzenia projektu, który używa `GetURLContentsAsync` metody do pobierania zawartości z sieci Web.  
  
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
 Poniższy kod przedstawia rozszerzenia projektu, który używa metody `HttpClient.GetByteArrayAsync` do pobierania zawartości z sieci Web.  
  
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
