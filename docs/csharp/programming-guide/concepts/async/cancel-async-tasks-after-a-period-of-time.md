---
title: Anulowanie zadań asynchronicznych po upływie czasu (C#)
description: Użyj metody CancellationTokenSource. CancelAfter w języku C#, aby zaplanować anulowanie wszystkich skojarzonych zadań nieukończonych w okresie w tym przykładzie.
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: f32af1d893c60ac17648f60fa3aa90adaa0383e8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925295"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="3f1a0-103">Anulowanie zadań asynchronicznych po upływie czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="3f1a0-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="3f1a0-104">Istnieje możliwość anulowania operacji asynchronicznej po upływie okresu czasu przy użyciu <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, jeśli nie chcesz czekać na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-104">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="3f1a0-105">Ta metoda służy do planowania anulowania wszystkich skojarzonych zadań, które nie zostały ukończone w okresie wyznaczonym przez `CancelAfter` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-105">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="3f1a0-106">Ten przykład dodaje do kodu, który został opracowany w wyniku [anulowania zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) , aby pobrać listę witryn sieci Web i wyświetlić długość zawartości każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-106">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="3f1a0-107">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-107">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="3f1a0-108">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="3f1a0-108">Download the example</span></span>

<span data-ttu-id="3f1a0-109">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-109">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="3f1a0-110">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-110">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="3f1a0-111">Na pasku menu wybierz **plik**  >  **Otwórz**  >  **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-111">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="3f1a0-112">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-112">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="3f1a0-113">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterTime** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-113">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="3f1a0-114">Wybierz klawisz **F5** , aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-114">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="3f1a0-115">(Lub naciśnij klawisz **Ctrl** + **Naciśnij klawisz F5** , aby uruchomić projekt bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-115">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="3f1a0-116">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-116">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="3f1a0-117">Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-117">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="3f1a0-118">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="3f1a0-118">Build the example</span></span>

<span data-ttu-id="3f1a0-119">Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) , aby anulować listę zadań.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-119">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="3f1a0-120">W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-120">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="3f1a0-121">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-121">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="3f1a0-122">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-122">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="3f1a0-123">Aby określić maksymalny czas, po jakim zadania są oznaczane jako anulowane, należy dodać wywołanie do `CancelAfter` `startButton_Click` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-123">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="3f1a0-124">Dodanie jest oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-124">The addition is marked with asterisks.</span></span>

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 <span data-ttu-id="3f1a0-125">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-125">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="3f1a0-126">Oto przykład danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-126">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="3f1a0-127">Pełny przykład</span><span class="sxs-lookup"><span data-stu-id="3f1a0-127">Complete example</span></span>

<span data-ttu-id="3f1a0-128">Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.cs na przykład.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-128">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="3f1a0-129">Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="3f1a0-129">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="3f1a0-130">Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="3f1a0-130">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="3f1a0-131">Możesz pobrać projekt z [przykładu asynchronicznego: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="3f1a0-131">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a><span data-ttu-id="3f1a0-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f1a0-132">See also</span></span>

- [<span data-ttu-id="3f1a0-133">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="3f1a0-133">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="3f1a0-134">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="3f1a0-134">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="3f1a0-135">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="3f1a0-135">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="3f1a0-136">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="3f1a0-136">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="3f1a0-137">Próbka asynchroniczna: dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3f1a0-137">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
