---
title: Przepływ sterowania w programach asynchroniczny (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204442"
---
# <a name="control-flow-in-async-programs-c"></a>Przepływ sterowania w programach asynchroniczny (C#)

Programy asynchroniczne można łatwiej pisać i obsługiwać `async` `await` za pomocą słów kluczowych. Jednak wyniki mogą cię zaskoczyć, jeśli nie rozumiesz, jak działa program. W tym temacie śledzenia przepływu kontroli za pośrednictwem prostego programu asynchronicznego, aby pokazać, kiedy kontrola przenosi się z jednej metody do drugiej i jakie informacje są przesyłane za każdym razem.

Ogólnie rzecz biorąc, należy oznaczyć metody, które zawierają kod asynchroniczny z modyfikatora [async (C#).](../../../language-reference/keywords/async.md) W metodzie oznaczonej modyfikatorem asynchronicznym można użyć operatora [await (C#),](../../../language-reference/operators/await.md) aby określić, gdzie metoda wstrzymuje oczekiwanie na zakończenie procesu asynchronicznego. Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i await (C#)](./index.md).

W poniższym przykładzie użyto metod asynchronicznej do pobierania zawartości określonej witryny sieci Web jako ciągu i wyświetlania długości ciągu. Przykład zawiera następujące dwie metody.

- `startButton_Click`, który `AccessTheWebAsync` wywołuje i wyświetla wynik.

- `AccessTheWebAsync`, który pobiera zawartość witryny jako ciąg i zwraca długość ciągu. `AccessTheWebAsync`używa metody asynchronicznej, <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>aby pobrać zawartość.

Ponumerowane linie wyświetlania pojawiają się w strategicznych punktach w całym programie, aby pomóc Ci zrozumieć, jak działa program i wyjaśnić, co dzieje się w każdym zaznaczonym punkcie. Linie wyświetlania są oznaczone jako "ONE" do "SIX". Etykiety reprezentują kolejność, w jakiej program dociera do tych wierszy kodu.

Poniższy kod przedstawia konspekt programu.

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

Każda z oznaczonych lokalizacji, "ONE" do "SIX", wyświetla informacje o bieżącym stanie programu. Zostaną wyświetlone następujące dane wyjściowe:

```output
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a>Konfigurowanie programu

Można pobrać kod, który ten temat używa z MSDN lub można go utworzyć samodzielnie.

> [!NOTE]
> Aby uruchomić przykład, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.

### <a name="download-the-program"></a>Pobierz program

Aplikację dla tego tematu można pobrać z [próbki asynchronicznej: Przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Poniższe kroki otwierają i uruchamiają program.

1. Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.

2. Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .

3. Przejdź do folderu, w który znajduje się rozpakowany przykładowy kod, otwórz plik rozwiązania (.sln), a następnie wybierz klawisz **F5** do utworzenia i uruchomienia projektu.

### <a name="create-the-program-yourself"></a>Stwórz program samodzielnie

Poniższy projekt Fundacji prezentacji systemu Windows (WPF) zawiera przykład kodu dla tego tematu.

Aby uruchomić projekt, wykonaj następujące kroki:

1. Uruchom program Visual Studio.

2. Na pasku menu wybierz pozycję **Plik** > **nowy** > **projekt**.

     Zostanie otwarte okno dialogowe **Nowy projekt.**

3. Wybierz kategorię **Zainstalowane** > **pulpitu systemu Windows** Visual**C#,** > a następnie wybierz **pozycję Aplikacja WPF** z listy szablonów projektów.

4. Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz przycisk **OK.**

     Nowy projekt pojawi się w **Eksploratorze rozwiązań**.

5. W Edytorze kodu programu Visual Studio wybierz kartę **MainWindow.xaml.**

     Jeśli karta nie jest widoczna, otwórz menu skrótów mainwindow.xaml w **Eksploratorze rozwiązań**, a następnie wybierz pozycję **Wyświetl kod**.

6. W widoku **XAML** MainWindow.xaml, zastąp kod następującym kodem.

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     Proste okno zawierające pole tekstowe i przycisk pojawi się w widoku **projektowym** pliku MainWindow.xaml.

7. Dodaj odwołanie <xref:System.Net.Http>do pliku .

8. W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz pozycję **Wyświetl kod**.

9. W MainWindow.xaml.cs należy zastąpić kod następującym kodem.

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**

    Zostaną wyświetlone następujące dane wyjściowe:

    ```output
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a>Śledzenie programu

### <a name="steps-one-and-two"></a>Kroki pierwsze i drugie

Pierwsze dwie linie wyświetlania `startButton_Click` śledzą `AccessTheWebAsync`ścieżkę jako wywołania i `AccessTheWebAsync` wywołają metodę <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>asynchroniczną . Na poniższej ilustracji przedstawiono wywołania z metody na metodę.

![Kroki pierwsze i drugie](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Typ zwracany `AccessTheWebAsync` obu `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>i jest . Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą. Dla `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat typów zwracania metody asynchronicznej, zobacz [Async Return Types (C#).](./async-return-types.md)

Zwracana przez zadania metoda asynchroniczna zwraca wystąpienie zadania, gdy formant przenosi się z powrotem do obiektu wywołującego. Control zwraca z metody asynchronicznej `await` do obiektu wywołującego, gdy operator zostanie napotkany w wywoływanej metody lub po zakończeniu wywoływanej metody. Linie wyświetlania oznaczone jako "TRZY" do "SIX" śledzą tę część procesu.

### <a name="step-three"></a>Krok trzeci

W `AccessTheWebAsync`przypadku metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> asynchronicznej jest wywoływana w celu pobrania zawartości docelowej strony sieci Web. Formant powraca `client.GetStringAsync` `AccessTheWebAsync` z `client.GetStringAsync` do when powraca.

 Metoda `client.GetStringAsync` zwraca zadanie ciągu, który jest przypisany do zmiennej `getStringTask` w . `AccessTheWebAsync` W poniższym wierszu w przykładowym programie przedstawiono wywołanie `client.GetStringAsync` i przypisanie.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Można myśleć o zadaniu jako `client.GetStringAsync` obietnicy, aby wygenerować rzeczywisty ciąg ostatecznie. W międzyczasie, `AccessTheWebAsync` jeśli ma pracy, aby to zrobić, że `client.GetStringAsync`nie zależy od `client.GetStringAsync` obiecanego ciągu z , że praca może być kontynuowana podczas oczekiwania. W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "TRZY", stanowią możliwość wykonywania niezależnej pracy

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Poniższa instrukcja zawiesza `AccessTheWebAsync` `getStringTask` postęp w czasie oczekiwania.

```csharp
string urlContents = await getStringTask;
```

 Na poniższej ilustracji przedstawiono `client.GetStringAsync` przepływ kontroli `getStringTask` z do `getStringTask` przypisania do i od utworzenia do stosowania operatora await.

 ![Krok trzeci](./media/asynctrace-three.png "AsyncTrace-Trzy")

 Wyrażenie await zawiesza `AccessTheWebAsync` `client.GetStringAsync` się, dopóki nie powróci. W międzyczasie kontrola powraca do `AccessTheWebAsync`obiektu `startButton_Click`wywołującego , .

> [!NOTE]
> Zazwyczaj oczekujesz wywołania metody asynchronicznej natychmiast. Na przykład następujące przypisanie może zastąpić poprzedni kod, `getStringTask`który tworzy, a następnie oczekuje:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> W tym temacie operator await jest stosowany później, aby pomieścić linie wyjściowe, które oznaczają przepływ kontroli za pośrednictwem programu.

### <a name="step-four"></a>Krok czwarty

Zadeklarowany typ `AccessTheWebAsync` zwracany jest `Task<int>`. W związku `AccessTheWebAsync` z tym po zawieszeniu zwraca `startButton_Click`zadanie liczby całkowitej do . Należy zrozumieć, że zwrócone zadanie `getStringTask`nie jest . Zwrócone zadanie jest nowe zadanie liczby całkowitej, która reprezentuje to, co `AccessTheWebAsync`pozostaje do zrobienia w zawieszonej metody . Zadanie jest obietnicą `AccessTheWebAsync` do wyprodukowania liczby całkowitej po zakończeniu zadania.

Następująca instrukcja przypisuje to `getLengthTask` zadanie do zmiennej.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Podobnie `AccessTheWebAsync`jak `startButton_Click` w , można kontynuować pracę, która nie zależy od`getLengthTask`wyników zadania asynchronicznego ( ) dopóki zadanie nie jest oczekiwane. Następujące wiersze wyjściowe reprezentują tę pracę.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 Postęp `startButton_Click` w jest `getLengthTask` zawieszony, gdy jest oczekiwana. Następująca instrukcja `startButton_Click` przypisania zawiesza się do czasu `AccessTheWebAsync` jego zakończenia.

```csharp
int contentLength = await getLengthTask;
```

 Na poniższej ilustracji strzałki pokazują przepływ kontroli od `AccessTheWebAsync` wyrażenia await do `getLengthTask`przypisania wartości do `startButton_Click` `getLengthTask` , a następnie normalne przetwarzanie, dopóki nie będzie oczekiwane.

 ![Krok czwarty](./media/asynctrace-four.png "AsyncTrace-FOUR")

### <a name="step-five"></a>Krok piąty

Gdy `client.GetStringAsync` sygnalizuje, że jest `AccessTheWebAsync` kompletny, przetwarzanie jest zwolniony z zawieszenia i może kontynuować przeszłości await instrukcji. Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Operand return instrukcji , `urlContents.Length`jest przechowywany w `AccessTheWebAsync` zadaniu, które zwraca. Wyrażenie await pobiera tę `getLengthTask` wartość `startButton_Click`z in .

 Na poniższej ilustracji przedstawiono `client.GetStringAsync` transfer `getStringTask`kontroli po zakończeniu (i ) .

 ![Krok piąty](./media/asynctrace-five.png "AsyncTrace-FIVE")

 `AccessTheWebAsync`biegnie do zakończenia, a `startButton_Click`kontrola powraca do , który oczekuje na zakończenie.

### <a name="step-six"></a>Krok szósty

Gdy `AccessTheWebAsync` sygnały, że jest zakończona, przetwarzanie może `startButton_Async`kontynuować przeszłości await instrukcji w . W rzeczywistości program nie ma nic więcej do zrobienia.

Następujące linie wyjściowe reprezentują wznowienie przetwarzania w: `startButton_Async`

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Wyrażenie await pobiera `getLengthTask` z wartości całkowitej, która jest operand return `AccessTheWebAsync`instrukcji w . Następująca instrukcja przypisuje tę `contentLength` wartość do zmiennej.

```csharp
int contentLength = await getLengthTask;
```

 Na poniższej ilustracji przedstawiono `AccessTheWebAsync` `startButton_Click`powrót kontroli z do .

 ![Krok szósty](./media/asynctrace-six.png "AsyncTrace-6")

## <a name="see-also"></a>Zobacz też

- [Programowanie asynchroniczne z async i await (C#)](./index.md)
- [Typy zwrotu asynchronicznego (C#)](./async-return-types.md)
- [Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
