---
title: 'Porady: równoległe żądania sieci Web za pomocą Async i Await'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 40bab392af94ba941c2562e885a8d2e08aeea5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396587"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a>Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)

W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone. Operator [await](../../../language-reference/operators/await-operator.md) jest stosowany do zadania w punkcie metody, w którym przetwarzanie nie może być kontynuowane do momentu zakończenia zadania. Często zadanie jest oczekiwane zaraz po jego utworzeniu, tak jak pokazano w poniższym przykładzie.

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

Można jednak oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli program ma inne zadania do wykonania, które nie zależą od ukończenia zadania.

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

Między rozpoczęciem zadania i oczekiwaniem na niego można uruchomić inne zadania. Dodatkowe zadania niejawnie uruchamiają się równolegle, ale nie są tworzone żadne dodatkowe wątki.

Poniższy program uruchamia trzy asynchroniczne pobieranie w sieci Web, a następnie czeka na ich kolejność, w jakiej są wywoływane. Zwróć uwagę, że po uruchomieniu programu zadania nie zawsze kończą się w kolejności, w której zostały utworzone i oczekujące. Zaczynają one działać, gdy są tworzone, i co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie wyrażenie await.

> [!NOTE]
> Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

Aby uzyskać inny przykład, który uruchamia wiele zadań w tym samym czasie, zobacz [How to: rozszerzając Przewodnik Async przy użyciu Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

Kod dla tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).

### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt

1. Aby skonfigurować aplikację WPF, wykonaj następujące czynności. Szczegółowe instrukcje dotyczące tych kroków można znaleźć w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Utwórz aplikację WPF, która zawiera pole tekstowe i przycisk. Nadaj nazwę przyciskowi `startButton` i nazwij pole tekstowe `resultsTextBox` .

    - Dodaj odwołanie do <xref:System.Net.Http> .

    - W pliku MainWindow. XAML. vb Dodaj `Imports` instrukcję dla elementu `System.Net.Http` .

### <a name="to-add-the-code"></a>Aby dodać kod

1. W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow. XAML. vb.

2. Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow. XAML. vb.

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync` która dyskuje aplikację.

3. Dodaj do projektu następujące metody pomocy technicznej:

    - `ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web jako tablicy bajtów. Metoda pomocy technicznej, a `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.

    - `DisplayResults`Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. Ten ekran jest wyświetlany po zakończeniu pobierania każdego zadania.

     Skopiuj następujące metody i wklej je po `startButton_Click` procedurze obsługi zdarzeń w MainWindow. XAML. vb.

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

4. Na koniec Zdefiniuj metodę `CreateMultipleTasksAsync` , która wykonuje następujące czynności.

    - Metoda deklaruje `HttpClient` obiekt, do którego należy uzyskać dostęp za pomocą <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody `ProcessURLAsync` .

    - Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601> , gdzie `TResult` jest liczbą całkowitą. Po zakończeniu każdego zadania program `DisplayResults` wyświetla adres URL zadania i długość pobranej zawartości. Ponieważ zadania są wykonywane asynchronicznie, kolejność, w której wyniki są wyświetlane, może różnić się od kolejności, w której zostały zadeklarowane.

    - Metoda oczekuje na zakończenie każdego zadania. Każdy `Await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` do momentu zakończenia oczekującego zadania. Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego wykonanego zadania.

    - Po zakończeniu zadań i pobraniu wartości całkowitych Metoda sumuje długości witryn sieci Web i wyświetla wynik.

     Skopiuj poniższą metodę i wklej ją do rozwiązania.

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

5. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

     Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność, w jakiej się kończą, nie musi być kolejnością, w której są one tworzone i oczekiwane.

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

## <a name="see-also"></a>Zobacz też

- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](index.md)
- [Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
