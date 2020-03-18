---
title: Obsługa reentrancy w akcjonorach asynchronicznej (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451866"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Obsługa reentrancy w akcjonorach asynchronicznej (C#)

Po dołączeniu kodu asynchronicznego w aplikacji, należy wziąć pod uwagę i ewentualnie zapobiec reentrancy, który odnosi się do ponownego wprowadzenia operacji asynchronicznej przed jej zakończeniem. Jeśli nie zidentyfikować i obsługiwać możliwości reentrancy, może to spowodować nieoczekiwane wyniki.

**W tym temacie**

- [Rozpoznawanie Reentrancy](#BKMK_RecognizingReentrancy)

- [Obsługa Reentrancy](#BKMK_HandlingReentrancy)

  - [Wyłączanie przycisku Start](#BKMK_DisableTheStartButton)

  - [Anulowanie i ponowne uruchomienie operacji](#BKMK_CancelAndRestart)

  - [Uruchamianie wielu operacji i kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

- [Przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample)

> [!NOTE]
> Aby uruchomić przykład, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

> [!NOTE]
> Transport Layer Security (TLS) w wersji 1.2 jest teraz minimalną wersją do użycia w tworzeniu aplikacji. Jeśli aplikacja jest przeznaczona dla wersji .NET Framework wcześniej niż 4.7, zapoznaj się z następującym artykułem dla [rozwiązań TLS (Transport Layer Security) z platformą .NET Framework](../../../../framework/network-programming/tls.md).

## <a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie Reentrancy

W przykładzie w tym temacie użytkownicy wybierają przycisk **Start,** aby zainicjować aplikację asynchroniczną, która pobiera serię witryn sieci Web i oblicza całkowitą liczbę pobranych bajtów. Synchroniczna wersja przykładu będzie odpowiadać w ten sam sposób, niezależnie od tego, ile razy użytkownik wybierze przycisk, ponieważ po raz pierwszy wątek interfejsu użytkownika ignoruje te zdarzenia, dopóki aplikacja nie zakończy działa. W aplikacji asynchronicznej jednak wątek interfejsu użytkownika nadal odpowiadać i może ponownie wprowadzić operację asynchroniczną przed zakończeniem.

W poniższym przykładzie przedstawiono oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz. Pojawi się lista pobranych witryn sieci Web z rozmiarem w bajtach każdej witryny. Całkowita liczba bajtów pojawi się na końcu.

```output
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

Jeśli jednak użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany wielokrotnie, a proces pobierania jest wprowadzany ponownie za każdym razem. W rezultacie kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przetoczy wyniki, a całkowita liczba bajtów jest mylące.

```output
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

Można przejrzeć kod, który tworzy to dane wyjściowe, przewijając do końca tego tematu. Możesz eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub używając kodu na końcu tego tematu, aby utworzyć własny projekt. Aby uzyskać więcej informacji i instrukcje, zobacz [Przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).

## <a name="BKMK_HandlingReentrancy"></a>Obsługa Reentrancy

Reentrancy można obsługiwać na różne sposoby, w zależności od tego, co chcesz zrobić aplikacji. W tym temacie przedstawiono następujące przykłady:

- [Wyłączanie przycisku Start](#BKMK_DisableTheStartButton)

  Wyłącz przycisk **Start,** gdy operacja jest uruchomiona, aby użytkownik nie mógł go przerwać.

- [Anulowanie i ponowne uruchomienie operacji](#BKMK_CancelAndRestart)

  Anuluj wszystkie operacje, które są nadal uruchomione, gdy użytkownik ponownie wybierze przycisk **Start,** a następnie pozwól kontynuować ostatnio żądaną operację.

- [Uruchamianie wielu operacji i kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

  Zezwalaj na wszystkie żądane operacje, aby były uruchamiane asynchronicznie, ale koordynuj wyświetlanie danych wyjściowych, tak aby wyniki każdej operacji były wyświetlane razem i w kolejności.

### <a name="BKMK_DisableTheStartButton"></a>Wyłączanie przycisku Start

Przycisk **Start** można zablokować, gdy operacja jest uruchomiona, wyłączając `StartButton_Click` przycisk u góry programu obsługi zdarzeń. Następnie można ponownie włączyć przycisk `finally` z poziomu bloku po zakończeniu operacji, aby użytkownicy mogli ponownie uruchomić aplikację.

Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w podstawowym kodzie, który znajduje się w [przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [przykładów asynchronii: Reentrancy w aplikacjach komputerowych .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu jest DisableStartButton.

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

W wyniku zmian przycisk nie odpowiada podczas `AccessTheWebAsync` pobierania stron internetowych, więc nie można ponownie wprowadzić procesu.

### <a name="BKMK_CancelAndRestart"></a>Anulowanie i ponowne uruchomienie operacji

Zamiast wyłączać przycisk **Start,** możesz zachować przycisk aktywny, ale jeśli użytkownik ponownie wybierze ten przycisk, anuluj operację, która jest już uruchomiona i pozwól, aby ostatnio rozpoczęta operacja była kontynuowana.

Aby uzyskać więcej informacji na temat anulowania, zobacz [Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md).

Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w podstawowym kodzie, który znajduje się w [przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [przykładów asynchronii: Reentrancy w aplikacjach komputerowych .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to CancelAndRestart.

1. Deklaruj `cts`zmienną, <xref:System.Threading.CancellationTokenSource> która jest w zakresie dla wszystkich metod.

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. W `StartButton_Click`, ustalić, czy operacja jest już w toku. Jeśli wartość `cts` jest null, żadna operacja nie jest już aktywna. Jeśli wartość nie jest null, operacja, która jest już uruchomiona jest anulowana.

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. Po zakończeniu `StartButton_Click`bieżącego procesu jest zakończona, więc `cts` ustaw wartość z powrotem na null.

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

Poniższy kod pokazuje wszystkie `StartButton_Click`zmiany w pliku . Dodatki są oznaczone gwiazdkami.

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

W `AccessTheWebAsync`, wprowadzić następujące zmiany.

- Dodaj parametr, aby zaakceptować `StartButton_Click`token anulowania z .

- Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody, aby pobrać `GetAsync` strony <xref:System.Threading.CancellationToken> internetowe, ponieważ akceptuje argument.

- Przed `DisplayResults` wywołaniem połączenia w celu wyświetlenia wyników dla każdej pobranej witryny sieci Web sprawdź, `ct` czy bieżąca operacja nie została anulowana.

Poniższy kod pokazuje te zmiany, które są oznaczone gwiazdkami.

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

Jeśli wybierzesz przycisk **Start** kilka razy, gdy ta aplikacja jest uruchomiona, powinna ona dawać wyniki, które przypominają następujące dane wyjściowe.

```output
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

Aby wyeliminować listy częściowe, wyczyść `StartButton_Click` pierwszy wiersz kodu, aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchamia operację.

### <a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i kolejkowanie danych wyjściowych

Ten trzeci przykład jest najbardziej skomplikowany, ponieważ aplikacja uruchamia inną operację asynchroniczną za każdym razem, gdy użytkownik wybierze przycisk **Start,** a wszystkie operacje są uruchamiane do zakończenia. Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe z operacji są prezentowane sekwencyjnie. Oznacza to, że rzeczywiste działanie pobierania jest przeplotem, jak pokazuje dane wyjściowe w [rozpoznawaniu Reentrancy,](#BKMK_RecognizingReentrancy) ale lista wyników dla każdej grupy jest prezentowana oddzielnie.

Operacje współużytkują globalną <xref:System.Threading.Tasks.Task>, `pendingWork`która służy jako strażnik dla procesu wyświetlania.

Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w podstawowym kodzie, który znajduje się w [przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać gotową aplikację z [przykładów asynchronii: Reentrancy w aplikacjach komputerowych .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to QueueResults.

Na poniższym wyjściu przedstawiono wynik, jeśli użytkownik wybierze przycisk **Start** tylko raz. Etykieta litery, A, wskazuje, że wynik pochodzi z pierwszego wybrania przycisku **Start.** Liczby pokazują kolejność adresów URL na liście celów pobierania.

```output
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

Jeśli użytkownik wybierze przycisk **Start** trzy razy, aplikacja generuje dane wyjściowe, które przypominają następujące wiersze. Wiersze informacji, które rozpoczynają się od znaku funta (#) śledzą postęp aplikacji.

```output
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

Grupy B i C rozpoczynają się przed zakończeniem grupy A, ale dane wyjściowe dla każdej grupy są wyświetlane oddzielnie. Wszystkie dane wyjściowe dla grupy A pojawia się najpierw, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, w jakiej adresy URL są wyświetlane na liście adresów URL.

Nie można jednak przewidzieć kolejności, w jakiej faktycznie dochodzi do pobrań. Po uruchomieniu wielu grup wszystkie generowane przez nie zadania pobierania są aktywne. Nie można zakładać, że A-1 zostanie pobrany przed B-1 i nie można zakładać, że A-1 zostanie pobrany przed A-2.

#### <a name="global-definitions"></a>Definicje globalne

Przykładowy kod zawiera następujące dwie deklaracje globalne, które są widoczne ze wszystkich metod.

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

Zmienna `Task` `pendingWork`, nadzoruje proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy. Zmienna znaków, oznacza dane wyjściowe z różnych grup, `group`aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.

#### <a name="the-click-event-handler"></a>Program obsługi zdarzeń click

Program obsługi `StartButton_Click`zdarzeń , zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start.** Następnie wywołuje `AccessTheWebAsync` program obsługi, aby uruchomić operację pobierania.

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

#### <a name="the-accessthewebasync-method"></a>Metoda AccessTheWebAsync

W tym `AccessTheWebAsync` przykładzie dzieli się na dwie metody. Pierwsza metoda, `AccessTheWebAsync`uruchamia wszystkie zadania pobierania dla grupy `pendingWork` i konfiguruje do sterowania procesem wyświetlania. Metoda używa language Integrated Query (zapytanie <xref:System.Linq.Enumerable.ToArray%2A> LINQ) i uruchomić wszystkie zadania pobierania w tym samym czasie.

`AccessTheWebAsync`następnie `FinishOneGroupAsync` wzywa do oczekiwania na zakończenie każdego pobrania i wyświetlania jego długości.

`FinishOneGroupAsync`zwraca zadanie przypisane do `pendingWork` pliku `AccessTheWebAsync`. Ta wartość zapobiega przerwaniu przez inną operację przed zakończeniem zadania.

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

Ta metoda przechodzi przez zadania pobierania w grupie, oczekując na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do sumy.

Pierwsza instrukcja `FinishOneGroupAsync` `pendingWork` w używań, aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub który już czeka. Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na swoją kolej.

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

#### <a name="points-of-interest"></a>Punkty szczególne

Wiersze informacji, które zaczynają się od znaku funta (#) w danych wyjściowych wyjaśnić, jak działa ten przykład.

Dane wyjściowe pokazuje następujące wzorce.

- Grupę można uruchomić, gdy poprzednia grupa wyświetla swoje dane wyjściowe, ale wyświetlanie danych wyjściowych poprzedniej grupy nie jest przerywane.

    ```output
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

- Zadanie `pendingWork` ma wartość null `FinishOneGroupAsync` na początku tylko dla grupy A, która została uruchomiona jako pierwsza. Grupa A nie ukończyła jeszcze wyrażenia await, `FinishOneGroupAsync`gdy osiągnie . W związku z tym formant `AccessTheWebAsync`nie powrócił do `pendingWork` , a pierwsze przypisanie nie wystąpił.

- Następujące dwa wiersze zawsze pojawiają się razem w danych wyjściowych. Kod nigdy nie jest przerywany między `StartButton_Click` rozpoczęciem operacji grupy a `pendingWork`przypisaniem zadania dla grupy do .

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    Po wejściu `StartButton_Click`grupy operacja nie kończy wyrażenia await, dopóki operacja `FinishOneGroupAsync`nie zostanie wkroczona. W związku z tym żadna inna operacja może uzyskać kontrolę podczas tego segmentu kodu.

## <a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładowej aplikacji

Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, utworzyć samodzielnie lub przejrzeć kod na końcu tego tematu bez implementowania aplikacji.

> [!NOTE]
> Aby uruchomić przykład jako aplikacja klasyczna Windows Presentation Foundation (WPF), musisz mieć program Visual Studio 2012 lub nowszy i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

### <a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji

1. Pobierz skompresowany plik z [przykładów asynchronii: Reentrancy w aplikacjach komputerowych .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

3. Na pasku menu wybierz pozycję **Plik**, **Otwórz**, **Projekt/Rozwiązanie**.

4. Przejdź do folderu, w który znajduje się zdekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln).

5. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.

6. Wybierz klawisze CTRL+F5 do tworzenia i uruchamiania projektu.

### <a name="BKMK_BuildingTheApp"></a>Tworzenie aplikacji

W poniższej sekcji przedstawiono kod do tworzenia przykładu jako aplikacja WPF.

##### <a name="to-build-a-wpf-app"></a>Aby utworzyć aplikację WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt.**

3. W okienku **Zainstalowane szablony** rozwiń węzeł **Visual C#,** a następnie rozwiń węzeł **Windows**.

4. Na liście typów projektów wybierz pozycję **Aplikacja WPF**.

5. Nazwij `WebsiteDownloadWPF`projekt , wybierz wersję .NET Framework 4.6 lub nowszą, a następnie kliknij przycisk **OK.**

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

6. W Edytorze kodu programu Visual Studio wybierz kartę **MainWindow.xaml.**

     Jeśli karta nie jest widoczna, otwórz menu skrótów mainwindow.xaml w **Eksploratorze rozwiązań**, a następnie wybierz pozycję **Wyświetl kod**.

7. W widoku **XAML** MainWindow.xaml, zastąp kod następującym kodem.

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

     Proste okno zawierające pole tekstowe i przycisk pojawi się w widoku **projektowym** pliku MainWindow.xaml.

8. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy pozycję **Odwołania** i wybierz polecenie **Dodaj odwołanie**.

     Dodaj odwołanie <xref:System.Net.Http>do , jeśli nie jest jeszcze zaznaczone.

9. W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz pozycję **Wyświetl kod**.

10. W MainWindow.xaml.cs należy zastąpić kod następującym kodem.

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
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
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

11. Wybierz klawisze CTRL+F5, aby uruchomić program, a następnie wybierz przycisk **Start** kilka razy.

12. Wprowadzanie zmian z [Wyłącz przycisk Start](#BKMK_DisableTheStartButton), [Anuluj i uruchom operację](#BKMK_CancelAndRestart)lub [Uruchom wiele operacji i Kolejkuj dane wyjściowe,](#BKMK_RunMultipleOperations) aby obsłużyć reentrancy.

## <a name="see-also"></a>Zobacz też

- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z async i await (C#)](./index.md)
