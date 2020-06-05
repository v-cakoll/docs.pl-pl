---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 2d1af14016f82b5de875d3638b132e14c7d2280d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396639"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)

Po dołączeniu kodu asynchronicznego do aplikacji należy rozważyć i prawdopodobnie zapobiec współużytkowania wątkowości, który odwołuje się do ponownego wprowadzania operacji asynchronicznej przed ukończeniem. Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.

> [!NOTE]
> Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

> [!NOTE]
> Transport Layer Security (TLS) w wersji 1,2 jest teraz minimalną wersją do użycia podczas opracowywania aplikacji. Jeśli aplikacja jest przeznaczona dla .NET Framework wersji wcześniejszej niż 4,7, zapoznaj się z poniższym artykułem dotyczącym [Transport Layer Security (TLS) najlepszymi rozwiązaniami](../../../../framework/network-programming/tls.md)dotyczącymi .NET Framework.

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie współużytkowania wątkowości

W przykładzie w tym temacie użytkownicy wybierają przycisk **Start** , aby zainicjować aplikację asynchroniczną, która pobiera serię witryn sieci Web i oblicza łączną liczbę pobieranych bajtów. Synchroniczna wersja przykładu reaguje w taki sam sposób, niezależnie od tego, ile razy użytkownik wybierze przycisk, ponieważ po raz pierwszy wątek interfejsu użytkownika ignoruje te zdarzenia do momentu zakończenia działania aplikacji. W aplikacji asynchronicznej jednak wątek interfejsu użytkownika nadal odpowiada i można ponownie wprowadzić operację asynchroniczną przed jej ukończeniem.

W poniższym przykładzie pokazano oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz. Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiarem w bajtach każdej lokacji. Całkowita liczba bajtów pojawia się na końcu.

```console
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

```console
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

Możesz przejrzeć kod tworzący dane wyjściowe, przewijając do końca tego tematu. Można eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub korzystając z kodu na końcu tego tematu, aby utworzyć własny projekt, aby uzyskać więcej informacji i instrukcje, zobacz [przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Obsługa współużytkowania wątkowości

Możesz obsłużyć współużytkowania wątkowości na różne sposoby, w zależności od tego, co aplikacja ma robić. W tym temacie przedstawiono następujące przykłady:

- [Wyłącz przycisk Start](#BKMK_DisableTheStartButton)

  Wyłącz przycisk **Start** , gdy operacja jest uruchomiona, aby użytkownik nie mógł go przerwać.

- [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart)

  Anuluj wszystkie operacje, które nadal działają, gdy użytkownik wybierze ponownie przycisk **Start** , a następnie pozwól na kontynuowanie ostatnio żądanej operacji.

- [Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

  Zezwalaj na działanie wszystkich żądanych operacji asynchronicznie, ale koordynuj wyświetlanie danych wyjściowych, tak aby wyniki każdej operacji były wyświetlane razem i w określonej kolejności.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Wyłącz przycisk Start

Można zablokować przycisk **Start** , gdy operacja jest uruchomiona, wyłączając przycisk w górnej części `StartButton_Click` procedury obsługi zdarzeń. Następnie można ponownie włączyć przycisk w `Finally` bloku po zakończeniu operacji, aby umożliwić użytkownikom ponowne uruchomienie aplikacji.

Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami. Możesz dodać zmiany do kodu na końcu tego tematu lub można pobrać ukończoną aplikację z [przykładów asynchronicznych: współużytkowania wątkowości w aplikacjach klasycznych platformy .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to DisableStartButton.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' This line is commented out to make the results clearer in the output.
    'ResultsTextBox.Text = ""

    ' ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = False

    Try
        Await AccessTheWebAsync()

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    ' ***Enable the Start button in case you want to run the program again.
    Finally
        StartButton.IsEnabled = True

    End Try
End Sub
```

W wyniku zmian przycisk nie odpowiada, podczas gdy `AccessTheWebAsync` Pobiera witryny sieci Web, więc nie można ponownie wprowadzić tego procesu.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>Anuluj i ponownie uruchom operację

Zamiast wyłączać przycisk **Start** , można zachować aktywny przycisk, ale jeśli użytkownik ponownie wybierze ten przycisk, należy anulować operację, która jest już uruchomiona, i pozostawić ostatnio uruchomioną operację.

Aby uzyskać więcej informacji na temat anulowania, zobacz [dostrajanie aplikacji asynchronicznej (Visual Basic)](fine-tuning-your-async-application.md).

Aby skonfigurować ten scenariusz, wprowadź następujące zmiany w kodzie podstawowym, który jest dostępny podczas [przeglądania i uruchamiania przykładowej aplikacji](#BKMD_SettingUpTheExample). Możesz również pobrać ukończoną aplikację z [przykładów asynchronicznych: współużytkowania wątkowości w aplikacjach klasycznych platformy .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa tego projektu to CancelAndRestart.

1. Zadeklaruj <xref:System.Threading.CancellationTokenSource> zmienną, `cts` która znajduje się w zakresie dla wszystkich metod.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. W programie `StartButton_Click` Ustal, czy operacja jest już w toku. Jeśli wartość `cts` jest równa `Nothing` , żadna operacja nie jest już aktywna. Jeśli wartość nie jest `Nothing` , operacja, która jest już uruchomiona, została anulowana.

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. Ustaw `cts` inną wartość, która reprezentuje bieżący proces.

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. Na koniec `StartButton_Click` bieżący proces jest zakończony, więc ustaw wartość z `cts` powrotem na `Nothing` .

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click` . Dodatki są oznaczone gwiazdkami.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

    ' This line is commented out to make the results clearer.
    'ResultsTextBox.Text = ""

    ' *** If a download process is underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If

    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS

    Try
        ' *** Send a token to carry the message if the operation is canceled.
        Await AccessTheWebAsync(cts.Token)

    Catch ex As OperationCanceledException
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    End Try

    ' *** When the process is complete, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
End Sub
```

`AccessTheWebAsync`Wprowadź następujące zmiany w programie.

- Dodaj parametr, aby zaakceptować token anulowania z `StartButton_Click` .

- Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody, aby pobrać witryny sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argument.

- Przed wywołaniem `DisplayResults` , aby wyświetlić wyniki dla każdej pobranej witryny sieci Web, sprawdź, czy `ct` bieżąca operacja nie została anulowana.

 Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.

```vb
' *** Provide a parameter for the CancellationToken from StartButton_Click.
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task

    ' Declare an HttpClient object.
    Dim client = New HttpClient()

    ' Make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()

    Dim total = 0
    Dim position = 0

    For Each url In urlList
        ' *** Use the HttpClient.GetAsync method because it accepts a
        ' cancellation token.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' *** Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' *** Check for cancellations before displaying information about the
        ' latest site.
        ct.ThrowIfCancellationRequested()

        position += 1
        DisplayResults(url, urlContents, position)

        ' Update the total.
        total += urlContents.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

Jeśli wybierzesz przycisk **Start** kilka razy podczas działania tej aplikacji, powinny one generować wyniki podobne do następujących:

```console
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

Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w, `StartButton_Click` Aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchomi operację.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych

Trzeci przykład to najbardziej skomplikowany sposób, w jaki aplikacja uruchamia kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze przycisk **Start** , a wszystkie operacje są wykonywane do ukończenia. Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są prezentowane sekwencyjnie. Oznacza to, że rzeczywista czynność pobierania jest przeplatana, ponieważ dane wyjściowe [rozpoznawania współużytkowania wątkowości](#BKMK_RecognizingReentrancy) są wyświetlane, ale lista wyników dla każdej grupy jest prezentowana osobno.

Operacje współużytkują globalny <xref:System.Threading.Tasks.Task> , `pendingWork` , który służy jako strażnik dla procesu wyświetlania.

Możesz uruchomić ten przykład, wklejając zmiany do kodu w trakcie [tworzenia aplikacji](#BKMK_BuildingTheApp), lub postępuj zgodnie z instrukcjami w temacie [Pobieranie aplikacji](#BKMK_DownloadingTheApp) , aby pobrać przykład, a następnie Uruchom projekt QueueResults.

Poniższe dane wyjściowe pokazują wynik, jeśli użytkownik wybierze przycisk **Start** tylko raz. Etykieta litery, A, wskazuje, że wynik jest z pierwszego momentu wybrania przycisku **Start** . Liczby pokazują kolejność adresów URL na liście celów pobierania.

```console
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

```console
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

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

`Task`Zmienna, `pendingWork` , widzi proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy. Zmienna znaku, `group` , oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.

#### <a name="the-click-event-handler"></a>Procedura obsługi zdarzeń kliknięcia

Program obsługi zdarzeń, `StartButton_Click` , zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start** . Następnie procedura obsługi wywołuje `AccessTheWebAsync` do uruchomienia operacji pobierania.

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' ***Verify that each group's results are displayed together, and that
    ' the groups display in order, by marking each group with a letter.
    group = ChrW(AscW(group) + 1)
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)

    Try
        ' *** Pass the group value to AccessTheWebAsync.
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)

        ' The following line verifies a successful return from the download and
        ' display procedures.
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."

    End Try
End Sub
```

#### <a name="the-accessthewebasync-method"></a>Metoda AccessTheWebAsync

Ten przykład dzieli `AccessTheWebAsync` na dwie metody. Pierwsza metoda, `AccessTheWebAsync` , uruchamia wszystkie zadania pobierania dla grupy i konfiguruje, `pendingWork` Aby kontrolować proces wyświetlania. Metoda używa języka Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> do uruchamiania wszystkich zadań pobierania w tym samym czasie.

`AccessTheWebAsync`następnie wywołuje `FinishOneGroupAsync` do czeka na zakończenie każdego pobierania i wyświetla jego długość.

`FinishOneGroupAsync`zwraca zadanie, które jest przypisane do elementu `pendingWork` w `AccessTheWebAsync` . Ta wartość uniemożliwia przerwanie przez inną operację przed ukończeniem zadania.

```vb
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)

    Dim client = New HttpClient()

    ' Make a list of the web addresses to download.
    Dim urlList As List(Of String) = SetUpURLList()

    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Dim getContentTasks As Task(Of Byte())() =
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()

    ' ***Call the method that awaits the downloads and displays the results.
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)

    ResultsTextBox.Text &=
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)

    ' ***This task is complete when a group has finished downloading and displaying.
    Await pendingWork

    ' You can do other work here or just return.
    Return grp
End Function
```

#### <a name="the-finishonegroupasync-method"></a>Metoda FinishOneGroupAsync

Ta metoda przechodzi przez zadania pobierania w grupie, czekające na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając do niej długość.

Pierwsza instrukcja w programie `FinishOneGroupAsync` używa do upewnienia się `pendingWork` , że wprowadzenie metody nie zakłóca operacji, która jest już w procesie wyświetlania lub już oczekuje. Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na jej włączenie.

```vb
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task

    ' Wait for the previous group to finish displaying results.
    If pendingWork IsNot Nothing Then
        Await pendingWork
    End If

    Dim total = 0

    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    For i As Integer = 0 To contentTasks.Length - 1
        ' Await the download of a particular URL, and then display the URL and
        ' its length.
        Dim content As Byte() = Await contentTasks(i)
        DisplayResults(urls(i), content, i, grp)
        total += content.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

Możesz uruchomić ten przykład, wklejając zmiany do kodu w trakcie [tworzenia aplikacji](#BKMK_BuildingTheApp), lub postępuj zgodnie z instrukcjami podanymi w temacie [Pobieranie aplikacji](#BKMK_DownloadingTheApp) , aby pobrać przykład, a następnie Uruchom projekt QueueResults.

#### <a name="points-of-interest"></a>Punkty orientacyjne

Linie informacyjne, które zaczynają się od znaku funta (#) w danych wyjściowych, wyjaśniają sposób działania tego przykładu.

Dane wyjściowe przedstawiają następujące wzorce.

- Grupę można uruchomić, gdy poprzednia grupa wyświetla dane wyjściowe, ale nie przerywa się wyświetlania danych wyjściowych poprzedniej grupy.

  ```console
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

- `pendingWork`Zadanie jest `Nothing` na początku `FinishOneGroupAsync` tylko dla grupy A, która rozpoczęła się w pierwszej kolejności. Grupa A jeszcze nie ukończyła wyrażenia await, gdy osiągnie `FinishOneGroupAsync` . W związku z tym formant nie został zwrócony do `AccessTheWebAsync` i pierwsze przypisanie do nie zostało wykonane `pendingWork` .

- Dwa następujące wiersze są zawsze wyświetlane razem w danych wyjściowych. Kod nigdy nie zostanie przerwany między rozpoczęciem operacji grupy w `StartButton_Click` i przypisaniem zadania dla grupy do `pendingWork` .

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Po wprowadzeniu grupy `StartButton_Click` operacja nie kończy wyrażenia await do momentu wejścia operacji `FinishOneGroupAsync` . W związku z tym żadna inna operacja nie może uzyskać kontroli podczas tego segmentu kodu.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładowej aplikacji

Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.

> [!NOTE]
> Aby uruchomić przykład jako aplikację klasyczną Windows Presentation Foundation (WPF), na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji

1. Pobierz skompresowany plik z [próbek asynchronicznych: współużytkowania wątkowości w aplikacjach klasycznych platformy .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.

3. Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.

4. Przejdź do folderu, który zawiera zdekompresować przykładowy kod, a następnie otwórz plik rozwiązania (. sln).

5. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz polecenie **Ustaw jako StartUpProject**.

6. Wybierz kombinację klawiszy CTRL + F5, aby skompilować i uruchomić projekt.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Kompilowanie aplikacji

Poniższa sekcja zawiera kod służący do kompilowania przykładu jako aplikacji WPF.

##### <a name="to-build-a-wpf-app"></a>Aby skompilować aplikację WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W okienku **zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie rozwiń pozycję **Windows**.

4. Na liście typów projektów wybierz pozycję **Aplikacja WPF**.

5. Nazwij projekt `WebsiteDownloadWPF` , wybierz .NET Framework wersja 4,6 lub nowsza, a następnie kliknij przycisk **OK** .

     Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

6. W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .

     Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.

7. W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.

    ```xaml
    <Window x:Class="MainWindow"
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

8. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **odwołania** i wybierz polecenie **Dodaj odwołanie**.

     Dodaj odwołanie do <xref:System.Net.Http> , jeśli nie zostało jeszcze wybrane.

9. W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.

10. W MainWindow. XAML. vb Zastąp kod następującym kodem.

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

            ' This line is commented out to make the results clearer in the output.
            'ResultsTextBox.Text = ""

            Try
                Await AccessTheWebAsync()

            Catch ex As Exception
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."

            End Try
        End Sub

        Private Async Function AccessTheWebAsync() As Task

            ' Declare an HttpClient object.
            Dim client = New HttpClient()

            ' Make a list of web addresses.
            Dim urlList As List(Of String) = SetUpURLList()

            Dim total = 0
            Dim position = 0

            For Each url In urlList
                ' GetByteArrayAsync returns a task. At completion, the task
                ' produces a byte array.
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

                position += 1
                DisplayResults(url, urlContents, position)

                ' Update the total.
                total += urlContents.Length
            Next

            ' Display the total count for all of the websites.
            ResultsTextBox.Text &=
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
        End Function

        Private Function SetUpURLList() As List(Of String)
            Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. Naciśnij klawisze CTRL + F5, aby uruchomić program, a następnie wybierz przycisk **Start** kilka razy.

12. Wprowadź zmiany, aby [wyłączyć przycisk Start](#BKMK_DisableTheStartButton), [anulować i ponownie uruchomić operację](#BKMK_CancelAndRestart)albo [uruchomić wiele operacji i kolejkować dane wyjściowe](#BKMK_RunMultipleOperations) , aby obsłużyć współużytkowania wątkowości.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](index.md)
