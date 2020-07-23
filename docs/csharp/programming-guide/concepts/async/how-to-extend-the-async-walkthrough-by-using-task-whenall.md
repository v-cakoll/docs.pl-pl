---
title: Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)
description: Dowiedz się, jak poprawić wydajność rozwiązania asynchronicznego w języku C# przy użyciu metody Task. WhenAll. Ta metoda asynchronicznie czeka na wiele operacji asynchronicznych.
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 275f4aeca854f8938642dbea40bf7fd9dc5362d9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925218"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="5fffb-104">Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="5fffb-104">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="5fffb-105">W przewodniku można poprawić wydajność rozwiązania asynchronicznego [: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5fffb-105">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5fffb-106">Ta metoda asynchronicznie czeka na wiele operacji asynchronicznych, które są reprezentowane jako kolekcja zadań.</span><span class="sxs-lookup"><span data-stu-id="5fffb-106">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="5fffb-107">W instruktażu można zauważyć, że witryny sieci Web pobierają różne stawki.</span><span class="sxs-lookup"><span data-stu-id="5fffb-107">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="5fffb-108">Czasami jedna z witryn sieci Web działa bardzo wolno, co opóźnia wszystkie pozostałe pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5fffb-108">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="5fffb-109">Po uruchomieniu rozwiązań asynchronicznych, które zostały skompilowane w przewodniku, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem jest uruchomienie wszystkich pobrań w tym samym czasie i szybsze pobieranie będzie kontynuowane bez czekania na ten, który jest opóźniony.</span><span class="sxs-lookup"><span data-stu-id="5fffb-109">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="5fffb-110">Metoda zostanie zastosowana `Task.WhenAll` do kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="5fffb-110">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="5fffb-111">Aplikacja `WhenAll` zwraca pojedyncze zadanie, które nie zostanie ukończone, dopóki każde zadanie w kolekcji nie zostanie ukończone.</span><span class="sxs-lookup"><span data-stu-id="5fffb-111">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="5fffb-112">Zadania są uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone.</span><span class="sxs-lookup"><span data-stu-id="5fffb-112">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="5fffb-113">Zadania można wykonać w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5fffb-113">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5fffb-114">Poniższe procedury opisują rozszerzenia dla aplikacji asynchronicznych, które są opracowywane w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5fffb-114">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="5fffb-115">Aplikacje można opracowywać, wykonując Instruktaż lub pobierając kod z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="5fffb-115">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="5fffb-116">Aby uruchomić ten przykład, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="5fffb-116">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="5fffb-117">Aby dodać zadanie. WhenAll do rozwiązania GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="5fffb-117">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="5fffb-118">Dodaj `ProcessURLAsync` metodę do pierwszej aplikacji opracowanej w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5fffb-118">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="5fffb-119">Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), Otwórz projekt AsyncWalkthrough, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="5fffb-119">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="5fffb-120">Jeśli kod został opracowany przez wypełnienie przewodnika, należy dodać `ProcessURLAsync` do aplikacji, która zawiera `GetURLContentsAsync` metodę.</span><span class="sxs-lookup"><span data-stu-id="5fffb-120">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="5fffb-121">Plik MainWindow.xaml.cs dla tej aplikacji to pierwszy przykład w sekcji "pełne przykłady kodu z przewodnika".</span><span class="sxs-lookup"><span data-stu-id="5fffb-121">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="5fffb-122">`ProcessURLAsync`Metoda konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` pierwotnym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="5fffb-122">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="5fffb-123">Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="5fffb-123">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="5fffb-124">Skomentuj lub Usuń `foreach` pętlę w `SumPageSizesAsync` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5fffb-124">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="5fffb-125">Utwórz kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="5fffb-125">Create a collection of tasks.</span></span> <span data-ttu-id="5fffb-126">Poniższy kod definiuje [zapytanie](../linq/index.md) , które podczas wykonywania przez <xref:System.Linq.Enumerable.ToArray%2A> metodę, tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-126">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="5fffb-127">Zadania są uruchamiane, gdy zapytanie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="5fffb-127">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="5fffb-128">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-128">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="5fffb-129">Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-129">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="5fffb-130">`Task.WhenAll`zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="5fffb-130">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="5fffb-131">W poniższym przykładzie `await` wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="5fffb-131">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="5fffb-132">Wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-132">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="5fffb-133">Dodaj następujący kod do `SumPageSizesAsync` , tuż po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="5fffb-133">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="5fffb-134">Na koniec Użyj <xref:System.Linq.Enumerable.Sum%2A> metody, aby obliczyć sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-134">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="5fffb-135">Dodaj następujący wiersz do `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-135">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="5fffb-136">Aby dodać zadanie. WhenAll do rozwiązania HttpClient. GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="5fffb-136">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="5fffb-137">Dodaj następującą wersję programu `ProcessURLAsync` do drugiej aplikacji, która została opracowana w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5fffb-137">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="5fffb-138">Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough_HttpClient, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="5fffb-138">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="5fffb-139">Jeśli kod został opracowany przez wypełnienie przewodnika, należy dodać `ProcessURLAsync` do aplikacji używającej `HttpClient.GetByteArrayAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="5fffb-139">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="5fffb-140">Plik MainWindow.xaml.cs dla tej aplikacji to drugi przykład w sekcji "kompletne przykłady kodu z przewodnika".</span><span class="sxs-lookup"><span data-stu-id="5fffb-140">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="5fffb-141">`ProcessURLAsync`Metoda konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` pierwotnym instruktażu.</span><span class="sxs-lookup"><span data-stu-id="5fffb-141">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="5fffb-142">Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="5fffb-142">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="5fffb-143">Jedyną różnicą z `ProcessURLAsync` metody opisanej w poprzedniej procedurze jest użycie <xref:System.Net.Http.HttpClient> wystąpienia, `client` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-143">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="5fffb-144">Skomentuj lub Usuń `For Each` `foreach` pętlę lub w `SumPageSizesAsync` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5fffb-144">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="5fffb-145">Zdefiniuj [zapytanie](../linq/index.md) , które po wykonaniu przez <xref:System.Linq.Enumerable.ToArray%2A> metodę tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-145">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="5fffb-146">Zadania są uruchamiane, gdy zapytanie jest oceniane.</span><span class="sxs-lookup"><span data-stu-id="5fffb-146">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="5fffb-147">Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-147">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="5fffb-148">Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-148">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="5fffb-149">`Task.WhenAll`zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="5fffb-149">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="5fffb-150">W poniższym przykładzie `await` wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="5fffb-150">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="5fffb-151">Po zakończeniu `await` wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-151">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="5fffb-152">Dodaj następujący kod do `SumPageSizesAsync` , tuż po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="5fffb-152">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="5fffb-153">Na koniec Użyj <xref:System.Linq.Enumerable.Sum%2A> metody, aby uzyskać sumę długości wszystkich witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-153">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="5fffb-154">Dodaj następujący wiersz do `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="5fffb-154">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="5fffb-155">Aby przetestować rozwiązania Task. WhenAll</span><span class="sxs-lookup"><span data-stu-id="5fffb-155">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="5fffb-156">Dla dowolnego rozwiązania wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="5fffb-156">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="5fffb-157">Dane wyjściowe powinny wyglądać podobnie do danych wyjściowych z rozwiązań asynchronicznych w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="5fffb-157">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="5fffb-158">Należy jednak zauważyć, że witryny sieci Web są wyświetlane w innej kolejności za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="5fffb-158">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="5fffb-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fffb-159">Example</span></span>

<span data-ttu-id="5fffb-160">Poniższy kod przedstawia rozszerzenia projektu, który używa `GetURLContentsAsync` metody do pobierania zawartości z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-160">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="5fffb-161">Przykład</span><span class="sxs-lookup"><span data-stu-id="5fffb-161">Example</span></span>

<span data-ttu-id="5fffb-162">Poniższy kod przedstawia rozszerzenia projektu, który używa metody `HttpClient.GetByteArrayAsync` do pobierania zawartości z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5fffb-162">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

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
                from url in urlList select ProcessURLAsync(url, client);

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="5fffb-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fffb-163">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5fffb-164">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="5fffb-164">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
