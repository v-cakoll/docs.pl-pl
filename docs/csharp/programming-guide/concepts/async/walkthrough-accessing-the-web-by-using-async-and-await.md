---
title: 'Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 33145f6a7ececd85e6eeaebb80a81f3075878761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338133"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)
Asynchroniczne programy można napisać łatwiejsze i bardziej intuicyjne za pomocą funkcji asynchronicznej/await. Możesz zapisać asynchroniczne kod, który wygląda jak synchroniczne kodu i umożliwić kompilatora obsługiwać funkcje wywołania zwrotnego trudne i kontynuacje, które kod asynchroniczny zazwyczaj pociąga za sobą.  
  
 Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów w postaci listy witryn sieci Web. Instruktaż następnie konwertuje aplikacji do asynchronicznego rozwiązania przy użyciu nowych funkcji.  
  
 Jeśli nie chcesz tworzyć aplikacje samodzielnie, możesz pobrać [próbki Async: uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   [Aby utworzyć aplikację programu WPF](#CreateWPFApp)  
  
-   [Projektowanie proste właściwości MainWindow WPF](#MainWindow)  
  
-   [Można dodać odwołania](#AddRef)  
  
-   [Aby dodać niezbędne przy użyciu dyrektyw](#usingDir)  
  
-   [Aby utworzyć aplikację synchroniczne](#synchronous)  
  
-   [Aby przetestować synchroniczne rozwiązania](#testSynch)  
  
-   [Aby przekonwertować GetURLContents metody asynchronicznej](#GetURLContents)  
  
-   [Aby przekonwertować SumPageSizes metody asynchronicznej](#SumPageSizes)  
  
-   [Aby przekonwertować startButton_Click metody asynchronicznej](#startButton)  
  
-   [Aby przetestować asynchroniczne rozwiązania](#testAsynch)  
  
-   [Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework](#GetURLContentsAsync)  
  
-   [Przykład](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
###  <a name="CreateWPFApp"></a> Aby utworzyć aplikację programu WPF  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku, wybierz pozycję Visual C#, a następnie wybierz **aplikacji WPF** z listy typów projektów.  
  
4.  W **nazwa** tekst wprowadź `AsyncExampleWPF`, a następnie wybierz pozycję **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> Projektowanie proste właściwości MainWindow WPF  
  
1.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
2.  Jeśli **przybornika** okno nie jest widoczne, otwórz **widoku** menu, a następnie wybierz pozycję **przybornika**.  
  
3.  Dodaj **przycisk** kontroli i **pole tekstowe** formant **właściwości MainWindow** okna.  
  
4.  Wyróżnij **pole tekstowe** kontroli i w **właściwości** okna, ustaw następujące wartości:  
  
    -   Ustaw **nazwa** właściwości `resultsTextBox`.  
  
    -   Ustaw **wysokość** właściwości 250.  
  
    -   Ustaw **szerokość** właściwości do 500.  
  
    -   Na **tekst** karcie, określ czcionkę o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.  
  
5.  Wyróżnij **przycisk** kontroli i w **właściwości** okna, ustaw następujące wartości:  
  
    -   Ustaw **nazwa** właściwości `startButton`.  
  
    -   Zmień wartość **zawartości** właściwość z **przycisk** do **Start**.  
  
6.  Ustaw pole tekstowe i przycisk Tak, aby znajdować się w **właściwości MainWindow** okna.  
  
     Aby uzyskać więcej informacji na temat projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> Można dodać odwołania  
  
1.  W **Eksploratora rozwiązań**, zaznacz nazwę projektu.  
  
2.  Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.  
  
     **Menedżera odwołań** zostanie wyświetlone okno dialogowe.  
  
3.  W górnej części okna dialogowego Sprawdź, czy projekt jest docelowo programu .NET Framework 4.5 lub nowszej.  
  
4.  W **zestawy** obszarze, wybierz **Framework** Jeśli nie jest już wybrana.  
  
5.  Na liście nazw wybierz **System.Net.Http** pole wyboru.  
  
6.  Wybierz **OK** przycisk, aby zamknąć okno dialogowe.  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> Aby dodać niezbędne przy użyciu dyrektyw  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.  
  
2.  Dodaj następujące `using` dyrektywy w górnej części pliku kodu, jeśli nie są one już istnieje.  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> Aby utworzyć aplikację synchroniczne  
  
1.  W oknie projektowania MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.  
  
2.  W MainWindow.xaml.cs, skopiuj następujący kod do treści `startButton_Click`:  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     Kod wywołuje metodę dyski aplikacji, `SumPageSizes`i wyświetla komunikat, gdy formant powróci do `startButton_Click`.  
  
3.  Kod dla rozwiązania synchroniczne zawiera następujących metod:  
  
    -   `SumPageSizes`, która pobiera listę adresów URL strony sieci Web z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.  
  
    -   `SetUpURLList`, które tworzy i zwraca listę adresów internetowych.  
  
    -   `GetURLContents`, które pliki do pobrania zawartości z poszczególnych witryn i zwraca zawartość jako tablicę bajtów.  
  
    -   `DisplayResults`, które wskazuje liczbę bajtów w tablicy bajtów dla każdego adresu URL.  
  
     Skopiuj następujące cztery metody, a następnie wklej je w obszarze `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs:  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290136.aspx",  
            "http://msdn.microsoft.com/library/ee256749.aspx",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> Aby przetestować synchroniczne rozwiązania  
  
1.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Powinna pojawić się dane wyjściowe podobne poniżej.  
  
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
  
     Zwróć uwagę, że ma kilka sekund, aby wyświetlić liczniki. W tym czasie wątku interfejsu użytkownika jest zablokowane podczas oczekiwania wymagane zasoby do pobrania. W związku z tym nie można przenieść zmaksymalizować, zminimalizować lub nawet zamknąć okna po wybraniu **Start** przycisku. Tych działań niepowodzeniem, dopóki zacząć występować liczby bajtów. Jeśli witryna sieci Web nie odpowiada, należy nie wskazuje witryn, które nie powiodło się. Trudno jest nawet zatrzymać oczekiwania i zamknąć program.  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> Aby przekonwertować GetURLContents metody asynchronicznej  
  
1.  Aby przekonwertować synchroniczne rozwiązania do asynchronicznego rozwiązania, najlepiej zacząć znajduje się w `GetURLContents` ponieważ wywołań <xref:System.Net.HttpWebRequest> — metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> — metoda <xref:System.IO.Stream.CopyTo%2A> są, których aplikacja uzyskuje dostęp do sieci web . .NET Framework ułatwia konwersję podając obu metod asynchronicznych wersji.  
  
     Aby uzyskać więcej informacji na temat metod, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.  
  
    > [!NOTE]
    >  Wykonaj kroki opisane w tym przewodniku, wyświetlane są kilka błędów. Można je zignorować i kontynuować z tym przewodnikiem.  
  
     Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, oparty na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  `GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>. W takim przypadku *zadań zwracanej zmiennej*, `TResult`, ma typ <xref:System.Net.WebResponse>. Zadanie jest obietnicę w celu uzyskania rzeczywistego `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.  
  
     Można pobrać `WebResponse` wartości z zadania, zastosuj [await](../../../../csharp/language-reference/keywords/await.md) operator wywołania `GetResponseAsync`, jak pokazano w następującym kodem.  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     `await` Operator wstrzymuje wykonywanie bieżącej metody `GetURLContents`, dopóki nie oczekiwano zadanie zostało ukończone. Tymczasem kontroli zwraca do wywołującego bieżącej metody. W tym przykładzie jest bieżąca metoda `GetURLContents`, a element wywołujący jest `SumPageSizes`. Po zakończeniu zadania, uzgodnionej `WebResponse` obiekt został utworzony jako wartość oczekiwano zadań i przypisaną do zmiennej `response`.  
  
     Poprzednia można podzielić na następujące dwie instrukcje wyjaśnienie, co się stanie.  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`. Następnie await operator jest stosowany do zadań, które można pobrać `WebResponse` wartość.  
  
     Jeśli Twoje metody asynchronicznej pracy, który nie jest zależny od ukończenia zadania, metoda można kontynuować pracy między te dwie instrukcje po wywołaniu metody async i przed `await` zastosować operatora. Przykłady można znaleźć [jak: wiele sieci Web żądania równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  Ponieważ dodano `await` wystąpi błąd kompilatora operatora w poprzednim kroku. Operator może być używana tylko w metody, które są oznaczone ikoną z [async](../../../../csharp/language-reference/keywords/async.md) modyfikator. Ignorowanie błędu podczas Powtórz kroki konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.  
  
    -   Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.  
  
    -   `CopyTo` Lub `CopyToAsync` metody kopiuje bajtów do jej argument `content`i nie zwraca wartości łatwy do rozpoznania. W wersji synchroniczne wywołanie `CopyTo` jest proste instrukcja, która nie zwraca wartości. Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>. Zadanie funkcje takie jak "Task(void)" i umożliwia metoda jest oczekiwane. Zastosuj `Await` lub `await` wywołania `CopyToAsync`, jak pokazano w następującym kodem.  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  Wszystkie opcje, które pozostanie w `GetURLContents` jest dostosowanie podpis metody. Można użyć `await` operator tylko w metodach, które są oznaczone ikoną z [async](../../../../csharp/language-reference/keywords/async.md) modyfikator. Dodaj modyfikator do Oznacz metodę jako *metody asynchronicznej*, jak pokazano w następującym kodem.  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  Zwracany typ metody asynchronicznej może być tylko <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, lub `void` w języku C#. Zazwyczaj typ zwracany `void` jest używana tylko w asynchronicznej obsłudze zdarzeń, gdzie `void` jest wymagana. W pozostałych przypadkach można użyć `Task(T)` Jeśli ukończono metoda ma [zwracać](../../../../csharp/language-reference/keywords/return.md) instrukcji, która zwraca wartość typu T i używasz `Task` Jeśli ukończono — metoda nie zwraca wartości łatwy do rozpoznania. Można potraktować `Task` zwracany typ jako oznaczające "Task(void)."  
  
     Aby uzyskać więcej informacji, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
     Metoda `GetURLContents` zawiera instrukcję return i instrukcja zwraca tablicę bajtów. W związku z tym typ zwracany wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów. W podpisie metody, należy wprowadzić następujące zmiany:  
  
    -   Zmiana typu zwracanego na `Task<byte[]>`.  
  
    -   Według Konwencji metod asynchronicznych mają nazwy, które kończą się "Async", aby zmienić nazwę metody `GetURLContentsAsync`.  
  
     Poniższy kod przedstawia tych zmian.  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     Z tymi zmianami kilka konwersji `GetURLContents` do metody asynchronicznej jest pełny.  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> Aby przekonwertować SumPageSizes metody asynchronicznej  
  
1.  Powtórz kroki z poprzedniej procedury `SumPageSizes`. Najpierw zmień wywołanie `GetURLContents` do wywołania asynchronicznego.  
  
    -   Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiono.  
  
    -   Zastosuj `await` zadania który `GetURLContentsAsync` zwraca uzyskanie bajt tablicy wartości.  
  
     Poniższy kod przedstawia tych zmian.  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     Poprzednie przypisania Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  W podpisie metody, należy wprowadzić następujące zmiany:  
  
    -   Oznacz metodę z `async` modyfikator.  
  
    -   Dodaj "Async" w nazwie metody.  
  
    -   Brak nie zadań zwracanej zmiennej, T, teraz ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `return` instrukcji.) Jednak metoda musi zwracać `Task` jako oczekujący. W związku z tym zmienić zwracany typ metody z `void` do `Task`.  
  
     Poniższy kod przedstawia tych zmian.  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     Konwersja typu `SumPageSizes` do `SumPageSizesAsync` została ukończona.  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> Aby przekonwertować startButton_Click metody asynchronicznej  
  
1.  W obsłudze zdarzeń, Zmień nazwę metody wywoływane z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiono.  
  
2.  Ponieważ `SumPageSizesAsync` jest to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.  
  
     Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`. Wywołanie zwraca `Task`, a nie `Task(T)`.  
  
     Jak w poprzedniej procedury można przekonwertować wywołanie za pomocą jednej instrukcji lub dwie instrukcje. Poniższy kod przedstawia tych zmian.  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  Aby uniknąć przypadkowego ponownego wprowadzania operacji, dodaj następującą instrukcję, w górnej części `startButton_Click` wyłączyć **Start** przycisku.  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     Można ponownie włączyć przycisk na końcu obsługi zdarzeń.  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     Aby uzyskać więcej informacji na temat ponownego rozpoczęcia, zobacz [Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).  
  
4.  Na koniec należy dodać `async` modyfikatora w deklaracji, aby program obsługi zdarzeń można zdefiniować oczekiwania `SumPagSizesAsync`.  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń. Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi zwracać `void`.  
  
     Konwersja projektu przetwarzania synchronicznego do asynchronicznego zostało ukończone.  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> Aby przetestować asynchroniczne rozwiązania  
  
1.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
2.  Powinna pojawić się dane wyjściowe podobne dane wyjściowe synchroniczne rozwiązania. Jednak zauważyć następujące różnice.  
  
    -   Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania. Na przykład oba programy zawierają wiersza w `startButton_Click` który czyści pola tekstowego. W zamierzeniu, wyczyść pole tekstowe między działa, jeśli wybierzesz **Start** przycisk raz drugi, po pojawieniu się jeden zestaw wyników. W to wersja synchroniczna pola tekstowego jest wyczyszczone tuż przed liczniki są wyświetlane po raz drugi, po zakończeniu pliki do pobrania i wątku interfejsu użytkownika będzie mógł wykonywać inne zadania. W wersjach asynchronicznych, pola tekstowego czyści natychmiast po wybraniu **Start** przycisku.  
  
    -   Przede wszystkim wątku interfejsu użytkownika nie jest blokowane podczas pliki do pobrania. Można przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web zliczane i wyświetlane. Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisk (x w czerwonym pola w prawym górnym rogu).  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework  
  
1.  .NET Framework 4.5 zapewnia wiele metod asynchronicznych, które są dostępne. Jeden z nich, <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, jest tylko dane potrzebne do tego przewodnika. Możesz użyć jej zamiast `GetURLContentsAsync` metody utworzonego w procedurze wcześniej.  
  
     Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`. Dodaj następujące oświadczenie na początku metody.  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  W `SumPageSizesAsync,` Zastąp wywołanie Twojej `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  Usuń lub komentarz `GetURLContentsAsync` metody zapisane.  
  
4.  Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Zachowanie tej wersji projektu powinien zgodne zachowanie opisano procedury "Aby przetestować asynchroniczne rozwiązania", ale z nawet mniejszym wysiłku z Twojej.  
  
##  <a name="BKMK_CompleteCodeExamples"></a> Przykład  
 Poniższy kod zawiera pełny przykład konwersji z synchronicznego do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metody zapisane. Należy zauważyć, że silnie podobny oryginalnego synchroniczne rozwiązania.  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 Poniższy kod zawiera pełny przykład rozwiązania, która używa `HttpClient` metody `GetByteArrayAsync`.  
  
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
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przykład Async: Uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [async](../../../../csharp/language-reference/keywords/async.md)  
 [await](../../../../csharp/language-reference/keywords/await.md)  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Programowanie asynchroniczne opartego na zadaniach (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
 [Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
