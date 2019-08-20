---
title: Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 5237d82506da5e304a8f265feab7d7f3beaa45b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595689"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Anuluj pozostałe zadania asynchroniczne po zakończeniu jednego (C#)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody razem <xref:System.Threading.CancellationToken>z, można anulować wszystkie pozostałe zadania po zakończeniu jednego zadania. `WhenAny` Metoda przyjmuje argument, który jest kolekcją zadań. Metoda uruchamia wszystkie zadania i zwraca pojedyncze zadanie. Pojedyncze zadanie zostanie ukończone, gdy dowolne zadanie w kolekcji zostanie zakończone.  
  
 W tym przykładzie pokazano, jak używać tokenu anulowania w połączeniu z `WhenAny` do pierwszego zadania, aby zakończyć z kolekcji zadań i anulować pozostałe zadania. Każde zadanie pobiera zawartość witryny sieci Web. W przykładzie jest wyświetlana długość zawartości pierwszego pobrania, która zostanie zakończona, a pozostałe pliki do pobrania zostaną anulowane.  
  
> [!NOTE]
>  Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.  
  
1. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.  
  
3. W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningCS.  
  
4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterOneTask** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.  
  
5. Wybierz klawisz F5, aby uruchomić projekt.  
  
     Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.  
  
6. Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.  
  
 Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Kompilowanie przykładu  
 Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) w celu anulowania listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.  
  
 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.  
  
 W pliku MainWindow.XAML.cs projektu **CancelAListOfTasks** Rozpocznij przejście przez przeniesienie kroków przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do następującej metody asynchronicznej.  
  
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
  
 W `AccessTheWebAsync`programie w tym przykładzie używa się zapytania <xref:System.Linq.Enumerable.ToArray%2A> , metody i `WhenAny` metody w celu utworzenia i uruchomienia tablicy zadań. Aplikacja `WhenAny` do tablicy zwraca pojedyncze zadanie, które w oczekiwany sposób oblicza pierwsze zadanie, aby osiągnąć zakończenie w tablicy zadań.  
  
 Wprowadź następujące zmiany w programie `AccessTheWebAsync`. Gwiazdki oznaczają zmiany w pliku kodu.  
  
1. Skomentuj lub Usuń pętlę.  
  
2. Utwórz zapytanie, które po wykonaniu tworzy kolekcję zadań ogólnych. Każde wywołanie `ProcessURLAsync` zwraca element, <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3. Wywołaj `ToArray` , aby wykonać zapytanie i uruchomić zadania. Zastosowanie `WhenAny` metody w następnym kroku spowoduje wykonanie zapytania i uruchomienie zadań bez użycia `ToArray`, ale inne metody mogą nie być. Najbezpieczniejszym sposobem jest wymuszenie jawnie wykonywania zapytania.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4. Wywołaj `WhenAny` kolekcję zadań. `WhenAny``Task(Of Task(Of Integer))` zwraca lub .`Task<Task<int>>`  Oznacza to, `WhenAny` że zwraca zadanie, które zostanie obliczone na `Task(Of Integer)` jeden `Task<int>` lub w oczekiwany sposób. To pojedyncze zadanie to pierwsze zadanie w kolekcji, które ma zostać zakończone. Zadanie, które zostało zakończone jako pierwszy jest `firstFinishedTask`przypisane do. Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie jest`TResult` liczbącałkowitą,ponieważjest`ProcessURLAsync`typem zwracanym.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5. W tym przykładzie interesuje Cię tylko zadanie, które zakończy się w pierwszej kolejności. W związku z <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> tym Użyj, aby anulować pozostałe zadania.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6. Na koniec oczekiwanie `firstFinishedTask` na pobranie pobranej zawartości.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 Uruchom program kilka razy, aby sprawdzić, czy w pierwszej kolejności pliki do pobrania zostały zakończone.  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełnym plikiem MainWindow.xaml.cs dla przykładu. Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.  
  
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
- [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)
- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
- [Przykład asynchroniczny: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
