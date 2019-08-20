---
title: Anulowanie zadań asynchronicznych po upływie czasu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: e00ff51e987275c6c84822f7095c82ed03b53176
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595760"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Anulowanie zadań asynchronicznych po upływie czasu (C#)

Istnieje możliwość anulowania operacji asynchronicznej po upływie okresu czasu przy użyciu <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, jeśli nie chcesz czekać na zakończenie operacji. Ta metoda służy do planowania anulowania wszystkich skojarzonych zadań, które nie zostały ukończone w okresie wyznaczonym przez `CancelAfter` wyrażenie.

Ten przykład dodaje do kodu, który został opracowany w wyniku [anulowania zadania asynchronicznego lub listy zadańC#()](./cancel-an-async-task-or-a-list-of-tasks.md) w celu pobrania listy witryn sieci Web i wyświetlenia długości zawartości każdej z nich.

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="download-the-example"></a>Pobierz przykład

Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.

1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku menu wybierz **plik** > **Otwórz** > **projekt/rozwiązanie**.

3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterTime** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.

5. Wybierz klawisz **F5** , aby uruchomić projekt. (Lub naciśnij klawisz **Ctrl**+**F5** , aby uruchomić projekt bez debugowania).

6. Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych.

Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.

## <a name="build-the-example"></a>Kompiluj przykład

Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) w celu anulowania listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.

Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.

Aby określić maksymalny czas, po jakim zadania są oznaczane jako anulowane, należy dodać `CancelAfter` wywołanie `startButton_Click`do, jak pokazano w poniższym przykładzie. Dodanie jest oznaczone gwiazdkami.

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

 Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych. Oto przykład danych wyjściowych.

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Pełny przykład

Poniższy kod jest pełnym tekstem pliku MainWindow.xaml.cs na przykład. Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.

Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.

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

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Przykład asynchroniczny: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
