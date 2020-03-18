---
title: Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: e829254c1cd47da16b14aa9c2c90312a97b4b581
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169977"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody wraz <xref:System.Threading.CancellationToken>z , można anulować wszystkie pozostałe zadania po zakończeniu jednego zadania. Metoda `WhenAny` przyjmuje argument, który jest zbiorem zadań. Metoda uruchamia wszystkie zadania i zwraca pojedyncze zadanie. Pojedyncze zadanie jest zakończone po zakończeniu dowolnego zadania w kolekcji.  
  
 W tym przykładzie pokazano, jak używać `WhenAny` tokenu anulowania w połączeniu z do przechowywania na pierwsze zadanie, aby zakończyć z kolekcji zadań i anulować pozostałe zadania. Każde zadanie pobiera zawartość witryny sieci Web. W przykładzie wyświetla długość zawartości pierwszego pobrania, aby zakończyć i anuluje inne pliki do pobrania.  
  
> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki Async: Dostrajanie aplikacji,](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj następujące kroki.  
  
1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz pozycję **Plik**, **Otwórz**, **Projekt/Rozwiązanie**.  
  
3. W oknie dialogowym **Otwieranie projektu** otwórz folder zawierający dekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln) dla asyncFineTuningCS.  
  
4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **CancelAfterOneTask,** a następnie wybierz pozycję **Ustaw jako projekt StartUp**.  
  
5. Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klawisze Ctrl+F5, aby uruchomić projekt bez debugowania go.  
  
6. Uruchom program kilka razy, aby sprawdzić, czy różne pliki do pobrania kończą się jako pierwsze.  
  
 Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Budowanie przykładu  
 Przykład w tym temacie dodaje do projektu, który został opracowany w [Anuluj zadanie asynchroniczne lub lista zadań (C#),](./cancel-an-async-task-or-a-list-of-tasks.md) aby anulować listę zadań. W przykładzie użyto tego samego interfejsu, chociaż przycisk **Anuluj** nie jest używany jawnie.  
  
 Aby samodzielnie utworzyć przykład, krok po kroku postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierz **cancelAlistoftasks** jako **projekt StartUp**. Dodaj zmiany w tym temacie do tego projektu.  
  
 W pliku MainWindow.xaml.cs projektu **CancelAListOfTasks** rozpocznij przejście, przenosząc kroki przetwarzania `AccessTheWebAsync` dla każdej witryny sieci Web z pętli do następującej metody asynchronicznej.  
  
```csharp  
// ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 W `AccessTheWebAsync`tym przykładzie użyto <xref:System.Linq.Enumerable.ToArray%2A> kwerendy, `WhenAny` metody i metody do tworzenia i uruchamiania tablicy zadań. Zastosowanie `WhenAny` do tablicy zwraca pojedyncze zadanie, które, gdy oczekuje, ocenia do pierwszego zadania, aby osiągnąć zakończenie w tablicy zadań.  
  
 W przewiń następujące zmiany w pliku `AccessTheWebAsync`. Gwiazdki oznaczają zmiany w pliku kodu.  
  
1. Skomentuj lub usuń pętlę.  
  
2. Utwórz kwerendę, która po wykonaniu tworzy kolekcję zadań ogólnych. Każde wywołanie <xref:System.Threading.Tasks.Task%601> zwraca `TResult` `ProcessURLAsync` where jest liczbą całkowitą.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Wywołanie, `ToArray` aby wykonać kwerendę i rozpocząć zadania. Zastosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie kwerendy i `ToArray`uruchomienie zadań bez użycia , ale inne metody mogą nie. Najbezpieczniejszą praktyką jest wymusić wykonanie kwerendy jawnie.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Wywołaj `WhenAny` kolekcję zadań. `WhenAny`zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.  Oznacza to, że zwraca zadanie, `WhenAny` `Task(Of Integer)` które `Task<int>` jest oceniane do jednego lub gdy jest oczekiwana. To pojedyncze zadanie jest pierwszym zadaniem w kolekcji do zakończenia. Zadanie, które zostało ukończone `firstFinishedTask`jako pierwsze, jest przypisane do pliku . Typ `firstFinishedTask` jest, <xref:System.Threading.Tasks.Task%601> `TResult` gdzie jest liczbą całkowitą, ponieważ `ProcessURLAsync`jest to typ zwracany .  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. W tym przykładzie jesteś zainteresowany tylko zadanie, które kończy się jako pierwsze. W związku <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> z tym należy anulować pozostałe zadania.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Na koniec `firstFinishedTask` poczekaj, aby pobrać długość pobranej zawartości.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Uruchom program kilka razy, aby sprawdzić, czy różne pliki do pobrania kończą się jako pierwsze.  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest kompletnym plikiem MainWindow.xaml.cs dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.  
  
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
  
namespace CancelAfterOneTask  
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
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
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
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.
            //    // Argument ct carries the message if the Cancel button is chosen.
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
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
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Przykład asynchronii: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
