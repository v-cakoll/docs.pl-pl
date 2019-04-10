---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 01557bf80f40d4197d29ab05cfb4838f5d993a82
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295747"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="b3adb-102">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="b3adb-102">Cancel an async task or a list of tasks (C#)</span></span>

<span data-ttu-id="b3adb-103">Można skonfigurować przycisk, który służy do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na zakończenie jego działania.</span><span class="sxs-lookup"><span data-stu-id="b3adb-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="b3adb-104">Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość jednej witryny sieci Web lub listę witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b3adb-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>

<span data-ttu-id="b3adb-105">W przykładach wykorzystano interfejs użytkownika, [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) opisuje.</span><span class="sxs-lookup"><span data-stu-id="b3adb-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>

> [!NOTE]
> <span data-ttu-id="b3adb-106">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b3adb-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="cancel-a-task"></a><span data-ttu-id="b3adb-107">Anuluj zadanie</span><span class="sxs-lookup"><span data-stu-id="b3adb-107">Cancel a task</span></span>

<span data-ttu-id="b3adb-108">Pierwszy przykład kojarzy **anulować** przycisk z pojedynczym zadaniem pobierania.</span><span class="sxs-lookup"><span data-stu-id="b3adb-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="b3adb-109">Jeśli wybierzesz przycisk podczas pobierania zawartości aplikacji, pobieranie zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="b3adb-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="b3adb-110">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="b3adb-110">Download the example</span></span>

<span data-ttu-id="b3adb-111">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="b3adb-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="b3adb-112">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3adb-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="b3adb-113">Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b3adb-113">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="b3adb-114">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="b3adb-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="b3adb-115">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelATask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b3adb-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="b3adb-116">Wybierz **F5** klawisz, aby uruchomić projekt (lub naciśnij **Ctrl**+**F5** uruchomić projekt bez debugowania go).</span><span class="sxs-lookup"><span data-stu-id="b3adb-116">Choose the **F5** key to run the project (or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

> [!TIP]
> <span data-ttu-id="b3adb-117">Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3adb-117">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="b3adb-118">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="b3adb-118">Build the example</span></span>
 <span data-ttu-id="b3adb-119">Poniższe zmiany powodują dodanie **anulować** przycisku do aplikacji, która pobiera witrynę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b3adb-119">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="b3adb-120">Jeśli nie chcesz pobrać lub kompilować przykładu, można przejrzeć produkt końcowy w sekcji "Kompletne przykłady" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3adb-120">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="b3adb-121">Gwiazdka oznacza zmiany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b3adb-121">Asterisks mark the changes in the code.</span></span>

 <span data-ttu-id="b3adb-122">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **StarterCode** jako **projekt startowy** zamiast **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="b3adb-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>

 <span data-ttu-id="b3adb-123">Następnie należy dodać następujące zmiany do pliku MainWindow.xaml.cs tego projektu.</span><span class="sxs-lookup"><span data-stu-id="b3adb-123">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>

1. <span data-ttu-id="b3adb-124">Zadeklaruj `CancellationTokenSource` zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod, które do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="b3adb-124">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="b3adb-125">Dodaj następującą obsługę zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b3adb-125">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="b3adb-126">Obsługa zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić `cts` po użytkownik zażąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="b3adb-126">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>

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

3. <span data-ttu-id="b3adb-127">Utwórz następujące zmiany w zdarzeniu Obsługa **Start** przycisku `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="b3adb-127">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>

    -   <span data-ttu-id="b3adb-128">Utwórz wystąpienie `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="b3adb-128">Instantiate the `CancellationTokenSource`, `cts`.</span></span>

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    -   <span data-ttu-id="b3adb-129">W wywołaniu `AccessTheWebAsync`, które pobiera zawartość określonej witryny sieci Web, wysyłanie <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwość `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="b3adb-129">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="b3adb-130">`Token` Właściwość propaguje komunikat, czy zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="b3adb-130">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="b3adb-131">Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik anuluje operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="b3adb-131">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="b3adb-132">Poniższy kod pokazuje zmiany.</span><span class="sxs-lookup"><span data-stu-id="b3adb-132">The following code shows the changes.</span></span>

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

4. <span data-ttu-id="b3adb-133">W `AccessTheWebAsync`, użyj <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> przeciążenia `GetAsync` method in Class metoda <xref:System.Net.Http.HttpClient> typu, aby pobrać zawartość witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b3adb-133">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="b3adb-134">Przekaż `ct`, <xref:System.Threading.CancellationToken> parametru `AccessTheWebAsync`, jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="b3adb-134">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="b3adb-135">Token niesie komunikat, jeśli użytkownik wybierze **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="b3adb-135">The token carries the message if the user chooses the **Cancel** button.</span></span>

     <span data-ttu-id="b3adb-136">Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="b3adb-136">The following code shows the changes in `AccessTheWebAsync`.</span></span>

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

5. <span data-ttu-id="b3adb-137">Jeśli nie anulujesz programu, wygeneruje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="b3adb-137">If you don’t cancel the program, it produces the following output.</span></span>

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     <span data-ttu-id="b3adb-138">Jeśli wybierzesz **anulować** przycisku, zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b3adb-138">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a><span data-ttu-id="b3adb-139">Anuluj listę zadań</span><span class="sxs-lookup"><span data-stu-id="b3adb-139">Cancel a list of tasks</span></span>

<span data-ttu-id="b3adb-140">Możesz rozszerzyć poprzedniego przykładu, aby anulować wiele zadań można skojarzyć takie same `CancellationTokenSource` z każdym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="b3adb-140">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="b3adb-141">Jeśli wybierzesz **anulować** przycisku, anulujesz wszystkie zadania, które nie są jeszcze kompletne.</span><span class="sxs-lookup"><span data-stu-id="b3adb-141">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>

### <a name="download-the-example"></a><span data-ttu-id="b3adb-142">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="b3adb-142">Download the example</span></span>

<span data-ttu-id="b3adb-143">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="b3adb-143">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="b3adb-144">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3adb-144">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="b3adb-145">Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b3adb-145">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="b3adb-146">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="b3adb-146">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="b3adb-147">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAListOfTasks** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b3adb-147">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="b3adb-148">Wybierz **F5** klawisz, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="b3adb-148">Choose the **F5** key to run the project.</span></span>

     <span data-ttu-id="b3adb-149">Wybierz **Ctrl**+**F5** kluczy, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="b3adb-149">Choose the **Ctrl**+**F5** keys to run the project without debugging it.</span></span>

<span data-ttu-id="b3adb-150">Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b3adb-150">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>

### <a name="build-the-example"></a><span data-ttu-id="b3adb-151">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="b3adb-151">Build the example</span></span>

<span data-ttu-id="b3adb-152">Aby rozszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelATask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b3adb-152">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="b3adb-153">Dodaj następujące zmiany do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="b3adb-153">Add the following changes to that project.</span></span> <span data-ttu-id="b3adb-154">Gwiazdka oznacza zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="b3adb-154">Asterisks mark the changes in the program.</span></span>

1. <span data-ttu-id="b3adb-155">Dodaj metodę, aby utworzyć listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="b3adb-155">Add a method to create a list of web addresses.</span></span>

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

2. <span data-ttu-id="b3adb-156">Wywołaj metodę `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="b3adb-156">Call the method in `AccessTheWebAsync`.</span></span>

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. <span data-ttu-id="b3adb-157">Dodaj następującą pętlę w `AccessTheWebAsync` Aby przetwarzać każdy adresu sieci web, na liście.</span><span class="sxs-lookup"><span data-stu-id="b3adb-157">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>

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

4. <span data-ttu-id="b3adb-158">Ponieważ `AccessTheWebAsync` Wyświetla długości, metoda nie musi niczego zwracać.</span><span class="sxs-lookup"><span data-stu-id="b3adb-158">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="b3adb-159">Usuń instrukcję return, a następnie zmień zwracany typ metody do <xref:System.Threading.Tasks.Task> zamiast <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="b3adb-159">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     <span data-ttu-id="b3adb-160">Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b3adb-160">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. <span data-ttu-id="b3adb-161">Jeśli nie anulujesz programu, wygeneruje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="b3adb-161">If you don’t cancel the program, it produces the following output.</span></span>

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

     <span data-ttu-id="b3adb-162">Jeśli wybierzesz **anulować** przycisku przed zakończeniu pobierania, dane wyjściowe zawierają długości plików o pobieraniu ukończonym przed anulowaniem.</span><span class="sxs-lookup"><span data-stu-id="b3adb-162">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a><span data-ttu-id="b3adb-163">Kompletne przykłady</span><span class="sxs-lookup"><span data-stu-id="b3adb-163">Complete examples</span></span>

<span data-ttu-id="b3adb-164">Poniższe sekcje zawierają kod dla każdego z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="b3adb-164">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="b3adb-165">Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="b3adb-165">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="b3adb-166">Można ściągnąć projekty z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="b3adb-166">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

### <a name="example---cancel-a-task"></a><span data-ttu-id="b3adb-167">Przykład — Anuluj zadanie</span><span class="sxs-lookup"><span data-stu-id="b3adb-167">Example - Cancel a task</span></span>

<span data-ttu-id="b3adb-168">Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.</span><span class="sxs-lookup"><span data-stu-id="b3adb-168">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>

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

### <a name="example---cancel-a-list-of-tasks"></a><span data-ttu-id="b3adb-169">Przykład — Anuluj listę zadań</span><span class="sxs-lookup"><span data-stu-id="b3adb-169">Example - Cancel a list of tasks</span></span>

<span data-ttu-id="b3adb-170">Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który Anuluje listę zadań.</span><span class="sxs-lookup"><span data-stu-id="b3adb-170">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b3adb-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3adb-171">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="b3adb-172">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="b3adb-172">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="b3adb-173">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="b3adb-173">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="b3adb-174">Próbka asynchroniczna: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="b3adb-174">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
