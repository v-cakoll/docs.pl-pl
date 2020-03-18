---
title: Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 9f7420113d4af83d7d057b772af307bd8d4bcc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169952"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="030ca-102">Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)</span><span class="sxs-lookup"><span data-stu-id="030ca-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="030ca-103">W metodzie asynchronicznej zadania są uruchamiane po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="030ca-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="030ca-104">Await [await](../../../language-reference/operators/await.md) operator jest stosowany do zadania w punkcie w metodzie, gdzie przetwarzanie nie można kontynuować, dopóki zadanie nie zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="030ca-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="030ca-105">Często zadanie jest oczekiwane, jak tylko zostanie utworzony, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="030ca-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="030ca-106">Można jednak oddzielić tworzenie zadania od oczekiwania na zadanie, jeśli program ma inną pracę do wykonania, która nie zależy od zakończenia zadania.</span><span class="sxs-lookup"><span data-stu-id="030ca-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="030ca-107">Między rozpoczęciem zadania a oczekiwaniem na nie można uruchomić inne zadania.</span><span class="sxs-lookup"><span data-stu-id="030ca-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="030ca-108">Dodatkowe zadania niejawnie uruchamiane równolegle, ale nie są tworzone żadne dodatkowe wątki.</span><span class="sxs-lookup"><span data-stu-id="030ca-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="030ca-109">Poniższy program uruchamia trzy asynchroniczne pliki do pobrania w sieci Web, a następnie czeka na nich w kolejności, w jakiej są nazywane.</span><span class="sxs-lookup"><span data-stu-id="030ca-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="030ca-110">Należy zauważyć, po uruchomieniu programu, że zadania nie zawsze zakończyć w kolejności, w jakiej są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="030ca-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="030ca-111">Zaczynają działać, gdy są tworzone, a co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie await wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="030ca-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="030ca-112">Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz program .NET Framework 4.5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="030ca-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="030ca-113">W innym przykładzie, który uruchamia wiele zadań w tym samym czasie, zobacz [Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="030ca-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="030ca-114">Kod tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="030ca-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="030ca-115">Aby skonfigurować projekt</span><span class="sxs-lookup"><span data-stu-id="030ca-115">To set up the project</span></span>  
  
1. <span data-ttu-id="030ca-116">Aby skonfigurować aplikację WPF, wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="030ca-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="030ca-117">Szczegółowe instrukcje dla tych kroków można znaleźć w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="030ca-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="030ca-118">Utwórz aplikację WPF zawierającą pole tekstowe i przycisk.</span><span class="sxs-lookup"><span data-stu-id="030ca-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="030ca-119">Nazwij `startButton`przycisk i nadawanie pola tekstowemu nazwy `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="030ca-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="030ca-120">Dodaj odwołanie <xref:System.Net.Http>do pliku .</span><span class="sxs-lookup"><span data-stu-id="030ca-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="030ca-121">W pliku MainWindow.xaml.cs dodaj `using` dyrektywę dla . `System.Net.Http`</span><span class="sxs-lookup"><span data-stu-id="030ca-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="030ca-122">Aby dodać kod</span><span class="sxs-lookup"><span data-stu-id="030ca-122">To add the code</span></span>  
  
1. <span data-ttu-id="030ca-123">W oknie projektu MainWindow.xaml kliknij dwukrotnie przycisk, `startButton_Click` aby utworzyć program obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="030ca-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="030ca-124">Skopiuj następujący kod i wklej go do treści `startButton_Click` w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="030ca-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="030ca-125">Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync`która napędza aplikację.</span><span class="sxs-lookup"><span data-stu-id="030ca-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="030ca-126">Dodaj następujące metody obsługi do projektu:</span><span class="sxs-lookup"><span data-stu-id="030ca-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="030ca-127">`ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody pobierania zawartości witryny jako tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="030ca-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="030ca-128">Metoda obsługi, `ProcessURLAsync` a następnie wyświetla i zwraca długość tablicy.</span><span class="sxs-lookup"><span data-stu-id="030ca-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="030ca-129">`DisplayResults`wyświetla liczbę bajtów w tablicy bajtów dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="030ca-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="030ca-130">Ten ekran pokazuje, kiedy każde zadanie zostało zakończone pobieranie.</span><span class="sxs-lookup"><span data-stu-id="030ca-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="030ca-131">Skopiuj następujące metody i `startButton_Click` wklej je po programie obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="030ca-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
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
  
4. <span data-ttu-id="030ca-132">Na koniec `CreateMultipleTasksAsync`zdefiniuj metodę , która wykonuje następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="030ca-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="030ca-133">Metoda deklaruje `HttpClient` obiekt, który należy uzyskać <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dostęp `ProcessURLAsync`do metody w programie .</span><span class="sxs-lookup"><span data-stu-id="030ca-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="030ca-134">Metoda tworzy i uruchamia trzy <xref:System.Threading.Tasks.Task%601>zadania `TResult` typu , gdzie jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="030ca-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="030ca-135">Po zakończeniu każdego `DisplayResults` zadania wyświetla adres URL zadania i długość pobranej zawartości.</span><span class="sxs-lookup"><span data-stu-id="030ca-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="030ca-136">Ponieważ zadania są uruchomione asynchronicznie, kolejność, w jakiej pojawiają się wyniki mogą różnić się od kolejności, w jakiej zostały zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="030ca-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="030ca-137">Metoda oczekuje na zakończenie każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="030ca-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="030ca-138">Każdy `await` operator zawiesza `CreateMultipleTasksAsync` wykonywanie do momentu zakończenia oczekiwanego zadania.</span><span class="sxs-lookup"><span data-stu-id="030ca-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="030ca-139">Operator pobiera również wartość zwracaną z `ProcessURLAsync` wywołania do z każdego ukończonego zadania.</span><span class="sxs-lookup"><span data-stu-id="030ca-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="030ca-140">Po zakończeniu zadań i pobraniu wartości całkowitych metoda sumuje długości witryn sieci Web i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="030ca-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="030ca-141">Skopiuj następującą metodę i wklej ją do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="030ca-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5. <span data-ttu-id="030ca-142">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="030ca-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="030ca-143">Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność ich zakończenia niekoniecznie jest kolejność, w jakiej są tworzone i oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="030ca-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="030ca-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="030ca-144">Example</span></span>  
 <span data-ttu-id="030ca-145">Poniższy kod zawiera pełny przykład.</span><span class="sxs-lookup"><span data-stu-id="030ca-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="030ca-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="030ca-146">See also</span></span>

- [<span data-ttu-id="030ca-147">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)</span><span class="sxs-lookup"><span data-stu-id="030ca-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="030ca-148">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="030ca-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="030ca-149">Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="030ca-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
