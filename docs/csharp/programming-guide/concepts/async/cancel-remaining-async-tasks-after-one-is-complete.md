---
title: "Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5e1a899223d0f6d15e6851c9320275bafe876118
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a>Anulowanie pozostałych zadań asynchronicznych po jednym jest pełna (C#)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> metody razem z <xref:System.Threading.CancellationToken>, możesz anulować wszystkie pozostałe zadania po zakończeniu zadania. `WhenAny` Metoda przyjmuje argument, który jest kolekcji zadań. Metoda uruchamiania wszystkich zadań i zwraca jedno zadanie. Pojedyncze zadanie zakończeniu po ukończeniu zadań w kolekcji.  
  
 W tym przykładzie pokazano, jak używać w połączeniu z tokenem anulowania `WhenAny` do przechowywania na pierwszym zadaniem Zakończ z kolekcji zadań i anulowanie pozostałych zadań. Każde zadanie pobiera zawartość witryny sieci Web. W przykładzie wyświetla długość zawartości pierwsza z nich do wykonania i anuluje inne pliki do pobrania.  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj następujące kroki.  
  
1.  Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningCS.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **CancelAfterOneTask** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
 Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Tworzenie w przykładzie  
 W przykładzie w tym temacie jest dodawany do projektu, który został napisany w [anulowanie zadania asynchronicznego lub listy zadań (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) anulować listy zadań. W przykładzie użyto tego samego interfejsu użytkownika, mimo że **anulować** przycisk nie jest używana jawnie.  
  
 Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAListOfTasks** jako **projekt startowy**. Dodaj zmiany w tym temacie do tego projektu.  
  
 W pliku MainWindow.xaml.cs **CancelAListOfTasks** projekt, uruchom przejście przez przeniesienie kroki przetwarzania dla każdej witryny sieci Web z pętli w `AccessTheWebAsync` do następującej metody asynchronicznej.  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 W `AccessTheWebAsync`, w tym przykładzie użyto kwerendy, <xref:System.Linq.Enumerable.ToArray%2A> metody i `WhenAny` metodę, aby utworzyć i uruchomić tablicy zadań. Stosowanie `WhenAny` do tablicy zwraca pojedyncze zadanie, gdy oczekiwane, daje w wyniku pierwszego zadania do wykonania w tablicy zadań.  
  
 Wprowadź następujące zmiany w `AccessTheWebAsync`. Gwiazdki oznaczyć zmiany w pliku kodu.  
  
1.  Komentarz lub usunąć pętli.  
  
2.  Utwórz kwerendę, która po wykonaniu tworzy kolekcję ogólnych zadań. Każde wywołanie `ProcessURLAsync` zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  Wywołanie `ToArray` do wykonania zapytania i uruchamiania zadań. Stosowanie `WhenAny` metody w następnym kroku może wykonać zapytania i uruchomić zadania bez użycia `ToArray`, ale inne metody nie mogą. Najbezpieczniejszym rozwiązaniem jest jawnie wymusić wykonywania zapytania.  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  Wywołanie `WhenAny` w kolekcji zadań. `WhenAny` Zwraca `Task(Of Task(Of Integer))` lub `Task<Task<int>>`.  Oznacza to `WhenAny` zwraca zadanie, które ocenia pojedynczej `Task(Of Integer)` lub `Task<int>` po jest oczekiwane. Jednego zadania jest pierwszym zadaniem w kolekcji, aby zakończyć. Zadanie, które zostało zakończone najpierw jest przypisany do `firstFinishedTask`. Typ `firstFinishedTask` jest <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą, ponieważ jest to typ zwracany `ProcessURLAsync`.  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  W tym przykładzie interesuje Cię tylko zadania, które kończy najpierw. Dlatego należy używać <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> na anulowanie pozostałych zadań.  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  Na koniec await `firstFinishedTask` można pobrać długości pobieranej zawartości.  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
    ```  
  
 Uruchom program kilka razy, aby sprawdzić, najpierw Zakończ różne pliki do pobrania.  
  
## <a name="complete-example"></a>Kompletny przykład  
 Poniższy kod jest pełny plik MainWindow.xaml.cs dla przykładu. Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.  
  
 Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.  
  
 Można pobrać projektu z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
            //        String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
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
            resultsTextBox.Text += String.Format("\r\nLength of the downloaded website:  {0}\r\n", length);  
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
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
