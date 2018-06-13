---
title: 'Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)'
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 4bdd3f32d2fa502de8ada352c522198a89a17f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339472"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="a67e7-102">Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="a67e7-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="a67e7-103">Może poprawić wydajność rozwiązania asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="a67e7-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a67e7-104">Ta metoda asynchronicznie oczekujące na wiele operacji asynchronicznych, które są reprezentowane jako kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="a67e7-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="a67e7-105">Zwróć uwagę, w tym przewodnikiem czy witryn sieci Web Pobierz w różnym tempie.</span><span class="sxs-lookup"><span data-stu-id="a67e7-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="a67e7-106">Czasami jednej z witryn sieci Web jest bardzo wolno, który wybrano opcję opóźnienia wszystkie pozostałe pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="a67e7-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="a67e7-107">Po uruchomieniu asynchroniczne rozwiązania, które można utworzyć w tym przewodnikiem, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby uruchomić wszystkie pobrane pliki w tym samym czasie i pozwól szybsze pobieranie kontynuować bez oczekiwania na to, że w  opóźnione.</span><span class="sxs-lookup"><span data-stu-id="a67e7-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="a67e7-108">Należy zastosować `Task.WhenAll` metody do kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="a67e7-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="a67e7-109">Stosowanie `WhenAll` zwraca pojedyncze zadanie, które nie są kompletne, do czasu ukończenia każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a67e7-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="a67e7-110">Wyświetlanie zadań do uruchomienia równoległego, ale nie dodatkowe wątki są tworzone.</span><span class="sxs-lookup"><span data-stu-id="a67e7-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="a67e7-111">Zadania można wykonać w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="a67e7-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a67e7-112">Poniższe procedury opisują rozszerzeń aplikacji async, które są opracowywane w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a67e7-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="a67e7-113">Aplikacje można tworzyć spełniając wskazówki lub pobieranie kodu z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="a67e7-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="a67e7-114">Aby uruchomić przykład, musi mieć programu Visual Studio 2012 lub nowszy jest zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="a67e7-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="a67e7-115">Aby dodać do rozwiązania GetURLContentsAsync Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="a67e7-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="a67e7-116">Dodaj `ProcessURLAsync` metody do pierwszej aplikacji, który został napisany w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a67e7-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="a67e7-117">Jeśli pobrano kod z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a67e7-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="a67e7-118">Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która obejmuje `GetURLContentsAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="a67e7-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="a67e7-119">Plik MainWindow.xaml.cs dla tej aplikacji jest pierwszym przykładzie w sekcji "Pełny kod przykłady z przewodnik".</span><span class="sxs-lookup"><span data-stu-id="a67e7-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="a67e7-120">`ProcessURLAsync` Metody konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` w oryginalnym wskazówki.</span><span class="sxs-lookup"><span data-stu-id="a67e7-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="a67e7-121">Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="a67e7-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="a67e7-122">Komentarz lub usunąć `foreach` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a67e7-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3.  <span data-ttu-id="a67e7-123">Utwórz kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="a67e7-123">Create a collection of tasks.</span></span> <span data-ttu-id="a67e7-124">Poniższy kod definiuje [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn.</span><span class="sxs-lookup"><span data-stu-id="a67e7-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="a67e7-125">Zadania są uruchamiane podczas szacowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="a67e7-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="a67e7-126">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="a67e7-127">Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="a67e7-128">`Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="a67e7-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="a67e7-129">W poniższym przykładzie `await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="a67e7-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="a67e7-130">Wyrażenie do tablicy liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="a67e7-131">Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="a67e7-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="a67e7-132">Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę obliczania sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="a67e7-133">Dodaj następujący wiersz do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="a67e7-134">Aby dodać Task.WhenAll rozwiązania HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="a67e7-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="a67e7-135">Dodaj następujące wersję `ProcessURLAsync` do drugiego aplikacji utworzoną w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a67e7-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="a67e7-136">Jeśli pobrano kod z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="a67e7-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="a67e7-137">Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która używa `HttpClient.GetByteArrayAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="a67e7-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="a67e7-138">Plik MainWindow.xaml.cs dla tej aplikacji jest drugi przykład w sekcji "Pełny kod przykłady z przewodnik".</span><span class="sxs-lookup"><span data-stu-id="a67e7-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="a67e7-139">`ProcessURLAsync` Metody konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` w oryginalnym wskazówki.</span><span class="sxs-lookup"><span data-stu-id="a67e7-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="a67e7-140">Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="a67e7-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="a67e7-141">Jedyną różnicą z `ProcessURLAsync` metody w poprzedniej procedurze jest używana <xref:System.Net.Http.HttpClient> wystąpienia, `client`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="a67e7-142">Komentarz lub usunąć `For Each` lub `foreach` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a67e7-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3.  <span data-ttu-id="a67e7-143">Zdefiniuj [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn.</span><span class="sxs-lookup"><span data-stu-id="a67e7-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="a67e7-144">Zadania są uruchamiane podczas szacowania zapytania.</span><span class="sxs-lookup"><span data-stu-id="a67e7-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="a67e7-145">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="a67e7-146">Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="a67e7-147">`Task.WhenAll` Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="a67e7-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="a67e7-148">W poniższym przykładzie `await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="a67e7-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="a67e7-149">Po zakończeniu `await` wyrażenie ma tablicę liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="a67e7-150">Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="a67e7-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="a67e7-151">Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="a67e7-152">Dodaj następujący wiersz do `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a67e7-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="a67e7-153">Aby przetestować rozwiązań Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="a67e7-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="a67e7-154">Dla obu rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a67e7-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="a67e7-155">Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a67e7-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="a67e7-156">Jednak zauważyć, że witryn sieci Web są wyświetlane w innej kolejności zawsze.</span><span class="sxs-lookup"><span data-stu-id="a67e7-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a67e7-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="a67e7-157">Example</span></span>  
 <span data-ttu-id="a67e7-158">Poniższy kod przedstawia rozszerzeń w projekcie, który używa `GetURLContentsAsync` metodę, aby pobrać zawartość z sieci web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
  
        }  
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="a67e7-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="a67e7-159">Example</span></span>  
 <span data-ttu-id="a67e7-160">Poniższy kod przedstawia rozszerzenia do projektu, który używa metody `HttpClient.GetByteArrayAsync` na pobieranie zawartości z sieci web.</span><span class="sxs-lookup"><span data-stu-id="a67e7-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURL(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
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
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="a67e7-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a67e7-161">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a67e7-162">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="a67e7-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
