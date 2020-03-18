---
title: 'Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281783"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a>Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)

Możesz pisać programy asynchroniczne łatwiej i intuicyjnie za pomocą funkcji async / await. Można napisać kod asynchroniczny, który wygląda jak kod synchroniczny i niech kompilator obsługi trudnych funkcji wywołania wywołania i kontynuacji, które zwykle pociąga za sobą kod asynchroniczny.

Aby uzyskać więcej informacji na temat funkcji Async, zobacz [Programowanie asynchroniczne z async i await (C#)](./index.md).

Ten instruktaż rozpoczyna się od synchronicznej aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów na liście witryn sieci Web. Następnie instruktaż konwertuje aplikację na rozwiązanie asynchroniczne przy użyciu nowych funkcji.

Jeśli nie chcesz samodzielnie tworzyć aplikacji, możesz pobrać [przykład programu Async: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic).](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)

> [!NOTE]
> Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

## <a name="create-a-wpf-application"></a>Tworzenie aplikacji WPF

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz pozycję **Plik** > **nowy** > **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt.**

3. W okienku **Zainstalowane szablony** wybierz pozycję Visual C#, a następnie wybierz **pozycję Aplikacja WPF** z listy typów projektów.

4. W **Name** polu tekstowym `AsyncExampleWPF`Nazwa wprowadź klawisz , a następnie wybierz przycisk **OK.**

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

## <a name="design-a-simple-wpf-mainwindow"></a>Projektowanie prostego Okna Głównego WPF

1. W Edytorze kodu programu Visual Studio wybierz kartę **MainWindow.xaml.**

2. Jeśli okno **Przybornik** nie jest widoczne, otwórz menu **Widok,** a następnie wybierz polecenie **Przybornik**.

3. Dodaj **button** kontroli i **TextBox** formantu **do MainWindow** okna.

4. Wyróżnij kontrolki **TextBox** i w oknie **Właściwości** ustaw następujące wartości:

    - Ustaw **Name** właściwość Name `resultsTextBox`na .

    - Ustaw **właściwość Height** na 250.

    - Ustaw **width** właściwość 500.

    - Na karcie **Tekst** określ czcionkę jednoosyjną, taką jak Lucida Console lub Global Monospace.

5. Wyróżnij kontrolki **Button** i w oknie **Właściwości** ustaw następujące wartości:

    - Ustaw **Name** właściwość Name `startButton`na .

    - Zmień wartość właściwości **Content** z **Button** na **Start**.

6. Umieść pole tekstowe i przycisk tak, aby oba były wyświetlane w oknie **MainWindow.**

     Aby uzyskać więcej informacji na temat projektanta XAML WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).

## <a name="add-a-reference"></a>Dodawanie odwołania

1. W **Eksploratorze rozwiązań**wyróżnij nazwę projektu.

2. Na pasku menu wybierz pozycję Dodaj**odwołanie** **do projektu** > .

     Pojawi się okno **dialogowe Menedżera odwołań.**

3. W górnej części okna dialogowego sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszego.

4. W kategorii **Zestawy** wybierz **pozycję Framework,** jeśli nie jest jeszcze wybrana.

5. Na liście nazw zaznacz pole wyboru **System.Net.Http.**

6. Wybierz przycisk **OK,** aby zamknąć okno dialogowe.

## <a name="add-necessary-using-directives"></a>Dodawanie niezbędnych za pomocą dyrektyw

1. W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz pozycję **Wyświetl kod**.

2. Dodaj następujące `using` dyrektywy w górnej części pliku kodu, jeśli nie są one jeszcze obecne.

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a>Tworzenie aplikacji synchronicznej

1. W oknie projektu MainWindow.xaml kliknij dwukrotnie przycisk **Start,** aby utworzyć program obsługi `startButton_Click` zdarzeń w MainWindow.xaml.cs.

2. W MainWindow.xaml.cs skopiuj następujący `startButton_Click`kod do treści:

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    Kod wywołuje metodę, która napędza `SumPageSizes`aplikację, i wyświetla komunikat, `startButton_Click`gdy formant powraca do .

3. Kod rozwiązania synchronicznego zawiera następujące cztery metody:

    - `SumPageSizes`, który pobiera listę adresów `SetUpURLList` URL stron `GetURLContents` `DisplayResults` internetowych, a następnie wywołuje i przetwarza każdy adres URL.

    - `SetUpURLList`, który tworzy i zwraca listę adresów internetowych.

    - `GetURLContents`, który pobiera zawartość każdej witryny sieci Web i zwraca zawartość jako tablicę bajtów.

    - `DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtów dla każdego adresu URL.

    Skopiuj następujące cztery metody, a `startButton_Click` następnie wklej je w programie obsługi zdarzeń w MainWindow.xaml.cs:

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
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
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
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a>Testowanie roztworu synchronicznego

Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**

Dane wyjściowe, które przypomina następującą listę powinny być wyświetlane:

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

Należy zauważyć, że wyświetlenie liczby zajmuje kilka sekund. W tym czasie wątek interfejsu użytkownika jest blokowany, gdy czeka na żądane zasoby do pobrania. W rezultacie po wybraniu przycisku **Start** nie można przenosić, maksymalizować, minimalizować ani nawet zamykać okna wyświetlania. Te wysiłki nie powiodą się, dopóki nie zaczną pojawiać się liczby bajtów. Jeśli witryna sieci Web nie odpowiada, nie masz żadnych wskazówek, która witryna nie powiodła się. Trudno nawet przestać czekać i zamknąć program.

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>Konwertowanie GetURLContents na metodę asynchroniczną

1. Aby przekonwertować rozwiązanie synchroniczne na rozwiązanie asynchroniczne, `GetURLContents` najlepszym miejscem do <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> uruchomienia jest, ponieważ wywołania metody i <xref:System.IO.Stream> metody <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web. .NET Framework ułatwia konwersję, dostarczając asynchroniczne wersje obu metod.

     Aby uzyskać więcej informacji na temat `GetURLContents`metod, które są używane w , zobacz <xref:System.Net.WebRequest>.

    > [!NOTE]
    > W miarę postępów w tym instruktażenie pojawia się kilka błędów kompilatora. Można je zignorować i kontynuować instruktaż.

     Zmień metodę, która jest wywoływana `GetURLContents` w `GetResponse` trzecim wierszu z asynchronicznej metody opartej na <xref:System.Net.WebRequest.GetResponseAsync%2A> zadaniach.

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. `GetResponseAsync`zwraca <xref:System.Threading.Tasks.Task%601>wartość . W takim przypadku *zmienna zwrotu zadania*, `TResult`ma typ <xref:System.Net.WebResponse>. Zadanie jest obietnicą do `WebResponse` wyprodukowania rzeczywistego obiektu po pobraniu żądanych danych i zadanie zostało uruchomione do zakończenia.

     Aby pobrać `WebResponse` wartość z zadania, należy zastosować operator `GetResponseAsync` [await](../../../language-reference/operators/await.md) do wywołania , jak pokazano w poniższym kodzie.

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     Operator `await` zawiesza wykonanie bieżącej metody, `GetURLContents`do czasu zakończenia oczekiwanego zadania. W międzyczasie formant powraca do obiektu wywołującego bieżącej metody. W tym przykładzie bieżąca `GetURLContents`metoda jest `SumPageSizes`, a obiekt wywołujący jest . Po zakończeniu zadania przyrzeczony `WebResponse` obiekt jest tworzony jako wartość oczekiwanego zadania i `response`przypisany do zmiennej .

     Poprzednia instrukcja może być podzielona na następujące dwie instrukcje, aby wyjaśnić, co się dzieje.

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` ć `Task<WebResponse>`lub . Następnie operator await jest stosowany do zadania, aby pobrać `WebResponse` wartość.

     Jeśli metoda asynchroniczne ma do zrobienia, że nie zależy od zakończenia zadania, metoda może kontynuować tę pracę między tymi `await` dwiema instrukcjami, po wywołaniu metody asynchronicznej i przed zastosowaniem operatora. Na przykład zobacz [Jak tworzyć wiele żądań sieci web równolegle przy użyciu asynchronii i await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i Jak rozszerzyć [instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. Ponieważ dodano `await` operator w poprzednim kroku, występuje błąd kompilatora. Operator może być używany tylko w metodach, które są oznaczone modyfikatorem [asynchronii.](../../../language-reference/keywords/async.md) Ignoruj błąd podczas powtarzania kroków `CopyTo` konwersji, aby `CopyToAsync`zastąpić wywołanie wywołaniem .

    - Zmień nazwę metody, która jest <xref:System.IO.Stream.CopyToAsync%2A>wywoływana do .

    - Lub `CopyTo` `CopyToAsync` metoda kopiuje bajty `content`do jego argumentu i nie zwraca znaczącej wartości. W wersji synchronicznej wywołanie `CopyTo` jest prostą instrukcją, która nie zwraca wartości. Wersja asynchroniczna `CopyToAsync`, <xref:System.Threading.Tasks.Task>zwraca wartość . Funkcja zadania, taka jak "Task(void)" i umożliwia oczekiwanie na metodę. Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         Poprzednia instrukcja skraca następujące dwa wiersze kodu.

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. Wszystko, co pozostaje `GetURLContents` do zrobienia w to, aby dostosować podpis metody. Operator `await` async można używać tylko w metodach oznaczonych modyfikatorem [asynchroni.](../../../language-reference/keywords/async.md) Dodaj modyfikator, aby oznaczyć metodę jako *metodę asynchronia*, jak pokazano w poniższym kodzie.

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. Zwracany typ metody asynchronicznej <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>może `void` być tylko , lub w języku C#. Zazwyczaj zwracany typ `void` jest używany tylko w programie obsługi `void` zdarzeń asynchronicznego, gdzie jest to wymagane. W innych przypadkach `Task(T)` można użyć, jeśli ukończona metoda ma [return](../../../language-reference/keywords/return.md) instrukcji, która `Task` zwraca wartość typu T i należy użyć, jeśli ukończona metoda nie zwraca wartość znaczącą. Typ zwracany `Task` można pomyśleć jako "Zadanie(unieważnienie)".

     Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](./async-return-types.md).

     Metoda `GetURLContents` ma return instrukcji i instrukcji zwraca tablicy bajtów. W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów. Wyconajmi należy wprowadzić następujące zmiany w podpisie metody:

    - Zmień typ zwracany na `Task<byte[]>`.

    - Zgodnie z konwencją metody asynchroniczne mają nazwy, które kończą `GetURLContentsAsync`się na "Async", więc zmień nazwę metody .

     Poniższy kod pokazuje te zmiany.

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     Z tych kilku zmian, `GetURLContents` konwersja do metody asynchronicznej jest zakończona.

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>Konwertowanie sumpagesizes na metodę asynchroniczną

1. Powtórz kroki z poprzedniej `SumPageSizes`procedury dla . Najpierw zmień wywołanie `GetURLContents` do wywołania asynchronicznego.

    - Zmień nazwę metody, która jest `GetURLContents` wywoływana z na `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.

    - Zastosuj `await` do zadania, które `GetURLContentsAsync` zwraca, aby uzyskać wartość tablicy bajtów.

     Poniższy kod pokazuje te zmiany.

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     Poprzednie przypisanie skraca następujące dwa wiersze kodu.

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. Wyczyć następujące zmiany w podpisie metody:

    - Oznacz metodę `async` modyfikatorem.

    - Dodaj "Async" do nazwy metody.

    - Nie ma zmiennej zwrotu zadania, `SumPageSizesAsync` T, tym razem, ponieważ nie zwraca `return` wartość dla T. (Metoda nie ma instrukcji.) Jednak metoda musi `Task` zwrócić, aby być oczekiwany. W związku z tym należy `void` zmienić `Task`typ zwracany metody z na .

    Poniższy kod pokazuje te zmiany.

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     Konwersja `SumPageSizes` do `SumPageSizesAsync` jest zakończona.

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>Konwertowanie startButton_Click na metodę asynchroniczną

1. W programie obsługi zdarzeń zmień nazwę `SumPageSizes` metody `SumPageSizesAsync`wywoływanej z na , jeśli jeszcze tego nie zrobiono.

2. Ponieważ `SumPageSizesAsync` jest metodą asynchronicznej, zmień kod w programie obsługi zdarzeń, aby oczekiwać na wynik.

     Wywołanie `SumPageSizesAsync` do odzwierciedlenia wywołania `CopyToAsync` w `GetURLContentsAsync`. Wywołanie zwraca `Task`, `Task(T)`a nie .

     Podobnie jak w poprzednich procedurach, można przekonwertować wywołanie przy użyciu jednej instrukcji lub dwóch instrukcji. Poniższy kod pokazuje te zmiany.

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. Aby zapobiec przypadkowemu ponownemu wprowadzeniu operacji, dodaj `startButton_Click` następującą instrukcję u góry, aby wyłączyć przycisk **Start.**

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     Można ponownie włączyć przycisk na końcu programu obsługi zdarzeń.

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     Aby uzyskać więcej informacji na temat reentrancy, zobacz [Obsługa Reentrancy w Async Apps (C#)](./handling-reentrancy-in-async-apps.md).

4. Na koniec `async` dodaj modyfikator do deklaracji, `SumPagSizesAsync`aby program obsługi zdarzeń mógł poczekać .

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     Zazwyczaj nazwy programów obsługi zdarzeń nie są zmieniane. Typ zwracany nie jest `Task` zmieniany, ponieważ `void`programy obsługi zdarzeń muszą zwracać .

     Konwersja projektu z synchronicznego do przetwarzania asynchronicznego została zakończona.

## <a name="test-the-asynchronous-solution"></a>Testowanie rozwiązania asynchronicznego

1. Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**

2. Dane wyjściowe, które przypomina dane wyjściowe rozwiązania synchronicznego powinny pojawić się. Należy jednak zauważyć następujące różnice.

    - Wyniki nie wszystkie występują w tym samym czasie, po zakończeniu przetwarzania. Na przykład oba programy zawierają `startButton_Click` wiersz, który czyści pole tekstowe. Celem jest wyczyszczenie pola tekstowego między działami, jeśli wybierzesz przycisk **Start** po raz drugi, po pojawieniu się jednego zestawu wyników. W wersji synchronicznej pole tekstowe jest wyczyszczone tuż przed pojawieniem się zliczania po raz drugi, po zakończeniu pobierania i wątku interfejsu użytkownika jest wolny do wykonywania innych prac. W wersji asynchronicznej pole tekstowe zostanie wyczyszczone natychmiast po wybraniu przycisku **Start.**

    - Co najważniejsze, wątek interfejsu użytkownika nie jest blokowany podczas pobierania. Okno można przenosić lub zmieniać rozmiar podczas pobierania, zliczania i wyświetlania zasobów sieci Web. Jeśli jedna z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając przycisk **Zamknij** (x w czerwonym polu w prawym górnym rogu).

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a>Zamień metodę GetURLContentsAsync metodą .NET Framework

1. .NET Framework 4.5 zawiera wiele metod asynchronii, których można użyć. Jeden z <xref:System.Net.Http.HttpClient> nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>metoda , robi to, czego potrzebujesz do tego instruktażenia. Można go używać zamiast `GetURLContentsAsync` metody, która została utworzona we wcześniejszej procedurze.

     Pierwszym krokiem jest `HttpClient` utworzenie obiektu `SumPageSizesAsync`w metodzie . Dodaj następującą deklarację na początku metody.

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. W `SumPageSizesAsync,` zastąpić wywołanie `GetURLContentsAsync` metody z wywołaniem `HttpClient` metody.

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. Usuń lub skomentuj `GetURLContentsAsync` metodę, którą napisałeś.

4. Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**

     Zachowanie tej wersji projektu powinny być zgodne z zachowaniem, które opisuje procedura "Aby przetestować rozwiązanie asynchroniczne", ale przy jeszcze mniejszym wysiłku ze strony ciebie.

## <a name="example-code"></a>Przykładowy kod

Poniższy kod zawiera pełny przykład konwersji z synchronicznego do rozwiązania asynchronicznego przy `GetURLContentsAsync` użyciu metody asynchronicznej, który został zanapisał. Należy zauważyć, że bardzo przypomina oryginalne, synchroniczne rozwiązanie.

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

Poniższy kod zawiera pełny przykład rozwiązania, `HttpClient` które `GetByteArrayAsync`używa metody.

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a>Zobacz też

- [Przykład asynchroniczny: uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Typy zwrotu asynchronicznego (C#)](./async-return-types.md)
- [Programowanie asynchroniczne oparte na zadaniach (TAP)](https://www.microsoft.com/download/details.aspx?id=19957)
- [Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
