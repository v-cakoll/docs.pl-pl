---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595720"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="e218f-102">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="e218f-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="e218f-103">Można skonfigurować przycisk, którego można użyć do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na jej zakończenie.</span><span class="sxs-lookup"><span data-stu-id="e218f-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="e218f-104">Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji pobierającej zawartość jednej witryny sieci Web lub listy witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e218f-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="e218f-105">W przykładach użyto interfejsu użytkownika, który [dostraja aplikację asynchroniczną (C#)](./fine-tuning-your-async-application.md) .</span><span class="sxs-lookup"><span data-stu-id="e218f-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="e218f-106">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="e218f-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="e218f-107">Anulowanie zadania</span><span class="sxs-lookup"><span data-stu-id="e218f-107">Cancel a task</span></span>

<span data-ttu-id="e218f-108">Pierwszy przykład kojarzy przycisk **Anuluj** z pojedynczym zadaniem pobierania.</span><span class="sxs-lookup"><span data-stu-id="e218f-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="e218f-109">Jeśli wybierzesz przycisk podczas pobierania zawartości przez aplikację, pobieranie zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="e218f-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="e218f-110">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="e218f-110">Download the example</span></span>

<span data-ttu-id="e218f-111">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="e218f-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e218f-112">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e218f-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e218f-113">Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e218f-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e218f-114">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="e218f-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="e218f-115">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelATask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="e218f-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e218f-116">Wybierz klawisz **F5** , aby uruchomić projekt (lub naciśnij klawisz **Ctrl**+**F5** , aby uruchomić projekt bez debugowania).</span><span class="sxs-lookup"><span data-stu-id="e218f-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="e218f-117">Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e218f-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="e218f-118">Kompiluj przykład</span><span class="sxs-lookup"><span data-stu-id="e218f-118">Build the example</span></span>
 <span data-ttu-id="e218f-119">Następujące zmiany umożliwiają dodanie przycisku **Anuluj** do aplikacji, która pobiera witrynę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e218f-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="e218f-120">Jeśli nie chcesz pobierać ani kompilować przykładu, możesz przejrzeć końcowy produkt w sekcji "kompletne przykłady" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e218f-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="e218f-121">Gwiazdki oznaczają zmiany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="e218f-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="e218f-122">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **StarterCode** jako **projekt startowy** , a nie **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="e218f-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="e218f-123">Następnie Dodaj następujące zmiany do pliku MainWindow.xaml.cs tego projektu.</span><span class="sxs-lookup"><span data-stu-id="e218f-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="e218f-124">Zadeklaruj `cts`zmienną, która znajduje się w zakresie dla wszystkich metod, które mają do niego dostęp. `CancellationTokenSource`</span><span class="sxs-lookup"><span data-stu-id="e218f-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="e218f-125">Dodaj następujący program obsługi zdarzeń dla przycisku **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="e218f-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="e218f-126">Procedura obsługi zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metody do powiadamiania `cts` , gdy użytkownik zażąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="e218f-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. <span data-ttu-id="e218f-127">Wprowadź następujące zmiany w obsłudze zdarzeń dla przycisku `startButton_Click` **Start** .</span><span class="sxs-lookup"><span data-stu-id="e218f-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="e218f-128">Utwórz wystąpienie obiektu `cts`,. `CancellationTokenSource`</span><span class="sxs-lookup"><span data-stu-id="e218f-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="e218f-129">W wywołaniu `AccessTheWebAsync`elementu, który pobiera zawartość określonej witryny sieci Web, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> Wyślij Właściwość `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="e218f-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="e218f-130">`Token` Właściwość propaguje komunikat w przypadku żądania anulowania.</span><span class="sxs-lookup"><span data-stu-id="e218f-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="e218f-131">Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik zdecyduje się anulować operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="e218f-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="e218f-132">Poniższy kod przedstawia zmiany.</span><span class="sxs-lookup"><span data-stu-id="e218f-132">The following code shows the changes.</span></span>

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. <span data-ttu-id="e218f-133">W `AccessTheWebAsync`programie <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> Użyj przeciążenia`GetAsync` metody w<xref:System.Net.Http.HttpClient> typie, aby pobrać zawartość witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e218f-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="e218f-134">Pass `ct` ,parametr`AccessTheWebAsync`,jakodrugiargument. <xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="e218f-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="e218f-135">Token przenosi komunikat, jeśli użytkownik wybierze przycisk **Anuluj** .</span><span class="sxs-lookup"><span data-stu-id="e218f-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="e218f-136">Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e218f-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. <span data-ttu-id="e218f-137">Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e218f-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="e218f-138">Jeśli wybierzesz przycisk **Anuluj** , zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e218f-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="e218f-139">Anulowanie listy zadań</span><span class="sxs-lookup"><span data-stu-id="e218f-139">Cancel a list of tasks</span></span>

<span data-ttu-id="e218f-140">Możesz poszerzyć poprzedni przykład, aby anulować wiele zadań, kojarząc to samo `CancellationTokenSource` wystąpienie z każdym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="e218f-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="e218f-141">Jeśli wybierzesz przycisk **Anuluj** , anulujesz wszystkie zadania, które nie zostały jeszcze ukończone.</span><span class="sxs-lookup"><span data-stu-id="e218f-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="e218f-142">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="e218f-142">Download the example</span></span>

<span data-ttu-id="e218f-143">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="e218f-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="e218f-144">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e218f-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="e218f-145">Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="e218f-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="e218f-146">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="e218f-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="e218f-147">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAListOfTasks** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="e218f-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="e218f-148">Wybierz klawisz **F5** , aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="e218f-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="e218f-149">Wybierz **klawisz Ctrl**+**F5** , aby uruchomić projekt bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="e218f-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="e218f-150">Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e218f-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="e218f-151">Kompiluj przykład</span><span class="sxs-lookup"><span data-stu-id="e218f-151">Build the example</span></span>

<span data-ttu-id="e218f-152">Aby poszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelATask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="e218f-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="e218f-153">Dodaj następujące zmiany do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="e218f-153">Add the following changes to that project.</span></span> <span data-ttu-id="e218f-154">Gwiazdki oznaczają zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="e218f-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="e218f-155">Dodaj metodę, aby utworzyć listę adresów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="e218f-155">Add a method to create a list of web addresses.</span></span>

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. <span data-ttu-id="e218f-156">Wywołaj metodę w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="e218f-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="e218f-157">Dodaj następującą pętlę w `AccessTheWebAsync` programie, aby przetwarzać poszczególne adresy sieci Web na liście.</span><span class="sxs-lookup"><span data-stu-id="e218f-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. <span data-ttu-id="e218f-158">Ponieważ `AccessTheWebAsync` wyświetla długości, metoda nie musi zwracać żadnych elementów.</span><span class="sxs-lookup"><span data-stu-id="e218f-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="e218f-159">Usuń instrukcję return i Zmień zwracany typ metody na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>zamiast.</span><span class="sxs-lookup"><span data-stu-id="e218f-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="e218f-160">Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e218f-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="e218f-161">Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e218f-161">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     <span data-ttu-id="e218f-162">Jeśli wybierzesz przycisk **Anuluj** przed ukończeniem pobierania, dane wyjściowe zawierają długości plików do pobrania, które zakończyły się przed anulowaniem.</span><span class="sxs-lookup"><span data-stu-id="e218f-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="e218f-163">Kompletne przykłady</span><span class="sxs-lookup"><span data-stu-id="e218f-163">Complete examples</span></span>

<span data-ttu-id="e218f-164">Poniższe sekcje zawierają kod dla każdego z powyższych przykładów.</span><span class="sxs-lookup"><span data-stu-id="e218f-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="e218f-165">Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="e218f-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="e218f-166">Możesz pobrać projekty z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="e218f-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="e218f-167">Przykład — anulowanie zadania</span><span class="sxs-lookup"><span data-stu-id="e218f-167">Example - Cancel a task</span></span>

<span data-ttu-id="e218f-168">Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.</span><span class="sxs-lookup"><span data-stu-id="e218f-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="e218f-169">Przykład — anulowanie listy zadań</span><span class="sxs-lookup"><span data-stu-id="e218f-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="e218f-170">Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje listę zadań.</span><span class="sxs-lookup"><span data-stu-id="e218f-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="e218f-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e218f-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="e218f-172">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="e218f-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="e218f-173">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="e218f-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="e218f-174">Przykład asynchroniczny: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="e218f-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
