---
title: Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204334"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="890d7-102">Anulowanie zadań asynchronicznych po pewnym czasie (C#)</span><span class="sxs-lookup"><span data-stu-id="890d7-102">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="890d7-103">Operację asynchroniczną można anulować po pewnym <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> czasie, używając metody, jeśli nie chcesz czekać na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="890d7-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="890d7-104">Ta metoda planuje anulowanie wszelkich skojarzonych zadań, które nie zostały ukończone `CancelAfter` w okresie określonym przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="890d7-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="890d7-105">W tym przykładzie dodaje do kodu, który został opracowany w [Anuluj zadanie asynchroniczne lub lista zadań (C#),](./cancel-an-async-task-or-a-list-of-tasks.md) aby pobrać listę witryn sieci Web i wyświetlić długość zawartości każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="890d7-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

> [!NOTE]
> <span data-ttu-id="890d7-106">Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="890d7-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-the-example"></a><span data-ttu-id="890d7-107">Pobierz przykład</span><span class="sxs-lookup"><span data-stu-id="890d7-107">Download the example</span></span>

<span data-ttu-id="890d7-108">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="890d7-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

1. <span data-ttu-id="890d7-109">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="890d7-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

2. <span data-ttu-id="890d7-110">Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .</span><span class="sxs-lookup"><span data-stu-id="890d7-110">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="890d7-111">W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="890d7-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4. <span data-ttu-id="890d7-112">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelAfterTime,** a następnie wybierz pozycję **Ustaw jako projekt StartUp**.</span><span class="sxs-lookup"><span data-stu-id="890d7-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>

5. <span data-ttu-id="890d7-113">Wybierz klawisz **F5,** aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="890d7-113">Choose the **F5** key to run the project.</span></span> <span data-ttu-id="890d7-114">(Lub naciśnij **klawisz Ctrl**+**F5,** aby uruchomić projekt bez debugowania).</span><span class="sxs-lookup"><span data-stu-id="890d7-114">(Or, press **Ctrl**+**F5** to run the project without debugging it).</span></span>

6. <span data-ttu-id="890d7-115">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą wyświetlać dane wyjściowe dla wszystkich witryn sieci Web, żadnych witryn sieci Web lub niektórych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="890d7-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>

<span data-ttu-id="890d7-116">Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="890d7-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>

## <a name="build-the-example"></a><span data-ttu-id="890d7-117">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="890d7-117">Build the example</span></span>

<span data-ttu-id="890d7-118">Przykład w tym temacie dodaje do projektu, który został opracowany w [Anuluj zadanie asynchroniczne lub lista zadań (C#),](./cancel-an-async-task-or-a-list-of-tasks.md) aby anulować listę zadań.</span><span class="sxs-lookup"><span data-stu-id="890d7-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="890d7-119">W przykładzie użyto tego samego interfejsu, chociaż przycisk **Anuluj** nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="890d7-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>

<span data-ttu-id="890d7-120">Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **cancelAlistoftasks** jako **projekt StartUp**.</span><span class="sxs-lookup"><span data-stu-id="890d7-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="890d7-121">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="890d7-121">Add the changes in this topic to that project.</span></span>

<span data-ttu-id="890d7-122">Aby określić maksymalny czas, zanim zadania zostaną oznaczone jako `CancelAfter` `startButton_Click`anulowane, dodaj wywołanie do , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="890d7-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="890d7-123">Dodatek jest oznaczony gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="890d7-123">The addition is marked with asterisks.</span></span>

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

 <span data-ttu-id="890d7-124">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą wyświetlać dane wyjściowe dla wszystkich witryn sieci Web, żadnych witryn sieci Web lub niektórych witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="890d7-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="890d7-125">Następujące dane wyjściowe są próbką.</span><span class="sxs-lookup"><span data-stu-id="890d7-125">The following output is a sample.</span></span>

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a><span data-ttu-id="890d7-126">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="890d7-126">Complete example</span></span>

<span data-ttu-id="890d7-127">Poniższy kod jest kompletnym tekstem MainWindow.xaml.cs pliku dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="890d7-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="890d7-128">Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="890d7-128">Asterisks mark the elements that were added for this example.</span></span>

<span data-ttu-id="890d7-129">Należy zauważyć, że należy <xref:System.Net.Http>dodać odwołanie do .</span><span class="sxs-lookup"><span data-stu-id="890d7-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="890d7-130">Możesz pobrać projekt z [próbki Async: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="890d7-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="890d7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="890d7-131">See also</span></span>

- [<span data-ttu-id="890d7-132">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="890d7-132">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="890d7-133">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)</span><span class="sxs-lookup"><span data-stu-id="890d7-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="890d7-134">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="890d7-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](./cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="890d7-135">Dostrajanie aplikacji asynchronicznej (C#)</span><span class="sxs-lookup"><span data-stu-id="890d7-135">Fine-Tuning Your Async Application (C#)</span></span>](./fine-tuning-your-async-application.md)
- [<span data-ttu-id="890d7-136">Przykład asynchronii: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="890d7-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
