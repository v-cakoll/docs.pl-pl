---
title: 'Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 1b98a0f29409fa49af1c9c8f7c91f2170981f7cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)
W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator jest stosowany do zadań w momencie w metodzie, której nie można kontynuować przetwarzania przed zakończeniem zadania. Często zadania jest oczekiwane, natychmiast po utworzeniu, jak przedstawiono na poniższym przykładzie.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Jednak można oddzielić Tworzenie zadania z oczekiwanie na zadanie, jeśli program ma wykonywać inne zadania, które nie są zależne od ukończenia zadania.  
  
```vb  
' The following line creates and starts the task.  
Dim myTask = someWebAccessMethodAsync(url)  
  
' While the task is running, you can do other work that does not depend  
' on the results of the task.  
' . . . . .  
  
' The application of Await suspends the rest of this method until the task is   
' complete.  
Dim result = Await myTask  
```  
  
 Między uruchamianie zadania i oczekujące na on, można uruchomić inne zadania. Dodatkowe zadania niejawnie równolegle, ale nie dodatkowe wątki są tworzone.  
  
 Następujący program uruchamia trzy pobieranie asynchroniczne sieci web i Oczekiwanie je w kolejności, w którym są nazywane. Powiadomienia i po uruchomieniu programu, w której zadania nie zawsze kończy się w kolejności, w którym są tworzone i oczekiwane. Decydując się uruchomić, kiedy są tworzone i co najmniej jednego zadania może zakończyć się pomyślnie przed metody osiągnie wyrażenia await.  
  
> [!NOTE]
>  Aby ukończyć ten projekt, musi mieć program Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.  
  
 Na przykład innego uruchamiania wielu zadań jednocześnie, zobacz [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Można pobrać kodu w tym przykładzie z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=254906).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1.  Aby skonfigurować aplikacji WPF, wykonaj następujące kroki. Szczegółowe instrukcje w tych krokach można znaleźć [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Tworzenie aplikacji programu WPF, która zawiera pole tekstowe i przycisk. Nazwa przycisku `startButton`oraz nazwę pola tekstowego `resultsTextBox`.  
  
    -   Dodaj odwołanie do <xref:System.Net.Http>.  
  
    -   W pliku MainWindow.xaml.vb Dodaj `Imports` instrukcji dla `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1.  W oknie projektowania MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb.  
  
2.  Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kod wywołuje metodę asynchroniczną `CreateMultipleTasksAsync`, które dyski aplikacji.  
  
3.  Dodaj następujące metody pomocy technicznej do projektu:  
  
    -   `ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metodę, aby pobrać zawartość witryny sieci Web w postaci tablicy bajtów. Metoda obsługi `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.  
  
    -   `DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. Pokazuje to wyświetlenie podczas każdego zadania został pobrany.  
  
     Skopiuj następujące metody i wklej je po `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb.  
  
    ```vb  
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
    ```  
  
4.  Na koniec zdefiniować metody `CreateMultipleTasksAsync`, która wykonuje następujące czynności.  
  
    -   Deklaruje metody `HttpClient` obiektu, który chcesz uzyskać dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.  
  
    -   Metoda utworzenie i uruchomienie zadania trzy typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą. Jak każdego zadania zakończeniu `DisplayResults` Wyświetla adres URL zadania i długość zawartości pobrane. Ponieważ zadania są uruchomione asynchronicznie, kolejność wyświetlania wyników może się różnić od kolejności, w której była zadeklarowana.  
  
    -   Metoda oczekujące na zakończenie wszystkich zadań. Każdy `Await` operator wstrzymuje wykonywanie `CreateMultipleTasksAsync` dopiero po zakończeniu zadania oczekiwano. Operator pobiera również wartość zwrotna z wywołania `ProcessURLAsync` z każdego ukończonego zadania.  
  
    -   Po zakończeniu zadania i wartości całkowite zostały pobrane, metoda sumuje długości witryn sieci Web i wyświetlane wyniki.  
  
     Następująca metoda skopiuj i wklej go do rozwiązania.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
    ```  
  
5.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze zakończone w tej samej kolejności i kolejność ich Zakończ nie musi być koniecznie kolejność, w którym są tworzone i oczekiwane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera pełny przykład.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
        resultsTextBox.Clear()  
        Await CreateMultipleTasksAsync()  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
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
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
