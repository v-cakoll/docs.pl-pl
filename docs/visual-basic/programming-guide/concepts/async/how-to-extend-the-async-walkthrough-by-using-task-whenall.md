---
title: 'Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
ms.openlocfilehash: 918a02eadde367d870df4c51bccadf86c04eeb02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="c66c8-102">Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c66c8-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="c66c8-103">Może poprawić wydajność rozwiązania asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="c66c8-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c66c8-104">Ta metoda asynchronicznie oczekujące na wiele operacji asynchronicznych, które są reprezentowane jako kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="c66c8-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="c66c8-105">Zwróć uwagę, w tym przewodnikiem czy witryn sieci Web Pobierz w różnym tempie.</span><span class="sxs-lookup"><span data-stu-id="c66c8-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="c66c8-106">Czasami jednej z witryn sieci Web jest bardzo wolno, który wybrano opcję opóźnienia wszystkie pozostałe pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c66c8-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="c66c8-107">Po uruchomieniu asynchroniczne rozwiązania, które można utworzyć w tym przewodnikiem, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby uruchomić wszystkie pobrane pliki w tym samym czasie i pozwól szybsze pobieranie kontynuować bez oczekiwania na to, że w  opóźnione.</span><span class="sxs-lookup"><span data-stu-id="c66c8-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="c66c8-108">Należy zastosować `Task.WhenAll` metody do kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="c66c8-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="c66c8-109">Stosowanie `WhenAll` zwraca pojedyncze zadanie, które nie są kompletne, do czasu ukończenia każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c66c8-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="c66c8-110">Wyświetlanie zadań do uruchomienia równoległego, ale nie dodatkowe wątki są tworzone.</span><span class="sxs-lookup"><span data-stu-id="c66c8-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="c66c8-111">Zadania można wykonać w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c66c8-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c66c8-112">Poniższe procedury opisują rozszerzeń aplikacji async, które są opracowywane w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="c66c8-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="c66c8-113">Aplikacje można tworzyć spełniając wskazówki lub pobieranie kodu z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="c66c8-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
>   
>  <span data-ttu-id="c66c8-114">Aby uruchomić przykład, musi mieć programu Visual Studio 2012 lub nowszy jest zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c66c8-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="c66c8-115">Aby dodać do rozwiązania GetURLContentsAsync Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="c66c8-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="c66c8-116">Dodaj `ProcessURLAsync` metody do pierwszej aplikacji, który został napisany w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="c66c8-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="c66c8-117">Jeśli pobrano kod z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191), otwórz projekt AsyncWalkthrough, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c66c8-117">If you downloaded the code from  [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="c66c8-118">Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która obejmuje `GetURLContentsAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="c66c8-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="c66c8-119">Plik MainWindow.xaml.vb dla tej aplikacji jest pierwszym przykładzie w sekcji "Pełny kod przykłady z przewodnik".</span><span class="sxs-lookup"><span data-stu-id="c66c8-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="c66c8-120">`ProcessURLAsync` Metody konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym wskazówki.</span><span class="sxs-lookup"><span data-stu-id="c66c8-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="c66c8-121">Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="c66c8-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="c66c8-122">Komentarz lub usunąć `For Each` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="c66c8-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="c66c8-123">Utwórz kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="c66c8-123">Create a collection of tasks.</span></span> <span data-ttu-id="c66c8-124">Poniższy kod definiuje [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn.</span><span class="sxs-lookup"><span data-stu-id="c66c8-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="c66c8-125">Zadania są uruchamiane podczas szacowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="c66c8-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="c66c8-126">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="c66c8-127">Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="c66c8-128">`Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="c66c8-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="c66c8-129">W poniższym przykładzie `Await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="c66c8-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="c66c8-130">Wyrażenie do tablicy liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="c66c8-131">Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="c66c8-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="c66c8-132">Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę obliczania sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="c66c8-133">Dodaj następujący wiersz do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="c66c8-134">Aby dodać Task.WhenAll rozwiązania HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="c66c8-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="c66c8-135">Dodaj następujące wersję `ProcessURLAsync` do drugiego aplikacji utworzoną w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="c66c8-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="c66c8-136">Jeśli pobrano kod z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191), otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c66c8-136">If you downloaded the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="c66c8-137">Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która używa `HttpClient.GetByteArrayAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="c66c8-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="c66c8-138">Plik MainWindow.xaml.vb dla tej aplikacji jest drugi przykład w sekcji "Pełny kod przykłady z przewodnik".</span><span class="sxs-lookup"><span data-stu-id="c66c8-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="c66c8-139">`ProcessURLAsync` Metody konsoliduje akcje w treści `For Each` pętli w `SumPageSizesAsync` w oryginalnym wskazówki.</span><span class="sxs-lookup"><span data-stu-id="c66c8-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="c66c8-140">Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="c66c8-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="c66c8-141">Jedyną różnicą z `ProcessURLAsync` metody w poprzedniej procedurze jest używana <xref:System.Net.Http.HttpClient> wystąpienia, `client`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="c66c8-142">Komentarz lub usunąć `For Each` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="c66c8-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
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
  
3.  <span data-ttu-id="c66c8-143">Zdefiniuj [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn.</span><span class="sxs-lookup"><span data-stu-id="c66c8-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="c66c8-144">Zadania są uruchamiane podczas szacowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="c66c8-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="c66c8-145">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="c66c8-146">Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="c66c8-147">`Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="c66c8-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="c66c8-148">W poniższym przykładzie `Await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="c66c8-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="c66c8-149">Po zakończeniu `Await` wyrażenie ma tablicę liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="c66c8-150">Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="c66c8-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="c66c8-151">Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="c66c8-152">Dodaj następujący wiersz do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="c66c8-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="c66c8-153">Aby przetestować rozwiązań Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="c66c8-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="c66c8-154">Dla obu rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c66c8-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="c66c8-155">Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="c66c8-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="c66c8-156">Jednak zauważyć, że witryn sieci Web są wyświetlane w innej kolejności zawsze.</span><span class="sxs-lookup"><span data-stu-id="c66c8-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c66c8-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="c66c8-157">Example</span></span>  
 <span data-ttu-id="c66c8-158">Poniższy kod przedstawia rozszerzeń w projekcie, który używa `GetURLContentsAsync` metodę, aby pobrać zawartość z sieci web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="c66c8-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="c66c8-159">Example</span></span>  
 <span data-ttu-id="c66c8-160">Poniższy kod przedstawia rozszerzenia do projektu, który używa metody `HttpClient.GetByteArrayAsync` na pobieranie zawartości z sieci web.</span><span class="sxs-lookup"><span data-stu-id="c66c8-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c66c8-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c66c8-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c66c8-162">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c66c8-162">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
