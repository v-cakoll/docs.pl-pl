---
title: Anulowanie zadania asynchronicznego lub listy zadań (C#)
ms.date: 07/20/2015
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 93526f772f79e993767fd8f29087b6caf4e29468
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595720"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a>Anulowanie zadania asynchronicznego lub listy zadań (C#)

Można skonfigurować przycisk, którego można użyć do anulowania aplikacji asynchronicznej, jeśli nie chcesz czekać na jej zakończenie. Postępując zgodnie z przykładami w tym temacie, można dodać przycisk anulowania do aplikacji pobierającej zawartość jednej witryny sieci Web lub listy witryn sieci Web.

W przykładach użyto interfejsu użytkownika, który [dostraja aplikację asynchroniczną (C#)](./fine-tuning-your-async-application.md) .

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="cancel-a-task"></a>Anulowanie zadania

Pierwszy przykład kojarzy przycisk **Anuluj** z pojedynczym zadaniem pobierania. Jeśli wybierzesz przycisk podczas pobierania zawartości przez aplikację, pobieranie zostanie anulowane.

### <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelATask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz **F5** , aby uruchomić projekt (lub naciśnij klawisz **Ctrl**+**F5** , aby uruchomić projekt bez debugowania).

> [!TIP]
> Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Kompiluj przykład
 Następujące zmiany umożliwiają dodanie przycisku **Anuluj** do aplikacji, która pobiera witrynę sieci Web. Jeśli nie chcesz pobierać ani kompilować przykładu, możesz przejrzeć końcowy produkt w sekcji "kompletne przykłady" na końcu tego tematu. Gwiazdki oznaczają zmiany w kodzie.

 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **StarterCode** jako **projekt startowy** , a nie **CancelATask**.

 Następnie Dodaj następujące zmiany do pliku MainWindow.xaml.cs tego projektu.

1. Zadeklaruj `cts`zmienną, która znajduje się w zakresie dla wszystkich metod, które mają do niego dostęp. `CancellationTokenSource`

    ```csharp
    public partial class MainWindow : Window
    {
        // ***Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. Dodaj następujący program obsługi zdarzeń dla przycisku **Anuluj** . Procedura obsługi zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metody do powiadamiania `cts` , gdy użytkownik zażąda anulowania.

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

3. Wprowadź następujące zmiany w obsłudze zdarzeń dla przycisku `startButton_Click` **Start** .

    - Utwórz wystąpienie obiektu `cts`,. `CancellationTokenSource`

        ```csharp
        // ***Instantiate the CancellationTokenSource.
        cts = new CancellationTokenSource();
        ```

    - W wywołaniu `AccessTheWebAsync`elementu, który pobiera zawartość określonej witryny sieci Web, <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> Wyślij Właściwość `cts` jako argument. `Token` Właściwość propaguje komunikat w przypadku żądania anulowania. Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik zdecyduje się anulować operację pobierania. Poniższy kod przedstawia zmiany.

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

4. W `AccessTheWebAsync`programie <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> Użyj przeciążenia`GetAsync` metody w<xref:System.Net.Http.HttpClient> typie, aby pobrać zawartość witryny sieci Web. Pass `ct` ,parametr`AccessTheWebAsync`,jakodrugiargument. <xref:System.Threading.CancellationToken> Token przenosi komunikat, jeśli użytkownik wybierze przycisk **Anuluj** .

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

5. Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe.

    ```text
    Ready to download.
    Length of the downloaded string: 158125.
    ```

     Jeśli wybierzesz przycisk **Anuluj** , zanim program zakończy pobieranie zawartości, program generuje następujące dane wyjściowe.

    ```text
    Ready to download.
    Download canceled.
    ```

## <a name="cancel-a-list-of-tasks"></a>Anulowanie listy zadań

Możesz poszerzyć poprzedni przykład, aby anulować wiele zadań, kojarząc to samo `CancellationTokenSource` wystąpienie z każdym zadaniem. Jeśli wybierzesz przycisk **Anuluj** , anulujesz wszystkie zadania, które nie zostały jeszcze ukończone.

### <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAListOfTasks** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz **F5** , aby uruchomić projekt.

     Wybierz **klawisz Ctrl**+**F5** , aby uruchomić projekt bez debugowania.

Jeśli nie chcesz pobierać projektu, możesz przejrzeć pliki MainWindow.xaml.cs na końcu tego tematu.

### <a name="build-the-example"></a>Kompiluj przykład

Aby poszerzyć przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelATask** jako **projekt startowy**. Dodaj następujące zmiany do tego projektu. Gwiazdki oznaczają zmiany w programie.

1. Dodaj metodę, aby utworzyć listę adresów sieci Web.

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

2. Wywołaj metodę w `AccessTheWebAsync`.

    ```csharp
    // ***Call SetUpURLList to make a list of web addresses.
    List<string> urlList = SetUpURLList();
    ```

3. Dodaj następującą pętlę w `AccessTheWebAsync` programie, aby przetwarzać poszczególne adresy sieci Web na liście.

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

4. Ponieważ `AccessTheWebAsync` wyświetla długości, metoda nie musi zwracać żadnych elementów. Usuń instrukcję return i Zmień zwracany typ metody na <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>zamiast.

    ```csharp
    async Task AccessTheWebAsync(CancellationToken ct)
    ```

     Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.

    ```csharp
    await AccessTheWebAsync(cts.Token);
    ```

5. Jeśli nie anulujesz programu, program generuje następujące dane wyjściowe.

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

     Jeśli wybierzesz przycisk **Anuluj** przed ukończeniem pobierania, dane wyjściowe zawierają długości plików do pobrania, które zakończyły się przed anulowaniem.

    ```text
    Length of the downloaded string: 35939.

    Length of the downloaded string: 237682.

    Length of the downloaded string: 128607.

    Downloads canceled.
    ```

## <a name="complete-examples"></a>Kompletne przykłady

Poniższe sekcje zawierają kod dla każdego z powyższych przykładów. Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.

Możesz pobrać projekty z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

### <a name="example---cancel-a-task"></a>Przykład — anulowanie zadania

Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje pojedyncze zadanie.

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

Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu, który anuluje listę zadań.

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
- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Przykład asynchroniczny: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
