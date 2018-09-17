---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 2aadfccd8b38922b72dfc21daf27f610adffc922
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45692810"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="300ae-102">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="300ae-102">Cancel an Async Task or a List of Tasks (C#)</span></span>
<span data-ttu-id="300ae-103">Można skonfigurować przycisk, który służy do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na zakończenie jego działania.</span><span class="sxs-lookup"><span data-stu-id="300ae-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="300ae-104">Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość jednej witryny sieci Web lub listę witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="300ae-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="300ae-105">W przykładach wykorzystano interfejs użytkownika, [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) opisuje.</span><span class="sxs-lookup"><span data-stu-id="300ae-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="300ae-106">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="300ae-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a> <span data-ttu-id="300ae-107">Anuluj zadanie</span><span class="sxs-lookup"><span data-stu-id="300ae-107">Cancel a Task</span></span>  
 <span data-ttu-id="300ae-108">Pierwszy przykład kojarzy **anulować** przycisk z pojedynczym zadaniem pobierania.</span><span class="sxs-lookup"><span data-stu-id="300ae-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="300ae-109">Jeśli wybierzesz przycisk podczas pobierania zawartości aplikacji, pobieranie zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="300ae-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="300ae-110">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="300ae-110">Downloading the Example</span></span>  
 <span data-ttu-id="300ae-111">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="300ae-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="300ae-112">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="300ae-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="300ae-113">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="300ae-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="300ae-114">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="300ae-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="300ae-115">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelATask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="300ae-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="300ae-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="300ae-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="300ae-117">Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="300ae-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="300ae-118">Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="300ae-118">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="300ae-119">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="300ae-119">Building the Example</span></span>  
 <span data-ttu-id="300ae-120">Poniższe zmiany powodują dodanie **anulować** przycisku do aplikacji, która pobiera witrynę sieci Web.</span><span class="sxs-lookup"><span data-stu-id="300ae-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="300ae-121">Jeśli nie chcesz pobrać lub kompilować przykładu, można przejrzeć produkt końcowy w sekcji "Kompletne przykłady" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="300ae-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="300ae-122">Gwiazdka oznacza zmiany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="300ae-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="300ae-123">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **StarterCode** jako **projekt startowy** zamiast **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="300ae-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="300ae-124">Następnie należy dodać następujące zmiany do pliku MainWindow.xaml.cs tego projektu.</span><span class="sxs-lookup"><span data-stu-id="300ae-124">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>  
  
1.  <span data-ttu-id="300ae-125">Zadeklaruj `CancellationTokenSource` zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod, które do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="300ae-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="300ae-126">Dodaj następującą obsługę zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="300ae-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="300ae-127">Obsługa zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić `cts` po użytkownik zażąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="300ae-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
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
  
3.  <span data-ttu-id="300ae-128">Utwórz następujące zmiany w zdarzeniu Obsługa **Start** przycisku `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="300ae-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="300ae-129">Utwórz wystąpienie `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="300ae-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   <span data-ttu-id="300ae-130">W wywołaniu `AccessTheWebAsync`, które pobiera zawartość określonej witryny sieci Web, wysyłanie <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwość `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="300ae-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="300ae-131">`Token` Właściwość propaguje komunikat, czy zażądano anulowania.</span><span class="sxs-lookup"><span data-stu-id="300ae-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="300ae-132">Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik anuluje operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="300ae-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="300ae-133">Poniższy kod pokazuje zmiany.</span><span class="sxs-lookup"><span data-stu-id="300ae-133">The following code shows the changes.</span></span>  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
4.  <span data-ttu-id="300ae-134">W `AccessTheWebAsync`, użyj <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> przeciążenia `GetAsync` method in Class metoda <xref:System.Net.Http.HttpClient> typu, aby pobrać zawartość witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="300ae-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="300ae-135">Przekaż `ct`, <xref:System.Threading.CancellationToken> parametru `AccessTheWebAsync`, jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="300ae-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="300ae-136">Token niesie komunikat, jeśli użytkownik wybierze **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="300ae-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="300ae-137">Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="300ae-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  <span data-ttu-id="300ae-138">Jeśli nie anulujesz programu, wygeneruje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="300ae-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="300ae-139">Jeśli wybierzesz **anulować** przycisku, zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="300ae-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="300ae-140">Anuluj listę zadań</span><span class="sxs-lookup"><span data-stu-id="300ae-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="300ae-141">Możesz rozszerzyć poprzedniego przykładu, aby anulować wiele zadań można skojarzyć takie same `CancellationTokenSource` z każdym zadaniem.</span><span class="sxs-lookup"><span data-stu-id="300ae-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="300ae-142">Jeśli wybierzesz **anulować** przycisku, anulujesz wszystkie zadania, które nie są jeszcze kompletne.</span><span class="sxs-lookup"><span data-stu-id="300ae-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="300ae-143">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="300ae-143">Downloading the Example</span></span>  
 <span data-ttu-id="300ae-144">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="300ae-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="300ae-145">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="300ae-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="300ae-146">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="300ae-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="300ae-147">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="300ae-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="300ae-148">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAListOfTasks** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="300ae-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="300ae-149">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="300ae-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="300ae-150">Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="300ae-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="300ae-151">Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="300ae-151">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="300ae-152">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="300ae-152">Building the Example</span></span>  
 <span data-ttu-id="300ae-153">Aby rozszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelATask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="300ae-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="300ae-154">Dodaj następujące zmiany do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="300ae-154">Add the following changes to that project.</span></span> <span data-ttu-id="300ae-155">Gwiazdka oznacza zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="300ae-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="300ae-156">Dodaj metodę, aby utworzyć listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="300ae-156">Add a method to create a list of web addresses.</span></span>  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
    private List<string> SetUpURLList()  
    {  
        List<string> urls = new List<string>   
        {   
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
    ```  
  
2.  <span data-ttu-id="300ae-157">Wywołaj metodę `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="300ae-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  <span data-ttu-id="300ae-158">Dodaj następującą pętlę w `AccessTheWebAsync` Aby przetwarzać każdy adresu sieci web, na liście.</span><span class="sxs-lookup"><span data-stu-id="300ae-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  <span data-ttu-id="300ae-159">Ponieważ `AccessTheWebAsync` Wyświetla długości, metoda nie musi niczego zwracać.</span><span class="sxs-lookup"><span data-stu-id="300ae-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="300ae-160">Usuń instrukcję return, a następnie zmień zwracany typ metody do <xref:System.Threading.Tasks.Task> zamiast <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="300ae-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     <span data-ttu-id="300ae-161">Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="300ae-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  <span data-ttu-id="300ae-162">Jeśli nie anulujesz programu, wygeneruje następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="300ae-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="300ae-163">Jeśli wybierzesz **anulować** przycisku przed zakończeniu pobierania, dane wyjściowe zawierają długości plików o pobieraniu ukończonym przed anulowaniem.</span><span class="sxs-lookup"><span data-stu-id="300ae-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="300ae-164">Kompletne przykłady</span><span class="sxs-lookup"><span data-stu-id="300ae-164">Complete Examples</span></span>  
 <span data-ttu-id="300ae-165">Poniższe sekcje zawierają kod dla każdego z poprzednich przykładów.</span><span class="sxs-lookup"><span data-stu-id="300ae-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="300ae-166">Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="300ae-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="300ae-167">Można ściągnąć projekty z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="300ae-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="300ae-168">Anuluj zadanie-przykład</span><span class="sxs-lookup"><span data-stu-id="300ae-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="300ae-169">Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.</span><span class="sxs-lookup"><span data-stu-id="300ae-169">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
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
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="300ae-170">Anuluj listę zadań-przykład</span><span class="sxs-lookup"><span data-stu-id="300ae-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="300ae-171">Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który Anuluje listę zadań.</span><span class="sxs-lookup"><span data-stu-id="300ae-171">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="300ae-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="300ae-172">See Also</span></span>

- <xref:System.Threading.CancellationTokenSource>  
- <xref:System.Threading.CancellationToken>  
- [<span data-ttu-id="300ae-173">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="300ae-173">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="300ae-174">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="300ae-174">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [<span data-ttu-id="300ae-175">Próbka asynchroniczna: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="300ae-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
