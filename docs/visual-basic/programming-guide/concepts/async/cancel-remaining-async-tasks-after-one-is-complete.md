---
title: Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 5dab0c4aa14710fe78d2473675aea8b8c8bb73b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43874800"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="11a8c-102">Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11a8c-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="11a8c-103">Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda wraz z <xref:System.Threading.CancellationToken>, możesz anulować wszystkie pozostałe zadania po wykonaniu jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="11a8c-104">`WhenAny` Metoda przyjmuje argument, który jest kolekcją zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="11a8c-105">Metoda uruchamia wszystkie zadania i zwrócenie pojedynczego zadania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="11a8c-106">Pojedyncze zadanie jest ukończone po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="11a8c-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="11a8c-107">W tym przykładzie przedstawiono sposób użycia tokenu anulowania w połączeniu z `WhenAny` do przechowywania na pierwszym zadaniu do ukończenia zadań i anulowania pozostałych zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="11a8c-108">Każde zadanie powoduje pobieranie zawartości witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="11a8c-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="11a8c-109">Przykład wyświetla długość zawartości pierwszego pobieranego i anuluje inne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="11a8c-110">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="11a8c-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="11a8c-111">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="11a8c-111">Downloading the Example</span></span>  
 <span data-ttu-id="11a8c-112">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="11a8c-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="11a8c-113">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="11a8c-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="11a8c-114">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="11a8c-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="11a8c-115">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="11a8c-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="11a8c-116">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAfterOneTask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="11a8c-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="11a8c-117">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="11a8c-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="11a8c-118">Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="11a8c-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="11a8c-119">Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="11a8c-120">Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="11a8c-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="11a8c-121">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="11a8c-121">Building the Example</span></span>  
 <span data-ttu-id="11a8c-122">W przykładzie w tym temacie dodaje do projektu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) umożliwiający anulowanie listy zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](https://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="11a8c-123">W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="11a8c-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="11a8c-124">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="11a8c-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="11a8c-125">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="11a8c-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="11a8c-126">W pliku MainWindow.xaml.vb **CancelAListOfTasks** projektu, uruchom przejścia przez przeniesienie kroków przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="11a8c-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="11a8c-127">W `AccessTheWebAsync`, w tym przykładzie użyto zapytania, <xref:System.Linq.Enumerable.ToArray%2A> metody i `WhenAny` metodę, aby utworzyć i uruchomić szereg zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="11a8c-128">Stosowanie `WhenAny` do tablicy powoduje zwrócenie pojedynczego zadania, gdy jest oczekiwane, daje w wyniku pierwsze zadanie do wykonania w tablicy zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="11a8c-129">Wprowadź następujące zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="11a8c-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="11a8c-130">Gwiazdka oznacza zmiany w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="11a8c-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="11a8c-131">Skomentuj lub usuń pętlę.</span><span class="sxs-lookup"><span data-stu-id="11a8c-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="11a8c-132">Utwórz zapytanie, które, po wykonaniu, daje kolekcję zadań rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="11a8c-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="11a8c-133">Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="11a8c-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  <span data-ttu-id="11a8c-134">Wywołaj `ToArray` do wykonywania zapytania i uruchomić zadania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="11a8c-135">Stosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez używania `ToArray`, ale niekoniecznie innych metod.</span><span class="sxs-lookup"><span data-stu-id="11a8c-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="11a8c-136">Najbezpieczniejszym rozwiązaniem jest jawne wymuszenie wykonania zapytania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="11a8c-137">Wywołaj `WhenAny` na kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="11a8c-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="11a8c-138">`WhenAny` Zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="11a8c-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="11a8c-139">Oznacza to, że `WhenAny` zwraca klasę task, która ocenia do pojedynczego `Task(Of Integer)` lub `Task<int>` gdy jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="11a8c-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="11a8c-140">To pojedyncze zadanie jest pierwszym zadaniem w kolekcji, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="11a8c-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="11a8c-141">Przydzielono zadanie, które zostanie ukończone jako pierwsze `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="11a8c-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="11a8c-142">Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą, ponieważ jest to typ zwracany `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="11a8c-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="11a8c-143">W tym przykładzie interesuje Cię tylko zadanie, które zakończy się pierwsza.</span><span class="sxs-lookup"><span data-stu-id="11a8c-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="11a8c-144">W związku z tym, użyj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> anulować pozostałe zadania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="11a8c-145">Na koniec await `firstFinishedTask` na pobranie długości pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="11a8c-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="11a8c-146">Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="11a8c-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="11a8c-147">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="11a8c-147">Complete Example</span></span>  
 <span data-ttu-id="11a8c-148">Poniższy kod jest kompletny plik MainWindow.xaml.vb lub MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="11a8c-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="11a8c-149">Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="11a8c-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="11a8c-150">Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="11a8c-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="11a8c-151">Można ściągnąć projekt z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="11a8c-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11a8c-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11a8c-152">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="11a8c-153">Dostrajanie aplikacji Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11a8c-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="11a8c-154">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11a8c-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="11a8c-155">Próbka asynchroniczna: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="11a8c-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
