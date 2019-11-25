---
title: Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAllC#()
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: afd7dda4e876b7faa54ae4a8e62d640d2b9aaf07
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970032"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a>Jak rozłożyć Instruktaż asynchroniczny za pomocą metody Task. WhenAllC#()

Wydajność rozwiązania asynchronicznego można poprawić w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) za pomocą metody <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Ta metoda asynchronicznie czeka na wiele operacji asynchronicznych, które są reprezentowane jako kolekcja zadań.

W instruktażu można zauważyć, że witryny sieci Web pobierają różne stawki. Czasami jedna z witryn sieci Web działa bardzo wolno, co opóźnia wszystkie pozostałe pliki do pobrania. Po uruchomieniu rozwiązań asynchronicznych, które można skompilować w przewodniku, można łatwo zakończyć działanie programu, jeśli nie chcesz czekać, ale lepszym rozwiązaniem jest uruchomienie wszystkich pobrań w tym samym czasie i szybsze pobieranie będzie kontynuowane bez czekania na ten  Wydłuż.

Metoda `Task.WhenAll` jest stosowana do kolekcji zadań. Aplikacja `WhenAll` zwraca pojedyncze zadanie, które nie zostanie ukończone, dopóki każde zadanie w kolekcji nie zostanie ukończone. Zadania są uruchamiane równolegle, ale żadne dodatkowe wątki nie są tworzone. Zadania można wykonać w dowolnej kolejności.

> [!IMPORTANT]
> Poniższe procedury opisują rozszerzenia dla aplikacji asynchronicznych, które są opracowywane w [przewodniku: uzyskiwanie dostępu do sieci WebC#za pomocą Async i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md). Aplikacje można opracowywać, wykonując Instruktaż lub pobierając kod z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).
>
> Aby uruchomić ten przykład, na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a>Aby dodać zadanie. WhenAll do rozwiązania GetURLContentsAsync

1. Dodaj metodę `ProcessURLAsync` do pierwszej aplikacji, która została opracowana w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocąC#Async i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), Otwórz projekt AsyncWalkthrough, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow.XAML.cs.

    - Jeśli opracowano kod przez wykonanie przewodnika, należy dodać `ProcessURLAsync` do aplikacji zawierającej metodę `GetURLContentsAsync`. Plik MainWindow.xaml.cs dla tej aplikacji to pierwszy przykład w sekcji "pełne przykłady kodu z przewodnika".

    Metoda `ProcessURLAsync` konsoliduje akcje w treści pętli `foreach` w `SumPageSizesAsync` w pierwotnym instruktażu. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Skomentuj lub Usuń pętlę `foreach` w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.

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

3. Utwórz kolekcję zadań. Poniższy kod definiuje [zapytanie](../linq/index.md) , które podczas wykonywania przez metodę <xref:System.Linq.Enumerable.ToArray%2A> tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest oceniane.

    Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `urlList`.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.

    W poniższym przykładzie wyrażenie `await` oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Wyrażenie daje w wyniku tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tuż po kodzie dodanym w poprzednim kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Na koniec użyj metody <xref:System.Linq.Enumerable.Sum%2A>, aby obliczyć sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a>Aby dodać zadanie. WhenAll do rozwiązania HttpClient. GetByteArrayAsync

1. Dodaj następującą wersję `ProcessURLAsync` do drugiej aplikacji, która została opracowana w [przewodniku: uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md).

    - Jeśli pobrano kod z [przykładów kodu programisty](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), otwórz projekt AsyncWalkthrough_HttpClient, a następnie Dodaj `ProcessURLAsync` do pliku MainWindow.XAML.cs.

    - Jeśli opracowano kod przez wykonanie przewodnika, należy dodać `ProcessURLAsync` do aplikacji używającej metody `HttpClient.GetByteArrayAsync`. Plik MainWindow.xaml.cs dla tej aplikacji to drugi przykład w sekcji "kompletne przykłady kodu z przewodnika".

    Metoda `ProcessURLAsync` konsoliduje akcje w treści pętli `foreach` w `SumPageSizesAsync` w pierwotnym instruktażu. Metoda asynchronicznie pobiera zawartość określonej witryny sieci Web jako tablicę bajtową, a następnie wyświetla i zwraca długość tablicy bajtów.

    Jedyną różnicą między metodą `ProcessURLAsync` w poprzedniej procedurze jest użycie wystąpienia <xref:System.Net.Http.HttpClient>, `client`.

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. Skomentuj lub Usuń `For Each` lub `foreach` pętlę w `SumPageSizesAsync`, jak pokazano w poniższym kodzie.

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

3. Zdefiniuj [zapytanie](../linq/index.md) , które podczas wykonywania przez metodę <xref:System.Linq.Enumerable.ToArray%2A> tworzy kolekcję zadań, które pobierają zawartość każdej witryny sieci Web. Zadania są uruchamiane, gdy zapytanie jest oceniane.

    Dodaj następujący kod do metody `SumPageSizesAsync` po deklaracji `client` i `urlList`.

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. Następnie Zastosuj `Task.WhenAll` do kolekcji zadań, `downloadTasks`. `Task.WhenAll` zwraca jedno zadanie, które kończy się po zakończeniu wszystkich zadań w kolekcji zadań.

    W poniższym przykładzie wyrażenie `await` oczekuje na zakończenie pojedynczego zadania, które `WhenAll` zwraca. Po zakończeniu wyrażenie `await` oblicza tablicę liczb całkowitych, gdzie każda liczba całkowita jest długością pobranej witryny sieci Web. Dodaj następujący kod do `SumPageSizesAsync`, tuż po kodzie dodanym w poprzednim kroku.

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. Na koniec użyj metody <xref:System.Linq.Enumerable.Sum%2A>, aby uzyskać sumę długości wszystkich witryn sieci Web. Dodaj następujący wiersz do `SumPageSizesAsync`.

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a>Aby przetestować rozwiązania Task. WhenAll

- Dla dowolnego rozwiązania wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** . Dane wyjściowe powinny wyglądać podobnie do danych wyjściowych z rozwiązań asynchronicznych w [przewodniku: uzyskiwanie dostępu do sieci WebC#za pomocą Async i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md). Należy jednak zauważyć, że witryny sieci Web są wyświetlane w innej kolejności za każdym razem.

## <a name="example"></a>Przykład

Poniższy kod przedstawia rozszerzenia projektu, który używa metody `GetURLContentsAsync` do pobierania zawartości z sieci Web.

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

Poniższy kod przedstawia rozszerzenia projektu, który używa metody `HttpClient.GetByteArrayAsync` do pobierania zawartości z sieci Web.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md)
