---
title: 'Instrukcje: Wiele żądań sieci Web równolegle za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 3ea41c1fa0fce3a35635e069061f1953c6395406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335423"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="73ca5-102">Instrukcje: Wiele żądań sieci Web równolegle za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="73ca5-102">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>
<span data-ttu-id="73ca5-103">W metodzie asynchronicznej zadania są uruchamiane po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="73ca5-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="73ca5-104">[Await](../../../../csharp/language-reference/keywords/await.md) operator jest stosowany do zadania w tym punkcie metody, których nie można kontynuować przetwarzania przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-104">The [await](../../../../csharp/language-reference/keywords/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="73ca5-105">Często zadanie jest oczekiwane, zaraz po jego utworzeniu, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="73ca5-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="73ca5-106">Jednakże można oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli w programie trzeba wykonać inne prace, które nie są zależne od zakończenia tego zadania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="73ca5-107">Między rozpoczęciem zadania i oczekiwaniem na, możesz uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="73ca5-108">Dodatkowe zadania w sposób niejawny uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone.</span><span class="sxs-lookup"><span data-stu-id="73ca5-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="73ca5-109">Następujący program uruchamia trzy asynchroniczne web pobierania, a następnie oczekuje na ich zakończenie w kolejności, w którym są nazywane.</span><span class="sxs-lookup"><span data-stu-id="73ca5-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="73ca5-110">Zwróć uwagę, po uruchomieniu programu, który zadania nie są zawsze kończone w kolejności, w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="73ca5-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="73ca5-111">Zaczynają działać, gdyż zostały utworzone, gdy jeden lub więcej zadań może zakończyć zanim metoda osiągnie wyrażenie await.</span><span class="sxs-lookup"><span data-stu-id="73ca5-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73ca5-112">Aby wykonać ten projekt, jest posiadanie programu Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="73ca5-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="73ca5-113">Inny przykład, który rozpoczyna się wiele zadań, w tym samym czasie, zobacz [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="73ca5-113">For another example that starts multiple tasks at the same time, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="73ca5-114">Możesz pobrać kod dla tego przykładu z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="73ca5-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="73ca5-115">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="73ca5-115">To set up the project</span></span>  
  
1. <span data-ttu-id="73ca5-116">Aby skonfigurować aplikację programu WPF, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="73ca5-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="73ca5-117">Można znaleźć szczegółowe instrukcje tych kroków w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="73ca5-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="73ca5-118">Tworzenie aplikacji WPF, która zawiera pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="73ca5-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="73ca5-119">Nazwij przycisk `startButton`i pole tekstowego `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="73ca5-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="73ca5-120">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="73ca5-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="73ca5-121">W pliku MainWindow.xaml.cs Dodaj `using` dyrektywy dla `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="73ca5-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="73ca5-122">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="73ca5-122">To add the code</span></span>  
  
1. <span data-ttu-id="73ca5-123">W oknie projektu, MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="73ca5-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="73ca5-124">Skopiuj poniższy kod i wklej go w treść `startButton_Click` w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="73ca5-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="73ca5-125">Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync`, która steruje aplikacją.</span><span class="sxs-lookup"><span data-stu-id="73ca5-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="73ca5-126">Dodaj następujące metody pomocy technicznej do projektu:</span><span class="sxs-lookup"><span data-stu-id="73ca5-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="73ca5-127">`ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="73ca5-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="73ca5-128">Metoda pomocnicza `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="73ca5-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="73ca5-129">`DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="73ca5-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="73ca5-130">To wyświetlane, gdy każde zadanie zakończy pobieranie.</span><span class="sxs-lookup"><span data-stu-id="73ca5-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="73ca5-131">Kopiuj poniższe metody i wklej je za `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="73ca5-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="73ca5-132">Na koniec zdefiniuj metodę `CreateMultipleTasksAsync`, który wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="73ca5-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="73ca5-133">Metoda deklaruje `HttpClient` obiektu, który jest potrzebny na dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="73ca5-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="73ca5-134">Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="73ca5-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="73ca5-135">Gdy poszczególne podzadania zakończą, `DisplayResults` Wyświetla adres URL tego zadania i długość pobranej treści.</span><span class="sxs-lookup"><span data-stu-id="73ca5-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="73ca5-136">Ponieważ zadania odbywają się asynchronicznie, kolejność, w jakiej są wyświetlane wyniki mogą różnić się od kolejności, w którym zostały zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="73ca5-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="73ca5-137">Metoda czeka na zakończenie każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="73ca5-138">Każdy `await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` aż oczekiwane zadanie się zakończy.</span><span class="sxs-lookup"><span data-stu-id="73ca5-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="73ca5-139">Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego ukończonego zadania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="73ca5-140">Kiedy zadania zostały ukończone i pobraniu wartości całkowitych, metoda sumuje długość witryn sieci Web i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="73ca5-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="73ca5-141">Kopiuj następującą metodę i wkleić go do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="73ca5-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="73ca5-142">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="73ca5-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="73ca5-143">Uruchom program kilka razy, aby sprawdzić, czy te trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność ich zakończenia niekoniecznie jest kolejnością w którym są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="73ca5-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73ca5-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="73ca5-144">Example</span></span>  
 <span data-ttu-id="73ca5-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="73ca5-145">The following code contains the full example.</span></span>  
  
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
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
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
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="73ca5-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73ca5-146">See also</span></span>

- [<span data-ttu-id="73ca5-147">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="73ca5-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="73ca5-148">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="73ca5-148">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="73ca5-149">Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="73ca5-149">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
