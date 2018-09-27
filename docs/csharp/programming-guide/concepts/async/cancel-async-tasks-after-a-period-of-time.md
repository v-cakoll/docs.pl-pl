---
title: Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: b95b87e1e93a9c8f8c74680a917a128d45172ed5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397348"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)

Możesz anulować operację asynchroniczną po upływie pewnego czasu za pomocą <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, jeśli nie chcesz czekać na zakończenie operacji. Ta metoda planuje anulowanie skojarzonych zadań, które nie są ukończone przed upływem czasu, który jest wyznaczone przez `CancelAfter` wyrażenia.

Ten przykład dodaje do kodu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) można pobrać listy witryn sieci Web i wyświetlającym długość zawartości każdej z nich.

> [!NOTE]
> Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.

## <a name="download-the-example"></a>Pobierz przykład

Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.

1.  Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.

2.  Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.

3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.

4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAfterTime** projektu, a następnie wybierz **Ustaw jako projekt startowy**.

5.  Wybierz **F5** klawisz, aby uruchomić projekt. (Lub naciśnij **Ctrl**+**F5** uruchomić projekt bez debugowania go).

6.  Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe są pokazywane dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web.

Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.

## <a name="build-the-example"></a>Budowanie przykładu

W przykładzie w tym temacie dodaje do projektu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) umożliwiający anulowanie listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używany jawnie.

Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.

Aby określić maksymalny czas, zanim zadania są oznaczane jako anulowane, należy dodać wywołanie `CancelAfter` do `startButton_Click`, jak pokazano w poniższym przykładzie. Dodatek jest oznaczony gwiazdkami.

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

 Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe są pokazywane dla wszystkich witryn sieci Web, witryn sieci Web lub niektórych witryn sieci web. Poniższe dane wyjściowe są przykładowe.

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Kompletny przykład

Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.cs dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.

Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.

Można ściągnąć projekt z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/ee256749.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
