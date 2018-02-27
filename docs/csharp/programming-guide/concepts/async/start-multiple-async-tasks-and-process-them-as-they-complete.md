---
title: "Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a5339e1d2d592f3ae2a2b5c0e4e96e2bff2df64c
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="b0ea6-102">Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ea6-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="b0ea6-103">Przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, można uruchomić wielu zadań jednocześnie i je jeden po drugim Przetwarzaj one jest ukończona, a nie ich przetworzyć w kolejności, w którym jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="b0ea6-104">W poniższym przykładzie użyto zapytania, aby utworzyć kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="b0ea6-105">Każde zadanie pobiera zawartość z określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="b0ea6-106">W każdej iteracji chwilę pętli, oczekiwano wywołania `WhenAny` zwraca zadanie w kolekcji zadań najpierw zakończy jej pobierania.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="b0ea6-107">To zadanie jest usunięty z kolekcji i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="b0ea6-108">Pętla jest powtarzany do momentu Kolekcja nie zawiera więcej zadań.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0ea6-109">Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="b0ea6-110">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="b0ea6-110">Downloading the Example</span></span>  
 <span data-ttu-id="b0ea6-111">Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="b0ea6-112">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="b0ea6-113">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="b0ea6-114">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="b0ea6-115">W **Eksploratora rozwiązań**, otwórz menu skrótów **ProcessTasksAsTheyFinish** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="b0ea6-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="b0ea6-117">Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="b0ea6-118">Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="b0ea6-119">Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="b0ea6-120">Tworzenie w przykładzie</span><span class="sxs-lookup"><span data-stu-id="b0ea6-120">Building the Example</span></span>  
 <span data-ttu-id="b0ea6-121">W tym przykładzie dodaje kod, który został napisany w [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) i używa tego samego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="b0ea6-122">Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAfterOneTask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="b0ea6-123">Dodaj zmiany w tym temacie umożliwiają `AccessTheWebAsync` metody w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="b0ea6-124">Zmiany są oznaczone gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="b0ea6-125">**CancelAfterOneTask** Projekt już zawiera zapytanie, które po wykonaniu tworzy kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="b0ea6-126">Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="b0ea6-127">W pliku MainWindow.xaml.cs projektu, wprowadź następujące zmiany do `AccessTheWebAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="b0ea6-128">Wykonanie kwerendy, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="b0ea6-129">Dodaj chwilę pętli, które wykonuje następujące czynności dla każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="b0ea6-130">Oczekujące na wywołanie `WhenAny` do identyfikowania pierwszego zadania w kolekcji, aby zakończyć jej pobierania.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="b0ea6-131">To zadanie usuwa z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="b0ea6-132">Oczekujące na `firstFinishedTask`, który jest zwracany przez wywołanie do `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="b0ea6-133">`firstFinishedTask` Zmienna jest <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="b0ea6-134">Zadanie zostało już ukończone, ale należy poczekać na można pobrać długości pobrany witryny sieci Web, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="b0ea6-135">Aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności należy uruchomić kilka razy projektu.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="b0ea6-136">Można użyć `WhenAny` w pętli, zgodnie z opisem w tym przykładzie, aby rozwiązać problemy z działaniem niewielkiej liczby zadań.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="b0ea6-137">Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="b0ea6-138">Aby uzyskać dodatkowe informacje i przykłady, zobacz [przetwarzania zadań w chwili zakończenia](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="b0ea6-138">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="b0ea6-139">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="b0ea6-139">Complete Example</span></span>  
 <span data-ttu-id="b0ea6-140">Następujący kod jest pełny tekst pliku MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="b0ea6-141">Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="b0ea6-142">Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="b0ea6-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="b0ea6-143">Można pobrać projektu z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="b0ea6-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
namespace ProcessTasksAsTheyFinish  
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
            resultsTextBox.Clear();  
  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";  
            }  
  
            cts = null;  
        }  
  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURL(url, client, ct);  
  
            // ***Use ToList to execute the query and start the tasks.   
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
  
            // ***Add a loop to process the tasks one at a time until none remain.  
            while (downloadTasks.Count > 0)  
            {  
                    // Identify the first task that completes.  
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
                    // ***Remove the selected task from the list so that you don't  
                    // process it more than once.  
                    downloadTasks.Remove(firstFinishedTask);  
  
                    // Await the completed task.  
                    int length = await firstFinishedTask;  
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
    }  
}  
  
// Sample Output:  
  
// Length of the download:  226093  
// Length of the download:  412588  
// Length of the download:  175490  
// Length of the download:  204890  
// Length of the download:  158855  
// Length of the download:  145790  
// Length of the download:  44908  
// Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0ea6-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0ea6-144">See Also</span></span>  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [<span data-ttu-id="b0ea6-145">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ea6-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="b0ea6-146">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="b0ea6-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="b0ea6-147">Próbka asynchronicznych: Dostrajanie aplikacji dokładnej</span><span class="sxs-lookup"><span data-stu-id="b0ea6-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
