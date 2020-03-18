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
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)
W metodzie asynchronicznej zadania są uruchamiane po ich utworzeniu. Await [await](../../../language-reference/operators/await.md) operator jest stosowany do zadania w punkcie w metodzie, gdzie przetwarzanie nie można kontynuować, dopóki zadanie nie zostanie zakończone. Często zadanie jest oczekiwane, jak tylko zostanie utworzony, jak pokazano w poniższym przykładzie.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Można jednak oddzielić tworzenie zadania od oczekiwania na zadanie, jeśli program ma inną pracę do wykonania, która nie zależy od zakończenia zadania.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Między rozpoczęciem zadania a oczekiwaniem na nie można uruchomić inne zadania. Dodatkowe zadania niejawnie uruchamiane równolegle, ale nie są tworzone żadne dodatkowe wątki.  
  
 Poniższy program uruchamia trzy asynchroniczne pliki do pobrania w sieci Web, a następnie czeka na nich w kolejności, w jakiej są nazywane. Należy zauważyć, po uruchomieniu programu, że zadania nie zawsze zakończyć w kolejności, w jakiej są tworzone i oczekiwane. Zaczynają działać, gdy są tworzone, a co najmniej jedno zadanie może zakończyć się, zanim metoda osiągnie await wyrażeń.  
  
> [!NOTE]
> Aby ukończyć ten projekt, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz program .NET Framework 4.5 lub nowszy.  
  
 W innym przykładzie, który uruchamia wiele zadań w tym samym czasie, zobacz [Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Kod tego przykładu można pobrać z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1. Aby skonfigurować aplikację WPF, wykonaj następujące kroki. Szczegółowe instrukcje dla tych kroków można znaleźć w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Utwórz aplikację WPF zawierającą pole tekstowe i przycisk. Nazwij `startButton`przycisk i nadawanie pola tekstowemu nazwy `resultsTextBox`.  
  
    - Dodaj odwołanie <xref:System.Net.Http>do pliku .  
  
    - W pliku MainWindow.xaml.cs dodaj `using` dyrektywę dla . `System.Net.Http`  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1. W oknie projektu MainWindow.xaml kliknij dwukrotnie przycisk, `startButton_Click` aby utworzyć program obsługi zdarzeń w MainWindow.xaml.cs.  
  
2. Skopiuj następujący kod i wklej go do treści `startButton_Click` w MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync`która napędza aplikację.  
  
3. Dodaj następujące metody obsługi do projektu:  
  
    - `ProcessURLAsync`używa <xref:System.Net.Http.HttpClient> metody pobierania zawartości witryny jako tablicy bajtów. Metoda obsługi, `ProcessURLAsync` a następnie wyświetla i zwraca długość tablicy.  
  
    - `DisplayResults`wyświetla liczbę bajtów w tablicy bajtów dla każdego adresu URL. Ten ekran pokazuje, kiedy każde zadanie zostało zakończone pobieranie.  
  
     Skopiuj następujące metody i `startButton_Click` wklej je po programie obsługi zdarzeń w MainWindow.xaml.cs.  
  
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
  
4. Na koniec `CreateMultipleTasksAsync`zdefiniuj metodę , która wykonuje następujące kroki.  
  
    - Metoda deklaruje `HttpClient` obiekt, który należy uzyskać <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> dostęp `ProcessURLAsync`do metody w programie .  
  
    - Metoda tworzy i uruchamia trzy <xref:System.Threading.Tasks.Task%601>zadania `TResult` typu , gdzie jest liczbą całkowitą. Po zakończeniu każdego `DisplayResults` zadania wyświetla adres URL zadania i długość pobranej zawartości. Ponieważ zadania są uruchomione asynchronicznie, kolejność, w jakiej pojawiają się wyniki mogą różnić się od kolejności, w jakiej zostały zadeklarowane.  
  
    - Metoda oczekuje na zakończenie każdego zadania. Każdy `await` operator zawiesza `CreateMultipleTasksAsync` wykonywanie do momentu zakończenia oczekiwanego zadania. Operator pobiera również wartość zwracaną z `ProcessURLAsync` wywołania do z każdego ukończonego zadania.  
  
    - Po zakończeniu zadań i pobraniu wartości całkowitych metoda sumuje długości witryn sieci Web i wyświetla wynik.  
  
     Skopiuj następującą metodę i wklej ją do rozwiązania.  
  
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
  
5. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start.**  
  
     Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność ich zakończenia niekoniecznie jest kolejność, w jakiej są tworzone i oczekiwane.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
