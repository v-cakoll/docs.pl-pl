---
title: Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970032"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="ad65b-102">Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="ad65b-102">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="ad65b-103">Można zwiększyć wydajność rozwiązania asynchronicznego w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ad65b-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ad65b-104">Ta metoda asynchronicznie oczekuje na wiele operacji asynchronicznych, które są reprezentowane jako zbiór zadań.</span><span class="sxs-lookup"><span data-stu-id="ad65b-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="ad65b-105">Być może zauważyłeś w instruktażenie, że strony internetowe pobierają po różnych cenach.</span><span class="sxs-lookup"><span data-stu-id="ad65b-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="ad65b-106">Czasami jedna ze stron internetowych jest bardzo powolna, co opóźnia wszystkie pozostałe pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="ad65b-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="ad65b-107">Po uruchomieniu rozwiązań asynchronicznych, które tworzysz w instruktażu, można zakończyć program łatwo, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby, aby rozpocząć wszystkie pliki do pobrania w tym samym czasie i niech szybsze pobieranie kontynuować bez czekania na ten, który jest Opóźnione.</span><span class="sxs-lookup"><span data-stu-id="ad65b-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="ad65b-108">Metoda jest `Task.WhenAll` stosowana do kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="ad65b-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="ad65b-109">Aplikacja `WhenAll` zwraca pojedyncze zadanie, które nie zostało ukończone, dopóki nie zostanie ukończone każde zadanie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ad65b-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="ad65b-110">Zadania wydają się działać równolegle, ale nie są tworzone żadne dodatkowe wątki.</span><span class="sxs-lookup"><span data-stu-id="ad65b-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="ad65b-111">Zadania można wykonać w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="ad65b-111">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad65b-112">W poniższych procedurach opisano rozszerzenia aplikacji asynchronicznych, które zostały opracowane w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ad65b-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ad65b-113">Aplikacje można tworzyć, wykonując instruktaże lub pobierając kod z [przykładów kodu dewelopera.](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)</span><span class="sxs-lookup"><span data-stu-id="ad65b-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="ad65b-114">Aby uruchomić przykład, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ad65b-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="ad65b-115">Aby dodać Task.WhenAll do rozwiązania GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="ad65b-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="ad65b-116">Dodaj `ProcessURLAsync` metodę do pierwszej aplikacji, która została opracowana w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ad65b-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="ad65b-117">Jeśli kod został pobrany z [przykładów kodu dewelopera,](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)otwórz `ProcessURLAsync` projekt AsyncWalkthrough, a następnie dodaj do pliku MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="ad65b-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="ad65b-118">Jeśli został opracowany kod, wykonując instruktaże, `ProcessURLAsync` dodaj `GetURLContentsAsync` do aplikacji, która zawiera metodę.</span><span class="sxs-lookup"><span data-stu-id="ad65b-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="ad65b-119">Plik MainWindow.xaml.cs dla tej aplikacji jest pierwszym przykładem w sekcji "Kompletne przykłady kodu z instruktażenia".</span><span class="sxs-lookup"><span data-stu-id="ad65b-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="ad65b-120">Metoda `ProcessURLAsync` konsoliduje akcje w treści `foreach` pętli `SumPageSizesAsync` w oryginalnym instruktaże.</span><span class="sxs-lookup"><span data-stu-id="ad65b-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="ad65b-121">Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="ad65b-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="ad65b-122">Skomentuj lub `foreach` usuń `SumPageSizesAsync`pętlę w , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad65b-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="ad65b-123">Tworzenie kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="ad65b-123">Create a collection of tasks.</span></span> <span data-ttu-id="ad65b-124">Poniższy kod definiuje [kwerendę,](../linq/index.md) która po <xref:System.Linq.Enumerable.ToArray%2A> wykonaniu przez metodę tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-124">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="ad65b-125">Zadania są uruchamiane, gdy kwerenda jest oceniana.</span><span class="sxs-lookup"><span data-stu-id="ad65b-125">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="ad65b-126">Dodaj następujący kod `SumPageSizesAsync` do metody `urlList`po deklaracji .</span><span class="sxs-lookup"><span data-stu-id="ad65b-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="ad65b-127">Zastosuj `Task.WhenAll` `downloadTasks`do zbierania zadań, .</span><span class="sxs-lookup"><span data-stu-id="ad65b-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="ad65b-128">`Task.WhenAll`zwraca pojedyncze zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="ad65b-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="ad65b-129">W poniższym `await` przykładzie wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ad65b-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="ad65b-130">Wyrażenie jest obliczane do tablicy liczb całkowitych, gdzie każda liczba całkowita jest długość pobranej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="ad65b-131">Dodaj następujący kod `SumPageSizesAsync`do , tuż po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="ad65b-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="ad65b-132">Na koniec <xref:System.Linq.Enumerable.Sum%2A> użyj metody, aby obliczyć sumę długości wszystkich stron internetowych.</span><span class="sxs-lookup"><span data-stu-id="ad65b-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="ad65b-133">Dodaj następujący wiersz `SumPageSizesAsync`do .</span><span class="sxs-lookup"><span data-stu-id="ad65b-133">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="ad65b-134">Aby dodać Task.WhenAll do rozwiązania HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="ad65b-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="ad65b-135">Dodaj następującą `ProcessURLAsync` wersję do drugiej aplikacji, która została opracowana w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ad65b-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="ad65b-136">Jeśli kod został pobrany z [przykładów kodu dewelopera,](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do MainWindow.xaml.cs pliku.</span><span class="sxs-lookup"><span data-stu-id="ad65b-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="ad65b-137">Jeśli został opracowany kod, wykonując instruktaże, `ProcessURLAsync` dodaj `HttpClient.GetByteArrayAsync` do aplikacji, która używa metody.</span><span class="sxs-lookup"><span data-stu-id="ad65b-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="ad65b-138">Plik MainWindow.xaml.cs dla tej aplikacji jest drugim przykładem w sekcji "Kompletne przykłady kodu z instruktażu".</span><span class="sxs-lookup"><span data-stu-id="ad65b-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="ad65b-139">Metoda `ProcessURLAsync` konsoliduje akcje w treści `foreach` pętli `SumPageSizesAsync` w oryginalnym instruktaże.</span><span class="sxs-lookup"><span data-stu-id="ad65b-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="ad65b-140">Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="ad65b-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="ad65b-141">Jedyną różnicą `ProcessURLAsync` od metody w poprzedniej <xref:System.Net.Http.HttpClient> procedurze `client`jest użycie wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ad65b-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="ad65b-142">Skomentuj lub `For Each` usuń `foreach` lub `SumPageSizesAsync`pętlę w , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad65b-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

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

3. <span data-ttu-id="ad65b-143">Zdefiniuj [kwerendę,](../linq/index.md) która po wykonaniu <xref:System.Linq.Enumerable.ToArray%2A> przez metodę tworzy zbiór zadań, które pobierają zawartość każdej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-143">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="ad65b-144">Zadania są uruchamiane, gdy kwerenda jest oceniana.</span><span class="sxs-lookup"><span data-stu-id="ad65b-144">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="ad65b-145">Dodaj następujący kod `SumPageSizesAsync` do metody `client` po `urlList`deklaracji i .</span><span class="sxs-lookup"><span data-stu-id="ad65b-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="ad65b-146">Następnie zastosuj `Task.WhenAll` `downloadTasks`do zbierania zadań, .</span><span class="sxs-lookup"><span data-stu-id="ad65b-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="ad65b-147">`Task.WhenAll`zwraca pojedyncze zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="ad65b-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="ad65b-148">W poniższym `await` przykładzie wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ad65b-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="ad65b-149">Po zakończeniu `await` wyrażenie jest obliczane do tablicy liczb całkowitych, gdzie każda liczba całkowita jest długość pobranej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="ad65b-150">Dodaj następujący kod `SumPageSizesAsync`do , tuż po kodzie dodanym w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="ad65b-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="ad65b-151">Na koniec <xref:System.Linq.Enumerable.Sum%2A> użyj metody, aby uzyskać sumę długości wszystkich stron internetowych.</span><span class="sxs-lookup"><span data-stu-id="ad65b-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="ad65b-152">Dodaj następujący wiersz `SumPageSizesAsync`do .</span><span class="sxs-lookup"><span data-stu-id="ad65b-152">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="ad65b-153">Aby przetestować rozwiązania Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="ad65b-153">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="ad65b-154">Dla jednego z rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="ad65b-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="ad65b-155">Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchroniczny w [Instruktaż: Dostęp do sieci Web za pomocą async i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="ad65b-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="ad65b-156">Należy jednak zauważyć, że strony internetowe pojawiają się w innej kolejności za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="ad65b-156">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="ad65b-157">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad65b-157">Example</span></span>

<span data-ttu-id="ad65b-158">Poniższy kod pokazuje rozszerzenia do projektu, `GetURLContentsAsync` który używa metody do pobierania zawartości z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

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

## <a name="example"></a><span data-ttu-id="ad65b-159">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad65b-159">Example</span></span>

<span data-ttu-id="ad65b-160">Poniższy kod pokazuje rozszerzenia do projektu, `HttpClient.GetByteArrayAsync` który używa metody do pobierania zawartości z sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad65b-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad65b-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad65b-161">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ad65b-162">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)</span><span class="sxs-lookup"><span data-stu-id="ad65b-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
