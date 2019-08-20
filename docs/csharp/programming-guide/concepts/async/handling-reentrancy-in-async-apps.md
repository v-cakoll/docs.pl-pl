---
title: Obsługa współużytkowania wątkowości w aplikacjach asynchronicznychC#()
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 78d6b786e5d54a75325d8a7a31b3e12eef7184e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595642"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Obsługa współużytkowania wątkowości w aplikacjach asynchronicznychC#()

Po dołączeniu kodu asynchronicznego do aplikacji należy rozważyć i prawdopodobnie zapobiec współużytkowania wątkowości, który odwołuje się do ponownego wprowadzania operacji asynchronicznej przed ukończeniem. Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.

**W tym temacie**

- [Rozpoznawanie współużytkowania wątkowości](#BKMK_RecognizingReentrancy)

- [Obsługa współużytkowania wątkowości](#BKMK_HandlingReentrancy)

  - [Wyłącz przycisk Start](#BKMK_DisableTheStartButton)

  - [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart)

  - [Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

- [Przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample)

> [!NOTE]
> Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

## <a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie współużytkowania wątkowości

W przykładzie w tym temacie użytkownicy wybierają przycisk **Start** , aby zainicjować aplikację asynchroniczną, która pobiera serię witryn sieci Web i oblicza łączną liczbę pobieranych bajtów. Synchroniczna wersja przykładu reaguje w taki sam sposób, niezależnie od tego, ile razy użytkownik wybierze przycisk, ponieważ po raz pierwszy wątek interfejsu użytkownika ignoruje te zdarzenia do momentu zakończenia działania aplikacji. W aplikacji asynchronicznej jednak wątek interfejsu użytkownika nadal odpowiada i można ponownie wprowadzić operację asynchroniczną przed jej ukończeniem.

W poniższym przykładzie pokazano oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz. Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiarem w bajtach każdej lokacji. Całkowita liczba bajtów pojawia się na końcu.

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

Jeśli jednak użytkownik wybierze przycisk więcej niż raz, program obsługi zdarzeń jest wywoływany wielokrotnie, a proces pobierania jest ponownie wprowadzany za każdym razem. W związku z tym kilka operacji asynchronicznych jest uruchomionych w tym samym czasie, dane wyjściowe pozostawią wyniki, a całkowita liczba bajtów jest myląca.

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

Możesz przejrzeć kod tworzący dane wyjściowe, przewijając do końca tego tematu. Można eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub używając kodu na końcu tego tematu w celu utworzenia własnego projektu. Aby uzyskać więcej informacji i instrukcje, zobacz [przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).

## <a name="BKMK_HandlingReentrancy"></a>Obsługa współużytkowania wątkowości

Możesz obsłużyć współużytkowania wątkowości na różne sposoby, w zależności od tego, co aplikacja ma robić. W tym temacie przedstawiono następujące przykłady:

- [Wyłącz przycisk Start](#BKMK_DisableTheStartButton)

  Wyłącz przycisk **Start** , gdy operacja jest uruchomiona, aby użytkownik nie mógł go przerwać.

- [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart)

  Anuluj wszystkie operacje, które nadal działają, gdy użytkownik wybierze ponownie przycisk **Start** , a następnie pozwól na kontynuowanie ostatnio żądanej operacji.

- [Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

  Zezwalaj na działanie wszystkich żądanych operacji asynchronicznie, ale koordynuj wyświetlanie danych wyjściowych, tak aby wyniki każdej operacji były wyświetlane razem i w określonej kolejności.

### <a name="BKMK_DisableTheStartButton"></a>Wyłącz przycisk Start

Można zablokować przycisk **Start** , gdy operacja jest uruchomiona, wyłączając przycisk w górnej części `StartButton_Click` procedury obsługi zdarzeń. Następnie można ponownie włączyć przycisk `finally` w bloku po zakończeniu operacji, aby umożliwić użytkownikom ponowne uruchomienie aplikacji.

Aby skonfigurować ten scenariusz, wprowadź następujące zmiany w kodzie podstawowym, który jest dostępny podczas [przeglądania i uruchamiania przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać ukończoną aplikację z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET. Nazwa projektu to DisableStartButton.

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

W wyniku zmian przycisk nie odpowiada, podczas gdy `AccessTheWebAsync` pobiera witryny sieci Web, więc nie można ponownie wprowadzić tego procesu.

### <a name="BKMK_CancelAndRestart"></a>Anuluj i ponownie uruchom operację

Zamiast wyłączać przycisk **Start** , można zachować aktywny przycisk, ale jeśli użytkownik ponownie wybierze ten przycisk, należy anulować operację, która jest już uruchomiona, i pozostawić ostatnio uruchomioną operację.

Aby uzyskać więcej informacji na temat anulowania, zobacz [dostrajanie aplikacji asynchronicznejC#()](./fine-tuning-your-async-application.md).

Aby skonfigurować ten scenariusz, wprowadź następujące zmiany w kodzie podstawowym, który jest dostępny podczas [przeglądania i uruchamiania przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać ukończoną aplikację z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET. Nazwa projektu to CancelAndRestart.

1. Zadeklaruj `cts`zmienną, która znajduje się w zakresie dla wszystkich metod. <xref:System.Threading.CancellationTokenSource>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. W `StartButton_Click`programie Ustal, czy operacja jest już w toku. Jeśli wartość `cts` jest równa null, żadna operacja nie jest już aktywna. Jeśli wartość nie jest równa null, operacja, która jest już uruchomiona, została anulowana.

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. Ustaw `cts` inną wartość, która reprezentuje bieżący proces.

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. Na końcu `StartButton_Click`bieżący proces jest zakończony, więc ustaw wartość z `cts` powrotem na wartość null.

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click`. Dodatki są oznaczone gwiazdkami.

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

Wprowadź `AccessTheWebAsync`następujące zmiany w programie.

- Dodaj parametr, aby zaakceptować token anulowania z `StartButton_Click`.

- Użyj metody <xref:System.Net.Http.HttpClient.GetAsync%2A> , aby pobrać witryny sieci Web `GetAsync` , ponieważ <xref:System.Threading.CancellationToken> akceptuje argument.

- Przed wywołaniem `DisplayResults` , aby wyświetlić wyniki dla każdej pobranej witryny `ct` sieci Web, sprawdź, czy bieżąca operacja nie została anulowana.

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

Jeśli wybierzesz przycisk **Start** kilka razy podczas działania tej aplikacji, powinny one generować wyniki podobne do następujących.

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

Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w `StartButton_Click` , aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchomi operację.

### <a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych

Trzeci przykład to najbardziej skomplikowany sposób, w jaki aplikacja uruchamia kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze przycisk **Start** , a wszystkie operacje są wykonywane do ukończenia. Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są prezentowane sekwencyjnie. Oznacza to, że rzeczywista czynność pobierania jest przeplatana, ponieważ dane wyjściowe [rozpoznawania współużytkowania wątkowości](#BKMK_RecognizingReentrancy) są wyświetlane, ale lista wyników dla każdej grupy jest prezentowana osobno.

Operacje współużytkują globalny <xref:System.Threading.Tasks.Task>, `pendingWork`, który służy jako strażnik dla procesu wyświetlania.

Aby skonfigurować ten scenariusz, wprowadź następujące zmiany w kodzie podstawowym, który jest dostępny podczas [przeglądania i uruchamiania przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać ukończoną aplikację z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET. Nazwa projektu to QueueResults.

Poniższe dane wyjściowe pokazują wynik, jeśli użytkownik wybierze przycisk **Start** tylko raz. Etykieta litery, A, wskazuje, że wynik jest z pierwszego momentu wybrania przycisku **Start** . Liczby pokazują kolejność adresów URL na liście celów pobierania.

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

Jeśli użytkownik wybierze przycisk **Start** trzy razy, aplikacja generuje dane wyjściowe podobne do następujących wierszy. Linie informacyjne, które zaczynają się od znaku funta (#) śledzą postęp aplikacji.

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

Grupy B i C rozpoczynają się przed zakończeniem grupy A, ale dane wyjściowe dla każdej grupy są wyświetlane oddzielnie. Wszystkie dane wyjściowe dla grupy A są wyświetlane jako pierwsze, po których następuje wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i, dla każdej grupy, zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, w jakiej znajdują się na liście adresów URL.

Nie można jednak przewidzieć kolejności, w której istnieją pliki do pobrania. Po rozpoczęciu wielu grup zadania pobierania, które generują, są aktywne. Nie można założyć, że wartość-1 zostanie pobrana przed B-1 i nie można założyć, że A-1 zostanie pobrane przed-2.

#### <a name="global-definitions"></a>Definicje globalne

Przykładowy kod zawiera następujące dwie deklaracje globalne, które są widoczne dla wszystkich metod.

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

`Task` Zmienna ,`pendingWork`, widzi proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy. Zmienna znaku, `group`, oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.

#### <a name="the-click-event-handler"></a>Procedura obsługi zdarzeń kliknięcia

Program obsługi zdarzeń, `StartButton_Click`, zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start** . Następnie procedura obsługi wywołuje `AccessTheWebAsync` do uruchomienia operacji pobierania.

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

Ten przykład dzieli `AccessTheWebAsync` na dwie metody. Pierwsza metoda `AccessTheWebAsync`,, uruchamia wszystkie zadania pobierania dla grupy i `pendingWork` konfiguruje, aby kontrolować proces wyświetlania. Metoda używa języka Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> do uruchamiania wszystkich zadań pobierania w tym samym czasie.

`AccessTheWebAsync`następnie wywołuje `FinishOneGroupAsync` do czeka na zakończenie każdego pobierania i wyświetla jego długość.

`FinishOneGroupAsync`zwraca zadanie, które jest przypisane do `pendingWork` elementu `AccessTheWebAsync`w. Ta wartość uniemożliwia przerwanie przez inną operację przed ukończeniem zadania.

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

Ta metoda przechodzi przez zadania pobierania w grupie, czekające na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając do niej długość.

Pierwsza instrukcja w programie `FinishOneGroupAsync` używa `pendingWork` do upewnienia się, że wprowadzenie metody nie zakłóca operacji, która jest już w procesie wyświetlania lub już oczekuje. Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na jej włączenie.

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

#### <a name="points-of-interest"></a>Punkty orientacyjne

Linie informacyjne, które zaczynają się od znaku funta (#) w danych wyjściowych, wyjaśniają sposób działania tego przykładu.

Dane wyjściowe przedstawiają następujące wzorce.

- Grupę można uruchomić, gdy poprzednia grupa wyświetla dane wyjściowe, ale nie przerywa się wyświetlania danych wyjściowych poprzedniej grupy.

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

- Zadanie ma wartość null na `FinishOneGroupAsync` początku tylko dla grupy A, która rozpoczęła się w pierwszej kolejności. `pendingWork` Grupa A jeszcze nie ukończyła wyrażenia await, gdy osiągnie `FinishOneGroupAsync`. W związku z tym formant nie `AccessTheWebAsync`został zwrócony do i pierwsze przypisanie `pendingWork` do nie zostało wykonane.

- Dwa następujące wiersze są zawsze wyświetlane razem w danych wyjściowych. Kod nigdy nie zostanie przerwany między rozpoczęciem operacji grupy w `StartButton_Click` i przypisaniem zadania dla grupy do. `pendingWork`

    ```
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    Po wprowadzeniu `StartButton_Click`grupy operacja nie kończy wyrażenia await do momentu wejścia `FinishOneGroupAsync`operacji. W związku z tym żadna inna operacja nie może uzyskać kontroli podczas tego segmentu kodu.

## <a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładowej aplikacji

Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.

> [!NOTE]
> Aby uruchomić przykład jako aplikację klasyczną Windows Presentation Foundation (WPF), na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

### <a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji

1. Pobierz skompresowany plik z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET.

2. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

3. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

4. Przejdź do folderu, który zawiera zdekompresować przykładowy kod, a następnie otwórz plik rozwiązania (. sln).

5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz polecenie **Ustaw jako StartUpProject**.

6. Wybierz kombinację klawiszy CTRL + F5, aby skompilować i uruchomić projekt.

### <a name="BKMK_BuildingTheApp"></a>Kompilowanie aplikacji

Poniższa sekcja zawiera kod służący do kompilowania przykładu jako aplikacji WPF.

##### <a name="to-build-a-wpf-app"></a>Aby skompilować aplikację WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **pliku**, **New**, **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3. W okienku **zainstalowane szablony** rozwiń pozycję **Wizualizacja C#** , a następnie rozwiń pozycję **Windows**.

4. Na liście typów projektów wybierz pozycję **Aplikacja WPF**.

5. Nazwij projekt `WebsiteDownloadWPF`, a następnie wybierz przycisk **OK** .

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

6. W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .

     Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.

7. W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.

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

     Proste okno zawierające pole tekstowe i przycisk pojawia się w widoku **projekt** MainWindow. XAML.

8. Dodaj odwołanie do <xref:System.Net.Http>.

9. W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow.XAML.cs, a następnie wybierz polecenie **Wyświetl kod**.

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

11. Naciśnij klawisze CTRL + F5, aby uruchomić program, a następnie wybierz przycisk **Start** kilka razy.

12. Wprowadź zmiany, aby [wyłączyć przycisk Start](#BKMK_DisableTheStartButton), [anulować i ponownie uruchomić operację](#BKMK_CancelAndRestart)albo [uruchomić wiele operacji i kolejkować dane wyjściowe](#BKMK_RunMultipleOperations) , aby obsłużyć współużytkowania wątkowości.

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await (C#)](./index.md)
