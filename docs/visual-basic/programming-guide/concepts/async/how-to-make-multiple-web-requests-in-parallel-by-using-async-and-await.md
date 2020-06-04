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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="2e0ee-102">Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0ee-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="2e0ee-103">W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="2e0ee-104">Operator [await](../../../language-reference/operators/await-operator.md) jest stosowany do zadania w punkcie metody, w którym przetwarzanie nie może być kontynuowane do momentu zakończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-104">The [Await](../../../language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="2e0ee-105">Często zadanie jest oczekiwane zaraz po jego utworzeniu, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>

```vb
Dim result = Await someWebAccessMethodAsync(url)
```

<span data-ttu-id="2e0ee-106">Można jednak oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli program ma inne zadania do wykonania, które nie zależą od ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>

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

<span data-ttu-id="2e0ee-107">Między rozpoczęciem zadania i oczekiwaniem na niego można uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="2e0ee-108">Dodatkowe zadania niejawnie uruchamiają się równolegle, ale nie są tworzone żadne dodatkowe wątki.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>

<span data-ttu-id="2e0ee-109">Poniższy program uruchamia trzy asynchroniczne pobieranie w sieci Web, a następnie czeka na ich kolejność, w jakiej są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="2e0ee-110">Zwróć uwagę, że po uruchomieniu programu zadania nie zawsze kończą się w kolejności, w której zostały utworzone i oczekujące.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="2e0ee-111">Zaczynają one działać, gdy są tworzone, i co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie wyrażenie await.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>

> [!NOTE]
> <span data-ttu-id="2e0ee-112">Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>

<span data-ttu-id="2e0ee-113">Aby uzyskać inny przykład, który uruchamia wiele zadań w tym samym czasie, zobacz [How to: rozszerzając Przewodnik Async przy użyciu Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="2e0ee-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

<span data-ttu-id="2e0ee-114">Kod dla tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="2e0ee-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>

### <a name="to-set-up-the-project"></a><span data-ttu-id="2e0ee-115">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="2e0ee-115">To set up the project</span></span>

1. <span data-ttu-id="2e0ee-116">Aby skonfigurować aplikację WPF, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="2e0ee-117">Szczegółowe instrukcje dotyczące tych kroków można znaleźć w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="2e0ee-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="2e0ee-118">Utwórz aplikację WPF, która zawiera pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="2e0ee-119">Nadaj nazwę przyciskowi `startButton` i nazwij pole tekstowe `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="2e0ee-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>

    - <span data-ttu-id="2e0ee-120">Dodaj odwołanie do <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="2e0ee-120">Add a reference for <xref:System.Net.Http>.</span></span>

    - <span data-ttu-id="2e0ee-121">W pliku MainWindow. XAML. vb Dodaj `Imports` instrukcję dla elementu `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="2e0ee-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>

### <a name="to-add-the-code"></a><span data-ttu-id="2e0ee-122">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="2e0ee-122">To add the code</span></span>

1. <span data-ttu-id="2e0ee-123">W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="2e0ee-124">Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>

    ```vb
    resultsTextBox.Clear()
    Await CreateMultipleTasksAsync()
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."
    ```

     <span data-ttu-id="2e0ee-125">Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync` która dyskuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>

3. <span data-ttu-id="2e0ee-126">Dodaj do projektu następujące metody pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="2e0ee-126">Add the following support methods to the project:</span></span>

    - <span data-ttu-id="2e0ee-127">`ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web jako tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="2e0ee-128">Metoda pomocy technicznej, a `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>

    - <span data-ttu-id="2e0ee-129">`DisplayResults`Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="2e0ee-130">Ten ekran jest wyświetlany po zakończeniu pobierania każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-130">This display shows when each task has finished downloading.</span></span>

     <span data-ttu-id="2e0ee-131">Skopiuj następujące metody i wklej je po `startButton_Click` procedurze obsługi zdarzeń w MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

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

4. <span data-ttu-id="2e0ee-132">Na koniec Zdefiniuj metodę `CreateMultipleTasksAsync` , która wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>

    - <span data-ttu-id="2e0ee-133">Metoda deklaruje `HttpClient` obiekt, do którego należy uzyskać dostęp za pomocą <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="2e0ee-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>

    - <span data-ttu-id="2e0ee-134">Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601> , gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="2e0ee-135">Po zakończeniu każdego zadania program `DisplayResults` wyświetla adres URL zadania i długość pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="2e0ee-136">Ponieważ zadania są wykonywane asynchronicznie, kolejność, w której wyniki są wyświetlane, może różnić się od kolejności, w której zostały zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>

    - <span data-ttu-id="2e0ee-137">Metoda oczekuje na zakończenie każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="2e0ee-138">Każdy `Await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` do momentu zakończenia oczekującego zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="2e0ee-139">Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego wykonanego zadania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>

    - <span data-ttu-id="2e0ee-140">Po zakończeniu zadań i pobraniu wartości całkowitych Metoda sumuje długości witryn sieci Web i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>

     <span data-ttu-id="2e0ee-141">Skopiuj poniższą metodę i wklej ją do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-141">Copy the following method, and paste it into your solution.</span></span>

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

5. <span data-ttu-id="2e0ee-142">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="2e0ee-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="2e0ee-143">Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność, w jakiej się kończą, nie musi być kolejnością, w której są one tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>

## <a name="example"></a><span data-ttu-id="2e0ee-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e0ee-144">Example</span></span>

<span data-ttu-id="2e0ee-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="2e0ee-145">The following code contains the full example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2e0ee-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e0ee-146">See also</span></span>

- [<span data-ttu-id="2e0ee-147">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0ee-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="2e0ee-148">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0ee-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="2e0ee-149">Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e0ee-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
