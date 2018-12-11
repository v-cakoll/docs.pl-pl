---
title: 'Instrukcje: Wiele żądań sieci Web równolegle za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 527cca572e48cd4b6b895c828327a5770ac83d89
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125603"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Instrukcje: Wiele żądań sieci Web równolegle za pomocą async i await (C#)
W metodzie asynchronicznej zadania są uruchamiane po ich utworzeniu. [Await](../../../../csharp/language-reference/keywords/await.md) operator jest stosowany do zadania w tym punkcie metody, których nie można kontynuować przetwarzania przed zakończeniem zadania. Często zadanie jest oczekiwane, zaraz po jego utworzeniu, co ilustruje poniższy przykład.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Jednakże można oddzielić Tworzenie zadania od oczekiwania na zadanie, jeśli w programie trzeba wykonać inne prace, które nie są zależne od zakończenia tego zadania.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Między rozpoczęciem zadania i oczekiwaniem na, możesz uruchomić inne zadania. Dodatkowe zadania w sposób niejawny uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone.  
  
 Następujący program uruchamia trzy asynchroniczne web pobierania, a następnie oczekuje na ich zakończenie w kolejności, w którym są nazywane. Zwróć uwagę, po uruchomieniu programu, który zadania nie są zawsze kończone w kolejności, w którym są tworzone i oczekiwane. Zaczynają działać, gdyż zostały utworzone, gdy jeden lub więcej zadań może zakończyć zanim metoda osiągnie wyrażenie await.  
  
> [!NOTE]
>  Aby wykonać ten projekt, jest posiadanie programu Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.  
  
 Inny przykład, który rozpoczyna się wiele zadań, w tym samym czasie, zobacz [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Możesz pobrać kod dla tego przykładu z [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1.  Aby skonfigurować aplikację programu WPF, wykonaj następujące czynności. Można znaleźć szczegółowe instrukcje tych kroków w [instruktażu: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Tworzenie aplikacji WPF, która zawiera pole tekstowe i przycisk. Nazwij przycisk `startButton`i pole tekstowego `resultsTextBox`.  
  
    -   Dodaj odwołanie do <xref:System.Net.Http>.  
  
    -   W pliku MainWindow.xaml.cs Dodaj `using` dyrektywy dla `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1.  W oknie projektu, MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.  
  
2.  Skopiuj poniższy kod i wklej go w treść `startButton_Click` w MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod wywołuje metodę asynchroniczną, `CreateMultipleTasksAsync`, która steruje aplikacją.  
  
3.  Dodaj następujące metody pomocy technicznej do projektu:  
  
    -   `ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metody do pobierania zawartości witryny sieci Web w postaci tablicy bajtów. Metoda pomocnicza `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.  
  
    -   `DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. To wyświetlane, gdy każde zadanie zakończy pobieranie.  
  
     Kopiuj poniższe metody i wklej je za `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.  
  
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
  
4.  Na koniec zdefiniuj metodę `CreateMultipleTasksAsync`, który wykonuje następujące czynności.  
  
    -   Metoda deklaruje `HttpClient` obiektu, który jest potrzebny na dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.  
  
    -   Metoda tworzy i uruchamia trzy zadania typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą. Gdy poszczególne podzadania zakończą, `DisplayResults` Wyświetla adres URL tego zadania i długość pobranej treści. Ponieważ zadania odbywają się asynchronicznie, kolejność, w jakiej są wyświetlane wyniki mogą różnić się od kolejności, w którym zostały zadeklarowane.  
  
    -   Metoda czeka na zakończenie każdego zadania. Każdy `await` operator zawiesza wykonywanie `CreateMultipleTasksAsync` aż oczekiwane zadanie się zakończy. Operator pobiera również wartość zwracaną z wywołania `ProcessURLAsync` z każdego ukończonego zadania.  
  
    -   Kiedy zadania zostały ukończone i pobraniu wartości całkowitych, metoda sumuje długość witryn sieci Web i wyświetla wynik.  
  
     Kopiuj następującą metodę i wkleić go do rozwiązania.  
  
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
  
5.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Uruchom program kilka razy, aby sprawdzić, czy te trzy zadania nie zawsze kończą się w tej samej kolejności i czy kolejność ich zakończenia niekoniecznie jest kolejnością w którym są tworzone i oczekiwane.  
  
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

- [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
