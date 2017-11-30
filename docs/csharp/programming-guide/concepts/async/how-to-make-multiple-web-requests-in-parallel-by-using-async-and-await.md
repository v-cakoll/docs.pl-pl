---
title: "Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 11b6fef5356f97c53dc973b13eb5f1e8c31dbe72
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="cb625-102">Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="cb625-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="cb625-103">W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone.</span><span class="sxs-lookup"><span data-stu-id="cb625-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="cb625-104">[Await](../../../../csharp/language-reference/keywords/await.md) operator jest stosowany do zadań w momencie w metodzie, której nie można kontynuować przetwarzania przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="cb625-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="cb625-105">Często zadania jest oczekiwane, natychmiast po utworzeniu, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb625-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="cb625-106">Jednak można oddzielić Tworzenie zadania z oczekiwanie na zadanie, jeśli program ma wykonywać inne zadania, które nie są zależne od ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="cb625-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="cb625-107">Między uruchamianie zadania i oczekujące na on, można uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="cb625-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="cb625-108">Dodatkowe zadania niejawnie równolegle, ale nie dodatkowe wątki są tworzone.</span><span class="sxs-lookup"><span data-stu-id="cb625-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="cb625-109">Następujący program uruchamia trzy pobieranie asynchroniczne sieci web i Oczekiwanie je w kolejności, w którym są nazywane.</span><span class="sxs-lookup"><span data-stu-id="cb625-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="cb625-110">Powiadomienia i po uruchomieniu programu, w której zadania nie zawsze kończy się w kolejności, w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="cb625-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="cb625-111">Decydując się uruchomić, kiedy są tworzone i co najmniej jednego zadania może zakończyć się pomyślnie przed metody osiągnie wyrażenia await.</span><span class="sxs-lookup"><span data-stu-id="cb625-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb625-112">Aby ukończyć ten projekt, musi mieć program Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cb625-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="cb625-113">Na przykład innego uruchamiania wielu zadań jednocześnie, zobacz [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="cb625-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="cb625-114">Można pobrać kodu w tym przykładzie z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=254906).</span><span class="sxs-lookup"><span data-stu-id="cb625-114">You can download the code for this example from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=254906).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="cb625-115">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="cb625-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="cb625-116">Aby skonfigurować aplikacji WPF, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="cb625-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="cb625-117">Szczegółowe instrukcje w tych krokach można znaleźć [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="cb625-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="cb625-118">Tworzenie aplikacji programu WPF, która zawiera pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="cb625-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="cb625-119">Nazwa przycisku `startButton`oraz nazwę pola tekstowego `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="cb625-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="cb625-120">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="cb625-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="cb625-121">W pliku MainWindow.xaml.cs Dodaj `using` dyrektywy dla `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="cb625-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="cb625-122">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="cb625-122">To add the code</span></span>  
  
1.  <span data-ttu-id="cb625-123">W oknie projektowania MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cb625-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="cb625-124">Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cb625-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="cb625-125">Kod wywołuje metodę asynchroniczną `CreateMultipleTasksAsync`, które dyski aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cb625-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="cb625-126">Dodaj następujące metody pomocy technicznej do projektu:</span><span class="sxs-lookup"><span data-stu-id="cb625-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="cb625-127">`ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metodę, aby pobrać zawartość witryny sieci Web w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="cb625-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="cb625-128">Metoda obsługi `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="cb625-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="cb625-129">`DisplayResults`Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cb625-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="cb625-130">Pokazuje to wyświetlenie podczas każdego zadania został pobrany.</span><span class="sxs-lookup"><span data-stu-id="cb625-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="cb625-131">Skopiuj następujące metody i wklej je po `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cb625-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
4.  <span data-ttu-id="cb625-132">Na koniec zdefiniować metody `CreateMultipleTasksAsync`, która wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="cb625-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="cb625-133">Deklaruje metody `HttpClient` obiektu, który chcesz uzyskać dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="cb625-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="cb625-134">Metoda utworzenie i uruchomienie zadania trzy typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="cb625-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="cb625-135">Jak każdego zadania zakończeniu `DisplayResults` Wyświetla adres URL zadania i długość zawartości pobrane.</span><span class="sxs-lookup"><span data-stu-id="cb625-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="cb625-136">Ponieważ zadania są uruchomione asynchronicznie, kolejność wyświetlania wyników może się różnić od kolejności, w której była zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="cb625-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="cb625-137">Metoda oczekujące na zakończenie wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="cb625-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="cb625-138">Każdy `await` operator wstrzymuje wykonywanie `CreateMultipleTasksAsync` dopiero po zakończeniu zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="cb625-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="cb625-139">Operator pobiera również wartość zwrotna z wywołania `ProcessURLAsync` z każdego ukończonego zadania.</span><span class="sxs-lookup"><span data-stu-id="cb625-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="cb625-140">Po zakończeniu zadania i wartości całkowite zostały pobrane, metoda sumuje długości witryn sieci Web i wyświetlane wyniki.</span><span class="sxs-lookup"><span data-stu-id="cb625-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="cb625-141">Następująca metoda skopiuj i wklej go do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cb625-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("http://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text +=  
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
    ```  
  
5.  <span data-ttu-id="cb625-142">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="cb625-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="cb625-143">Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze zakończone w tej samej kolejności i kolejność ich Zakończ nie musi być koniecznie kolejność, w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="cb625-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb625-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb625-144">Example</span></span>  
 <span data-ttu-id="cb625-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="cb625-145">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("http://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cb625-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb625-146">See Also</span></span>  
 [<span data-ttu-id="cb625-147">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="cb625-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="cb625-148">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="cb625-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="cb625-149">Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="cb625-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
