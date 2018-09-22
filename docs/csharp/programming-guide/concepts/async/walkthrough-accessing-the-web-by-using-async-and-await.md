---
title: 'Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 24ce1e405019ef83ff6bcbb61552d6fc5d911935
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577612"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)

Asynchroniczne programy można napisać bardziej łatwo i intuicyjnie za pomocą funkcji async/await. Można napisać kod asynchroniczny, który wygląda jak synchroniczny kod i pozwolić kompilatorowi obsługi funkcji wywołania zwrotnego trudne i kontynuacje, które kodu asynchronicznego zazwyczaj pociąga za sobą.

Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczba bajtów na liście witryn sieci Web. Instruktaż następnie konwertuje ją do asynchronicznego rozwiązania przy użyciu nowych funkcji.

Jeśli nie chcesz samodzielnie tworzyć aplikacje, możesz pobrać [próbka asynchroniczna: dostęp do instruktażu sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).

> [!NOTE]
> Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.

## <a name="create-a-wpf-application"></a>Tworzenie aplikacji WPF

1.  Uruchom program Visual Studio.

2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  W **zainstalowane szablony** okienku wybierz pozycję Visual C#, a następnie wybierz **aplikacji WPF** z listy typów projektów.

4.  W **nazwa** tekstu wprowadź `AsyncExampleWPF`, a następnie wybierz **OK** przycisku.

     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.

## <a name="design-a-simple-wpf-mainwindow"></a>Projektowanie proste MainWindow WPF

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

## <a name="add-a-reference"></a>Dodaj odwołanie

1.  W **Eksploratora rozwiązań**, wyróżnij nazwę projektu.

2.  Na pasku menu wybierz **projektu** > **Dodaj odwołanie**.

     **Menadżer odwołań** pojawi się okno dialogowe.

3.  W górnej części okna dialogowego Sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszej.

4.  W **zestawy** kategorii, wybierz **Framework** Jeśli nie została jeszcze wybrana.

5.  Na liście nazw, wybierz **System.Net.Http** pole wyboru.

6.  Wybierz **OK** przycisk, aby zamknąć okno dialogowe.

## <a name="add-necessary-using-directives"></a>Dodaj to konieczne, dyrektyw using

1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.

2.  Dodaj następujący kod `using` dyrektywy u góry pliku kodu, jeśli tak nie jest już obecny.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Tworzenie aplikacji synchroniczne

1.  W oknie projektu, MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.

2.  W MainWindow.xaml.cs, skopiuj poniższy kod do treści `startButton_Click`:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod wywołuje metodę, która napędza aplikację, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click`.

3.  Kod używany w rozwiązaniu synchronicznym zawiera poniższe cztery metody:

    -   `SumPageSizes`, która pobiera listę adresów URL strony sieci Web, z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.

    -   `SetUpURLList`, która tworzy i zwraca listę adresów internetowych.

    -   `GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość w postaci tablicy bajtów.

    -   `DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.

    Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs:

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

## <a name="test-the-synchronous-solution"></a>Testowanie rozwiązania synchroniczne

Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.

Powinien pojawić się dane wyjściowe podobne do poniższej liście:

```text
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

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Konwertuj GetURLContents metody asynchronicznej

1.  Aby konwertować synchroniczne rozwiązanie do asynchronicznego rozwiązania, najlepszym miejscem do rozpoczęcia jest w `GetURLContents` ponieważ wywołania <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web . .NET Framework ułatwia konwersję poprzez dostarczenie asynchronicznych wersji obu tych metod.

     Aby uzyskać więcej informacji o metodach, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.

    > [!NOTE]
    > Postępuj zgodnie z instrukcjami w tym przewodniku, wyświetlane są kilka błędów kompilatora. Można je zignorować i kontynuować z tym przewodnikiem.

     Zmień metodę, która jest wywołana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, opartego na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  `GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>. W tym przypadku *zmiennej zwracanego zadania*, `TResult`, ma typ <xref:System.Net.WebResponse>. Zadanie jest obietnicą utworzenia rzeczywistej `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.

     Aby pobrać `WebResponse` wartości z zadania, zastosuj [await](../../../../csharp/language-reference/keywords/await.md) operator wywołania do `GetResponseAsync`, jak pokazano w poniższym kodzie.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     `await` Operator zawiesza wykonywanie bieżącej metody `GetURLContents`, aż oczekiwane zadanie zostało ukończone. W międzyczasie formant powraca do obiektu wywołującego metody bieżącej. W tym przykładzie jest bieżąca metoda `GetURLContents`, a obiekt wywołujący jest `SumPageSizes`. Po zakończeniu zadania, uzgodnionego `WebResponse` obiekt jest generowany z wartością oczekiwane zadanie i przypisana do zmiennej `response`.

     Poprzednia instrukcja można podzielić na dwie poniższe instrukcje, aby wyjaśnić, co się dzieje.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`. Await operator jest stosowany do zadania do pobrania, a następnie `WebResponse` wartość.

     Jeśli metoda async ma robić prace, które nie są zależne od zakończenia tego zadania, metody można kontynuować pracę między te dwie instrukcje po wywołaniu metody async i przed `await` jest stosowany operator. Przykłady, zobacz [jak: wiele sieci Web żądania równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3.  Ponieważ dodałeś `await` występuje błąd kompilatora operatora w poprzednim kroku. Operator może służyć tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator. Ignorowanie błędu podczas Powtórz procedurę konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.

    -   Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.

    -   `CopyTo` Lub `CopyToAsync` metoda kopiuje bajtów do jej argument `content`i nie zwraca zrozumiałą wartość. W wersji synchroniczne wywołanie `CopyTo` jest prostą instrukcję, która nie zwraca wartości. Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>. Zadanie funkcje takie jak "Task(void)" i włącza metodę oczekiwanie. Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.

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

4.  Wszystkie opcje, które pozostają do wykonania `GetURLContents` jest dostosowanie podpis metody. Możesz użyć `await` operatora tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator. Dodaj modyfikator do oznaczania metody jako *metody asynchronicznej*, jak pokazano w poniższym kodzie.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  Zwracany typ metody asynchronicznej może składać się wyłącznie <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, lub `void` w języku C#. Zwykle, zwracanym typem `void` jest używany tylko w przypadku programu async obsługi zdarzeń, gdzie `void` jest wymagana. W innych przypadkach należy użyć `Task(T)` Jeśli metoda ukończone ma [zwracają](../../../../csharp/language-reference/keywords/return.md) instrukcję, która zwraca wartość typu T i używasz `Task` jeśli ukończone metoda nie zwraca zrozumiałą wartość. Można potraktować `Task` zwracany typ, co oznacza "Task(void)."

     Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

     Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów. W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów. W podpisie metody, należy wprowadzić następujące zmiany:

    -   Zmień typ zwracany `Task<byte[]>`.

    -   Zgodnie z Konwencją metod asynchronicznych mają nazwy, które kończą się na "Async", więc Zmień nazwę metody `GetURLContentsAsync`.

     Poniższy kod przedstawia te zmiany.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Za pomocą tych kilku zmian konwersji `GetURLContents` metody asynchronicznej jest pełny.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Konwertuj SumPageSizes metody asynchronicznej

1.  Powtórz kroki z poprzedniej procedury, aby uzyskać `SumPageSizes`. Najpierw należy zmienić wywołanie `GetURLContents` do wywołania asynchronicznego.

    -   Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.

    -   Zastosuj `await` do zadania, `GetURLContentsAsync` zwraca uzyskać bajt tablica wartości.

     Poniższy kod przedstawia te zmiany.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Poprzednie przypisanie Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  W podpisie metody, należy wprowadzić następujące zmiany:

    -   Oznacz metodę z `async` modyfikator.

    -   Dodaj "Async" w nazwie metody.

    -   Nie jest zmienną zwracany nie zadań, T, tym razem, ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `return` instrukcja.) Jednak metoda musi zwracać `Task` jako oczekujący. W związku z tym, zmień zwracany typ metody z `void` do `Task`.

    Poniższy kod przedstawia te zmiany.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Konwersja `SumPageSizes` do `SumPageSizesAsync` zostało zakończone.

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a>Konwertuj startButton_Click metody asynchronicznej

1.  W procedurze obsługi zdarzeń Zmień nazwę wywoływanej metody z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiłeś.

2.  Ponieważ `SumPageSizesAsync` to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.

     Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`. To wywołanie zwraca `Task`, a nie `Task(T)`.

     Tak jak w poprzednich procedur można przekonwertować wywołanie za pomocą jednej instrukcji lub dwóch instrukcji. Poniższy kod przedstawia te zmiany.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  Aby uniknąć przypadkowego ponownego wprowadzania operacji, należy dodać następującą instrukcję w górnej części `startButton_Click` wyłączyć **Start** przycisku.

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Możesz włączyć przycisku na końcu programu obsługi zdarzeń.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [obsługi współużytkowania wątkowości w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4.  Na koniec należy dodać `async` modyfikator deklaracji, aby program obsługi zdarzeń może poczekać `SumPagSizesAsync`.

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń. Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi zwracać `void`.

     Konwersja przetwarzania synchronicznego w celu asynchronicznego projektu zostało ukończone.

## <a name="test-the-asynchronous-solution"></a>Testowanie rozwiązania asynchroniczne

1.  Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.

2.  Dane wyjściowe podobne dane wyjściowe w rozwiązaniu synchronicznym powinna zostać wyświetlona. Jednak zauważyć następujące różnice.

    -   Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania. Na przykład oba programy zawiera wiersz w `startButton_Click` , czyści pole tekstowe. Celem jest czyścić pole tekstowe między działa, jeśli wybierzesz **Start** przycisk, aby po raz drugi, po pojawieniu się jeden zestaw wyników. W to wersja synchroniczna pole tekstowe jest wyczyszczone przed zliczeń pojawiają się po raz drugi, gdy odbywa się pliki do pobrania i jest bezpłatna wykonywanie innych zadań w wątku interfejsu użytkownika. W wersjach asynchronicznych, pola tekstowego czyści natychmiast, po dokonaniu wyboru **Start** przycisku.

    -   Co najważniejsze wątek interfejsu użytkownika nie jest zablokowane podczas jej pliki do pobrania. Możesz przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web liczone, a wyświetlane. Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisku (x czerwone pola w prawym górnym rogu).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Replace — metoda GetURLContentsAsync za pomocą metody .NET Framework

1.  .NET Framework 4.5 zapewnia wiele metod asynchronicznych, których można użyć. Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, wykonuje tylko potrzebne w ramach tego przewodnika. Można używać go zamiast `GetURLContentsAsync` metody, który został utworzony w wcześniejszym etapie procedury.

     Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`. Dodaj następującą deklarację na początku metody.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  W `SumPageSizesAsync,` Zastąp wywołanie usługi `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  Usunąć lub skomentować `GetURLContentsAsync` metodę, która powstała z jednego.

4.  Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.

     Zachowanie tej wersji programu project powinien odpowiadać zachowanie, które opisano procedury "Aby test asynchronicznego rozwiązania", ale o jeszcze mniejszym nakładzie pracy ze strony użytkownika.

## <a name="example-code"></a>Przykładowy kod

Poniższy kod zawiera pełny przykład konwersja przez synchroniczny do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metodę, która powstała z jednego. Należy zauważyć, że silnie przypomina oryginalnej, synchroniczne rozwiązanie.

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

Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody `GetByteArrayAsync`.

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

## <a name="see-also"></a>Zobacz także

- [Próbka asynchroniczna: Dostęp do instruktażu sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Programowanie asynchroniczne opartego na zadaniach (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)
- [Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
