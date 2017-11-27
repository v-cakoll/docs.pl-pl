---
title: "Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a83ceb8a58104cc7a4c177ce6c7df9aded8af7e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)
Może poprawić wydajność rozwiązania asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Ta metoda asynchronicznie oczekujące na wiele operacji asynchronicznych, które są reprezentowane jako kolekcji zadań.  
  
 Zwróć uwagę, w tym przewodnikiem czy witryn sieci Web Pobierz w różnym tempie. Czasami jednej z witryn sieci Web jest bardzo wolno, który wybrano opcję opóźnienia wszystkie pozostałe pliki do pobrania. Po uruchomieniu asynchroniczne rozwiązania, które można utworzyć w tym przewodnikiem, można łatwo zakończyć program, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby uruchomić wszystkie pobrane pliki w tym samym czasie i pozwól szybsze pobieranie kontynuować bez oczekiwania na to, że w  opóźnione.  
  
 Należy zastosować `Task.WhenAll` metody do kolekcji zadań. Stosowanie `WhenAll` zwraca pojedyncze zadanie, które nie są kompletne, do czasu ukończenia każdego zadania w kolekcji. Wyświetlanie zadań do uruchomienia równoległego, ale nie dodatkowe wątki są tworzone. Zadania można wykonać w dowolnej kolejności.  
  
> [!IMPORTANT]
>  Poniższe procedury opisują rozszerzeń aplikacji async, które są opracowywane w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Aplikacje można tworzyć spełniając wskazówki lub pobieranie kodu z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191).  
>   
>  Aby uruchomić przykład, musi mieć programu Visual Studio 2012 lub nowszy jest zainstalowany na tym komputerze.  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać do rozwiązania GetURLContentsAsync Task.WhenAll  
  
1.  Dodaj `ProcessURLAsync` metody do pierwszej aplikacji, który został napisany w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191), otwórz projekt AsyncWalkthrough, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.cs.  
  
    -   Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która obejmuje `GetURLContentsAsync` metody. Plik MainWindow.xaml.cs dla tej aplikacji jest pierwszym przykładzie w sekcji "Pełny kod przykłady z przewodnik".  
  
     `ProcessURLAsync` Metody konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` w oryginalnym wskazówki. Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Komentarz lub usunąć `foreach` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3.  Utwórz kolekcję zadań. Poniższy kod definiuje [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn. Zadania są uruchamiane podczas szacowania zapytania.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList`.  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll`Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca. Wyrażenie do tablicy liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę obliczania sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać Task.WhenAll rozwiązania HttpClient.GetByteArrayAsync  
  
1.  Dodaj następujące wersję `ProcessURLAsync` do drugiego aplikacji utworzoną w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Jeśli pobrano kod z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191), otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do pliku MainWindow.xaml.cs.  
  
    -   Jeśli kod jest rozwinięte, wykonując przewodnika, Dodaj `ProcessURLAsync` do aplikacji, która używa `HttpClient.GetByteArrayAsync` metody. Plik MainWindow.xaml.cs dla tej aplikacji jest drugi przykład w sekcji "Pełny kod przykłady z przewodnik".  
  
     `ProcessURLAsync` Metody konsoliduje akcje w treści `foreach` pętli w `SumPageSizesAsync` w oryginalnym wskazówki. Metoda asynchronicznie pobiera zawartość z określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.  
  
     Jedyną różnicą z `ProcessURLAsync` metody w poprzedniej procedurze jest używana <xref:System.Net.Http.HttpClient> wystąpienia, `client`.  
  
    ```csharp  
    async Task<int> ProcessURL(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  Komentarz lub usunąć `For Each` lub `foreach` pętli w `SumPageSizesAsync`, jak pokazano w następującym kodem.  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3.  Zdefiniuj [zapytania](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) , gdy wykonywane przez <xref:System.Linq.Enumerable.ToArray%2A> metoda, tworzy zbiór zadań, które pobrania zawartości z poszczególnych witryn. Zadania są uruchamiane podczas szacowania zapytania.  
  
     Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList`.  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURL(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll`Zwraca pojedyncze zadanie, która kończy się po zakończeniu wszystkich zadań w kolekcji zadań.  
  
     W poniższym przykładzie `await` wyrażenie oczekujące na ukończenie pojedynczego zadanie, które `WhenAll` zwraca. Po zakończeniu `await` wyrażenie ma tablicę liczb całkowitych, w którym każdy liczba całkowita jest długość pobrany witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tylko po kodzie dodanym w poprzednim kroku.  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  Na koniec użyj <xref:System.Linq.Enumerable.Sum%2A> metodę, aby pobrać sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązań Task.WhenAll  
  
-   Dla obu rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku. Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchronicznych w [wskazówki: uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Jednak zauważyć, że witryn sieci Web są wyświetlane w innej kolejności zawsze.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzeń w projekcie, który używa `GetURLContentsAsync` metodę, aby pobrać zawartość z sieci web.  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
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
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
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
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia rozszerzenia do projektu, który używa metody `HttpClient.GetByteArrayAsync` na pobieranie zawartości z sieci web.  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
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
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURL(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURL(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
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
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
