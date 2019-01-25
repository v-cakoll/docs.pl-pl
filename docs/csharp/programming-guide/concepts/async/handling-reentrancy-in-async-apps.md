---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 9c00a857fd75a44a00781e43b94623f101c7d352
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620440"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)
Po dołączeniu asynchronicznego kodu w aplikacji należy wziąć pod uwagę i ewentualnie zapobiec współużytkowaniu wątkowości, która odwołuje się do ponownego wprowadzania operacji asynchronicznej, zanim została ukończona. Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.  
  
 **W tym temacie**  
  
-   [Uznawanie współużytkowania wątkowości](#BKMK_RecognizingReentrancy)  
  
-   [Obsługa współużytkowania wątkowości](#BKMK_HandlingReentrancy)  
  
    -   [Wyłącz przycisk Start](#BKMK_DisableTheStartButton)  
  
    -   [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart)  
  
    -   [Uruchom wiele operacji i Zakolejkuj dane wyjściowe](#BKMK_RunMultipleOperations)  
  
-   [Przeglądanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
##  <a name="BKMK_RecognizingReentrancy"></a> Uznawanie współużytkowania wątkowości  
 W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchroniczną aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które są pobierane. Synchroniczna wersja przykładu reaguje w taki sam sposób, bez względu ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątek interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się uruchamianie aplikacji. W asynchronicznej aplikacji jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i można ponownie wprowadzić operację asynchroniczną przed jego ukończeniem.  
  
 Poniższy przykład ukazuje oczekiwane dane wyjściowe, jeśli użytkownik wybierze **Start** przycisk tylko raz. Zostanie wyświetlona lista pobranych stron internetowych z rozmiar, w bajtach, w każdej lokacji. Całkowita liczba bajtów pojawia się na końcu.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Jednak jeśli użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany kilkakrotnie i proces pobierania jest ponownie inicjowany każdorazowo. W rezultacie kilka operacji asynchronicznych jest uruchomionych w tym samym czasie, dane wyjściowe przeplatają wyniki i całkowita liczba bajtów jest myląca ze.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Możesz przejrzeć kod, który generuje te dane wyjściowe przewijając do końca tego tematu. Możesz eksperymentować z kodem pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload, lub za pomocą kodu na końcu tego tematu, aby utworzyć własny projekt. Aby uzyskać więcej informacji oraz instrukcje, zobacz [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample).  
  
##  <a name="BKMK_HandlingReentrancy"></a> Obsługa współużytkowania wątkowości  
 Może obsługiwać współużytkowanie wątkowości na wiele sposobów, w zależności od tego, co ma robić Twoja aplikacja. Ten temat przedstawia następujące przykłady:  
  
-   [Wyłącz przycisk Start](#BKMK_DisableTheStartButton)  
  
     Wyłącz **Start** przycisku, gdy operacja jest uruchomiony, dzięki czemu użytkownik nie mógł jej przerwać.  
  
-   [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart)  
  
     Anulować wszelkie operacje, które wciąż działają, gdy użytkownik wybierze **Start** ponownie przycisk, a następnie kontynuuj umożliwiają niedawno żądanej operacji.  
  
-   [Uruchom wiele operacji i Zakolejkuj dane wyjściowe](#BKMK_RunMultipleOperations)  
  
     Zezwalaj wszystkim wymaganym operacjom na uruchamianie asynchronicznie, ale Koordynuj dane wyjściowe, tak aby wyniki z każdej operacji były wyświetlane razem i w kolejności.  
  
###  <a name="BKMK_DisableTheStartButton"></a> Wyłącz przycisk Start  
 Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku u góry `StartButton_Click` programu obsługi zdarzeń. Następnie możesz ponownie włączyć przycisk od wewnątrz `finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą uruchamiać aplikację ponownie.  
  
 Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [próbki asynchroniczne: Współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to DisableStartButton.  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 W wyniku zmian przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobiera strony internetowe, dzięki czemu nie trzeba ponownie wprowadzić ten proces.  
  
###  <a name="BKMK_CancelAndRestart"></a> Anuluj i ponownie uruchom operację  
 Zamiast wyłączać **Start** przycisku możesz zachować aktywny przycisk, ale, jeśli użytkownik wybierze ten przycisk ponownie, Anuluj operację, która jest już uruchomiona i umożliwić kontynuowanie operacji ostatnio rozpoczętej.  
  
 Aby uzyskać więcej informacji dotyczących anulowania, zobacz [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [próbki asynchroniczne: Współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to CancelAndRestart.  
  
1.  Zadeklaruj <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  W `StartButton_Click`, określić, czy operacja jest już w toku. Jeśli wartość `cts` jest wartość null, operacja nie jest już aktywny. Jeśli wartość nie jest null, operacja, która jest już uruchomiona zostanie anulowane.  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  Na koniec `StartButton_Click`, bieżący proces się zakończy, więc ustaw wartość `cts` powrót do wartości null.  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 Poniższy kod pokazuje wszystkie zmiany w `StartButton_Click`. Dodatki są oznaczone gwiazdkami.  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 W `AccessTheWebAsync`, wprowadź następujące zmiany.  
  
-   Dodaj parametr do akceptowania tokenu odwołania z `StartButton_Click`.  
  
-   Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody do pobierania witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.  
  
-   Przed wywołaniem `DisplayResults` do wyświetlania wyników dla każdej pobranej witryny sieci Web, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.  
  
 Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}     
```  
  
 Jeśli wybierzesz **Start** przycisk kilka razy ta aplikacja jest uruchomiona, powinno to dawać wyniki podobne do następujących danych wyjściowych.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w `StartButton_Click` aby czyścić pole tekstowe za każdym razem, kiedy użytkownik uruchamia operację.  
  
###  <a name="BKMK_RunMultipleOperations"></a> Uruchom wiele operacji i Zakolejkuj dane wyjściowe  
 Trzeci przykład jest najbardziej skomplikowany, w tym, że aplikacja rozpoczyna kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze **Start** przycisk, a wszystkie operacje do zakończenia. Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są przedstawiane sekwencyjnie. Oznacza to, że rzeczywiste działanie pobierania odbywa się z przeplotem, jako dane wyjściowe w [rozpoznawaniu współużytkowania wątkowości](#BKMK_RecognizingReentrancy) pokazuje, ale lista wyników dla każdej grupy jest prezentowana oddzielnie.  
  
 Operacje współkorzystają z globalnego <xref:System.Threading.Tasks.Task>, `pendingWork`, który służy jako strażnik dla procesu wyświetlania.  

 Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [próbki asynchroniczne: Współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu jest QueueResults.  
   
 Następujące dane wyjściowe pokazują wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz. Etykieta litery A, wskazuje, że wynik dotyczy po raz pierwszy **Start** wciśnięcia przycisku. Liczby pokazują kolejność adresów URL na liście elementów docelowych pobierania.  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 Jeśli użytkownik wybierze **Start** przycisk trzy razy, aplikacja generuje dane wyjściowe podobne do następujących wierszy. Linie informacyjne, rozpoczynające się od znaku funta Zaloguj (#) śledzą postęp aplikacji.  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 Grupy B i C uruchomić przed grupy A zostało zakończone, ale dane wyjściowe dla każdej grupy pojawiają się oddzielnie. Wszystkie dane wyjściowe dla grupy A pojawiają się pierwsze, wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i, dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, adresy URL są wyświetlane na liście adresów URL.  
  
 Jednak nie można przewidzieć kolejności, w której rzeczywiście wystąpi pobieranie. Po uruchomieniu wielu grup zadań pobierania, które generują wszystkie są aktywne. Nie można zakładać, że A-1 będą pobierane przed b-1 i nie można zakładać, że A-1 będą pobierane przed A-2.  
  
#### <a name="global-definitions"></a>Globalne definicje  
 Przykładowy kod zawiera poniższe dwie deklaracje globalne, które są widoczne ze wszystkich metod.  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 `Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i zapobiega żadnej grupy zakłócania pracy wyświetlania innej grupy. Zmienna znaku `group`, oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.  
  
#### <a name="the-click-event-handler"></a>Program obsługi zdarzeń kliknięcie  
 Program obsługi zdarzeń `StartButton_Click`, rośnie literę grupy za każdym razem, użytkownik wybierze **Start** przycisku. Następnie program obsługi zdarzeń wywołuje `AccessTheWebAsync` można uruchomić operację pobierania.  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a>The AccessTheWebAsync Method  
 Ten przykład dzieli `AccessTheWebAsync` na dwie metody. Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania dla grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania. Metoda wykorzystuje Language Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> można uruchomić zadania pobierania w tym samym czasie.  
  
 `AccessTheWebAsync` następnie wywołuje `FinishOneGroupAsync` oczekiwać na zakończenie każdego pobrania i wyświetlić jego długość.  
  
 `FinishOneGroupAsync` Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`. Ta wartość zapobiega przerywaniu przez inną operację przed zakończeniem zadania.  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a>Metoda FinishOneGroupAsync  
 Ta metoda przechodzi cyklicznie przez zadania pobierania w grupie, oczekujące na każdym z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do całkowitej.  
  
 Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub która już oczekuje. Jeśli taka operacja jest w toku, wchodząca operacja musi czekać na swoją kolej.  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}  
```  
  
   
#### <a name="points-of-interest"></a>Punktów orientacyjnych  
 Linie informacyjne, rozpoczynające się od znaku funta (#) w danych wyjściowych objaśnić, jak działa ten przykład.  
  
 Dane wyjściowe pokazują następujące wzorce.  
  
-   Grupę można uruchomić podczas poprzedniej grupy jest wyświetlanie danych wyjściowych, ale wyświetlanie danych wyjściowych poprzedniej grupy nie zostanie przerwane.  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   `pendingWork` Zadania ma wartość null na początku `FinishOneGroupAsync` tylko dla grupy A, uruchomionej w pierwszej kolejności. Grupa A jeszcze nie zakończyła wykonywania wyrażenia oczekiwania, po osiągnięciu `FinishOneGroupAsync`. W związku z tym, formant nie wrócił do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpiło.  
  
-   Następujące dwa wiersze zawsze pojawiają się razem w danych wyjściowych. Kod nigdy nie jest przerywany między rozpoczęciem operacji grupy `StartButton_Click` i przypisywaniem zadania dla grupy w celu `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Po przejściu grupy do stanu `StartButton_Click`, operacja nie kończy się i wyrażenie oczekuje, aż operacja wejdzie w stan `FinishOneGroupAsync`. Dlatego żadna inna operacja może przejmować kontroli w tym segmencie kodu.  
  
##  <a name="BKMD_SettingUpTheExample"></a> Przeglądanie i uruchamianie aplikacji przykładowych  
 Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować ją samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.  
  
> [!NOTE]
>  Aby uruchomić przykład jako aplikację pulpitu Windows Presentation Foundation (WPF), konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
###  <a name="BKMK_DownloadingTheApp"></a> Pobieranie aplikacji  
  
1.  Pobierz skompresowany plik z [próbki asynchroniczne: Współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).  
  
2.  Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.  
  
3.  Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.  
  
4.  Przejdź do folderu, który posiada zdekompresowany kod przykładu, a następnie otwórz plik rozwiązania (.sln).  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz **Ustaw jako projekt startowy**.  
  
6.  Wybierz kombinację klawiszy CTRL + F5 Aby skompilować i uruchomić projekt.  
  
###  <a name="BKMK_BuildingTheApp"></a> Kompilowanie aplikacji  
 W poniższej sekcji przedstawiono kod, aby zbudować przykład jako aplikację WPF.  
  
##### <a name="to-build-a-wpf-app"></a>Aby utworzyć aplikację WPF  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku rozwiń **Visual C#**, a następnie rozwiń węzeł **Windows**.  
  
4.  Na liście typów projektów, wybierz opcję **aplikacji WPF**.  
  
5.  Nadaj projektowi nazwę `WebsiteDownloadWPF`, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
6.  W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.  
  
     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.  
  
7.  W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.  
  
8.  Dodaj odwołanie do <xref:System.Net.Http>.  
  
9. W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.  
  
10. W MainWindow.xaml.cs Zastąp kod następującym kodem.  
  
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
  
    // Add the following using directives, and add a reference for System.Net.Http.  
    using System.Net.Http;  
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "https://msdn.microsoft.com/library/hh191443.aspx",  
                    "https://msdn.microsoft.com/library/aa578028.aspx",  
                    "https://msdn.microsoft.com/library/jj155761.aspx",  
                    "https://msdn.microsoft.com/library/hh290140.aspx",  
                    "https://msdn.microsoft.com/library/hh524395.aspx",  
                    "https://msdn.microsoft.com/library/ms404677.aspx",  
                    "https://msdn.microsoft.com",  
                    "https://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "https://".  
                var displayURL = url.Replace("https://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }  
        }  
    }  
    ```  
  
11. Wybierz klawisze CTRL + F5, aby uruchomić program, a następnie wybierz **Start** przycisk kilka razy.  
  
12. Wprowadź zmiany w [Wyłącz przycisk Start](#BKMK_DisableTheStartButton), [anulowania i ponownego uruchamiania operacji](#BKMK_CancelAndRestart), lub [uruchomić wiele operacji i kolejki danych wyjściowych](#BKMK_RunMultipleOperations) do obsługi współużytkowania wątkowości.  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
