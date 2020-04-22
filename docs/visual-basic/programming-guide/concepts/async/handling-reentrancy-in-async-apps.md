---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 110298a2ca937dbf39c94cfe9df29afb2e76a91c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021494"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Obsługa reentrancy w aplikacjach Async (Visual Basic)

Po dołączeniu kodu asynchroniowego w aplikacji, należy rozważyć i ewentualnie zapobiec reentrancy, który odnosi się do ponownego wniesienia operacji asynchroniiowej przed jej zakończeniem. Jeśli nie zidentyfikujesz i nie poradzisz sobie z możliwościami ponownego wniesienia, może to spowodować nieoczekiwane wyniki.

> [!NOTE]
> Aby uruchomić przykład, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

> [!NOTE]
> Transport Layer Security (TLS) w wersji 1.2 jest teraz minimalną wersją do użycia w rozwoju aplikacji. Jeśli aplikacja jest przeznaczona dla wersji programu .NET Framework wcześniejszej niż 4.7, zapoznaj się z poniższym artykułem, aby zapoznać się [z najlepszymi rozwiązaniami dotyczących zabezpieczeń warstwy transportu (TLS) z programem .NET Framework.](../../../../framework/network-programming/tls.md)

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie reentrancy

W przykładzie w tym temacie użytkownicy wybierają przycisk **Start,** aby zainicjować asynchroniczną aplikację, która pobiera serię witryn sieci Web i oblicza całkowitą liczbę pobranych bajtów. Synchroniczne wersji przykładu będzie reagować w ten sam sposób, niezależnie od tego, ile razy użytkownik wybiera przycisk, ponieważ po pierwszym czasie wątku interfejsu użytkownika ignoruje te zdarzenia, dopóki aplikacja zakończy się uruchomiony. W aplikacji asynchroniiowej jednak wątek interfejsu użytkownika nadal odpowiadać i może ponownie wreżyserować operację asynchroniza.

Poniższy przykład pokazuje oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz. Pojawi się lista pobranych witryn sieci Web o rozmiarze w bajtach każdej witryny. Całkowita liczba bajtów pojawia się na końcu.

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

Jednak jeśli użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany wielokrotnie, a proces pobierania jest ponownie wprowadzany za każdym razem. W rezultacie kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przeplata wyniki, a całkowita liczba bajtów jest mylące.

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

Można przejrzeć kod, który tworzy ten wynik, przewijając do końca tego tematu. Można eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub używając kodu na końcu tego tematu, aby utworzyć własny projekt Aby uzyskać więcej informacji i instrukcji, zobacz [Przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a>Obsługa reentrancy

Możesz obsługiwać reentrancy na różne sposoby, w zależności od tego, co aplikacja ma zrobić. W tym temacie przedstawiono następujące przykłady:

- [Wyłączanie przycisku Start](#BKMK_DisableTheStartButton)

  Wyłącz przycisk **Start,** gdy operacja jest uruchomiona, aby użytkownik nie mógł jej przerwać.

- [Anulowanie i ponowne uruchomienie operacji](#BKMK_CancelAndRestart)

  Anuluj dowolną operację, która jest nadal uruchomiona, gdy użytkownik ponownie wybierze przycisk **Start,** a następnie pozwól, aby ostatnio żądana operacja była kontynuowana.

- [Uruchamianie wielu operacji i kolejkowanie danych wyjściowych](#BKMK_RunMultipleOperations)

  Zezwalaj na uruchamianie wszystkich żądanych operacji asynchronicznie, ale koordynuje wyświetlanie danych wyjściowych, tak aby wyniki z każdej operacji były wyświetlane razem i w kolejności.

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a>Wyłączanie przycisku Start

Można zablokować **przycisk Start,** gdy operacja jest uruchomiona, wyłączając `StartButton_Click` przycisk w górnej części programu obsługi zdarzeń. Następnie można ponownie uruchomić przycisk z `Finally` poziomu bloku po zakończeniu operacji, dzięki czemu użytkownicy mogą ponownie uruchomić aplikację.

Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami. Możesz dodać zmiany do kodu na końcu tego tematu lub pobrać gotową aplikację z [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa projektu to DisableStartButton.

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

W wyniku zmian przycisk nie odpowiada podczas `AccessTheWebAsync` pobierania witryn sieci Web, więc nie można ponownie wprowadzić procesu.

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a>Anulowanie i ponowne uruchomienie operacji

Zamiast wyłączać przycisk **Start,** można zachować aktywny przycisk, ale jeśli użytkownik wybierze ten przycisk ponownie, anuluj operację, która jest już uruchomiona i pozwól kontynuować ostatnio rozpoczętą operację.

Aby uzyskać więcej informacji na temat anulowania, zobacz [Dostrajanie aplikacji Asynchronii (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).

Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w kodzie podstawowym, który jest dostarczany w [przeglądowi i uruchamianiu przykładowej aplikacji](#BKMD_SettingUpTheExample). Gotową aplikację można również pobrać z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Nazwa tego projektu to CancelAndRestart.

1. Deklaruj zmienną, <xref:System.Threading.CancellationTokenSource> `cts`czyli w zakresie dla wszystkich metod.

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. W `StartButton_Click`, określić, czy operacja jest już w toku. Jeśli wartość `cts` jest `Nothing`, żadna operacja nie jest już aktywna. Jeśli wartość nie `Nothing`jest , operacja, która jest już uruchomiona jest anulowana.

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

4. Na końcu `StartButton_Click`, bieżący proces jest zakończony, `cts` więc `Nothing`ustaw wartość z powrotem do .

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

Poniższy kod pokazuje wszystkie `StartButton_Click`zmiany w . Dodatki są oznaczone gwiazdkami.

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

W `AccessTheWebAsync`, wprowadzać następujące zmiany.

- Dodaj parametr, aby zaakceptować `StartButton_Click`token anulowania z .

- Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody, aby pobrać `GetAsync` witryny <xref:System.Threading.CancellationToken> sieci Web, ponieważ akceptuje argument.

- Przed `DisplayResults` wywołaniem, aby wyświetlić wyniki `ct` dla każdej pobranej witryny sieci Web, sprawdź, czy bieżąca operacja nie została anulowana.

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

Jeśli wybierzesz przycisk **Start** kilka razy, gdy ta aplikacja jest uruchomiona, powinno to spowodować wyniki, które przypominają następujące dane wyjściowe:

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

Aby wyeliminować listy częściowe, odkomentuj `StartButton_Click` pierwszy wiersz kodu, aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchomi operację.

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i kolejkowanie danych wyjściowych

Ten trzeci przykład jest najbardziej skomplikowane, ponieważ aplikacja uruchamia inną operację asynchroniczną za każdym razem, gdy użytkownik wybiera **przycisk Start** i wszystkie operacje uruchamiane do zakończenia. Wszystkie żądane operacje pobierają strony internetowe z listy asynchronicznie, ale dane wyjściowe z operacji są prezentowane sekwencyjnie. Oznacza to, że rzeczywista aktywność pobierania jest przeplotem, jak pokazuje dane wyjściowe w [rozpoznawaniu reentrancy,](#BKMK_RecognizingReentrancy) ale lista wyników dla każdej grupy jest przedstawiona oddzielnie.

Operacje mają wspólny <xref:System.Threading.Tasks.Task> `pendingWork`globalny , który służy jako strażnik dla procesu wyświetlania.

W tym przykładzie można uruchomić, wklejając zmiany do kodu w [tworzenie aplikacji](#BKMK_BuildingTheApp)lub postępuj zgodnie z instrukcjami w [pobieranie aplikacji,](#BKMK_DownloadingTheApp) aby pobrać przykład, a następnie uruchomić projekt QueueResults.

Poniższe dane wyjściowe pokazuje wynik, jeśli użytkownik wybiera **przycisk Start** tylko raz. Etykieta litery A wskazuje, że wynik pochodzi od pierwszego wybrania przycisku **Start.** Liczby pokazują kolejność adresów URL na liście docelowych pobierania.

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

Jeśli użytkownik wybierze przycisk **Start** trzy razy, aplikacja generuje dane wyjściowe, które przypominają następujące wiersze. Linie informacyjne rozpoczynające się od znaku funta (#) śledzą postęp aplikacji.

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

Grupy B i C rozpoczynają się przed zakończeniem grupy A, ale dane wyjściowe dla każdej grupy są wyświetlane oddzielnie. Najpierw pojawia się cały wynik dla grupy A, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, wny są wyświetlane na liście adresów URL.

Jednak nie można przewidzieć kolejność, w jakiej pliki do pobrania rzeczywiście się zdarzyć. Po uruchomieniu wielu grup wszystkie generowane przez nie zadania pobierania są aktywne. Nie można zakładać, że A-1 zostanie pobrany przed B-1 i nie można zakładać, że A-1 zostanie pobrany przed A-2.

#### <a name="global-definitions"></a>Definicje globalne

Przykładowy kod zawiera następujące dwie deklaracje globalne, które są widoczne ze wszystkich metod.

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

Zmienna `Task` `pendingWork`nadzoruje proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy. Zmienna znakowa , oznacza dane wyjściowe z różnych grup, `group`aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.

#### <a name="the-click-event-handler"></a>Obsługa zdarzeń kliknięć

Program obsługi `StartButton_Click`zdarzeń , zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start.** Następnie program `AccessTheWebAsync` obsługi wywołuje uruchomienie operacji pobierania.

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

#### <a name="the-accessthewebasync-method"></a>AccessTheWebAsync Metoda

W tym `AccessTheWebAsync` przykładzie dzieli się na dwie metody. Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania dla grupy `pendingWork` i konfiguruje do sterowania procesem wyświetlania. Metoda używa kwerendy zintegrowanej języka (LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> uruchomić wszystkie zadania pobierania w tym samym czasie.

`AccessTheWebAsync`następnie `FinishOneGroupAsync` wywołuje, aby oczekiwać na zakończenie każdego pobrania i wyświetlić jego długość.

`FinishOneGroupAsync`zwraca zadanie przypisane w `pendingWork` pliku `AccessTheWebAsync`. Ta wartość zapobiega przerwaniu przez inną operację przed zakończeniem zadania.

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

Ta metoda przechodzi przez zadania pobierania w grupie, oczekując na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do sumy.

Pierwsza instrukcja `FinishOneGroupAsync` w `pendingWork` użyciu, aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub który już czeka. Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na swoją kolej.

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

W tym przykładzie można uruchomić, wklejając zmiany do kodu w [tworzenie aplikacji](#BKMK_BuildingTheApp)lub postępuj zgodnie z instrukcjami w [pobieranie aplikacji,](#BKMK_DownloadingTheApp) aby pobrać przykład, a następnie uruchomić projekt QueueResults.

#### <a name="points-of-interest"></a>Punkty szczególne

Linie informacyjne, które zaczynają się od znaku funta (#) w danych wyjściowych, wyjaśniają, jak działa ten przykład.

Dane wyjściowe pokazuje następujące wzorce.

- Grupę można uruchomić, gdy poprzednia grupa wyświetla swoje dane wyjściowe, ale wyświetlanie danych wyjściowych poprzedniej grupy nie jest przerywane.

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

- Zadanie `pendingWork` jest `Nothing` na początku `FinishOneGroupAsync` tylko dla grupy A, która rozpoczęła się jako pierwsza. Grupa A nie ukończyła jeszcze wyrażenia await `FinishOneGroupAsync`po osiągnięciu . W związku z tym formantu nie wrócił do `AccessTheWebAsync`, a pierwsze przypisanie nie `pendingWork` wystąpiło.

- Następujące dwa wiersze są zawsze wyświetlane razem na wyjściu. Kod nigdy nie jest przerywany między uruchomieniem operacji grupy `StartButton_Click` a przypisaniem zadania dla grupy do `pendingWork`.

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  Po wprowadzeniu `StartButton_Click`grupy operacja nie kończy wyrażenia await, dopóki nie `FinishOneGroupAsync`zostanie wprowadzona operacja . W związku z tym żadna inna operacja może uzyskać kontrolę podczas tego segmentu kodu.

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładowej aplikacji

Aby lepiej zrozumieć przykładowej aplikacji, można go pobrać, skompilować go samodzielnie lub przejrzeć kod na końcu tego tematu bez implementowania aplikacji.

> [!NOTE]
> Aby uruchomić przykład jako windows presentation foundation (WPF) aplikacji klasycznej, musisz mieć Visual Studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji

1. Pobierz skompresowany plik z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.

3. Na pasku menu wybierz **pozycję Plik**, **Otwórz,** **Projekt/Rozwiązanie**.

4. Przejdź do folderu, w który znajduje się zdekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln).

5. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.

6. Wybierz klawisze CTRL+F5, aby utworzyć i uruchomić projekt.

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a>Tworzenie aplikacji

Poniższa sekcja zawiera kod do tworzenia przykładu jako aplikacji WPF.

##### <a name="to-build-a-wpf-app"></a>Aby utworzyć aplikację WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt.**

3. W okienku **Zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie rozwiń pozycję **Windows**.

4. Na liście typów projektów wybierz pozycję **Aplikacja WPF**.

5. Nazwij `WebsiteDownloadWPF`projekt , wybierz .NET Framework wersję 4.6 lub nowszą, a następnie kliknij przycisk **OK.**

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

6. W Edytorze kodów programu Visual Studio wybierz kartę **MainWindow.xaml.**

     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Wyświetl kod**.

7. W widoku **XAML** mainwindow.xaml zastąp kod następującym kodem.

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

     Proste okno zawierające pole tekstowe i przycisk pojawi się w widoku **Projekt** mainwindow.xaml.

8. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie**.

     Dodaj odwołanie <xref:System.Net.Http>dla , jeśli nie jest już zaznaczone.

9. W **Eksploratorze rozwiązań**otwórz menu skrótów dla pliku MainWindow.xaml.vb, a następnie wybierz polecenie **Wyświetl kod**.

10. W mainwindow.xaml.vb , zastąp kod następującym kodem.

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

11. Wybierz klawisze CTRL+F5, aby uruchomić program, a następnie wybierz kilka razy przycisk **Start.**

12. [Wykonuj](#BKMK_DisableTheStartButton)zmiany z przycisku Wyłącz przycisk Start , [Anuluj i uruchom ponownie operację](#BKMK_CancelAndRestart)lub Uruchom wiele operacji i [kolejka danych wyjściowych](#BKMK_RunMultipleOperations) do obsługi reentrancy.

## <a name="see-also"></a>Zobacz też

- [Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwania (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Programowanie asynchroniczne z async i await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
