---
title: Jak wykonać równolegle wiele żądań sieci Web za pomocą Async i Await (C#)
description: Dowiedz się, jak oddzielić Tworzenie zadania przy użyciu operatora await w języku C#, zamiast stosować go podczas tworzenia zadania.
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 899dfd9165d199a67a5178bb351081ee544b231f
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925166"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="a6c85-103">Jak wykonać równolegle wiele żądań sieci Web za pomocą Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="a6c85-103">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="a6c85-104">W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone.</span><span class="sxs-lookup"><span data-stu-id="a6c85-104">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="a6c85-105">Operator [await](../../../language-reference/operators/await.md) jest stosowany do zadania w punkcie metody, w którym przetwarzanie nie może być kontynuowane do momentu zakończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-105">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="a6c85-106">Często zadanie jest oczekiwane zaraz po jego utworzeniu, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a6c85-106">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="a6c85-107">Można jednak oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli program ma inne zadania do wykonania, które nie zależą od ukończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="a6c85-108">Między rozpoczęciem zadania i oczekiwaniem na niego można uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="a6c85-109">Dodatkowe zadania niejawnie uruchamiają się równolegle, ale nie są tworzone żadne dodatkowe wątki.</span><span class="sxs-lookup"><span data-stu-id="a6c85-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="a6c85-110">Poniższy program uruchamia trzy asynchroniczne pobieranie w sieci Web, a następnie czeka na ich kolejność, w jakiej są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a6c85-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="a6c85-111">Zwróć uwagę, że po uruchomieniu programu zadania nie zawsze kończą się w kolejności, w której zostały utworzone i oczekujące.</span><span class="sxs-lookup"><span data-stu-id="a6c85-111">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="a6c85-112">Zaczynają one działać, gdy są tworzone, i co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie wyrażenie await.</span><span class="sxs-lookup"><span data-stu-id="a6c85-112">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6c85-113">Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="a6c85-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="a6c85-114">Aby uzyskać inny przykład, który uruchamia wiele zadań w tym samym czasie, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a6c85-114">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="a6c85-115">Kod dla tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="a6c85-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="a6c85-116">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="a6c85-116">To set up the project</span></span>  
  
1. <span data-ttu-id="a6c85-117">Aby skonfigurować aplikację WPF, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="a6c85-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="a6c85-118">Szczegółowe instrukcje dotyczące tych kroków można znaleźć w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="a6c85-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="a6c85-119">Utwórz aplikację WPF, która zawiera pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="a6c85-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="a6c85-120">Nadaj nazwę przyciskowi `startButton` i nazwij pole tekstowe `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="a6c85-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="a6c85-121">Dodaj odwołanie do <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="a6c85-121">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="a6c85-122">W pliku MainWindow.xaml.cs Dodaj `using` dyrektywę dla `System.Net.Http` .</span><span class="sxs-lookup"><span data-stu-id="a6c85-122">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="a6c85-123">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="a6c85-123">To add the code</span></span>  
  
1. <span data-ttu-id="a6c85-124">W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="a6c85-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="a6c85-125">Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="a6c85-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="a6c85-126">Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync` która dyskuje aplikację.</span><span class="sxs-lookup"><span data-stu-id="a6c85-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="a6c85-127">Dodaj do projektu następujące metody pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="a6c85-127">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="a6c85-128">`ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web jako tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="a6c85-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="a6c85-129">Metoda pomocy technicznej, a `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="a6c85-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="a6c85-130">`DisplayResults`Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a6c85-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="a6c85-131">Ten ekran jest wyświetlany po zakończeniu pobierania każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-131">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="a6c85-132">Skopiuj następujące metody i wklej je po `startButton_Click` procedurze obsługi zdarzeń w MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="a6c85-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="a6c85-133">Na koniec Zdefiniuj metodę `CreateMultipleTasksAsync` , która wykonuje następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="a6c85-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="a6c85-134">Metoda deklaruje `HttpClient` obiekt, do którego należy uzyskać dostęp za pomocą <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody `ProcessURLAsync` .</span><span class="sxs-lookup"><span data-stu-id="a6c85-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="a6c85-135">Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601> , gdzie `TResult` jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="a6c85-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="a6c85-136">Po zakończeniu każdego zadania program `DisplayResults` wyświetla adres URL zadania i długość pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a6c85-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="a6c85-137">Ponieważ zadania są wykonywane asynchronicznie, kolejność, w której wyniki są wyświetlane, może różnić się od kolejności, w której zostały zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="a6c85-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="a6c85-138">Metoda oczekuje na zakończenie każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="a6c85-139">Każdy `await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` do momentu zakończenia oczekującego zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-139">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="a6c85-140">Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego wykonanego zadania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="a6c85-141">Po zakończeniu zadań i pobraniu wartości całkowitych Metoda sumuje długości witryn sieci Web i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="a6c85-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="a6c85-142">Skopiuj poniższą metodę i wklej ją do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a6c85-142">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="a6c85-143">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="a6c85-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="a6c85-144">Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność, w jakiej się kończą, nie musi być kolejnością, w której są one tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="a6c85-144">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6c85-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6c85-145">Example</span></span>  
 <span data-ttu-id="a6c85-146">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="a6c85-146">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6c85-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6c85-147">See also</span></span>

- [<span data-ttu-id="a6c85-148">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="a6c85-148">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="a6c85-149">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="a6c85-149">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="a6c85-150">Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="a6c85-150">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
