---
title: Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970032"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)

Można zwiększyć wydajność rozwiązania asynchronicznego w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) przy użyciu <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> metody. Ta metoda asynchronicznie oczekuje na wiele operacji asynchronicznych, które są reprezentowane jako zbiór zadań.

Być może zauważyłeś w instruktażenie, że strony internetowe pobierają po różnych cenach. Czasami jedna ze stron internetowych jest bardzo powolna, co opóźnia wszystkie pozostałe pliki do pobrania. Po uruchomieniu rozwiązań asynchronicznych, które tworzysz w instruktażu, można zakończyć program łatwo, jeśli nie chcesz czekać, ale lepszym rozwiązaniem byłoby, aby rozpocząć wszystkie pliki do pobrania w tym samym czasie i niech szybsze pobieranie kontynuować bez czekania na ten, który jest Opóźnione.

Metoda jest `Task.WhenAll` stosowana do kolekcji zadań. Aplikacja `WhenAll` zwraca pojedyncze zadanie, które nie zostało ukończone, dopóki nie zostanie ukończone każde zadanie w kolekcji. Zadania wydają się działać równolegle, ale nie są tworzone żadne dodatkowe wątki. Zadania można wykonać w dowolnej kolejności.

> [!IMPORTANT]
> W poniższych procedurach opisano rozszerzenia aplikacji asynchronicznych, które zostały opracowane w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Aplikacje można tworzyć, wykonując instruktaże lub pobierając kod z [przykładów kodu dewelopera.](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
>
> Aby uruchomić przykład, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać Task.WhenAll do rozwiązania GetURLContentsAsync

1. Dodaj `ProcessURLAsync` metodę do pierwszej aplikacji, która została opracowana w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Jeśli kod został pobrany z [przykładów kodu dewelopera,](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)otwórz `ProcessURLAsync` projekt AsyncWalkthrough, a następnie dodaj do pliku MainWindow.xaml.cs.

    - Jeśli został opracowany kod, wykonując instruktaże, `ProcessURLAsync` dodaj `GetURLContentsAsync` do aplikacji, która zawiera metodę. Plik MainWindow.xaml.cs dla tej aplikacji jest pierwszym przykładem w sekcji "Kompletne przykłady kodu z instruktażenia".

    Metoda `ProcessURLAsync` konsoliduje akcje w treści `foreach` pętli `SumPageSizesAsync` w oryginalnym instruktaże. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Skomentuj lub `foreach` usuń `SumPageSizesAsync`pętlę w , jak pokazano w poniższym kodzie.

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

3. Tworzenie kolekcji zadań. Poniższy kod definiuje [kwerendę,](../linq/index.md) która po <xref:System.Linq.Enumerable.ToArray%2A> wykonaniu przez metodę tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy kwerenda jest oceniana.

    Dodaj następujący kod `SumPageSizesAsync` do metody `urlList`po deklaracji .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Zastosuj `Task.WhenAll` `downloadTasks`do zbierania zadań, . `Task.WhenAll`zwraca pojedyncze zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.

    W poniższym `await` przykładzie wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Wyrażenie jest obliczane do tablicy liczb całkowitych, gdzie każda liczba całkowita jest długość pobranej witryny sieci Web. Dodaj następujący kod `SumPageSizesAsync`do , tuż po kodzie dodanym w poprzednim kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Na koniec <xref:System.Linq.Enumerable.Sum%2A> użyj metody, aby obliczyć sumę długości wszystkich stron internetowych. Dodaj następujący wiersz `SumPageSizesAsync`do .

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać Task.WhenAll do rozwiązania HttpClient.GetByteArrayAsync

1. Dodaj następującą `ProcessURLAsync` wersję do drugiej aplikacji, która została opracowana w [instruktaż: Uzyskiwanie dostępu do sieci Web za pomocą asynchronii i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Jeśli kod został pobrany z [przykładów kodu dewelopera,](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)otwórz projekt AsyncWalkthrough_HttpClient, a następnie dodaj `ProcessURLAsync` do MainWindow.xaml.cs pliku.

    - Jeśli został opracowany kod, wykonując instruktaże, `ProcessURLAsync` dodaj `HttpClient.GetByteArrayAsync` do aplikacji, która używa metody. Plik MainWindow.xaml.cs dla tej aplikacji jest drugim przykładem w sekcji "Kompletne przykłady kodu z instruktażu".

    Metoda `ProcessURLAsync` konsoliduje akcje w treści `foreach` pętli `SumPageSizesAsync` w oryginalnym instruktaże. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtów, a następnie wyświetla i zwraca długość tablicy bajtów.

    Jedyną różnicą `ProcessURLAsync` od metody w poprzedniej <xref:System.Net.Http.HttpClient> procedurze `client`jest użycie wystąpienia.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Skomentuj lub `For Each` usuń `foreach` lub `SumPageSizesAsync`pętlę w , jak pokazano w poniższym kodzie.

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

3. Zdefiniuj [kwerendę,](../linq/index.md) która po wykonaniu <xref:System.Linq.Enumerable.ToArray%2A> przez metodę tworzy zbiór zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy kwerenda jest oceniana.

    Dodaj następujący kod `SumPageSizesAsync` do metody `client` po `urlList`deklaracji i .

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Następnie zastosuj `Task.WhenAll` `downloadTasks`do zbierania zadań, . `Task.WhenAll`zwraca pojedyncze zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.

    W poniższym `await` przykładzie wyrażenie oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Po zakończeniu `await` wyrażenie jest obliczane do tablicy liczb całkowitych, gdzie każda liczba całkowita jest długość pobranej witryny sieci Web. Dodaj następujący kod `SumPageSizesAsync`do , tuż po kodzie dodanym w poprzednim kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Na koniec <xref:System.Linq.Enumerable.Sum%2A> użyj metody, aby uzyskać sumę długości wszystkich stron internetowych. Dodaj następujący wiersz `SumPageSizesAsync`do .

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązania Task.WhenAll

- Dla jednego z rozwiązań wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start.** Dane wyjściowe powinny przypominać dane wyjściowe z rozwiązań asynchroniczny w [Instruktaż: Dostęp do sieci Web za pomocą async i await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md). Należy jednak zauważyć, że strony internetowe pojawiają się w innej kolejności za każdym razem.

## <a name="example"></a>Przykład

Poniższy kod pokazuje rozszerzenia do projektu, `GetURLContentsAsync` który używa metody do pobierania zawartości z sieci Web.

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="example"></a>Przykład

Poniższy kod pokazuje rozszerzenia do projektu, `HttpClient.GetByteArrayAsync` który używa metody do pobierania zawartości z sieci Web.

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
                from url in urlList select ProcessURLAsync(url, client);

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
