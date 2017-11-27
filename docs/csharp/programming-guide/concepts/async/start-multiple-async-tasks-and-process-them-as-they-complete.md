---
title: "Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bf70bd5e79e962d8edaea2dc037f191707f4e047
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a>Rozpoczynanie wielu zadań asynchronicznych i przetwarzanie ich w chwili zakończenia (C#)
Przy użyciu <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, można uruchomić wielu zadań jednocześnie i je jeden po drugim Przetwarzaj one jest ukończona, a nie ich przetworzyć w kolejności, w którym jest uruchomiona.  
  
 W poniższym przykładzie użyto zapytania, aby utworzyć kolekcję zadań. Każde zadanie pobiera zawartość z określonej witryny sieci Web. W każdej iteracji chwilę pętli, oczekiwano wywołania `WhenAny` zwraca zadanie w kolekcji zadań najpierw zakończy jej pobierania. To zadanie jest usunięty z kolekcji i przetwarzane. Pętla jest powtarzany do momentu Kolekcja nie zawiera więcej zadań.  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
## <a name="downloading-the-example"></a>Pobieranie przykładu  
 Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046) , a następnie wykonaj następujące kroki.  
  
1.  Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningCS.  
  
4.  W **Eksploratora rozwiązań**, otwórz menu skrótów **ProcessTasksAsTheyFinish** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.  
  
5.  Wybierz klawisz F5, aby uruchomić projekt.  
  
     Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.  
  
6.  Uruchom projekt kilka razy, aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności.  
  
 Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.cs na końcu tego tematu.  
  
## <a name="building-the-example"></a>Tworzenie w przykładzie  
 W tym przykładzie dodaje kod, który został napisany w [anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)[anulowanie pozostałych zadań asynchronicznych po jednym jest kompletna](http://msdn.microsoft.com/library/8e800b58-235a-44b7-a02c-fa4375591d76) i używa tego samego interfejsu użytkownika.  
  
 Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **CancelAfterOneTask** jako **projekt startowy**. Dodaj zmiany w tym temacie umożliwiają `AccessTheWebAsync` metody w tym projekcie. Zmiany są oznaczone gwiazdki.  
  
 **CancelAfterOneTask** Projekt już zawiera zapytanie, które po wykonaniu tworzy kolekcję zadań. Każde wywołanie `ProcessURLAsync` w poniższym kodzie zwraca <xref:System.Threading.Tasks.Task%601> gdzie `TResult` jest liczbą całkowitą.  
  
```csharp  
IEnumerable<Task<int>> downloadTasksQuery =  
    from url in urlList select ProcessURL(url, client, ct);  
```  
  
 W pliku MainWindow.xaml.cs projektu, wprowadź następujące zmiany do `AccessTheWebAsync` metody.  
  
-   Wykonanie kwerendy, stosując <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> zamiast <xref:System.Linq.Enumerable.ToArray%2A>.  
  
    ```csharp  
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();  
    ```  
  
-   Dodaj chwilę pętli, które wykonuje następujące czynności dla każdego zadania w kolekcji.  
  
    1.  Oczekujące na wywołanie `WhenAny` do identyfikowania pierwszego zadania w kolekcji, aby zakończyć jej pobierania.  
  
        ```csharp  
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
        ```  
  
    2.  To zadanie usuwa z kolekcji.  
  
        ```csharp  
        downloadTasks.Remove(firstFinishedTask);  
        ```  
  
    3.  Oczekujące na `firstFinishedTask`, który jest zwracany przez wywołanie do `ProcessURLAsync`. `firstFinishedTask` Zmienna jest <xref:System.Threading.Tasks.Task%601> gdzie `TReturn` jest liczbą całkowitą. Zadanie zostało już ukończone, ale należy poczekać na można pobrać długości pobrany witryny sieci Web, jak przedstawiono na poniższym przykładzie.  
  
        ```csharp  
        int length = await firstFinishedTask;  
        resultsTextBox.Text += String.Format("\r\nLength of the download:  {0}", length);  
        ```  
  
 Aby sprawdzić, czy pobrane długości nie zawsze są wyświetlane w tej samej kolejności należy uruchomić kilka razy projektu.  
  
> [!CAUTION]
>  Można użyć `WhenAny` w pętli, zgodnie z opisem w tym przykładzie, aby rozwiązać problemy z działaniem niewielkiej liczby zadań. Jednak inne podejścia są bardziej wydajne, jeśli masz dużą liczbę zadań w celu przetworzenia. Aby uzyskać dodatkowe informacje i przykłady, zobacz [przetwarzania zadań jako zakończenie](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## <a name="complete-example"></a>Kompletny przykład  
 Następujący kod jest pełny tekst pliku MainWindow.xaml.cs dla przykładu. Gwiazdki Oznacz elementy, które zostały dodane w tym przykładzie.  
  
 Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.  
  
 Można pobrać projektu z [próbki Async: poprawnie dostrajanie Twoja aplikacja](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
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
 <xref:System.Threading.Tasks.Task.WhenAny%2A>  
 [Dostrajanie aplikacji Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Próbka asynchronicznych: Dostrajanie aplikacji dokładnej](http://go.microsoft.com/fwlink/?LinkId=255046)
