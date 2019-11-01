---
title: 'Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: feaa1e298cda852492e020a5fa81845fb887f102
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197026"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)

Można łatwiej pisać programy asynchroniczne i intuicyjnie przy użyciu funkcji asynchronicznych/await. Można napisać kod asynchroniczny, który wygląda podobnie do kodu synchronicznego i pozwolić kompilatorowi obsłużyć trudne funkcje wywołania zwrotnego i kontynuację, która zwykle wiąże się z kodem asynchronicznym.

Aby uzyskać więcej informacji o funkcji asynchronicznej, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

Ten Instruktaż rozpoczyna się od synchronicznej aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów na liście witryn sieci Web. Następnie Instruktaż konwertuje aplikację na rozwiązanie asynchroniczne przy użyciu nowych funkcji.

Jeśli nie chcesz samodzielnie kompilować aplikacji, możesz pobrać "przykład Async: uzyskiwanie dostępu do przewodnika sieci Web (C# i Visual Basic)" z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

W tym instruktażu wykonasz następujące zadania:

> [!div class="checklist"]
>
> - [Tworzenie aplikacji WPF](#create-a-wpf-application)
> - [Projektowanie prostego MainWindow WPF](#design-a-simple-wpf-mainwindow)
> - [Dodaj odwołanie](#add-a-reference)
> - [Dodaj wymagane instrukcje importów](#add-necessary-imports-statements)
> - [Tworzenie aplikacji synchronicznej](#create-a-synchronous-application)
> - [Testowanie rozwiązania synchronicznego](#test-the-synchronous-solution)
> - [Konwertuj GetURLContents na metodę asynchroniczną](#convert-geturlcontents-to-an-asynchronous-method)
> - [Konwertuj SumPageSizes na metodę asynchroniczną](#convert-sumpagesizes-to-an-asynchronous-method)
> - [Konwertuj startButton_Click na metodę asynchroniczną](#convert-startbutton_click-to-an-asynchronous-method)
> - [Przetestuj rozwiązanie asynchroniczne](#test-the-asynchronous-solution)
> - [Zastąp metodę GetURLContentsAsync metodą .NET Framework](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

Zapoznaj się z sekcją [przykładową](#example) kompletnego przykładu asynchronicznego.

## <a name="prerequisites"></a>Wymagania wstępne

Na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy. Aby uzyskać więcej informacji, zobacz stronę [pliki do pobrania](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) programu Visual Studio.

## <a name="create-a-wpf-application"></a>Tworzenie aplikacji WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

    Zostanie otwarte okno dialogowe **Nowy projekt** .

3. W okienku **zainstalowane szablony** wybierz pozycję Visual Basic, a następnie wybierz pozycję **Aplikacja WPF** z listy typów projektów.

4. W polu tekstowym **Nazwa** wprowadź `AsyncExampleWPF`, a następnie wybierz przycisk **OK** .

    Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.

## <a name="design-a-simple-wpf-mainwindow"></a>Projektowanie prostego MainWindow WPF

1. W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .

2. Jeśli okno **Przybornik** nie jest widoczne, otwórz menu **Widok** , a następnie wybierz **Przybornik**.

3. Dodaj kontrolkę **przycisk** i kontrolkę **TextBox** do okna **MainWindow** .

4. Zaznacz kontrolkę **TextBox** , a następnie w oknie **Właściwości** ustaw następujące wartości:

    - Ustaw właściwość **name** na `resultsTextBox`.

    - Ustaw właściwość **Height** na 250.

    - Ustaw właściwość **Width** na 500.

    - Na karcie **tekst** Określ czcionkę o stałej szerokości, taką jak Lucida Console lub globalne.

5. Zaznacz kontrolkę **przycisk** , a następnie w oknie **Właściwości** ustaw następujące wartości:

    - Ustaw właściwość **name** na `startButton`.

    - Zmień wartość właściwości **zawartości** z **przycisku** na **Rozpocznij**.

6. Umieść pole tekstowe i przycisk tak, aby oba elementy pojawiły się w oknie **MainWindow** .

    Aby uzyskać więcej informacji na temat projektant XAML WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Dodaj odwołanie

1. W **Eksplorator rozwiązań**zaznacz nazwę projektu.

2. Na pasku menu wybierz **projekt**, **Dodaj odwołanie**.

    Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .

3. W górnej części okna dialogowego upewnij się, że projekt ma wartość docelową .NET Framework 4,5 lub wyższą.

4. W obszarze **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.

5. Na liście nazw, zaznacz pole wyboru **System .NET. http** .

6. Wybierz przycisk **OK** , aby zamknąć okno dialogowe.

## <a name="add-necessary-imports-statements"></a>Dodaj wymagane instrukcje importów

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.

2. Dodaj następujące instrukcje `Imports` w górnej części pliku kodu, jeśli jeszcze nie istnieją.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Tworzenie aplikacji synchronicznej

1. W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk **Start** , aby utworzyć procedurę obsługi zdarzeń `startButton_Click` w pliku MainWindow. XAML. vb.

2. W MainWindow. XAML. vb Skopiuj następujący kod do treści `startButton_Click`:

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    Kod wywołuje metodę, która dysków aplikacji, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click`.

3. Kod rozwiązania synchronicznego zawiera następujące cztery metody:

    - `SumPageSizes`, który pobiera listę adresów URL stron sieci Web z `SetUpURLList`, a następnie wywołuje `GetURLContents` i `DisplayResults` do przetwarzania każdego adresu URL.

    - `SetUpURLList`, co umożliwia i zwraca listę adresów sieci Web.

    - `GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość jako tablicę bajtów.

    - `DisplayResults`, która wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.

    Skopiuj poniższe cztery metody, a następnie wklej je w ramach procedury obsługi zdarzeń `startButton_Click` w MainWindow. XAML. vb:

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a>Testowanie rozwiązania synchronicznego

1. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

    Powinny pojawić się dane wyjściowe podobne do poniższej listy:

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    Należy zauważyć, że wyświetlanie liczników zajmuje kilka sekund. W tym czasie wątek interfejsu użytkownika jest blokowany podczas oczekiwania na pobranie żądanych zasobów. W związku z tym nie można przenieść, zmaksymalizować ani zminimalizować, a nawet zamknąć okno wyświetlania po wybraniu przycisku **Rozpocznij** . Te działania kończą się niepowodzeniem, dopóki liczba bajtów nie zostanie wyświetlona. Jeśli witryna sieci Web nie odpowiada, nie ma informacji o tym, która lokacja nie powiodła się. Trudno jest nawet przestać czekać i zamknąć program.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Konwertuj GetURLContents na metodę asynchroniczną

1. Aby przekonwertować rozwiązanie synchroniczne na rozwiązanie asynchroniczne, najlepszym miejscem do uruchomienia jest w `GetURLContents`, ponieważ wywołania metody <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> i do metody <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> to miejsce, w którym aplikacja uzyskuje dostęp do sieci Web. .NET Framework ułatwia konwersję, dostarczając asynchroniczną wersję obu tych metod.

    Aby uzyskać więcej informacji na temat metod, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Po wykonaniu kroków opisanych w tym instruktażu wyświetlane są kilka błędów kompilatora. Można je zignorować i kontynuować z przewodnikiem.

    Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznej metody <xref:System.Net.WebRequest.GetResponseAsync%2A> opartej na zadaniach.

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` zwraca <xref:System.Threading.Tasks.Task%601>. W takim przypadku *zmienna zwracająca zadanie*, `TResult`, ma typ <xref:System.Net.WebResponse>. Zadanie to obietnica do utworzenia rzeczywistego obiektu `WebResponse` po pobraniu żądanych danych, a zadanie zostało wykonane w celu ukończenia.

    Aby pobrać wartość `WebResponse` z zadania, Zastosuj operator [await](../../../../visual-basic/language-reference/operators/await-operator.md) do wywołania `GetResponseAsync`, jak pokazano w poniższym kodzie.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    Operator `Await` zawiesza wykonywanie bieżącej metody, `GetURLContents`, dopóki zadanie nie zostanie ukończone. W międzyczasie formant powraca do obiektu wywołującego bieżącej metody. W tym przykładzie bieżąca metoda jest `GetURLContents`, a obiekt wywołujący jest `SumPageSizes`. Po zakończeniu zadania zaznaczono obiekt `WebResponse`, który jest tworzony jako wartość oczekującego zadania i przypisany do zmiennej `response`.

    Poprzednią instrukcję można podzielić na dwie następujące instrukcje, aby wyjaśnić, co się dzieje.

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`. Następnie do zadania zostanie zastosowany operator `Await`, aby pobrać wartość `WebResponse`.

    Jeśli metoda async działa tak, aby nie zależała od ukończenia zadania, Metoda może kontynuować działanie między tymi dwiema instrukcjami po wywołaniu metody asynchronicznej i przed zastosowaniem operatora await. Aby zapoznać się z przykładami, zobacz [How to: równoległe wykonywanie wielu żądań sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [instrukcje: rozszerzona instrukcja Async przy użyciu Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Ponieważ dodano operator `Await` w poprzednim kroku, wystąpi błąd kompilatora. Operatora można używać tylko w metodach, które są oznaczone modyfikatorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) . Zignoruj błąd podczas powtarzania kroków konwersji, aby zastąpić wywołanie do `CopyTo` z wywołaniem `CopyToAsync`.

    - Zmień nazwę metody, która jest wywoływana do <xref:System.IO.Stream.CopyToAsync%2A>.

    - Metoda `CopyTo` lub `CopyToAsync` Kopiuje bajty do jej argumentu, `content`i nie zwraca wartości znaczącej. W wersji synchronicznej wywołanie `CopyTo` jest prostą instrukcją, która nie zwraca wartości. Wersja asynchroniczna, `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>. Zadanie działa jak "Task (void)" i umożliwia oczekiwanie metody. Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         Poprzednia instrukcja skraca następujące dwa wiersze kodu.

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. Wszystkie te, które pozostały do wykonania w `GetURLContents` to dostosowanie sygnatury metody. Operatora `Await` można używać tylko w metodach, które są oznaczone modyfikatorem [Async](../../../../visual-basic/language-reference/modifiers/async.md) . Dodaj modyfikator, aby oznaczyć metodę jako *metodę asynchroniczną*, jak pokazano w poniższym kodzie.

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. Zwracany typ metody asynchronicznej może być <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. W Visual Basic Metoda musi być `Function`, która zwraca `Task` lub `Task(Of T)`, lub metoda musi być `Sub`. Zazwyczaj Metoda `Sub` jest używana tylko w obsłudze zdarzeń asynchronicznych, gdzie `Sub` jest wymagany. W innych przypadkach należy używać `Task(T)`, jeśli metoda zakończona zawiera instrukcję [Return](../../../../visual-basic/language-reference/statements/return-statement.md) , która zwraca wartość typu t, i używa `Task`, jeśli metoda zakończona nie zwraca wartości znaczącej.

    Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

    Metoda `GetURLContents` ma instrukcję return, a instrukcja zwraca tablicę bajtów. W związku z tym zwracanym typem wersji asynchronicznej jest zadanie (T), gdzie T jest tablicą bajtów. Wprowadź następujące zmiany w podpisie metody:

    - Zmień zwracany typ na `Task(Of Byte())`.

    - Zgodnie z Konwencją metody asynchroniczne mają nazwy kończące się na "Async", więc Zmień nazwę metody `GetURLContentsAsync`.

    Poniższy kod przedstawia te zmiany.

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    Po wprowadzeniu tych zmian konwersja `GetURLContents` na metodę asynchroniczną zostanie zakończona.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Konwertuj SumPageSizes na metodę asynchroniczną

1. Powtórz kroki opisane w poprzedniej procedurze dla `SumPageSizes`. Najpierw Zmień wywołanie `GetURLContents` na wywołanie asynchroniczne.

    - Zmień nazwę metody, która jest wywoływana z `GetURLContents` na `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiono.

    - Zastosuj `Await` do zadania, które `GetURLContentsAsync` zwraca, aby uzyskać wartość tablicy bajtowej.

    Poniższy kod przedstawia te zmiany.

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    Poprzednie przypisanie skraca dwa następujące wiersze kodu.

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. Wprowadź następujące zmiany w podpisie metody:

    - Oznacz metodę za pomocą modyfikatora `Async`.

    - Dodaj wartość "Async" do nazwy metody.

    - Brak zmiennej zwracanej zadania, T, ten czas, ponieważ `SumPageSizesAsync` nie zwraca wartości dla T. (metoda nie ma `Return` instrukcji.) Jednak metoda musi zwrócić `Task`, aby można było oczekiwać. W związku z tym Zmień typ metody z `Sub` na `Function`. Zwracany typ funkcji jest `Task`.

    Poniższy kod przedstawia te zmiany.

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    Konwersja `SumPageSizes` na `SumPageSizesAsync` została zakończona.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Konwertuj startButton_Click na metodę asynchroniczną

1. W programie obsługi zdarzeń Zmień nazwę wywołanej metody z `SumPageSizes` na `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiono.

2. Ponieważ `SumPageSizesAsync` jest metodą asynchroniczną, Zmień kod w programie obsługi zdarzeń, aby oczekiwać na wynik.

    Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`. Wywołanie zwraca `Task`, a nie `Task(T)`.

    Jak w poprzednich procedurach, można skonwertować wywołanie przy użyciu jednej instrukcji lub dwóch instrukcji. Poniższy kod przedstawia te zmiany.

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. Aby zapobiec przypadkowemu ponownemu wprowadzaniu operacji, Dodaj następującą instrukcję w górnej części `startButton_Click`, aby wyłączyć przycisk **Uruchom** .

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    Przycisk można ponownie włączyć na końcu programu obsługi zdarzeń.

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4. Na koniec Dodaj modyfikator `Async` do deklaracji, aby program obsługi zdarzeń mógł oczekiwać `SumPagSizesAsync`.

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    Zazwyczaj nazwy programów obsługi zdarzeń nie są zmieniane. Zwracany typ nie jest zmieniany na `Task`, ponieważ programy obsługi zdarzeń muszą być `Sub` procedurami w Visual Basic.

    Konwersja projektu z synchronicznego na przetwarzanie asynchroniczne zostało zakończone.

## <a name="test-the-asynchronous-solution"></a>Przetestuj rozwiązanie asynchroniczne

1. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

2. Powinny pojawić się dane wyjściowe podobne do danych wyjściowych rozwiązania synchronicznego. Jednak Zwróć uwagę na następujące różnice.

    - Wyniki nie są wykonywane w tym samym czasie po zakończeniu przetwarzania. Na przykład oba programy zawierają wiersz w `startButton_Click`, który czyści pole tekstowe. Celem jest wyczyszczenie pola tekstowego między uruchomieniami w przypadku wybrania przycisku **Rozpocznij** po raz drugi, po wyświetleniu jednego zestawu wyników. W wersji synchronicznej, pole tekstowe jest czyszczone tuż przed wyświetleniem liczby po raz drugi, po ukończeniu pobierania, a wątek interfejsu użytkownika jest bezpłatny, aby wykonać inne czynności. W wersji asynchronicznej, pole tekstowe czyści natychmiast po wybraniu przycisku **Rozpocznij** .

    - Co najważniejsze, wątek interfejsu użytkownika nie jest blokowany podczas pobierania. Możesz przenosić lub zmieniać rozmiar okna, gdy zasoby sieci Web są pobierane, zliczane i wyświetlane. Jeśli jedna z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając przycisk **Zamknij** (x w czerwono w prawym górnym rogu).

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>Zastąp metodę GetURLContentsAsync metodą .NET Framework

1. .NET Framework zawiera wiele metod asynchronicznych, których można użyć. Jednym z nich jest metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType>, która jest tylko potrzebne do tego przewodnika. Można jej użyć zamiast metody `GetURLContentsAsync` utworzonej we wcześniejszej procedurze.

    Pierwszym krokiem jest utworzenie obiektu <xref:System.Net.Http.HttpClient> w metodzie `SumPageSizesAsync`. Dodaj następującą deklarację na początku metody.

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. W `SumPageSizesAsync,` Zastąp wywołanie metody `GetURLContentsAsync` wywołaniem metody `HttpClient`.

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. Usuń lub Skomentuj zapisaną metodę `GetURLContentsAsync`.

4. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .

    Zachowanie tej wersji projektu powinno być zgodne z zachowaniem, że procedura "Aby przetestować rozwiązanie asynchroniczne" opisuje, ale nawet mniej wysiłku od użytkownika.

## <a name="example"></a>Przykład

Poniżej znajduje się pełny przykład przekonwertowanego rozwiązania asynchronicznego, które używa metody `GetURLContentsAsync` asynchronicznej. Należy zauważyć, że silnie przypomina oryginalne, synchroniczne rozwiązanie.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

Poniższy kod zawiera pełny przykład rozwiązania, które używa metody `HttpClient`, `GetByteArrayAsync`.

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a>Zobacz także

- [Przykład asynchroniczny: uzyskiwanie dostępu doC# przewodnika sieci Web (i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Programowanie asynchroniczne oparte na zadaniach (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
