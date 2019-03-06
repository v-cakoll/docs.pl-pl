---
title: 'Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: a9eb9f53b456b309997ef9e6fdb83b770478889b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379123"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)
Asynchroniczne programy można napisać bardziej łatwo i intuicyjnie za pomocą funkcji async/await. Można napisać kod asynchroniczny, który wygląda jak synchroniczny kod i pozwolić kompilatorowi obsługi funkcji wywołania zwrotnego trudne i kontynuacje, które kodu asynchronicznego zazwyczaj pociąga za sobą.  
  
 Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczba bajtów na liście witryn sieci Web. Instruktaż następnie konwertuje ją do asynchronicznego rozwiązania przy użyciu nowych funkcji.  
  
 Jeśli nie chcesz samodzielnie tworzyć aplikacje, możesz pobrać "próbka asynchroniczna: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic) "z [próbki kodu deweloperskiego](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 W tym instruktażu wykonasz następujące zadania:  
  
-   [Aby utworzyć aplikację WPF](#CreateWPFApp)  
  
-   [Aby zaprojektować proste MainWindow WPF](#MainWindow)  
  
-   [Aby dodać odwołanie](#AddRef)  
  
-   [Aby dodać niezbędne instrukcje Importy](#ImportsState)  
  
-   [Aby utworzyć aplikację synchroniczne](#synchronous)  
  
-   [Aby przetestować rozwiązaniu synchronicznym](#testSynch)  
  
-   [Aby przekonwertować GetURLContents metody asynchronicznej](#GetURLContents)  
  
-   [Aby przekonwertować SumPageSizes metody asynchronicznej](#SumPageSizes)  
  
-   [Aby przekonwertować startButton_Click metody asynchronicznej](#startButton)  
  
-   [Aby przetestować rozwiązania asynchroniczne](#testAsynch)  
  
-   [Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework](#GetURLContentsAsync)  
  
-   [Przykład](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Programu Visual Studio 2012 lub nowszym należy zainstalować na komputerze. Aby uzyskać więcej informacji, zobacz [witrynie internetowej firmy Microsoft](https://go.microsoft.com/fwlink/?LinkId=235233).  
  
### <a name="CreateWPFApp"></a> Aby utworzyć aplikację WPF  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz pozycję Visual Basic, a następnie wybierz **aplikacji WPF** z listy typów projektów.  
  
4.  W **nazwa** tekstu wprowadź `AsyncExampleWPF`, a następnie wybierz **OK** przycisku.  
  
     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
## <a name="BKMK_DesignWPFMainWin"></a>   
### <a name="MainWindow"></a> Aby zaprojektować proste MainWindow WPF  
  
1.  W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.  
  
2.  Jeśli **przybornika** okno nie jest widoczna, otwórz **widoku** menu, a następnie wybierz **przybornika**.  
  
3.  Dodaj **przycisk** kontroli i **TextBox** kontrolę **MainWindow** okna.  
  
4.  Wyróżnij **TextBox** sterowania i w **właściwości** okna, ustaw następujące wartości:  
  
    -   Ustaw **nazwa** właściwość `resultsTextBox`.  
  
    -   Ustaw **wysokość** właściwości do 250.  
  
    -   Ustaw **szerokość** właściwości do 500.  
  
    -   Na **tekstu** Określ czcionki o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.  
  
5.  Wyróżnij **przycisk** sterowania i w **właściwości** okna, ustaw następujące wartości:  
  
    -   Ustaw **nazwa** właściwość `startButton`.  
  
    -   Zmień wartość właściwości **zawartości** właściwość **przycisk** do **Start**.  
  
6.  Położenie pola tekstowego i przycisku Tak, aby znajdować się w **MainWindow** okna.  
  
     Aby uzyskać więcej informacji dotyczących projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
## <a name="BKMK_AddReference"></a>   
### <a name="AddRef"></a> Aby dodać odwołanie  
  
1.  W **Eksploratora rozwiązań**, wyróżnij nazwę projektu.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
     **Menadżer odwołań** pojawi się okno dialogowe.  
  
3.  W górnej części okna dialogowego Sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszej.  
  
4.  W **zestawy** obszaru, wybierz **Framework** Jeśli nie została jeszcze wybrana.  
  
5.  Na liście nazw, wybierz **System.Net.Http** pole wyboru.  
  
6.  Wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
## <a name="BKMK_AddStatesandDirs"></a>   
### <a name="ImportsState"></a> Aby dodać niezbędne instrukcje Importy  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **Wyświetl kod**.  
  
2.  Dodaj następujący kod `Imports` instrukcji na górze pliku kodu, jeśli tak nie jest już obecny.  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
## <a name="BKMK_CreatSynchApp"></a>   
### <a name="synchronous"></a> Aby utworzyć aplikację synchroniczne  
  
1.  W oknie projektu, MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.vb.  
  
2.  W pliku MainWindow.xaml.vb, skopiuj poniższy kod do treści `startButton_Click`:  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     Kod wywołuje metodę, która napędza aplikację, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click`.  
  
3.  Kod używany w rozwiązaniu synchronicznym zawiera poniższe cztery metody:  
  
    -   `SumPageSizes`, która pobiera listę adresów URL strony sieci Web, z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.  
  
    -   `SetUpURLList`, która tworzy i zwraca listę adresów internetowych.  
  
    -   `GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość w postaci tablicy bajtów.  
  
    -   `DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.  
  
     Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.vb:  
  
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
  
## <a name="BKMK_TestSynchSol"></a>   
### <a name="testSynch"></a> Aby przetestować rozwiązaniu synchronicznym  
  
1.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Powinien pojawić się dane wyjściowe podobne do poniższej listy.  
  
    ```  
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
  
     Należy zauważyć, że zajmuje kilka sekund, aby wyświetlić liczby elementów. W tym czasie wątku interfejsu użytkownika jest blokowany, aż do żądanych zasobów do pobrania. W rezultacie nie można przenieść zmaksymalizować, zminimalizować lub nawet Zamknij okna, po dokonaniu wyboru **Start** przycisku. Tych działań zakończyć się niepowodzeniem, dopóki nie pojawiają się rozpocząć liczby bajtów. Jeśli witryna sieci Web nie odpowiada, masz żadne oznaki, witryn, które nie powiodło się. Trudno jest nawet zakończyć oczekiwanie i zamknięcie programu.  
  
## <a name="BKMK_ConvertGtBtArr"></a>   
### <a name="GetURLContents"></a> Aby przekonwertować GetURLContents metody asynchronicznej  
  
1.  Aby konwertować synchroniczne rozwiązanie do asynchronicznego rozwiązania, najlepszym miejscem do rozpoczęcia jest w `GetURLContents` ponieważ wywołania <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web . .NET Framework ułatwia konwersję poprzez dostarczenie asynchronicznych wersji obu tych metod.  
  
     Aby uzyskać więcej informacji o metodach, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Postępuj zgodnie z instrukcjami w tym przewodniku, wyświetlane są kilka błędów kompilatora. Można je zignorować i kontynuować z tym przewodnikiem.  
  
     Zmień metodę, która jest wywołana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, opartego na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  `GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>. W tym przypadku *zmiennej zwracanego zadania*, `TResult`, ma typ <xref:System.Net.WebResponse>. Zadanie jest obietnicą utworzenia rzeczywistej `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.  
  
     Aby pobrać `WebResponse` wartości z zadania, zastosuj [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator wywołania do `GetResponseAsync`, jak pokazano w poniższym kodzie.  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     `Await` Operator zawiesza wykonywanie bieżącej metody `GetURLContents`, aż oczekiwane zadanie zostało ukończone. W międzyczasie formant powraca do obiektu wywołującego metody bieżącej. W tym przykładzie jest bieżąca metoda `GetURLContents`, a obiekt wywołujący jest `SumPageSizes`. Po zakończeniu zadania, uzgodnionego `WebResponse` obiekt jest generowany z wartością oczekiwane zadanie i przypisana do zmiennej `response`.  
  
     Poprzednia instrukcja można podzielić na dwie poniższe instrukcje, aby wyjaśnić, co się dzieje.  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`. Następnie `Await` operator jest stosowany do zadania do pobrania `WebResponse` wartość.  
  
     Jeśli metoda async ma robić prace, które nie są zależne od zakończenia tego zadania, metody można kontynuować pracę między te dwie instrukcje po wywołaniu metody asynchronicznej i przed await operator jest stosowany. Aby uzyskać przykłady, zobacz [jak: Wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Ponieważ dodałeś `Await` występuje błąd kompilatora operatora w poprzednim kroku. Operator może służyć tylko w przypadku metod, które są oznaczone [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator. Ignorowanie błędu podczas Powtórz procedurę konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.  
  
    -   Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Lub `CopyToAsync` metoda kopiuje bajtów do jej argument `content`i nie zwraca zrozumiałą wartość. W wersji synchroniczne wywołanie `CopyTo` jest prostą instrukcję, która nie zwraca wartości. Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>. Zadanie funkcje takie jak "Task(void)" i włącza metodę oczekiwanie. Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  Wszystkie opcje, które pozostają do wykonania `GetURLContents` jest dostosowanie podpis metody. Możesz użyć `Await` operatora tylko w przypadku metod, które są oznaczone [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator. Dodaj modyfikator do oznaczania metody jako *metody asynchronicznej*, jak pokazano w poniższym kodzie.  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  Zwracany typ metody asynchronicznej może składać się wyłącznie <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. W języku Visual Basic, metoda musi być `Function` zwracającego `Task` lub `Task(Of T)`, lub metoda musi być `Sub`. Zazwyczaj `Sub` metoda jest używana tylko w przypadku programu async obsługi zdarzeń, gdzie `Sub` jest wymagana. W innych przypadkach należy użyć `Task(T)` Jeśli metoda ukończone ma [zwracają](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcję, która zwraca wartość typu T i używasz `Task` jeśli ukończone metoda nie zwraca zrozumiałą wartość.  
  
     Aby uzyskać więcej informacji, zobacz [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
     Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów. W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów. W podpisie metody, należy wprowadzić następujące zmiany:  
  
    -   Zmień typ zwracany `Task(Of Byte())`.  
  
    -   Zgodnie z Konwencją metod asynchronicznych mają nazwy, które kończą się na "Async", więc Zmień nazwę metody `GetURLContentsAsync`.  
  
     Poniższy kod przedstawia te zmiany.  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     Za pomocą tych kilku zmian konwersji `GetURLContents` metody asynchronicznej jest pełny.  
  
## <a name="BKMK_ConvertSumPagSzs"></a>   
### <a name="SumPageSizes"></a> Aby przekonwertować SumPageSizes metody asynchronicznej  
  
1.  Powtórz kroki z poprzedniej procedury, aby uzyskać `SumPageSizes`. Najpierw należy zmienić wywołanie `GetURLContents` do wywołania asynchronicznego.  
  
    -   Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.  
  
    -   Zastosuj `Await` do zadania, `GetURLContentsAsync` zwraca uzyskać bajt tablica wartości.  
  
     Poniższy kod przedstawia te zmiany.  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     Poprzednie przypisanie Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  W podpisie metody, należy wprowadzić następujące zmiany:  
  
    -   Oznacz metodę z `Async` modyfikator.  
  
    -   Dodaj "Async" w nazwie metody.  
  
    -   Nie jest zmienną zwracany nie zadań, T, tym razem, ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `Return` instrukcja.) Jednak metoda musi zwracać `Task` jako oczekujący. W związku z tym, Zmień typ metody z `Sub` do `Function`. Zwracany typ funkcji jest `Task`.  
  
     Poniższy kod przedstawia te zmiany.  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     Konwersja `SumPageSizes` do `SumPageSizesAsync` zostało zakończone.  
  
## <a name="BKMK_Cnvrtbttn1"></a>   
### <a name="startButton"></a> Aby przekonwertować startButton_Click metody asynchronicznej  
  
1.  W procedurze obsługi zdarzeń Zmień nazwę wywoływanej metody z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiłeś.  
  
2.  Ponieważ `SumPageSizesAsync` to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.  
  
     Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`. To wywołanie zwraca `Task`, a nie `Task(T)`.  
  
     Tak jak w poprzednich procedur można przekonwertować wywołanie za pomocą jednej instrukcji lub dwóch instrukcji. Poniższy kod przedstawia te zmiany.  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  Aby uniknąć przypadkowego ponownego wprowadzania operacji, należy dodać następującą instrukcję w górnej części `startButton_Click` wyłączyć **Start** przycisku.  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     Możesz włączyć przycisku na końcu programu obsługi zdarzeń.  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [obsługi współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Na koniec należy dodać `Async` modyfikator deklaracji, aby program obsługi zdarzeń może poczekać `SumPagSizesAsync`.  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń. Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi być `Sub` procedury w Visual Basic.  
  
     Konwersja przetwarzania synchronicznego w celu asynchronicznego projektu zostało ukończone.  
  
## <a name="BKMK_testAsynchSolution"></a>   
### <a name="testAsynch"></a> Aby przetestować rozwiązania asynchroniczne  
  
1.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
2.  Dane wyjściowe podobne dane wyjściowe w rozwiązaniu synchronicznym powinna zostać wyświetlona. Jednak zauważyć następujące różnice.  
  
    -   Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania. Na przykład oba programy zawiera wiersz w `startButton_Click` , czyści pole tekstowe. Celem jest czyścić pole tekstowe między działa, jeśli wybierzesz **Start** przycisk, aby po raz drugi, po pojawieniu się jeden zestaw wyników. W to wersja synchroniczna pole tekstowe jest wyczyszczone przed zliczeń pojawiają się po raz drugi, gdy odbywa się pliki do pobrania i jest bezpłatna wykonywanie innych zadań w wątku interfejsu użytkownika. W wersjach asynchronicznych, pola tekstowego czyści natychmiast, po dokonaniu wyboru **Start** przycisku.  
  
    -   Co najważniejsze wątek interfejsu użytkownika nie jest zablokowane podczas jej pliki do pobrania. Możesz przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web liczone, a wyświetlane. Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisku (x czerwone pola w prawym górnym rogu).  
  
## <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
### <a name="GetURLContentsAsync"></a> Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework  
  
1.  .NET Framework 4.5 zapewnia wiele metod asynchronicznych, których można użyć. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, wykonuje tylko potrzebne w ramach tego przewodnika. Można używać go zamiast `GetURLContentsAsync` metody, który został utworzony w wcześniejszym etapie procedury.  
  
     Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`. Dodaj następującą deklarację na początku metody.  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  W `SumPageSizesAsync,` Zastąp wywołanie usługi `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  Usunąć lub skomentować `GetURLContentsAsync` metodę, która powstała z jednego.  
  
4.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Zachowanie tej wersji programu project powinien odpowiadać zachowanie, które opisano procedury "Aby test asynchronicznego rozwiązania", ale o jeszcze mniejszym nakładzie pracy ze strony użytkownika.  
  
## <a name="BKMK_CompleteCodeExamples"></a> Przykład  
 Poniższy kod zawiera pełny przykład konwersja przez synchroniczny do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metodę, która powstała z jednego. Należy zauważyć, że silnie przypomina oryginalnej, synchroniczne rozwiązanie.  
  
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
  
 Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody `GetByteArrayAsync`.  
  
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
  
        '' Two-step async call.  
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
- [Próbka asynchroniczna: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await, operator](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [Programowanie asynchroniczne opartego na zadaniach (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Instrukcje: Wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
