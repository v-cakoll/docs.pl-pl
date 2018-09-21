---
title: Przepływ sterowania w programach Async (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 49123dde51acaa82a2d8fa7d27fdf27087675034
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532220"
---
# <a name="control-flow-in-async-programs-c"></a>Przepływ sterowania w programach async (C#)

Pozwala pisać i łatwiej utrzymać asynchroniczne programy za pomocą `async` i `await` słów kluczowych. Jednak wyniki mogą Cię zaskoczyć, jeśli nie rozumiesz sposobu działania programu. W tym temacie omówiono, którą przepływ sterowania za pośrednictwem prostego programu asynchronicznego aby pokazać, kiedy sterowania przechodzi od jednej metody do innej i jakie informacje są przesyłane za każdym razem.

Ogólnie rzecz biorąc Oznacz metody, które zawierają kod asynchroniczny [async (C#)](../../../../csharp/language-reference/keywords/async.md) modyfikator. W metodzie, która jest oznaczona modyfikatorem asynchronicznym, można użyć [await (C#)](../../../../csharp/language-reference/keywords/await.md) operatora, aby określić, gdzie metoda wstrzymuje się oczekiwania wywołany proces asynchroniczny zakończyć. Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

W poniższym przykładzie użyto metody asynchronicznej, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu. Przykład zawiera następujących dwóch metod.

-   `startButton_Click`, która wywołuje metodę `AccessTheWebAsync` i wyświetla wynik.

-   `AccessTheWebAsync`, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu. `AccessTheWebAsync` używa asynchronicznej <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.

Ponumerowane wyświetlanych wierszy pojawiających się w strategiczny punktach w całym programie, aby lepiej zrozumieć, jak działa program i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony. Wyświetlane wiersze są oznaczone etykietami od "ONE"do "sześć." Etykiety reprezentują kolejność, w jakiej program osiąga te wiersze kodu.

Poniższy kod przedstawia zarys programu.

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
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("http://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

Każda z etykietami lokalizacje "ONE"do "6," Wyświetla informacje dotyczące bieżącego stanu programu. Są następujące wyniki:

```text
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

Kod, który używa tego tematu możesz pobrać z witryny MSDN lub tworzyć je samodzielnie.

> [!NOTE]
> Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.

### <a name="download-the-program"></a>Pobierz program

Możesz pobrać aplikację dotyczącą tego tematu z [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Poniższe kroki, Otwórz i uruchom program.

1.  Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.

2.  Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.

3.  Przejdź do folderu, który posiada rozpakowany przykładowego kodu, otwórz plik rozwiązania (.sln), a następnie wybierz **F5** klawisz, aby skompilować i uruchomić projekt.

### <a name="create-the-program-yourself"></a>Utwórz program, samodzielnie

Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu, w tym temacie.

Aby uruchomić projekt, należy wykonać następujące czynności:

1.  Uruchom program Visual Studio.

2.  Na pasku menu wybierz **pliku** > **New** > **projektu**.

     **Nowy projekt** zostanie otwarte okno dialogowe.

3.  Wybierz **zainstalowane** > **Visual C#** > **pulpitu Windows** kategorii, a następnie wybierz **aplikacja WPF** z listy szablonów projektu.

4.  Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz **OK** przycisku.

     Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.

5.  W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.

     Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.

6.  W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.

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

     Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.

7.  Dodaj odwołanie do <xref:System.Net.Http>.

8.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.

9. W MainWindow.xaml.cs Zastąp kod następującym kodem.

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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");

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

10. Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.

    Zostanie wyświetlone następujące dane wyjściowe:

    ```text
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

### <a name="steps-one-and-two"></a>Kroki 1 i 2

Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Poniższa ilustracja przedstawia wywołania z metody do metody.

![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")

Zwracanym typem obu metod `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>. Aby uzyskać `AccessTheWebAsync`, TResult jest liczbą całkowitą. Aby uzyskać `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat typów zwracanych w metodach asynchronicznych, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

Asynchroniczna metoda zwracania zadania Zwraca wystąpienie zadania Jeśli kontrola przechodzi do obiektu wywołującego. Formant powraca z metody asynchronicznej do obiektu wywołującego gdy `await` operator zostanie napotkany w metodzie wywoływanej, lub gdy metoda wywoływana się zakończy. Wyświetlane wiersze, które są oznaczone jako "Trzy"do "6" śledzą tę część procesu.

### <a name="step-three"></a>Krok 3

W `AccessTheWebAsync`, metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web. Formant powraca z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.

 `client.GetStringAsync` Metoda zwraca zadanie ciągu, która jest przypisana do `getStringTask` zmienną `AccessTheWebAsync`. Następujący wiersz w programie przykładowym pokazuje wywołanie `client.GetStringAsync` i przypisania.

```csharp
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");
```

 Można traktować zadanie jako zapowiedź `client.GetStringAsync` do produkcji rzeczywistego ciągu po pewnym czasie. W międzyczasie Jeśli `AccessTheWebAsync` ma robić prace, które nie są zależne od uzgodnionego ciągu z `client.GetStringAsync`, można kontynuować pracę podczas `client.GetStringAsync` oczekuje. W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują okazję do samodzielnej pracy

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Poniższa instrukcja wstrzymuje `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.

```csharp
string urlContents = await getStringTask;
```

 Na poniższej ilustracji przedstawiono przepływ sterowania od `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` do zastosowania operatora await.

 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")

 Wyrażenie await wstrzymuje `AccessTheWebAsync` aż `client.GetStringAsync` zwraca. W międzyczasie formant powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> Zazwyczaj można oczekiwać wywołania metody asynchronicznej natychmiast. Na przykład, następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`
>
> W tym temacie await operator jest stosowany później, aby pomieścić linie wyjściowych, oznaczające przepływ sterowania za pośrednictwem programu.

### <a name="step-four"></a>Krok czwarty

Deklarowanym typem zwracanym metody `AccessTheWebAsync` jest `Task<int>`. W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej do `startButton_Click`. Należy zrozumieć, że zwracane zadanie nie jest `getStringTask`. Zwracane zadanie jest nowym zadaniem liczby całkowitej określającej, co jeszcze pozostało do zrobienia WE wstrzymanej metodzie, `AccessTheWebAsync`. Zadanie jest obietnicą ze `AccessTheWebAsync` do utworzenia typu integer, po ukończeniu zadania.

Poniższa instrukcja przypisuje to zadanie `getLengthTask` zmiennej.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) dopóki trwa oczekiwanie na zadanie. Poniższe wiersze danych wyjściowych przedstawiają tę pracę.

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 Postęp w `startButton_Click` jest zawieszony gdy `getLengthTask` jest oczekiwane. Poniższa instrukcja przypisania wstrzymuje `startButton_Click` aż `AccessTheWebAsync` zostało zakończone.

```csharp
int contentLength = await getLengthTask;
```

 Na poniższej ilustracji, strzałki pokazują przepływ sterowania z wyrażenia oczekującego w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` aż `getLengthTask` jest oczekiwane.

 ![Krok czwarty](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 4")

### <a name="step-five"></a>Krok piąty

Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest zwalniane z zawieszenia i można kontynuować po instrukcji czekania. Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Argument instrukcji return `urlContents.Length`, jest zapisywany w zadaniu, `AccessTheWebAsync` zwraca. Wyrażenie await pobiera tę wartość ze `getLengthTask` w `startButton_Click`.

 Poniższa ilustracja przedstawia przekazanie sterowania po `client.GetStringAsync` (i `getStringTask`) są kompletne.

 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")

 `AccessTheWebAsync` przebieg do ukończenia, a formant powraca do `startButton_Click`, która oczekuje na zakończenie.

### <a name="step-six"></a>Krok SZÓSTY

Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie można kontynuować po instrukcji czekania w `startButton_Async`. W rzeczywistości program nie ma nic więcej do zrobienia.

Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w metodzie `startButton_Async`:

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Wyrażenie await pobiera ze `getLengthTask` wartość całkowitą, która jest argumentem instrukcji return w `AccessTheWebAsync`. Poniższa instrukcja przypisuje wartość do `contentLength` zmiennej.

```csharp
int contentLength = await getLengthTask;
```

 Poniższa ilustracja przedstawia powrót sterowania z `AccessTheWebAsync` do `startButton_Click`.

 ![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace 6")

## <a name="see-also"></a>Zobacz także

- [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Próbka asynchroniczna: Przepływ sterowania w programach Async (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
