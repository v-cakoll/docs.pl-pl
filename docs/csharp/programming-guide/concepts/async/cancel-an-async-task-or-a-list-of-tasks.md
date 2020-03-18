---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595720"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="611a7-102">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="611a7-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="611a7-103">Można skonfigurować przycisk, który służy do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na jej zakończenie.</span><span class="sxs-lookup"><span data-stu-id="611a7-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="611a7-104">Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość jednej witryny sieci Web lub listę witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="611a7-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="611a7-105">Przykłady używają interfejsu użytkownika, który [dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md) opisuje.</span><span class="sxs-lookup"><span data-stu-id="611a7-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="611a7-106">Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="611a7-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="611a7-107">Anulowanie zadania</span><span class="sxs-lookup"><span data-stu-id="611a7-107">Cancel a task</span></span>

<span data-ttu-id="611a7-108">Pierwszy przykład kojarzy przycisk **Anuluj** z jednym zadaniem pobierania.</span><span class="sxs-lookup"><span data-stu-id="611a7-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="611a7-109">Jeśli wybierzesz przycisk podczas pobierania zawartości przez aplikację, pobieranie zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="611a7-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="611a7-110">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="611a7-110">Download the example</span></span>

<span data-ttu-id="611a7-111">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="611a7-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="611a7-112">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="611a7-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="611a7-113">Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .</span><span class="sxs-lookup"><span data-stu-id="611a7-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="611a7-114">W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="611a7-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="611a7-115">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelATask,** a następnie wybierz pozycję **Ustaw jako projekt startup**.</span><span class="sxs-lookup"><span data-stu-id="611a7-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="611a7-116">Wybierz klawisz **F5,** aby uruchomić projekt (lub naciśnij klawisz **Ctrl**+**F5,** aby uruchomić projekt bez debugowania).</span><span class="sxs-lookup"><span data-stu-id="611a7-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="611a7-117">Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="611a7-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="611a7-118">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="611a7-118">Build the example</span></span>
 <span data-ttu-id="611a7-119">Poniższe zmiany dodają przycisk **Anuluj** do aplikacji, która pobiera witrynę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="611a7-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="611a7-120">Jeśli nie chcesz pobierać ani tworzyć przykładu, możesz przejrzeć produkt końcowy w sekcji "Pełne przykłady" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="611a7-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="611a7-121">Gwiazdki oznaczają zmiany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="611a7-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="611a7-122">Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **StarterCode** jako **projekt StartUp** zamiast **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="611a7-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="611a7-123">Następnie dodaj następujące zmiany do pliku MainWindow.xaml.cs tego projektu.</span><span class="sxs-lookup"><span data-stu-id="611a7-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="611a7-124">Deklaruj `cts`zmienną, `CancellationTokenSource` która jest w zakresie dla wszystkich metod, które uzyskują do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="611a7-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="611a7-125">Dodaj następujący program obsługi zdarzeń dla przycisku **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="611a7-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="611a7-126">Program obsługi zdarzeń używa metody, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> aby powiadomić, `cts` gdy użytkownik żąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="611a7-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

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

3. <span data-ttu-id="611a7-127">W programie obsługi zdarzeń dla **Start** przycisku `startButton_Click`Start wprowadzono następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="611a7-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    - <span data-ttu-id="611a7-128">Wystąpienia w ysłance `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="611a7-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - <span data-ttu-id="611a7-129">W wywołaniu `AccessTheWebAsync`, który pobiera zawartość określonej strony internetowej, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> wyślij `cts` właściwość jako argument.</span><span class="sxs-lookup"><span data-stu-id="611a7-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="611a7-130">Właściwość `Token` propaguje wiadomość, jeśli zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="611a7-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="611a7-131">Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik zdecyduje się anulować operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="611a7-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="611a7-132">Poniższy kod pokazuje zmiany.</span><span class="sxs-lookup"><span data-stu-id="611a7-132">The following code shows the changes.</span></span>

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

4. <span data-ttu-id="611a7-133">W `AccessTheWebAsync`, <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> użyj przeciążenia `GetAsync` metody <xref:System.Net.Http.HttpClient> w typie, aby pobrać zawartość strony internetowej.</span><span class="sxs-lookup"><span data-stu-id="611a7-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="611a7-134">Pass `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="611a7-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="611a7-135">Token niesie wiadomość, jeśli użytkownik wybierze przycisk **Anuluj.**</span><span class="sxs-lookup"><span data-stu-id="611a7-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="611a7-136">Poniższy kod pokazuje zmiany `AccessTheWebAsync`w pliku .</span><span class="sxs-lookup"><span data-stu-id="611a7-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

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

5. <span data-ttu-id="611a7-137">Jeśli program nie zostanie anulowany, generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="611a7-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="611a7-138">Jeśli wybierzesz przycisk **Anuluj** przed zakończeniem pobierania zawartości przez program, program wygeneruje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="611a7-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="611a7-139">Anulowanie listy zadań</span><span class="sxs-lookup"><span data-stu-id="611a7-139">Cancel a list of tasks</span></span>

<span data-ttu-id="611a7-140">Można rozszerzyć poprzedni przykład, aby anulować wiele zadań, `CancellationTokenSource` kojarząc to samo wystąpienie z każdym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="611a7-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="611a7-141">Jeśli wybierzesz przycisk **Anuluj,** anulujesz wszystkie zadania, które nie zostały jeszcze ukończone.</span><span class="sxs-lookup"><span data-stu-id="611a7-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="611a7-142">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="611a7-142">Download the example</span></span>

<span data-ttu-id="611a7-143">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="611a7-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="611a7-144">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="611a7-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="611a7-145">Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .</span><span class="sxs-lookup"><span data-stu-id="611a7-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="611a7-146">W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="611a7-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="611a7-147">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelAListOfTasks,** a następnie wybierz pozycję **Ustaw jako projekt StartUp**.</span><span class="sxs-lookup"><span data-stu-id="611a7-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="611a7-148">Wybierz klawisz **F5,** aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="611a7-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="611a7-149">Wybierz klawisze **Ctrl**+**F5,** aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="611a7-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="611a7-150">Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="611a7-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="611a7-151">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="611a7-151">Build the example</span></span>

<span data-ttu-id="611a7-152">Aby samodzielnie rozszerzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **cancelatask** jako **projekt StartUp**.</span><span class="sxs-lookup"><span data-stu-id="611a7-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="611a7-153">Dodaj następujące zmiany do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="611a7-153">Add the following changes to that project.</span></span> <span data-ttu-id="611a7-154">Gwiazdki oznaczają zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="611a7-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="611a7-155">Dodaj metodę tworzenia listy adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="611a7-155">Add a method to create a list of web addresses.</span></span>

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

2. <span data-ttu-id="611a7-156">Wywołaj metodę `AccessTheWebAsync`w pliku .</span><span class="sxs-lookup"><span data-stu-id="611a7-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="611a7-157">Dodaj następującą `AccessTheWebAsync` pętlę, aby przetworzyć każdy adres internetowy na liście.</span><span class="sxs-lookup"><span data-stu-id="611a7-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

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

4. <span data-ttu-id="611a7-158">Ponieważ `AccessTheWebAsync` wyświetla długości, metoda nie musi zwracać niczego.</span><span class="sxs-lookup"><span data-stu-id="611a7-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="611a7-159">Usuń return instrukcji i zmienić typ zwracany <xref:System.Threading.Tasks.Task> metody <xref:System.Threading.Tasks.Task%601>zamiast .</span><span class="sxs-lookup"><span data-stu-id="611a7-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="611a7-160">Wywołaj metodę `startButton_Click` z za pomocą instrukcji zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="611a7-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="611a7-161">Jeśli program nie zostanie anulowany, generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="611a7-161">If you don’t cancel the program, it produces the following output.</span></span>

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

     <span data-ttu-id="611a7-162">Jeśli wybierzesz przycisk **Anuluj** przed zakończeniem pobierania, dane wyjściowe zawierają długości pobierania, które zostały ukończone przed anulowaniem.</span><span class="sxs-lookup"><span data-stu-id="611a7-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="611a7-163">Kompletne przykłady</span><span class="sxs-lookup"><span data-stu-id="611a7-163">Complete examples</span></span>

<span data-ttu-id="611a7-164">Poniższe sekcje zawierają kod dla każdego z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="611a7-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="611a7-165">Należy zauważyć, że należy <xref:System.Net.Http>dodać odwołanie do .</span><span class="sxs-lookup"><span data-stu-id="611a7-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="611a7-166">Możesz pobrać projekty z [próbki Async: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="611a7-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="611a7-167">Przykład — anulowanie zadania</span><span class="sxs-lookup"><span data-stu-id="611a7-167">Example - Cancel a task</span></span>

<span data-ttu-id="611a7-168">Poniższy kod jest kompletnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.</span><span class="sxs-lookup"><span data-stu-id="611a7-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="611a7-169">Przykład — anulowanie listy zadań</span><span class="sxs-lookup"><span data-stu-id="611a7-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="611a7-170">Poniższy kod jest kompletnym MainWindow.xaml.cs pliku dla przykładu, który anuluje listę zadań.</span><span class="sxs-lookup"><span data-stu-id="611a7-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="611a7-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="611a7-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="611a7-172">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="611a7-172">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="611a7-173">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="611a7-173">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="611a7-174">Przykład asynchronii: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="611a7-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
