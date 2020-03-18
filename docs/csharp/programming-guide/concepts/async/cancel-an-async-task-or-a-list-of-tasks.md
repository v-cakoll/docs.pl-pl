---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595720"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Anulowanie zadania asynchronicznego lub listy zadań (C#)

Można skonfigurować przycisk, który służy do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na jej zakończenie. Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość jednej witryny sieci Web lub listę witryn sieci Web.

Przykłady używają interfejsu użytkownika, który [dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md) opisuje.

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

## <a name="cancel-a-task"></a>Anulowanie zadania

Pierwszy przykład kojarzy przycisk **Anuluj** z jednym zadaniem pobierania. Jeśli wybierzesz przycisk podczas pobierania zawartości przez aplikację, pobieranie zostanie anulowane.

### <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .

3. W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelATask,** a następnie wybierz pozycję **Ustaw jako projekt startup**.

5. Wybierz klawisz **F5,** aby uruchomić projekt (lub naciśnij klawisz **Ctrl**+**F5,** aby uruchomić projekt bez debugowania).

> [!TIP]
> Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Kompilowanie przykładu
 Poniższe zmiany dodają przycisk **Anuluj** do aplikacji, która pobiera witrynę sieci Web. Jeśli nie chcesz pobierać ani tworzyć przykładu, możesz przejrzeć produkt końcowy w sekcji "Pełne przykłady" na końcu tego tematu. Gwiazdki oznaczają zmiany w kodzie.

 Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **StarterCode** jako **projekt StartUp** zamiast **CancelATask**.

 Następnie dodaj następujące zmiany do pliku MainWindow.xaml.cs tego projektu.

1. Deklaruj `cts`zmienną, `CancellationTokenSource` która jest w zakresie dla wszystkich metod, które uzyskują do niej dostęp.

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Dodaj następujący program obsługi zdarzeń dla przycisku **Anuluj.** Program obsługi zdarzeń używa metody, <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> aby powiadomić, `cts` gdy użytkownik żąda anulowania.

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

3. W programie obsługi zdarzeń dla **Start** przycisku `startButton_Click`Start wprowadzono następujące zmiany.

    - Wystąpienia w ysłance `CancellationTokenSource`, `cts`.

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - W wywołaniu `AccessTheWebAsync`, który pobiera zawartość określonej strony internetowej, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> wyślij `cts` właściwość jako argument. Właściwość `Token` propaguje wiadomość, jeśli zażądano anulowania. Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik zdecyduje się anulować operację pobierania. Poniższy kod pokazuje zmiany.

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

4. W `AccessTheWebAsync`, <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> użyj przeciążenia `GetAsync` metody <xref:System.Net.Http.HttpClient> w typie, aby pobrać zawartość strony internetowej. Pass `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako drugi argument. Token niesie wiadomość, jeśli użytkownik wybierze przycisk **Anuluj.**

     Poniższy kod pokazuje zmiany `AccessTheWebAsync`w pliku .

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

5. Jeśli program nie zostanie anulowany, generuje następujące dane wyjściowe.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Jeśli wybierzesz przycisk **Anuluj** przed zakończeniem pobierania zawartości przez program, program wygeneruje następujące dane wyjściowe.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Anulowanie listy zadań

Można rozszerzyć poprzedni przykład, aby anulować wiele zadań, `CancellationTokenSource` kojarząc to samo wystąpienie z każdym zadaniem. Jeśli wybierzesz przycisk **Anuluj,** anulujesz wszystkie zadania, które nie zostały jeszcze ukończone.

### <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .

3. W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelAListOfTasks,** a następnie wybierz pozycję **Ustaw jako projekt StartUp**.

5. Wybierz klawisz **F5,** aby uruchomić projekt.

     Wybierz klawisze **Ctrl**+**F5,** aby uruchomić projekt bez debugowania go.

Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Kompilowanie przykładu

Aby samodzielnie rozszerzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **cancelatask** jako **projekt StartUp**. Dodaj następujące zmiany do tego projektu. Gwiazdki oznaczają zmiany w programie.

1. Dodaj metodę tworzenia listy adresów internetowych.

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

2. Wywołaj metodę `AccessTheWebAsync`w pliku .

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Dodaj następującą `AccessTheWebAsync` pętlę, aby przetworzyć każdy adres internetowy na liście.

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

4. Ponieważ `AccessTheWebAsync` wyświetla długości, metoda nie musi zwracać niczego. Usuń return instrukcji i zmienić typ zwracany <xref:System.Threading.Tasks.Task> metody <xref:System.Threading.Tasks.Task%601>zamiast .

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Wywołaj metodę `startButton_Click` z za pomocą instrukcji zamiast wyrażenia.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Jeśli program nie zostanie anulowany, generuje następujące dane wyjściowe.

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

     Jeśli wybierzesz przycisk **Anuluj** przed zakończeniem pobierania, dane wyjściowe zawierają długości pobierania, które zostały ukończone przed anulowaniem.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Kompletne przykłady

Poniższe sekcje zawierają kod dla każdego z poprzednich przykładów. Należy zauważyć, że należy <xref:System.Net.Http>dodać odwołanie do .

Możesz pobrać projekty z [próbki Async: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Przykład — anulowanie zadania

Poniższy kod jest kompletnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.

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

### <a name="example---cancel-a-list-of-tasks"></a>Przykład — anulowanie listy zadań

Poniższy kod jest kompletnym MainWindow.xaml.cs pliku dla przykładu, który anuluje listę zadań.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Przykład asynchronii: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
