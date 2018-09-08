---
title: Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)
ms.date: 07/20/2015
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: a23bdedbd9786fb930f92f5aa4b1025b83a4bcbe
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44222042"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich, po ich zakończeniu (C#)
Za pomocą <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, można uruchomić wiele zadań w tym samym czasie i przetwarzać je jedno po ich zakończeniu, zamiast przetwarzać je w kolejności, w którym są uruchamiane.  
  
 W poniższym przykładzie użyto zapytania, aby utworzyć kolekcję zadań. Każde zadanie powoduje pobieranie zawartości określonej witryny sieci Web. W każdej iteracji while oczekiwane wywołanie do pętli `WhenAny` zwraca zadanie w kolekcji zadań, którego pobieranie najpierw się zakończy. To zadanie jest usuwane z kolekcji i przetwarzane. Pętla powtarza, dopóki Kolekcja nie zawiera więcej zadań.  
  
> [!NOTE]
>  Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Można pobrać pełny projekt Windows Presentation Foundation (WPF) z [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a następnie wykonaj poniższe kroki.  
  
1.  Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (.sln) dla AsyncFineTuningCS.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **ProcessTasksAsTheyFinish** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klawisze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie pojawiają się zawsze w tej samej kolejności.  
  
 Jeśli nie chcesz wczytać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Budowanie przykładu  
 Ten przykład dodaje do kodu utworzonego w [anulowanie pozostałych zadań asynchronicznych po jednym jest pełny (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna](https://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) i używa tego samego interfejsu użytkownika.  
  
 Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykładu", ale wybierając **CancelAfterOneTask** jako **projekt startowy**. Dodaj zmiany w tym temacie, aby `AccessTheWebAsync` metody, w tym projekcie. Zmiany są oznaczone gwiazdkami.  
  
 **CancelAfterOneTask** projekt zawiera już zapytanie, którego wykonanie powoduje utworzenie kolekcji zadań. Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 W pliku MainWindow.xaml.cs w projekcie dokonaj następujących zmian do `AccessTheWebAsync` metody.  
  
-   Wykonanie zapytania przez zastosowanie <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   Dodaj chwilę pętli, która wykonuje następujące czynności dla każdego zadania w kolekcji.  
  
    1.  Czeka aby wywołanie `WhenAny` do zidentyfikowało pierwsze zadanie w kolekcji, aby zakończyć jego pobranie.  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  To zadanie usuwa z kolekcji.  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  Czeka na `firstFinishedTask`, który jest zwracany przez wywołanie `ProcessURLAsync`. `firstFinishedTask` Zmienna jest <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą. Zadanie zostało już ukończone, ale czeka na pobranie długości pobranej witryny sieci Web, co ilustruje poniższy przykład.  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 Należy uruchomić projekt kilka razy, aby sprawdzić, czy pobrane długości nie pojawiają się zawsze w tej samej kolejności.  
  
> [!CAUTION]
>  Możesz użyć `WhenAny` w pętli, jak opisano w przykładzie, aby rozwiązać problemy związane z małą liczbą zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań w celu przetworzenia. Aby uzyskać więcej informacji i przykładów, zobacz [zadania przetwarzania po ich zakończeniu](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).  
  
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
                    resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
            }  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
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
- [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
- [Próbka asynchroniczna: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
