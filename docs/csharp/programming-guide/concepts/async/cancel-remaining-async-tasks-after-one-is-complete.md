---
title: Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 9b968ec902d9653caa410e917af40c8a521e55b4
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859619"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="98d5a-102">Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)</span><span class="sxs-lookup"><span data-stu-id="98d5a-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="98d5a-103">Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda wraz z <xref:System.Threading.CancellationToken>, możesz anulować wszystkie pozostałe zadania po wykonaniu jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="98d5a-104">`WhenAny` Metoda przyjmuje argument, który jest kolekcją zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="98d5a-105">Metoda uruchamia wszystkie zadania i zwrócenie pojedynczego zadania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="98d5a-106">Pojedyncze zadanie jest ukończone po zakończeniu każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98d5a-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="98d5a-107">W tym przykładzie przedstawiono sposób użycia tokenu anulowania w połączeniu z `WhenAny` do przechowywania na pierwszym zadaniu do ukończenia zadań i anulowania pozostałych zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="98d5a-108">Każde zadanie powoduje pobieranie zawartości witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="98d5a-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="98d5a-109">Przykład wyświetla długość zawartości pierwszego pobieranego i anuluje inne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98d5a-110">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="98d5a-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="98d5a-111">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="98d5a-111">Downloading the Example</span></span>  
 <span data-ttu-id="98d5a-112">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="98d5a-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="98d5a-113">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="98d5a-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="98d5a-114">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="98d5a-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="98d5a-115">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="98d5a-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="98d5a-116">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAfterOneTask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="98d5a-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="98d5a-117">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="98d5a-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="98d5a-118">Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="98d5a-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="98d5a-119">Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="98d5a-120">Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="98d5a-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="98d5a-121">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="98d5a-121">Building the Example</span></span>  
 <span data-ttu-id="98d5a-122">W przykładzie w tym temacie dodaje do projektu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) umożliwiający anulowanie listy zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="98d5a-123">W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="98d5a-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="98d5a-124">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="98d5a-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="98d5a-125">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="98d5a-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="98d5a-126">W pliku MainWindow.xaml.cs **CancelAListOfTasks** projektu, uruchom przejścia przez przeniesienie kroków przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="98d5a-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="98d5a-127">W `AccessTheWebAsync`, w tym przykładzie użyto zapytania, <xref:System.Linq.Enumerable.ToArray%2A> metody i `WhenAny` metodę, aby utworzyć i uruchomić szereg zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="98d5a-128">Stosowanie `WhenAny` do tablicy powoduje zwrócenie pojedynczego zadania, gdy jest oczekiwane, daje w wyniku pierwsze zadanie do wykonania w tablicy zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="98d5a-129">Wprowadź następujące zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="98d5a-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="98d5a-130">Gwiazdka oznacza zmiany w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="98d5a-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="98d5a-131">Skomentuj lub usuń pętlę.</span><span class="sxs-lookup"><span data-stu-id="98d5a-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="98d5a-132">Utwórz zapytanie, które, po wykonaniu, daje kolekcję zadań rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="98d5a-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="98d5a-133">Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="98d5a-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="98d5a-134">Wywołaj `ToArray` do wykonywania zapytania i uruchomić zadania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="98d5a-135">Stosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez używania `ToArray`, ale niekoniecznie innych metod.</span><span class="sxs-lookup"><span data-stu-id="98d5a-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="98d5a-136">Najbezpieczniejszym rozwiązaniem jest jawne wymuszenie wykonania zapytania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="98d5a-137">Wywołaj `WhenAny` na kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="98d5a-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="98d5a-138">`WhenAny` Zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="98d5a-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="98d5a-139">Oznacza to, że `WhenAny` zwraca klasę task, która ocenia do pojedynczego `Task(Of Integer)` lub `Task<int>` gdy jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="98d5a-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="98d5a-140">To pojedyncze zadanie jest pierwszym zadaniem w kolekcji, aby zakończyć.</span><span class="sxs-lookup"><span data-stu-id="98d5a-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="98d5a-141">Przydzielono zadanie, które zostanie ukończone jako pierwsze `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="98d5a-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="98d5a-142">Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą, ponieważ jest to typ zwracany `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="98d5a-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="98d5a-143">W tym przykładzie interesuje Cię tylko zadanie, które zakończy się pierwsza.</span><span class="sxs-lookup"><span data-stu-id="98d5a-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="98d5a-144">W związku z tym, użyj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> anulować pozostałe zadania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="98d5a-145">Na koniec await `firstFinishedTask` na pobranie długości pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="98d5a-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="98d5a-146">Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="98d5a-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="98d5a-147">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="98d5a-147">Complete Example</span></span>  
 <span data-ttu-id="98d5a-148">Następujący kod jest pełnym MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="98d5a-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="98d5a-149">Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="98d5a-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="98d5a-150">Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="98d5a-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="98d5a-151">Można ściągnąć projekt z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="98d5a-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
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
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
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
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="98d5a-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98d5a-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="98d5a-153">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="98d5a-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="98d5a-154">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="98d5a-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="98d5a-155">Próbka asynchroniczna: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="98d5a-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
