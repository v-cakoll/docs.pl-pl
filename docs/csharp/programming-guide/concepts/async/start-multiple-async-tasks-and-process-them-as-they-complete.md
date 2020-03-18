---
title: Przetwarzanie zadań asynchronicznych po ich zakończeniu
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: b618fd6bf80551231d2b285fd0e8aef688d00d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "71736728"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Uruchom wiele zadań asynchronicznych i przetwarzaj je po ich ukończeniu (C#)

Za <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>pomocą , można uruchomić wiele zadań w tym samym czasie i przetwarzać je jeden po drugim, ponieważ są one zakończone, a nie przetwarzać je w kolejności, w jakiej są uruchamiane.

W poniższym przykładzie użyto kwerendy do utworzenia kolekcji zadań. Każde zadanie pobiera zawartość określonej witryny sieci Web. W każdej iteracji pętli while oczekiwane wywołanie zwraca `WhenAny` zadanie w kolekcji zadań, które kończy pobieranie jako pierwsze. To zadanie zostanie usunięte z kolekcji i przetworzone. Pętla powtarza się, dopóki kolekcja nie zawiera więcej zadań.

> [!NOTE]
> Aby uruchomić przykłady, na komputerze musi być zainstalowany program Visual Studio (2012 lub nowszy) oraz program .NET Framework 4.5 lub nowszy.

## <a name="download-an-example-solution"></a>Pobierz przykładowe rozwiązanie

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.

> [!TIP]
> Jeśli nie chcesz pobierać projektu, możesz przejrzeć *plik MainWindow.xaml.cs* na końcu tego tematu.

1. Wyodrębnij pliki pobrane z pliku *zip,* a następnie uruchom program Visual Studio.

2. Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .

3. W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający pobrany przykładowy kod, a następnie otwórz plik rozwiązania *(sln)* dla *asyncFineTuningCS*/*AsyncFineTuningVB*.

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **ProcessTasksAsTheyFinish,** a następnie wybierz pozycję **Ustaw jako projekt startup**.

5. Wybierz klawisz <kbd>F5,</kbd> aby uruchomić program z debugowaniem, lub naciśnij klawisze <kbd>Ctrl</kbd>+<kbd>F5,</kbd> aby uruchomić program bez debugowania.

6. Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.

## <a name="create-the-program-yourself"></a>Samodzielnie stwórz program

W tym przykładzie dodaje do kodu, który został opracowany w [Anuluj pozostałe zadania asynchroniczne po one is complete (C#)](cancel-remaining-async-tasks-after-one-is-complete.md)i używa tego samego interfejsu.

Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w [sekcji Pobieranie przykładu,](cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) ale ustaw **CancelAfterOneTask** jako projekt startowy. Dodaj zmiany w tym `AccessTheWebAsync` temacie do metody w tym projekcie. Zmiany są oznaczone gwiazdkami.

**Projekt CancelAfterOneTask** zawiera już kwerendę, która po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w następującym <xref:System.Threading.Tasks.Task%601>kodzie zwraca , gdzie `TResult` jest liczbą całkowitą:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

W *MainWindow.xaml.cs* pliku projektu należy wprowadzić następujące `AccessTheWebAsync` zmiany w metodzie:

- Wykonaj kwerendę, <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> stosując <xref:System.Linq.Enumerable.ToArray%2A>zamiast .

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- Dodaj `while` pętlę, która wykonuje następujące kroki dla każdego zadania w kolekcji:

    1. Oczekuje na wywołanie, aby `WhenAny` zidentyfikować pierwsze zadanie w kolekcji, aby zakończyć jego pobieranie.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Usuwa to zadanie z kolekcji.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. Oczekuje `firstFinishedTask`, który jest zwracany `ProcessURLAsync`przez połączenie . Zmienna `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> `TReturn` where jest liczbą całkowitą. Zadanie zostało już ukończone, ale oczekujesz na to, aby pobrać długość pobranej witryny sieci Web, jak pokazano w poniższym przykładzie. Jeśli zadanie jest `await` uszkodzony, spowoduje zgłosić pierwszy wyjątek `AggregateException`podrzędne `Result` przechowywane w `AggregateException`, w przeciwieństwie do czytania właściwości, które wyrzucając .

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

Uruchom program kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.

> [!CAUTION]
> Można użyć `WhenAny` w pętli, zgodnie z opisem w przykładzie, aby rozwiązać problemy, które obejmują niewielką liczbę zadań. Jednak inne podejścia są bardziej efektywne, jeśli masz dużą liczbę zadań do przetworzenia. Aby uzyskać więcej informacji i przykładów, zobacz [Przetwarzanie zadań po ich zakończeniu](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Kompletny przykład

Poniższy kod jest kompletnym tekstem *pliku MainWindow.xaml.cs* dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie. Należy również pamiętać, że należy <xref:System.Net.Http>dodać odwołanie do .

Możesz pobrać projekt z [próbki Async: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

// Add the following using directive.
using System.Threading;

namespace ProcessTasksAsTheyFinish
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
            resultsTextBox.Clear();

            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            try
            {
                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Create a query that, when executed, returns a collection of tasks.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURL(url, client, ct);

            // ***Use ToList to execute the query and start the tasks.
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

            // ***Add a loop to process the tasks one at a time until none remain.
            while (downloadTasks.Count > 0)
            {
                    // Identify the first task that completes.
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);

                    // ***Remove the selected task from the list so that you don't
                    // process it more than once.
                    downloadTasks.Remove(firstFinishedTask);

                    // Await the completed task.
                    int length = await firstFinishedTask;
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)
        {
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            return urlContents.Length;
        }
    }
}

// Sample Output:

// Length of the download:  226093
// Length of the download:  412588
// Length of the download:  175490
// Length of the download:  204890
// Length of the download:  158855
// Length of the download:  145790
// Length of the download:  44908
// Downloads complete.
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronicznej (C#)](fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z async i await (C#)](index.md)
- [Przykład asynchronii: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
