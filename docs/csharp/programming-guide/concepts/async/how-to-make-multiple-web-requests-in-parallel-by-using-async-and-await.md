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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Jak wykonać równolegle wiele żądań sieci Web za pomocą Async i Await (C#)
W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone. Operator [await](../../../language-reference/operators/await.md) jest stosowany do zadania w punkcie metody, w którym przetwarzanie nie może być kontynuowane do momentu zakończenia zadania. Często zadanie jest oczekiwane zaraz po jego utworzeniu, tak jak pokazano w poniższym przykładzie.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Można jednak oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli program ma inne zadania do wykonania, które nie zależą od ukończenia zadania.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Między rozpoczęciem zadania i oczekiwaniem na niego można uruchomić inne zadania. Dodatkowe zadania niejawnie uruchamiają się równolegle, ale nie są tworzone żadne dodatkowe wątki.  
  
 Poniższy program uruchamia trzy asynchroniczne pobieranie w sieci Web, a następnie czeka na ich kolejność, w jakiej są wywoływane. Zwróć uwagę, że po uruchomieniu programu zadania nie zawsze kończą się w kolejności, w której zostały utworzone i oczekujące. Zaczynają one działać, gdy są tworzone, i co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie wyrażenie await.  
  
> [!NOTE]
> Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
 Aby uzyskać inny przykład, który uruchamia wiele zadań w tym samym czasie, zobacz [jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Kod dla tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1. Aby skonfigurować aplikację WPF, wykonaj następujące czynności. Szczegółowe instrukcje dotyczące tych kroków można znaleźć w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Utwórz aplikację WPF, która zawiera pole tekstowe i przycisk. Nadaj nazwę przyciskowi `startButton` i nazwij pole tekstowe `resultsTextBox` .  
  
    - Dodaj odwołanie do <xref:System.Net.Http> .  
  
    - W pliku MainWindow.xaml.cs Dodaj `using` dyrektywę dla `System.Net.Http` .  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1. W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow.XAML.cs.  
  
2. Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.XAML.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync` która dyskuje aplikację.  
  
3. Dodaj do projektu następujące metody pomocy technicznej:  
  
    - `ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web jako tablicy bajtów. Metoda pomocy technicznej, a `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.  
  
    - `DisplayResults`Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. Ten ekran jest wyświetlany po zakończeniu pobierania każdego zadania.  
  
     Skopiuj następujące metody i wklej je po `startButton_Click` procedurze obsługi zdarzeń w MainWindow.XAML.cs.  
  
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
  
4. Na koniec Zdefiniuj metodę `CreateMultipleTasksAsync` , która wykonuje następujące czynności.  
  
    - Metoda deklaruje `HttpClient` obiekt, do którego należy uzyskać dostęp za pomocą <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> metody `ProcessURLAsync` .  
  
    - Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601> , gdzie `TResult` jest liczbą całkowitą. Po zakończeniu każdego zadania program `DisplayResults` wyświetla adres URL zadania i długość pobranej zawartości. Ponieważ zadania są wykonywane asynchronicznie, kolejność, w której wyniki są wyświetlane, może różnić się od kolejności, w której zostały zadeklarowane.  
  
    - Metoda oczekuje na zakończenie każdego zadania. Każdy `await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` do momentu zakończenia oczekującego zadania. Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego wykonanego zadania.  
  
    - Po zakończeniu zadań i pobraniu wartości całkowitych Metoda sumuje długości witryn sieci Web i wyświetla wynik.  
  
     Skopiuj poniższą metodę i wklej ją do rozwiązania.  
  
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
  
5. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .  
  
     Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność, w jakiej się kończą, nie musi być kolejnością, w której są one tworzone i oczekiwane.  
  
## <a name="example"></a>Przykład  
 Poniższy kod zawiera pełny przykład.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
- [Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
