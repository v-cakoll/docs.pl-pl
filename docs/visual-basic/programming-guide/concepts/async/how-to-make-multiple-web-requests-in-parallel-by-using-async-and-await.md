---
title: 'Instrukcje: Wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 3d5a41cab961f2ec054085b02a0047b69b488a1d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843152"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Instrukcje: Wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)
W metodzie asynchronicznej zadania są uruchamiane po ich utworzeniu. [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator jest stosowany do zadania w tym punkcie metody, których nie można kontynuować przetwarzania przed zakończeniem zadania. Często zadanie jest oczekiwane, zaraz po jego utworzeniu, co ilustruje poniższy przykład.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 Jednakże można oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli w programie trzeba wykonać inne prace, które nie są zależne od zakończenia tego zadania.  
  
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
  
 Między rozpoczęciem zadania i oczekiwaniem na, możesz uruchomić inne zadania. Dodatkowe zadania w sposób niejawny uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone.  
  
 Następujący program uruchamia trzy asynchroniczne web pobierania, a następnie oczekuje na ich zakończenie w kolejności, w którym są nazywane. Zwróć uwagę, po uruchomieniu programu, który zadania nie są zawsze kończone w kolejności, w którym są tworzone i oczekiwane. Zaczynają działać, gdyż zostały utworzone, gdy jeden lub więcej zadań może zakończyć zanim metoda osiągnie wyrażenie await.  
  
> [!NOTE]
>  Aby wykonać ten projekt, jest posiadanie programu Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.  
  
 Inny przykład, który rozpoczyna się wiele zadań, w tym samym czasie, zobacz [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Możesz pobrać kod dla tego przykładu z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1.  Aby skonfigurować aplikację programu WPF, wykonaj następujące czynności. Można znaleźć szczegółowe instrukcje tych kroków w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Tworzenie aplikacji WPF, która zawiera pole tekstowe i przycisk. Nazwij przycisk `startButton`i pole tekstowego `resultsTextBox`.  
  
    -   Dodaj odwołanie do <xref:System.Net.Http>.  
  
    -   W pliku MainWindow.xaml.vb Dodaj `Imports` poufności informacji dotyczące `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1.  W oknie projektu, MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.vb.  
  
2.  Skopiuj poniższy kod i wklej go w treść `startButton_Click` w MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync`, która steruje aplikacją.  
  
3.  Dodaj następujące metody pomocy technicznej do projektu:  
  
    -   `ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web w postaci tablicy bajtów. Metoda pomocnicza `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.  
  
    -   `DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. To wyświetlane, gdy każde zadanie zakończy pobieranie.  
  
     Kopiuj poniższe metody i wklej je za `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.vb.  
  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  Na koniec zdefiniuj metodę `CreateMultipleTasksAsync`, który wykonuje następujące czynności.  
  
    -   Metoda deklaruje `HttpClient` obiektu, który jest potrzebny na dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.  
  
    -   Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą. Gdy poszczególne podzadania zakończą, `DisplayResults` Wyświetla adres URL tego zadania i długość pobranej treści. Ponieważ zadania odbywają się asynchronicznie, kolejność, w jakiej są wyświetlane wyniki mogą różnić się od kolejności, w którym zostały zadeklarowane.  
  
    -   Metoda czeka na zakończenie każdego zadania. Każdy `Await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` aż oczekiwane zadanie się zakończy. Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego ukończonego zadania.  
  
    -   Kiedy zadania zostały ukończone i pobraniu wartości całkowitych, metoda sumuje długość witryn sieci Web i wyświetla wynik.  
  
     Kopiuj następującą metodę i wkleić go do rozwiązania.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
     Uruchom program kilka razy, aby sprawdzić, czy te trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność ich zakończenia niekoniecznie jest kolejnością w którym są tworzone i oczekiwane.  
  
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
            ProcessURLAsync("https://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
        ' Strip off the "https://".  
        Dim displayURL = url.Replace("https://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
