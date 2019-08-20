---
title: Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 5237d82506da5e304a8f265feab7d7f3beaa45b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595689"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="7ef2c-102">Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef2c-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="7ef2c-103">Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody razem <xref:System.Threading.CancellationToken>z, można anulować wszystkie pozostałe zadania po zakończeniu jednego zadania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="7ef2c-104">`WhenAny` Metoda przyjmuje argument, który jest kolekcją zadań.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="7ef2c-105">Metoda uruchamia wszystkie zadania i zwraca pojedyncze zadanie.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="7ef2c-106">Pojedyncze zadanie zostanie ukończone, gdy dowolne zadanie w kolekcji zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="7ef2c-107">W tym przykładzie pokazano, jak używać tokenu anulowania w połączeniu z `WhenAny` do pierwszego zadania, aby zakończyć z kolekcji zadań i anulować pozostałe zadania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="7ef2c-108">Każde zadanie pobiera zawartość witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="7ef2c-109">W przykładzie jest wyświetlana długość zawartości pierwszego pobrania, która zostanie zakończona, a pozostałe pliki do pobrania zostaną anulowane.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ef2c-110">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="7ef2c-111">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="7ef2c-111">Downloading the Example</span></span>  
 <span data-ttu-id="7ef2c-112">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="7ef2c-113">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="7ef2c-114">Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="7ef2c-115">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4. <span data-ttu-id="7ef2c-116">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterOneTask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="7ef2c-117">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="7ef2c-118">Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="7ef2c-119">Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="7ef2c-120">Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="7ef2c-121">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="7ef2c-121">Building the Example</span></span>  
 <span data-ttu-id="7ef2c-122">Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) w celu anulowania listy zadań.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="7ef2c-123">W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="7ef2c-124">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="7ef2c-125">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="7ef2c-126">W pliku MainWindow.XAML.cs projektu **CancelAListOfTasks** Rozpocznij przejście przez przeniesienie kroków przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do następującej metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="7ef2c-127">W `AccessTheWebAsync`programie w tym przykładzie używa się zapytania <xref:System.Linq.Enumerable.ToArray%2A> , metody i `WhenAny` metody w celu utworzenia i uruchomienia tablicy zadań.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="7ef2c-128">Aplikacja `WhenAny` do tablicy zwraca pojedyncze zadanie, które w oczekiwany sposób oblicza pierwsze zadanie, aby osiągnąć zakończenie w tablicy zadań.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="7ef2c-129">Wprowadź następujące zmiany w programie `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7ef2c-130">Gwiazdki oznaczają zmiany w pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-130">Asterisks mark the changes in the code file.</span></span>  
  
1. <span data-ttu-id="7ef2c-131">Skomentuj lub Usuń pętlę.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-131">Comment out or delete the loop.</span></span>  
  
2. <span data-ttu-id="7ef2c-132">Utwórz zapytanie, które po wykonaniu tworzy kolekcję zadań ogólnych.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="7ef2c-133">Każde wywołanie `ProcessURLAsync` zwraca element, <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. <span data-ttu-id="7ef2c-134">Wywołaj `ToArray` , aby wykonać zapytanie i uruchomić zadania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="7ef2c-135">Zastosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez użycia `ToArray`, ale inne metody mogą nie być.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="7ef2c-136">Najbezpieczniejszym sposobem jest wymuszenie jawnie wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. <span data-ttu-id="7ef2c-137">Wywołaj `WhenAny` kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="7ef2c-138">`WhenAny``Task(Of Task(Of Integer))` zwraca lub .`Task<Task<int>>`</span><span class="sxs-lookup"><span data-stu-id="7ef2c-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="7ef2c-139">Oznacza to, `WhenAny` że zwraca zadanie, które zostanie obliczone na `Task(Of Integer)` jeden `Task<int>` lub w oczekiwany sposób.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="7ef2c-140">To pojedyncze zadanie to pierwsze zadanie w kolekcji, które ma zostać zakończone.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="7ef2c-141">Zadanie, które zostało zakończone jako pierwszy jest `firstFinishedTask`przypisane do.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="7ef2c-142">Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie jest`TResult` liczbącałkowitą,ponieważjest`ProcessURLAsync`typem zwracanym.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. <span data-ttu-id="7ef2c-143">W tym przykładzie interesuje Cię tylko zadanie, które zakończy się w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="7ef2c-144">W związku z <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> tym Użyj, aby anulować pozostałe zadania.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. <span data-ttu-id="7ef2c-145">Na koniec oczekiwanie `firstFinishedTask` na pobranie pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="7ef2c-146">Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="7ef2c-147">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="7ef2c-147">Complete Example</span></span>  
 <span data-ttu-id="7ef2c-148">Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="7ef2c-149">Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="7ef2c-150">Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="7ef2c-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="7ef2c-151">Możesz pobrać projekt z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="7ef2c-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ef2c-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ef2c-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="7ef2c-153">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef2c-153">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="7ef2c-154">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="7ef2c-154">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="7ef2c-155">Przykład asynchroniczny: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="7ef2c-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
