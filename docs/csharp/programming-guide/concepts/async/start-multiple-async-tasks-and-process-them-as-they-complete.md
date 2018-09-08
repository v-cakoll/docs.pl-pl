---
title: Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a23bdedbd9786fb930f92f5aa4b1025b83a4bcbe
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44140414"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="0fb76-102">Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)</span><span class="sxs-lookup"><span data-stu-id="0fb76-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>
<span data-ttu-id="0fb76-103">Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, można uruchomić wiele zadań w tym samym czasie i przetwarzać je jedno po ich zakończeniu, zamiast przetwarzać je w kolejności, w którym są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="0fb76-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="0fb76-104">W poniższym przykładzie użyto zapytania, aby utworzyć kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="0fb76-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="0fb76-105">Każde zadanie powoduje pobieranie zawartości określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="0fb76-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="0fb76-106">W każdej iteracji while oczekiwane wywołanie do pętli `WhenAny` zwraca zadanie w kolekcji zadań, którego pobieranie najpierw się zakończy.</span><span class="sxs-lookup"><span data-stu-id="0fb76-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="0fb76-107">To zadanie jest usuwane z kolekcji i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="0fb76-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="0fb76-108">Pętla powtarza, dopóki Kolekcja nie zawiera więcej zadań.</span><span class="sxs-lookup"><span data-stu-id="0fb76-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0fb76-109">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="0fb76-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="0fb76-110">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="0fb76-110">Downloading the Example</span></span>  
 <span data-ttu-id="0fb76-111">Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="0fb76-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="0fb76-112">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0fb76-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="0fb76-113">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="0fb76-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="0fb76-114">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="0fb76-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="0fb76-115">W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProcessTasksAsTheyFinish** projektu, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="0fb76-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="0fb76-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="0fb76-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="0fb76-117">Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="0fb76-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="0fb76-118">Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie pojawiają się zawsze w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0fb76-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="0fb76-119">Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="0fb76-119">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="0fb76-120">Budowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="0fb76-120">Building the Example</span></span>  
 <span data-ttu-id="0fb76-121">Ten przykład dodaje do kodu utworzonego w [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna](https://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) i używa tego samego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0fb76-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[Cancel Remaining Async Tasks after One Is Complete](https://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) and uses the same UI.</span></span>  
  
 <span data-ttu-id="0fb76-122">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAfterOneTask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="0fb76-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="0fb76-123">Dodaj zmiany w tym temacie, aby `AccessTheWebAsync` metody, w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="0fb76-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="0fb76-124">Zmiany są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="0fb76-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="0fb76-125">**CancelAfterOneTask** projekt zawiera już zapytanie, którego wykonanie powoduje utworzenie kolekcji zadań.</span><span class="sxs-lookup"><span data-stu-id="0fb76-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="0fb76-126">Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0fb76-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 <span data-ttu-id="0fb76-127">W pliku MainWindow.xaml.cs w projekcie dokonaj następujących zmian do `AccessTheWebAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="0fb76-127">In the MainWindow.xaml.cs file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="0fb76-128">Wykonanie zapytania przez zastosowanie <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="0fb76-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   <span data-ttu-id="0fb76-129">Dodaj chwilę pętli, która wykonuje następujące czynności dla każdego zadania w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0fb76-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="0fb76-130">Czeka aby wywołanie `WhenAny` do zidentyfikowało pierwsze zadanie w kolekcji, aby zakończyć jego pobranie.</span><span class="sxs-lookup"><span data-stu-id="0fb76-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  <span data-ttu-id="0fb76-131">To zadanie usuwa z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="0fb76-131">Removes that task from the collection.</span></span>  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  <span data-ttu-id="0fb76-132">Czeka na `firstFinishedTask`, który jest zwracany przez wywołanie `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="0fb76-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="0fb76-133">`firstFinishedTask` Zmienna jest <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="0fb76-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="0fb76-134">Zadanie zostało już ukończone, ale czeka na pobranie długości pobranej witryny sieci Web, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="0fb76-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 <span data-ttu-id="0fb76-135">Należy uruchomić projekt kilka razy, aby sprawdzić, czy pobrane długości nie pojawiają się zawsze w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="0fb76-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0fb76-136">Możesz użyć `WhenAny` w pętli, jak opisano w przykładzie, aby rozwiązać problemy związane z małą liczbą zadań.</span><span class="sxs-lookup"><span data-stu-id="0fb76-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="0fb76-137">Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="0fb76-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="0fb76-138">Aby uzyskać więcej informacji i przykładów, zobacz [zadania przetwarzania po ich zakończeniu](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="0fb76-138">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="0fb76-139">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="0fb76-139">Complete Example</span></span>  
 <span data-ttu-id="0fb76-140">Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="0fb76-140">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="0fb76-141">Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0fb76-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="0fb76-142">Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="0fb76-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="0fb76-143">Można ściągnąć projekt z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="0fb76-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fb76-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0fb76-144">See Also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>  
- [<span data-ttu-id="0fb76-145">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="0fb76-145">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [<span data-ttu-id="0fb76-146">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="0fb76-146">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="0fb76-147">Próbka asynchroniczna: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="0fb76-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
