---
title: Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204334"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Anulowanie zadań asynchronicznych po pewnym czasie (C#)

Operację asynchroniczną można anulować po pewnym <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> czasie, używając metody, jeśli nie chcesz czekać na zakończenie operacji. Ta metoda planuje anulowanie wszelkich skojarzonych zadań, które nie zostały ukończone `CancelAfter` w okresie określonym przez wyrażenie.

W tym przykładzie dodaje do kodu, który został opracowany w [Anuluj zadanie asynchroniczne lub lista zadań (C#),](./cancel-an-async-task-or-a-list-of-tasks.md) aby pobrać listę witryn sieci Web i wyświetlić długość zawartości każdego z nich.

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

## <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .

3. W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelAfterTime,** a następnie wybierz pozycję **Ustaw jako projekt StartUp**.

5. Wybierz klawisz **F5,** aby uruchomić projekt. (Lub naciśnij **klawisz Ctrl**+**F5,** aby uruchomić projekt bez debugowania).

6. Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą wyświetlać dane wyjściowe dla wszystkich witryn sieci Web, żadnych witryn sieci Web lub niektórych witryn sieci Web.

Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.

## <a name="build-the-example"></a>Kompilowanie przykładu

Przykład w tym temacie dodaje do projektu, który został opracowany w [Anuluj zadanie asynchroniczne lub lista zadań (C#),](./cancel-an-async-task-or-a-list-of-tasks.md) aby anulować listę zadań. W przykładzie użyto tego samego interfejsu, chociaż przycisk **Anuluj** nie jest używany jawnie.

Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **cancelAlistoftasks** jako **projekt StartUp**. Dodaj zmiany w tym temacie do tego projektu.

Aby określić maksymalny czas, zanim zadania zostaną oznaczone jako `CancelAfter` `startButton_Click`anulowane, dodaj wywołanie do , jak pokazano w poniższym przykładzie. Dodatek jest oznaczony gwiazdkami.

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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
```

 Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą wyświetlać dane wyjściowe dla wszystkich witryn sieci Web, żadnych witryn sieci Web lub niektórych witryn sieci Web. Następujące dane wyjściowe są próbką.

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Kompletny przykład

Poniższy kod jest kompletnym tekstem MainWindow.xaml.cs pliku dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.

Należy zauważyć, że należy <xref:System.Net.Http>dodać odwołanie do .

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

namespace CancelAfterTime
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
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
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

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Przykład asynchronii: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
