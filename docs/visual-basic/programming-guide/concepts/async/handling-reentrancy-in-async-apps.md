---
title: "Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45dfc4dd4ab42c3ce8edd7e41b7b0401bb0db672
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a>Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)
Po dołączeniu kodu asynchroniczne w aplikacji należy wziąć pod uwagę i prawdopodobnie zapobiec ponowne wejście, który odwołuje się do ponownego wprowadzania operację asynchroniczną, zanim została ukończona. Jeśli nie identyfikowania i obsługi możliwości ponownego rozpoczęcia, może spowodować nieoczekiwane wyniki.  
  
 **W tym temacie**  
  
-   [Rozpoznawanie Wielobieżność](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Obsługa ponownego rozpoczęcia](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Wyłącz przycisk Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Anuluj i ponownie uruchom operację](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [Uruchamianie wielu operacji i danych wyjściowych w kolejce](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [Przeglądanie i uruchamianie przykładową aplikację](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
##  <a name="BKMK_RecognizingReentrancy"></a>Rozpoznawanie Wielobieżność  
 W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchronicznego aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które zostaną pobrane. Synchroniczną wersję przykładu będzie odpowiadać taki sam sposób niezależnie od ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątku interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się aplikacja działa. W aplikacji asynchroniczne jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i może ponownie operację asynchroniczną, zanim została ukończona.  
  
 W poniższym przykładzie przedstawiono oczekiwanych danych wyjściowych, jeśli użytkownik wybierze **Start** przycisk tylko raz. Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiar w bajtach, w każdej lokacji. Całkowita liczba bajtów pojawia się na końcu.  
  
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
  
 Jednak jeśli użytkownik wybierze przycisk więcej niż raz, program obsługi zdarzeń jest wywoływany wielokrotnie i proces pobierania jest ponownie wprowadzić hasło zawsze. W związku z tym kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przeplata wyniki, a całkowita liczba bajtów jest myląca.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
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
  
 Możesz przejrzeć kod, który generuje dane wyjściowe w tym przewijając na końcu tego tematu. Możesz eksperymentować z kodem pobrać rozwiązanie na komputerze lokalnym, a następnie uruchamiając projekt WebsiteDownload lub przy użyciu kodu na końcu tego tematu, aby utworzyć własny projekt, aby uzyskać więcej informacji oraz instrukcje, zobacz [ Przeglądanie i uruchamianie aplikacji przykład](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).  
  
##  <a name="BKMK_HandlingReentrancy"></a>Obsługa ponownego rozpoczęcia  
 Wielobieżność na różne sposoby, w zależności od tego, co ma aplikację w celu może obsłużyć. W tym temacie przedstawiono następujące przykłady:  
  
-   [Wyłącz przycisk Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Wyłącz **Start** przycisk podczas operacji jest uruchomiona, dzięki czemu użytkownik nie może przerwać go.  
  
-   [Anuluj i ponownie uruchom operację](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Anuluj wszelkie operacje, który jest nadal uruchomiona, gdy użytkownik wybierze **Start** przycisk ponownie, a następnie kontynuuj let najbardziej ostatnio żądanej operacji.  
  
-   [Uruchamianie wielu operacji i danych wyjściowych w kolejce](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     Zezwalaj na wszystkie żądane operacje wykonywane asynchronicznie, ale koordynuje wyświetlania danych wyjściowych, aby jednocześnie i w kolejności zostaną wyświetlone wyniki z każdej operacji.  
  
###  <a name="BKMK_DisableTheStartButton"></a>Wyłącz przycisk Start  
 Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku w górnej części `StartButton_Click` obsługi zdarzeń. Następnie można ponownie włączyć za pomocą przycisku `Finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą ponownie uruchom aplikację.  
  
 Poniższy kod przedstawia te zmiany, które są oznaczone ikoną z gwiazdki. Zmiany można dodać do kodu na końcu tego tematu, lub możesz pobrać Zakończono aplikację z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571). Nazwa projektu jest DisableStartButton.  
  
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
  
 W wyniku zmian, przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobierania witryny sieci Web, więc nie można ponownie wprowadzić hasło procesu.  
  
###  <a name="BKMK_CancelAndRestart"></a>Anuluj i ponownie uruchom operację  
 Zamiast wyłączenie **Start** przycisku, można zachować aktywnego przycisku, ale, jeśli użytkownik wybierze ponownie, ten przycisk Anuluj operację, która jest już uruchomiona i kontynuowania operacji najbardziej ostatnio uruchomiono.  
  
 Aby uzyskać więcej informacji na temat anulowania, zobacz [Fine-Tuning Twoja aplikacja Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Aby skonfigurować ten scenariusz, wprowadź następujące zmiany do podstawowego kodu, który znajduje się w [przeglądanie i uruchamianie aplikacji przykład](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645). Możesz również pobrać Zakończono aplikacji z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571). Nazwa tego projektu jest CancelAndRestart.  
  
1.  Deklarowanie <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  W `StartButton_Click`, określić, czy operacja jest już przetwarzane. Jeśli wartość `cts` jest `Nothing`, nie jest operacja już aktywne. Jeśli wartość nie jest `Nothing`, która jest już uruchomiona operacja została anulowana.  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  Na koniec `StartButton_Click`, bieżący proces zostanie zakończony, a więc ustaw wartość `cts` do `Nothing`.  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click`. Dodatki są oznaczone gwiazdki.  
  
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
  
 W `AccessTheWebAsync`, wprowadź następujące zmiany.  
  
-   Dodawanie parametru do akceptowania token anulowania z `StartButton_Click`.  
  
-   Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metodę, aby pobrać witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.  
  
-   Przed wywołaniem `DisplayResults` do wyświetlenia wyników dla poszczególnych witryn pobrany, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.  
  
 Poniższy kod przedstawia te zmiany, które są oznaczone ikoną z gwiazdki.  
  
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
  
 Jeśli wybierzesz **Start** przycisk kilka razy uruchomiona ta aplikacja powinna generować wyniki podobne do następujących danych wyjściowych.  
  
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
  
 Aby wyeliminować częściowej listy, usuń znaczniki komentarza pierwszego wiersza kodu w `StartButton_Click` do wyczyść pola tekstowego użytkownik uruchamia ponownie wykonać operację.  
  
###  <a name="BKMK_RunMultipleOperations"></a>Uruchamianie wielu operacji i danych wyjściowych w kolejce  
 W tym przykładzie trzeci jest najbardziej skomplikowanych, że operacja asynchroniczna za każdym razem, użytkownik zdecyduje się na uruchomieniu aplikacji **Start** przycisk, a wszystkie operacje uruchomienia aż do ukończenia. Żądanych operacji pobierania witryny sieci Web z listy asynchronicznie, ale dane wyjściowe z działania są prezentowane sekwencyjnie. Oznacza to, że przeplatana rzeczywistego działania pobierania jako danych wyjściowych w [rozpoznawanie Wielobieżność](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pokazuje, ale lista wyników dla każdej grupy są przedstawione oddzielnie.  
  
 Operacje udostępniania globalnym <xref:System.Threading.Tasks.Task>, `pendingWork`, która służy jako kontroler proces wyświetlania.  
  
 W tym przykładzie można uruchomić wklejając zmian w kodzie w [kompilowania aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub można postępuj zgodnie z instrukcjami [pobieranie aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobierania go, a następnie uruchom projekt QueueResults.  
  
 Następujące dane wyjściowe przedstawia wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz. Etykieta litera, A, wskazuje, że wynik jest od momentu pierwszego **Start** przycisk zostanie wybrany. Numery wyświetlić kolejność adresów URL na liście elementów docelowych pobierania.  
  
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
  
 Jeśli użytkownik zdecyduje się **Start** trzy razy przycisk, aplikacja generuje dane wyjściowe podobne następujące wiersze. Wiersze informacji rozpoczynających się od krzyżyk podpisać śledzenia (#) postęp aplikacji.  
  
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
  
 Grupy B i C uruchomić przed zakończył grupy A, ale dane wyjściowe dla każdej grupy jest wyświetlany osobno. Wszystkie dane wyjściowe dla grupy A występuje jako pierwszy, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grup w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności adresy URL są wyświetlane na liście adresów URL.  
  
 Jednak nie można przewidzieć kolejność, w którym rzeczywistego wystąpienia pliki do pobrania. Po uruchomieniu wielu grup zadań pobierania, które generują one są wszystkie aktywne. Nie można zakładać, że a – 1 zostaną pobrane przed b-1 i nie można zakładać, że a – 1 zostaną pobrane przed A-2.  
  
#### <a name="global-definitions"></a>Definicje globalnej  
 Przykładowy kod zawiera następujące dwa deklaracje globalne, które są widoczne na wszystkie metody.  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 `Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i uniemożliwia dowolną grupę zakłócania pracy wyświetlania innej grupy. Zmienna znak `group`, dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności etykiet.  
  
#### <a name="the-click-event-handler"></a>Obsługi zdarzeń kliknięcia  
 Program obsługi zdarzeń, `StartButton_Click`, rośnie litery grupy za każdym razem, użytkownik wybierze **Start** przycisku. Następnie wywołań obsługi `AccessTheWebAsync` się uruchomić operacji pobierania.  
  
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
 W tym przykładzie dzieli `AccessTheWebAsync` do dwóch metod. Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania. Metoda używa języka zapytanie zintegrowanym (LINQ query) i <xref:System.Linq.Enumerable.ToArray%2A> uruchomić wszystkie zadania pobierania w tym samym czasie.  
  
 `AccessTheWebAsync`następnie wywołuje `FinishOneGroupAsync` poczekać na ukończenie każdego pobrania i wyświetlenia jej długość.  
  
 `FinishOneGroupAsync`Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`. Czy wartość zapobiega przerwania przez inną operację przed ukończeniem zadania.  
  
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
 Ta metoda przełączanie po kolei zadania pobierania w grupie, oczekiwanie na każdym z nich, wyświetlanie długość pobrany witryny sieci Web i dodawanie długość do całkowitej.  
  
 Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzanie metody zakłócał operacja, która jest już w procesie wyświetlania lub już jest oczekiwane. Jeśli takie działanie jest w toku, wprowadzając operacji oczekiwania kolei.  
  
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
  
 W tym przykładzie można uruchomić wklejając zmian w kodzie w [kompilowania aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub można postępuj zgodnie z instrukcjami [pobieranie aplikacji](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobierania go, a następnie uruchom projekt QueueResults.  
  
#### <a name="points-of-interest"></a>Ważne  
 Wiersze informacji rozpoczynające się znakiem numeru (#) w danych wyjściowych wyjaśnienie, jak działa w tym przykładzie.  
  
 Dane wyjściowe zawierają następujące wzorce.  
  
-   Grupy można uruchomić podczas poprzedniej grupy są wyświetlane dane wyjściowe, ale nie jest przerywana wyświetlanie wynik poprzedniego grupy.  
  
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
  
-   `pendingWork` Zadanie jest `Nothing` na początku `FinishOneGroupAsync` tylko dla grupy A, które uruchamiane jako pierwsze. Grupy A jeszcze nie ukończone wyrażenie await, po osiągnięciu `FinishOneGroupAsync`. W związku z tym kontroli nie zwróciła do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpił.  
  
-   Następujące dwa wiersze zawsze występować razem w danych wyjściowych. Ten kod nie przerywa pracy między uruchamiania operacji grupy `StartButton_Click` i przypisywanie zadań dla grupy w celu `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Po wprowadzeniu grupy `StartButton_Click`, operacja nie wykona wyrażenie await do czasu operacji wejścia `FinishOneGroupAsync`. W związku z tym żadnych innych operacji przejąć kontrolę podczas tego segmentu kodu.  
  
##  <a name="BKMD_SettingUpTheExample"></a>Przeglądanie i uruchamianie przykładową aplikację  
 Aby lepiej zrozumieć przykładową aplikację, można go pobrać, kompilacji samodzielnie lub przejrzeć kod na końcu tego tematu bez stosowania aplikacji.  
  
> [!NOTE]
>  Do uruchomienia w przykładzie jako aplikację pulpitu systemu Windows Presentation Foundation (WPF), musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
###  <a name="BKMK_DownloadingTheApp"></a>Pobieranie aplikacji  
  
1.  Pobierz skompresowany plik z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](http://go.microsoft.com/fwlink/?LinkId=266571).  
  
2.  Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.  
  
3.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
4.  Przejdź do folderu, który przechowuje zdekompresowanych przykładowy kod, a następnie otwórz plik rozwiązania (sln).  
  
5.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.  
  
6.  Wybierz klawisze CTRL + F5, aby skompilować i uruchomić projekt.  
  
###  <a name="BKMK_BuildingTheApp"></a>Tworzenie aplikacji  
 W poniższej sekcji przedstawiono kod służący do kompilacji w przykładzie jako aplikacji WPF.  
  
##### <a name="to-build-a-wpf-app"></a>Do utworzenia aplikacji WPF  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku rozwiń **Visual Basic**, a następnie rozwiń węzeł **Windows**.  
  
4.  Lista typów projektów, wybranie **aplikacji WPF**.  
  
5.  Nazwij projekt `WebsiteDownloadWPF`, a następnie wybierz pozycję **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
6.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
     Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.  
  
7.  W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.  
  
    ```vb  
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
  
     Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.  
  
8.  Dodaj odwołanie do <xref:System.Net.Http>.  
  
9. W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **kod widoku**.  
  
10. W MainWindow.xaml.vb Zastąp kod następującym kodem.  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
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
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. Wybierz klawiszy CTRL + F5, uruchom program, a następnie wybierz pozycję **Start** przycisk kilka razy.  
  
12. Wprowadź zmiany z [Wyłącz przycisk Start](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Anuluj i ponownie uruchom operację](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub [uruchomić wiele operacji i kolejki danych wyjściowych](http://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do obsługi ponownego rozpoczęcia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
