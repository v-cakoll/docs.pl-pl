---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 01557bf80f40d4197d29ab05cfb4838f5d993a82
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61702753"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Anulowanie zadania asynchronicznego lub listy zadań (C#)

Można skonfigurować przycisk, który służy do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na zakończenie jego działania. Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość jednej witryny sieci Web lub listę witryn sieci Web.

W przykładach wykorzystano interfejs użytkownika, [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) opisuje.

> [!NOTE]
> Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.

## <a name="cancel-a-task"></a>Anuluj zadanie

Pierwszy przykład kojarzy **anulować** przycisk z pojedynczym zadaniem pobierania. Jeśli wybierzesz przycisk podczas pobierania zawartości aplikacji, pobieranie zostanie anulowane.

### <a name="download-the-example"></a>Pobierz przykład

Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.

1. Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.

3. W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelATask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.

5. Wybierz **F5** klawisz, aby uruchomić projekt (lub naciśnij **Ctrl**+**F5** uruchomić projekt bez debugowania go).

> [!TIP]
> Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Budowanie przykładu
 Poniższe zmiany powodują dodanie **anulować** przycisku do aplikacji, która pobiera witrynę sieci Web. Jeśli nie chcesz pobrać lub kompilować przykładu, można przejrzeć produkt końcowy w sekcji "Kompletne przykłady" na końcu tego tematu. Gwiazdka oznacza zmiany w kodzie.

 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **StarterCode** jako **projekt startowy** zamiast **CancelATask** .

 Następnie należy dodać następujące zmiany do pliku MainWindow.xaml.cs tego projektu.

1. Zadeklaruj `CancellationTokenSource` zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod, które do niego dostęp.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Dodaj następującą obsługę zdarzeń dla **anulować** przycisku. Obsługa zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić `cts` po użytkownik zażąda anulowania.

    ```csharp
    // ***Add an event handler for the Cancel button.
    private void cancelButton_Click(object sender, RoutedEventArgs e)
    {
        if (cts != null)
        {
            cts.Cancel();
        }
    }
    ```

3. Utwórz następujące zmiany w zdarzeniu Obsługa **Start** przycisku `startButton_Click`.

    - Utwórz wystąpienie `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - W wywołaniu `AccessTheWebAsync`, które pobiera zawartość określonej witryny sieci Web, wysyłanie <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwość `cts` jako argument. `Token` Właściwość propaguje komunikat, czy zażądano anulowania. Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik anuluje operację pobierania. Poniższy kod pokazuje zmiany.

        ```csharp
        try
        {
            // ***Send a token to carry the message if cancellation is requested.
            int contentLength = await AccessTheWebAsync(cts.Token);
            resultsTextBox.Text += $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }
        // *** If cancellation is requested, an OperationCanceledException results.
        catch (OperationCanceledException)
        {
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";
        }
        catch (Exception)
        {
            resultsTextBox.Text += "\r\nDownload failed.\r\n";
        }
        ```

4. W `AccessTheWebAsync`, użyj <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> przeciążenia `GetAsync` method in Class metoda <xref:System.Net.Http.HttpClient> typu, aby pobrać zawartość witryny sieci Web. Przekaż `ct`, <xref:System.Threading.CancellationToken> parametru `AccessTheWebAsync`, jako drugi argument. Token niesie komunikat, jeśli użytkownik wybierze **anulować** przycisku.

     Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.

    ```csharp
    // ***Provide a parameter for the CancellationToken.
    async Task<int> AccessTheWebAsync(CancellationToken ct)
    {
        HttpClient client = new HttpClient();

        resultsTextBox.Text += "\r\nReady to download.\r\n";

        // You might need to slow things down to have a chance to cancel.
        await Task.Delay(250);

        // GetAsync returns a Task<HttpResponseMessage>.
        // ***The ct argument carries the message if the Cancel button is chosen.
        HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // The result of the method is the length of the downloaded website.
        return urlContents.Length;
    }
    ```

5. Jeśli nie anulujesz programu, wygeneruje następujące wyniki.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Jeśli wybierzesz **anulować** przycisku, zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Anuluj listę zadań

Możesz rozszerzyć poprzedniego przykładu, aby anulować wiele zadań można skojarzyć takie same `CancellationTokenSource` z każdym zadaniem. Jeśli wybierzesz **anulować** przycisku, anulujesz wszystkie zadania, które nie są jeszcze kompletne.

### <a name="download-the-example"></a>Pobierz przykład

Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.

1. Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.

3. W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAListOfTasks** projektu, a następnie wybierz **Ustaw jako projekt startowy**.

5. Wybierz **F5** klawisz, aby uruchomić projekt.

     Wybierz **Ctrl**+**F5** kluczy, aby uruchomić projekt bez debugowania go.

Jeśli nie chcesz wczytać projekt, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Budowanie przykładu

Aby rozszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelATask** jako **projekt startowy**. Dodaj następujące zmiany do tego projektu. Gwiazdka oznacza zmiany w programie.

1. Dodaj metodę, aby utworzyć listę adresów internetowych.

    ```csharp
    // ***Add a method that creates a list of web addresses.
    private List<string> SetUpURLList()
    {
        List<string> urls = new List<string>
        {
            "https://msdn.microsoft.com",
            "https://msdn.microsoft.com/library/hh290138.aspx",
            "https://msdn.microsoft.com/library/hh290140.aspx",
            "https://msdn.microsoft.com/library/dd470362.aspx",
            "https://msdn.microsoft.com/library/aa578028.aspx",
            "https://msdn.microsoft.com/library/ms404677.aspx",
            "https://msdn.microsoft.com/library/ff730837.aspx"
        };
        return urls;
    }
    ```

2. Wywołaj metodę `AccessTheWebAsync`.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Dodaj następującą pętlę w `AccessTheWebAsync` Aby przetwarzać każdy adresu sieci web, na liście.

    ```csharp
    // ***Add a loop to process the list of web addresses.
    foreach (var url in urlList)
    {
        // GetAsync returns a Task<HttpResponseMessage>.
        // Argument ct carries the message if the Cancel button is chosen.
        // ***Note that the Cancel button can cancel all remaining downloads.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
    }
    ```

4. Ponieważ `AccessTheWebAsync` Wyświetla długości, metoda nie musi niczego zwracać. Usuń instrukcję return, a następnie zmień zwracany typ metody do <xref:System.Threading.Tasks.Task> zamiast <xref:System.Threading.Tasks.Task%601>.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Jeśli nie anulujesz programu, wygeneruje następujące wyniki.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Length of the downloaded string: 158124.

    Length of the downloaded string: 204890.

    Length of the downloaded string: 175488.

    Length of the downloaded string: 145790.

    Downloads complete.
    ```

     Jeśli wybierzesz **anulować** przycisku przed zakończeniu pobierania, dane wyjściowe zawierają długości plików o pobieraniu ukończonym przed anulowaniem.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Kompletne przykłady

Poniższe sekcje zawierają kod dla każdego z poprzednich przykładów. Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.

Można ściągnąć projekty z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Przykład — Anuluj zadanie

Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.

using System.Threading;
namespace CancelATask
{
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // ***Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Send a token to carry the message if cancellation is requested.
                int contentLength = await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }
            // *** If cancellation is requested, an OperationCanceledException results.
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownload failed.\r\n";
            }

            // ***Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // ***Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // ***Provide a parameter for the CancellationToken.
        async Task<int> AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            resultsTextBox.Text += "\r\nReady to download.\r\n";

            // You might need to slow things down to have a chance to cancel.
            await Task.Delay(250);

            // GetAsync returns a Task<HttpResponseMessage>.
            // ***The ct argument carries the message if the Cancel button is chosen.
            HttpResponseMessage response = await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            // The result of the method is the length of the downloaded website.
            return urlContents.Length;
        }
    }

    // Output for a successful download:

    // Ready to download.

    // Length of the downloaded string: 158125.

    // Or, if you cancel:

    // Ready to download.

    // Download canceled.
}
```

### <a name="example---cancel-a-list-of-tasks"></a>Przykład — Anuluj listę zadań

Poniższy kod jest pełnym MainWindow.xaml.cs dla przykładu, który Anuluje listę zadań.

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

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive for System.Threading.
using System.Threading;

namespace CancelAListOfTasks
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                await AccessTheWebAsync(cts.Token);
                // ***Small change in the display lines.
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.";
            }

            // Set the CancellationTokenSource to null when the download is complete.
            cts = null;
        }

        // Add an event handler for the Cancel button.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        // Provide a parameter for the CancellationToken.
        // ***Change the return type to Task because the method has no return statement.
        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // ***Call SetUpURLList to make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Add a loop to process the list of web addresses.
            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // ***Note that the Cancel button can cancel all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        // ***Add a method that creates a list of web addresses.
        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Output if you do not choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Length of the downloaded string: 158124.

    //Length of the downloaded string: 204890.

    //Length of the downloaded string: 175488.

    //Length of the downloaded string: 145790.

    //Downloads complete.

    // Sample output if you choose to cancel:

    //Length of the downloaded string: 35939.

    //Length of the downloaded string: 237682.

    //Length of the downloaded string: 128607.

    //Downloads canceled.
}
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
