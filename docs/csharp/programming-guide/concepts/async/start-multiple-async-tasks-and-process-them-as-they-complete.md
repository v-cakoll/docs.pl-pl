---
title: Przetwarzaj zadania asynchroniczne po ich zakończeniu
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: 35b4e42d7da5b8bc9069083ffc47d990bcb637a8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595594"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ichC#ukończenia ()

Korzystając z <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>programu, można uruchomić wiele zadań w tym samym czasie i przetworzyć je w taki sposób, aby były wykonywane, a nie przetwarzane w kolejności, w której są uruchamiane.

Poniższy przykład używa zapytania, aby utworzyć kolekcję zadań. Każde zadanie pobiera zawartość określonej witryny sieci Web. W każdej iteracji pętli while oczekiwane wywołanie `WhenAny` zwraca zadanie w kolekcji zadań, które kończą najpierw pobieranie. To zadanie jest usuwane z kolekcji i przetwarzane. Pętla powtarza się, dopóki kolekcja nie będzie zawierać żadnych zadań.

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio (2012 lub nowszy) oraz .NET Framework 4,5 lub nowszy.

## <a name="download-an-example-solution"></a>Pobierz przykładowe rozwiązanie

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

> [!TIP]
> Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.

1. Wyodrębnij pobrane pliki z pliku zip, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się pobrany przykładowy kod, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **ProcessTasksAsTheyFinish** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz **F5** , aby uruchomić program (lub naciśnij klawisz **Ctrl**+**F5** , aby uruchomić program bez debugowania).

6. Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.

## <a name="create-the-program-yourself"></a>Samodzielne tworzenie programu

Ten przykład dodaje do kodu, który został opracowany w polu [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)i używa tego samego interfejsu użytkownika.

Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami podanymi w sekcji [pobieranie przykładu](./cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) , ale ustaw **CancelAfterOneTask** jako projekt startowy. Dodaj zmiany w tym temacie do `AccessTheWebAsync` metody w tym projekcie. Zmiany są oznaczone gwiazdkami.

Projekt **CancelAfterOneTask** zawiera już zapytanie, które po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca a <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest liczbą całkowitą:

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

W pliku MainWindow.XAML.cs projektu wprowadź następujące zmiany `AccessTheWebAsync` w metodzie.

- Wykonaj zapytanie, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> <xref:System.Linq.Enumerable.ToArray%2A>zamiast.

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

- `while` Dodaj pętlę, która wykonuje następujące kroki dla każdego zadania w kolekcji:

    1. Oczekuje na wywołanie `WhenAny` do zidentyfikowania pierwszego zadania w kolekcji, aby zakończyć jego pobieranie.

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2. Usuwa to zadanie z kolekcji.

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3. Czeka, który jest zwracany przez `ProcessURLAsync`wywołanie metody. `firstFinishedTask` `firstFinishedTask` Zmienna togdzie`TReturn`jestliczbącałkowitą. <xref:System.Threading.Tasks.Task%601> Zadanie zostało już ukończone, ale czeka na pobranie długości pobranej witryny sieci Web, jak pokazano w poniższym przykładzie.

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

Uruchom program kilka razy, aby sprawdzić, czy pobrane długości nie zawsze pojawiają się w tej samej kolejności.

> [!CAUTION]
> Można użyć `WhenAny` w pętli, jak opisano w przykładzie, w celu rozwiązania problemów obejmujących niewielką liczbę zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań do przetworzenia. Aby uzyskać więcej informacji i przykładów, zobacz [Przetwarzanie zadań po ich zakończeniu](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).

## <a name="complete-example"></a>Pełny przykład

Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.cs na przykład. Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu. Należy również pamiętać, że należy dodać odwołanie do <xref:System.Net.Http>.

Możesz pobrać projekt z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
- [Przykład asynchroniczny: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
