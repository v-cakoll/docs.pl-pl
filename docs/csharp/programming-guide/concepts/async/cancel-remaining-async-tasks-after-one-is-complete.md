---
title: Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 9b968ec902d9653caa410e917af40c8a521e55b4
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859619"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metoda wraz z <xref:System.Threading.CancellationToken>, możesz anulować wszystkie pozostałe zadania po wykonaniu jednego zadania. `WhenAny` Metoda przyjmuje argument, który jest kolekcją zadań. Metoda uruchamia wszystkie zadania i zwrócenie pojedynczego zadania. Pojedyncze zadanie jest ukończone po zakończeniu każdego zadania w kolekcji.  
  
 W tym przykładzie przedstawiono sposób użycia tokenu anulowania w połączeniu z `WhenAny` do przechowywania na pierwszym zadaniu do ukończenia zadań i anulowania pozostałych zadań. Każde zadanie powoduje pobieranie zawartości witryny sieci Web. Przykład wyświetla długość zawartości pierwszego pobieranego i anuluje inne pliki do pobrania.  
  
> [!NOTE]
>  Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [próbka asynchroniczna: Poprawnie Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.  
  
1. Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.  
  
3. W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **CancelAfterOneTask** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
5. Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6. Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
 Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Budowanie przykładu  
 W przykładzie w tym temacie dodaje do projektu utworzonego w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) umożliwiający anulowanie listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używany jawnie.  
  
 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.  
  
 W pliku MainWindow.xaml.cs **CancelAListOfTasks** projektu, uruchom przejścia przez przeniesienie kroków przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do metody asynchronicznej.  
  
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
  
 W `AccessTheWebAsync`, w tym przykładzie użyto zapytania, <xref:System.Linq.Enumerable.ToArray%2A> metody i `WhenAny` metodę, aby utworzyć i uruchomić szereg zadań. Stosowanie `WhenAny` do tablicy powoduje zwrócenie pojedynczego zadania, gdy jest oczekiwane, daje w wyniku pierwsze zadanie do wykonania w tablicy zadań.  
  
 Wprowadź następujące zmiany w `AccessTheWebAsync`. Gwiazdka oznacza zmiany w pliku kodu.  
  
1. Skomentuj lub usuń pętlę.  
  
2. Utwórz zapytanie, które, po wykonaniu, daje kolekcję zadań rodzajowych. Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Wywołaj `ToArray` do wykonywania zapytania i uruchomić zadania. Stosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez używania `ToArray`, ale niekoniecznie innych metod. Najbezpieczniejszym rozwiązaniem jest jawne wymuszenie wykonania zapytania.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Wywołaj `WhenAny` na kolekcji zadań. `WhenAny` Zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.  Oznacza to, że `WhenAny` zwraca klasę task, która ocenia do pojedynczego `Task(Of Integer)` lub `Task<int>` gdy jest oczekiwane. To pojedyncze zadanie jest pierwszym zadaniem w kolekcji, aby zakończyć. Przydzielono zadanie, które zostanie ukończone jako pierwsze `firstFinishedTask`. Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą, ponieważ jest to typ zwracany `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. W tym przykładzie interesuje Cię tylko zadanie, które zakończy się pierwsza. W związku z tym, użyj <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> anulować pozostałe zadania.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Na koniec await `firstFinishedTask` na pobranie długości pobranej zawartości.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
## <a name="complete-example"></a>Kompletny przykład  
 Następujący kod jest pełnym MainWindow.xaml.cs dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane w tym przykładzie.  
  
 Należy zauważyć, że musisz dodać odwołanie do <xref:System.Net.Http>.  
  
 Można ściągnąć projekt z [próbka asynchroniczna: Dostrajania aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
