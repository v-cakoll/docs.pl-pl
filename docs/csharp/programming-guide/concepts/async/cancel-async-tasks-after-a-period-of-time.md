---
title: "Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 717fffb21d38fb356110a3b492b5b9f540a17577
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="3b32a-102">Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32a-102">Cancel Async Tasks after a Period of Time (C#)</span></span>
<span data-ttu-id="3b32a-103">Możesz anulować operację asynchroniczną, po upływie pewnego czasu za pomocą <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metodę, jeśli nie chcesz czekać na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="3b32a-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="3b32a-104">Ta metoda umożliwia zaplanowanie anulowania wszelkie skojarzone zadania, które nie są kompletne w określonym przedziale czasu określony przez `CancelAfter` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3b32a-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="3b32a-105">W tym przykładzie dodaje kod, który został napisany w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) Aby pobrać listę witryn sieci Web i wyświetlić długość zawartości każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="3b32a-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3b32a-106">Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3b32a-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="3b32a-107">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="3b32a-107">Downloading the Example</span></span>  
 <span data-ttu-id="3b32a-108">Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="3b32a-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="3b32a-109">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b32a-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3b32a-110">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="3b32a-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="3b32a-111">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="3b32a-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="3b32a-112">W **Eksploratora rozwiązań**, otwórz menu skrótów **CancelAfterTime** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="3b32a-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="3b32a-113">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="3b32a-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="3b32a-114">Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="3b32a-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="3b32a-115">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą być wyświetlane dane wyjściowe dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web.</span><span class="sxs-lookup"><span data-stu-id="3b32a-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="3b32a-116">Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3b32a-116">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="3b32a-117">Tworzenie w przykładzie</span><span class="sxs-lookup"><span data-stu-id="3b32a-117">Building the Example</span></span>  
 <span data-ttu-id="3b32a-118">W przykładzie w tym temacie jest dodawany do projektu, który został napisany w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) anulować listy zadań.</span><span class="sxs-lookup"><span data-stu-id="3b32a-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="3b32a-119">W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używana jawnie.</span><span class="sxs-lookup"><span data-stu-id="3b32a-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="3b32a-120">Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="3b32a-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="3b32a-121">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="3b32a-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="3b32a-122">Aby określić maksymalny czas, zanim zadania są oznaczone jako anulowane, dodaj wywołanie `CancelAfter` do `startButton_Click`, jak pokazano na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3b32a-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="3b32a-123">Dodanie jest oznaczona atrybutem gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="3b32a-123">The addition is marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="3b32a-124">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą być wyświetlane dane wyjściowe dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web.</span><span class="sxs-lookup"><span data-stu-id="3b32a-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="3b32a-125">Następujące dane wyjściowe to przykład.</span><span class="sxs-lookup"><span data-stu-id="3b32a-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="3b32a-126">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="3b32a-126">Complete Example</span></span>  
 <span data-ttu-id="3b32a-127">Następujący kod jest pełny tekst pliku MainWindow.xaml.cs dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="3b32a-127">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="3b32a-128">Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3b32a-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="3b32a-129">Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="3b32a-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="3b32a-130">Można pobrać projektu z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="3b32a-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="3b32a-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b32a-131">See Also</span></span>  
 [<span data-ttu-id="3b32a-132">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32a-132">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="3b32a-133">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32a-133">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="3b32a-134">Anulowanie zadania asynchronicznego lub listy zadań (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32a-134">Cancel an Async Task or a List of Tasks (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [<span data-ttu-id="3b32a-135">Dostrajanie aplikacji Async (C#)</span><span class="sxs-lookup"><span data-stu-id="3b32a-135">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="3b32a-136">Próbka asynchronicznych: Dostrajanie aplikacji dokładnej</span><span class="sxs-lookup"><span data-stu-id="3b32a-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
