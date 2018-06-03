---
title: 'Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 4d4ccda6657dd4d889e8495fa000715c1f7a5ba6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728446"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="0a64a-102">Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a64a-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="0a64a-103">W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone.</span><span class="sxs-lookup"><span data-stu-id="0a64a-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="0a64a-104">[Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator jest stosowany do zadań w momencie w metodzie, której nie można kontynuować przetwarzania przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="0a64a-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="0a64a-105">Często zadania jest oczekiwane, natychmiast po utworzeniu, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0a64a-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="0a64a-106">Jednak można oddzielić Tworzenie zadania z oczekiwanie na zadanie, jeśli program ma wykonywać inne zadania, które nie są zależne od ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="0a64a-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
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
  
 <span data-ttu-id="0a64a-107">Między uruchamianie zadania i oczekujące na on, można uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="0a64a-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="0a64a-108">Dodatkowe zadania niejawnie równolegle, ale nie dodatkowe wątki są tworzone.</span><span class="sxs-lookup"><span data-stu-id="0a64a-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="0a64a-109">Następujący program uruchamia trzy pobieranie asynchroniczne sieci web i Oczekiwanie je w kolejności, w którym są nazywane.</span><span class="sxs-lookup"><span data-stu-id="0a64a-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="0a64a-110">Powiadomienia i po uruchomieniu programu, w której zadania nie zawsze kończy się w kolejności, w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="0a64a-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="0a64a-111">Decydując się uruchomić, kiedy są tworzone i co najmniej jednego zadania może zakończyć się pomyślnie przed metody osiągnie wyrażenia await.</span><span class="sxs-lookup"><span data-stu-id="0a64a-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a64a-112">Aby ukończyć ten projekt, musi mieć program Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0a64a-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="0a64a-113">Na przykład innego uruchamiania wielu zadań jednocześnie, zobacz [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="0a64a-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="0a64a-114">Można pobrać kodu w tym przykładzie z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="0a64a-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="0a64a-115">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="0a64a-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="0a64a-116">Aby skonfigurować aplikacji WPF, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="0a64a-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="0a64a-117">Szczegółowe instrukcje w tych krokach można znaleźć [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="0a64a-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="0a64a-118">Tworzenie aplikacji programu WPF, która zawiera pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="0a64a-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="0a64a-119">Nazwa przycisku `startButton`oraz nazwę pola tekstowego `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0a64a-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="0a64a-120">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="0a64a-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="0a64a-121">W pliku MainWindow.xaml.vb Dodaj `Imports` instrukcji dla `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="0a64a-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="0a64a-122">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="0a64a-122">To add the code</span></span>  
  
1.  <span data-ttu-id="0a64a-123">W oknie projektowania MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="0a64a-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="0a64a-124">Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="0a64a-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="0a64a-125">Kod wywołuje metodę asynchroniczną `CreateMultipleTasksAsync`, które dyski aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0a64a-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="0a64a-126">Dodaj następujące metody pomocy technicznej do projektu:</span><span class="sxs-lookup"><span data-stu-id="0a64a-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="0a64a-127">`ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metodę, aby pobrać zawartość witryny sieci Web w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="0a64a-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="0a64a-128">Metoda obsługi `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="0a64a-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="0a64a-129">`DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="0a64a-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="0a64a-130">Pokazuje to wyświetlenie podczas każdego zadania został pobrany.</span><span class="sxs-lookup"><span data-stu-id="0a64a-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="0a64a-131">Skopiuj następujące metody i wklej je po `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="0a64a-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
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
  
4.  <span data-ttu-id="0a64a-132">Na koniec zdefiniować metody `CreateMultipleTasksAsync`, która wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="0a64a-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="0a64a-133">Deklaruje metody `HttpClient` obiektu, który chcesz uzyskać dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="0a64a-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="0a64a-134">Metoda utworzenie i uruchomienie zadania trzy typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0a64a-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="0a64a-135">Jak każdego zadania zakończeniu `DisplayResults` Wyświetla adres URL zadania i długość zawartości pobrane.</span><span class="sxs-lookup"><span data-stu-id="0a64a-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="0a64a-136">Ponieważ zadania są uruchomione asynchronicznie, kolejność wyświetlania wyników może się różnić od kolejności, w której była zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="0a64a-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="0a64a-137">Metoda oczekujące na zakończenie wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="0a64a-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="0a64a-138">Każdy `Await` operator wstrzymuje wykonywanie `CreateMultipleTasksAsync` dopiero po zakończeniu zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="0a64a-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="0a64a-139">Operator pobiera również wartość zwrotna z wywołania `ProcessURLAsync` z każdego ukończonego zadania.</span><span class="sxs-lookup"><span data-stu-id="0a64a-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="0a64a-140">Po zakończeniu zadania i wartości całkowite zostały pobrane, metoda sumuje długości witryn sieci Web i wyświetlane wyniki.</span><span class="sxs-lookup"><span data-stu-id="0a64a-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="0a64a-141">Następująca metoda skopiuj i wklej go do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="0a64a-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5.  <span data-ttu-id="0a64a-142">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0a64a-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="0a64a-143">Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze zakończone w tej samej kolejności i kolejność ich Zakończ nie musi być koniecznie kolejność, w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="0a64a-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a64a-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a64a-144">Example</span></span>  
 <span data-ttu-id="0a64a-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="0a64a-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0a64a-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a64a-146">See Also</span></span>  
 [<span data-ttu-id="0a64a-147">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a64a-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="0a64a-148">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a64a-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="0a64a-149">Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a64a-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
