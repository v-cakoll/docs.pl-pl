---
title: "Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 509f9e690a5157c2d80ba9726354ce57a9d7ff26
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)
W metodzie asynchronicznej zadania są uruchamiane, gdy są tworzone. [Await](../../../../csharp/language-reference/keywords/await.md) operator jest stosowany do zadań w momencie w metodzie, której nie można kontynuować przetwarzania przed zakończeniem zadania. Często zadania jest oczekiwane, natychmiast po utworzeniu, jak przedstawiono na poniższym przykładzie.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Jednak można oddzielić Tworzenie zadania z oczekiwanie na zadanie, jeśli program ma wykonywać inne zadania, które nie są zależne od ukończenia zadania.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Między uruchamianie zadania i oczekujące na on, można uruchomić inne zadania. Dodatkowe zadania niejawnie równolegle, ale nie dodatkowe wątki są tworzone.  
  
 Następujący program uruchamia trzy pobieranie asynchroniczne sieci web i Oczekiwanie je w kolejności, w którym są nazywane. Powiadomienia i po uruchomieniu programu, w której zadania nie zawsze kończy się w kolejności, w którym są tworzone i oczekiwane. Decydując się uruchomić, kiedy są tworzone i co najmniej jednego zadania może zakończyć się pomyślnie przed metody osiągnie wyrażenia await.  
  
> [!NOTE]
>  Aby ukończyć ten projekt, musi mieć program Visual Studio 2012 lub nowszym i .NET Framework 4.5 lub nowszy jest zainstalowany na tym komputerze.  
  
 Na przykład innego uruchamiania wielu zadań jednocześnie, zobacz [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Można pobrać kodu w tym przykładzie z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Aby skonfigurować projekt  
  
1.  Aby skonfigurować aplikacji WPF, wykonaj następujące kroki. Szczegółowe instrukcje w tych krokach można znaleźć [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Tworzenie aplikacji programu WPF, która zawiera pole tekstowe i przycisk. Nazwa przycisku `startButton`oraz nazwę pola tekstowego `resultsTextBox`.  
  
    -   Dodaj odwołanie do <xref:System.Net.Http>.  
  
    -   W pliku MainWindow.xaml.cs Dodaj `using` dyrektywy dla `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Aby dodać kod  
  
1.  W oknie projektowania MainWindow.xaml, kliknij dwukrotnie przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.  
  
2.  Skopiuj poniższy kod i wklej go do treści `startButton_Click` w MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kod wywołuje metodę asynchroniczną `CreateMultipleTasksAsync`, które dyski aplikacji.  
  
3.  Dodaj następujące metody pomocy technicznej do projektu:  
  
    -   `ProcessURLAsync` używa <xref:System.Net.Http.HttpClient> metodę, aby pobrać zawartość witryny sieci Web w postaci tablicy bajtów. Metoda obsługi `ProcessURLAsync` następnie wyświetla i zwraca długość tablicy.  
  
    -   `DisplayResults` Wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL. Pokazuje to wyświetlenie podczas każdego zadania został pobrany.  
  
     Skopiuj następujące metody i wklej je po `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.  
  
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
  
4.  Na koniec zdefiniować metody `CreateMultipleTasksAsync`, która wykonuje następujące czynności.  
  
    -   Deklaruje metody `HttpClient` obiektu, który chcesz uzyskać dostęp do metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> w `ProcessURLAsync`.  
  
    -   Metoda utworzenie i uruchomienie zadania trzy typu <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą. Jak każdego zadania zakończeniu `DisplayResults` Wyświetla adres URL zadania i długość zawartości pobrane. Ponieważ zadania są uruchomione asynchronicznie, kolejność wyświetlania wyników może się różnić od kolejności, w której była zadeklarowana.  
  
    -   Metoda oczekujące na zakończenie wszystkich zadań. Każdy `await` operator wstrzymuje wykonywanie `CreateMultipleTasksAsync` dopiero po zakończeniu zadania oczekiwano. Operator pobiera również wartość zwrotna z wywołania `ProcessURLAsync` z każdego ukończonego zadania.  
  
    -   Po zakończeniu zadania i wartości całkowite zostały pobrane, metoda sumuje długości witryn sieci Web i wyświetlane wyniki.  
  
     Następująca metoda skopiuj i wklej go do rozwiązania.  
  
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
  
5.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Uruchom program kilka razy, aby sprawdzić, czy trzy zadania nie zawsze zakończone w tej samej kolejności i kolejność ich Zakończ nie musi być koniecznie kolejność, w którym są tworzone i oczekiwane.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
