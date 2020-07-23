---
title: Przetwarzaj zadania asynchroniczne po ich zakończeniu
description: Ten przykład pokazuje, jak używać Task. WhenAny w języku C# do uruchamiania wielu zadań i przetwarzać wyniki po zakończeniu, zamiast przetwarzać je w kolejności, w jakiej zostały uruchomione.
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a7cfa0bdf783fe9bb735241ca398fde7895f1493
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925153"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="67997-103">Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ich kończenia (C#)</span><span class="sxs-lookup"><span data-stu-id="67997-103">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="67997-104">Korzystając z programu <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , można uruchomić wiele zadań w tym samym czasie i przetworzyć je w taki sposób, aby były wykonywane, a nie przetwarzane w kolejności, w której są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="67997-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="67997-105">Poniższy przykład używa zapytania, aby utworzyć kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="67997-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="67997-106">Każde zadanie pobiera zawartość określonej witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="67997-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="67997-107">W każdej iteracji pętli while oczekiwane wywołanie `WhenAny` zwraca zadanie w kolekcji zadań, które kończą najpierw pobieranie.</span><span class="sxs-lookup"><span data-stu-id="67997-107">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="67997-108">To zadanie jest usuwane z kolekcji i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="67997-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="67997-109">Pętla powtarza się, dopóki kolekcja nie będzie zawierać żadnych zadań.</span><span class="sxs-lookup"><span data-stu-id="67997-109">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="67997-110">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio (2012 lub nowszy) oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="67997-110">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="67997-111">Pobierz przykładowe rozwiązanie</span><span class="sxs-lookup"><span data-stu-id="67997-111">Download an example solution</span></span>

<span data-ttu-id="67997-112">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="67997-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="67997-113">Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik *MainWindow.XAML.cs* na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="67997-113">If you don't want to download the project, you can review the *MainWindow.xaml.cs* file at the end of this topic instead.</span></span>

1. <span data-ttu-id="67997-114">Wyodrębnij pobrane pliki z pliku *zip* , a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67997-114">Extract the files that you downloaded from the *.zip* file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="67997-115">Na pasku menu wybierz **plik**  >  **Otwórz**  >  **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="67997-115">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="67997-116">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się pobrany przykładowy kod, a następnie otwórz plik rozwiązania (*. sln*) dla *AsyncFineTuningCS* / *AsyncFineTuningVB*.</span><span class="sxs-lookup"><span data-stu-id="67997-116">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (*.sln*) file for *AsyncFineTuningCS*/*AsyncFineTuningVB*.</span></span>

4. <span data-ttu-id="67997-117">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProcessTasksAsTheyFinish** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="67997-117">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="67997-118">Wybierz klawisz <kbd>F5</kbd> , aby uruchomić program z debugowaniem lub naciśnij klawisze <kbd>Ctrl</kbd> + <kbd>F5</kbd> , aby uruchomić program bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="67997-118">Choose the <kbd>F5</kbd> key to run the program with debugging or, press <kbd>Ctrl</kbd>+<kbd>F5</kbd> keys to run the program without debugging it.</span></span>

6. <span data-ttu-id="67997-119">Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="67997-119">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="67997-120">Samodzielne tworzenie programu</span><span class="sxs-lookup"><span data-stu-id="67997-120">Create the program yourself</span></span>

<span data-ttu-id="67997-121">Ten przykład dodaje do kodu, który został opracowany w polu [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)i używa tego samego interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="67997-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="67997-122">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami podanymi w sekcji [pobieranie przykładu](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) , ale ustaw **CancelAfterOneTask** jako projekt startowy.</span><span class="sxs-lookup"><span data-stu-id="67997-122">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="67997-123">Dodaj zmiany w tym temacie do `AccessTheWebAsync` metody w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="67997-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="67997-124">Zmiany są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="67997-124">The changes are marked with asterisks.</span></span>

<span data-ttu-id="67997-125">Projekt **CancelAfterOneTask** zawiera już zapytanie, które po wykonaniu tworzy kolekcję zadań.</span><span class="sxs-lookup"><span data-stu-id="67997-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="67997-126">Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca a <xref:System.Threading.Tasks.Task%601> , gdzie `TResult` jest liczbą całkowitą:</span><span class="sxs-lookup"><span data-stu-id="67997-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="67997-127">W pliku *MainWindow.XAML.cs* projektu wprowadź następujące zmiany w `AccessTheWebAsync` metodzie:</span><span class="sxs-lookup"><span data-stu-id="67997-127">In the *MainWindow.xaml.cs* file of the project, make the following changes to the `AccessTheWebAsync` method:</span></span>

- <span data-ttu-id="67997-128">Wykonaj zapytanie, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A> .</span><span class="sxs-lookup"><span data-stu-id="67997-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- <span data-ttu-id="67997-129">Dodaj `while` pętlę, która wykonuje następujące kroki dla każdego zadania w kolekcji:</span><span class="sxs-lookup"><span data-stu-id="67997-129">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1. <span data-ttu-id="67997-130">Oczekuje na wywołanie do `WhenAny` zidentyfikowania pierwszego zadania w kolekcji, aby zakończyć jego pobieranie.</span><span class="sxs-lookup"><span data-stu-id="67997-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. <span data-ttu-id="67997-131">Usuwa to zadanie z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="67997-131">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. <span data-ttu-id="67997-132">Czeka `firstFinishedTask` , który jest zwracany przez wywołanie metody `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="67997-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="67997-133">`firstFinishedTask`Zmienna to <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="67997-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="67997-134">Zadanie zostało już ukończone, ale czeka na pobranie długości pobranej witryny sieci Web, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="67997-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="67997-135">Jeśli zadanie jest błędne, `await` program zgłosi pierwszy wyjątek podrzędny zapisany w `AggregateException` , w przeciwieństwie do odczytu właściwości, `Result` która spowodowałaby wygenerowanie `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="67997-135">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the `Result` property which would throw the `AggregateException`.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="67997-136">Uruchom program kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.</span><span class="sxs-lookup"><span data-stu-id="67997-136">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="67997-137">Można użyć `WhenAny` w pętli, jak opisano w przykładzie, w celu rozwiązania problemów obejmujących niewielką liczbę zadań.</span><span class="sxs-lookup"><span data-stu-id="67997-137">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="67997-138">Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań do przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="67997-138">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="67997-139">Aby uzyskać więcej informacji i przykładów, zobacz [Przetwarzanie zadań po ich zakończeniu](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="67997-139">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="67997-140">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="67997-140">Complete example</span></span>

<span data-ttu-id="67997-141">Poniższy kod jest pełnym tekstem pliku *MainWindow.XAML.cs* na przykład.</span><span class="sxs-lookup"><span data-stu-id="67997-141">The following code is the complete text of the *MainWindow.xaml.cs* file for the example.</span></span> <span data-ttu-id="67997-142">Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="67997-142">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="67997-143">Należy również pamiętać, że należy dodać odwołanie do <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="67997-143">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="67997-144">Możesz pobrać projekt z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="67997-144">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a><span data-ttu-id="67997-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="67997-145">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="67997-146">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="67997-146">Fine-Tuning Your Async Application (C#)</span></span>](fine-tuning-your-async-application.md)
- [<span data-ttu-id="67997-147">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="67997-147">Asynchronous Programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="67997-148">Próbka asynchroniczna: dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="67997-148">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
