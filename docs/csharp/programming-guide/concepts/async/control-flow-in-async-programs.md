---
title: Przepływ sterowania w aplikacjach asynchronicznych (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 7367b55a665a911a4d94f7b235cdc559a69854cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="control-flow-in-async-programs-c"></a>Przepływ sterowania w aplikacjach asynchronicznych (C#)
Możesz wpisać i obsługa asynchroniczne programy łatwiej przy użyciu `async` i `await` słów kluczowych. Jednak wyniki, może Cię zaskoczył Jeśli nie znasz sposób działania programu. Ślady tego tematu, które przepływu sterowania za pośrednictwem programu async proste do wyświetlenia, gdy formant są przenoszone z jednej metody do innej i jakie informacje są przesyłane za każdym razem.  
  
> [!NOTE]
>  `async` i `await` słowa kluczowe wprowadzono w programie Visual Studio 2012.  
  
 Ogólnie rzecz biorąc, możesz oznaczyć metody, które zawierają asynchroniczne kodu za pomocą [async (C#)](../../../../csharp/language-reference/keywords/async.md) modyfikator. W przypadku metody oznaczonej za pomocą modyfikatora async służy [await (C#)](../../../../csharp/language-reference/keywords/await.md) operatora, aby określić, gdzie metoda wstrzymuje oczekiwania na ukończenie wywołanego procesu asynchronicznego. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 W poniższym przykładzie użyto metody asynchroniczne, aby pobrać zawartość z określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu. Przykład zawiera następujących dwóch metod.  
  
-   `startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetla wyniki.  
  
-   `AccessTheWebAsync`, która pobiera zawartość witryny sieci Web w postaci ciągu i zwraca długość ciągu. `AccessTheWebAsync` korzysta z asynchronicznego <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.  
  
 Numerowane wyświetlania wiersze pojawiają się w punktach strategicznych w programie, aby lepiej zrozumieć, jak program zostanie uruchomiony i wyjaśniający, co się stanie w każdym punkcie, który jest oznaczony jako. Wyświetlanie linii są oznaczone jako "Jeden"do "sześć." Etykiety opisania kolejności, w którym program osiągnie tych wierszy kodu.  
  
 Poniższy kod przedstawia konspektu programu.  
  
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
  
 Każdej z etykietą lokalizacji, "ONE"do "6," Wyświetla informacje o bieżącym stanie programu. Są następujące wyniki.  
  
```  
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
 Kod, który korzysta z tego tematu możesz pobrać z MSDN lub można utworzyć ją samodzielnie.  
  
> [!NOTE]
>  Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.  
  
### <a name="download-the-program"></a>Pobierz Program  
 Możesz pobrać aplikację dla tego tematu z [próbki Async: przepływ sterowania w aplikacjach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Poniższe kroki Otwórz i uruchom program.  
  
1.  Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.  
  
3.  Przejdź do folderu, która przechowuje rozpakowane przykładowy kod, otwórz plik rozwiązania (sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.  
  
### <a name="build-the-program-yourself"></a>Samodzielnie kompilacji programu  
 Następujący projekt Windows Presentation Foundation (WPF) zawiera przykładowy kod dla tego tematu.  
  
 Aby uruchomić projekt, wykonaj następujące czynności:  
  
1.  Uruchom program Visual Studio.  
  
2.  Na pasku menu wybierz **pliku**, **nowy**, **projektu**.  
  
     **Nowy projekt** zostanie otwarte okno dialogowe.  
  
3.  W **zainstalowane szablony** okienku wybierz **Visual C#**, a następnie wybierz pozycję **aplikacji WPF** z listy typów projektów.  
  
4.  Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz pozycję **OK** przycisku.  
  
     Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.  
  
5.  Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.  
  
     Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.  
  
6.  W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.  
  
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
  
     Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.  
  
7.  Dodaj odwołanie do <xref:System.Net.Http>.  
  
8.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.  
  
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
  
10. Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.  
  
     Następujące dane wyjściowe powinny być wyświetlane.  
  
    ```  
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
 Wyświetlanie pierwszych dwóch linii śledzenia ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Poniższa ilustracja przedstawia wywołania metody metody.  
  
 ![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Zwracany typ `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>. Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą. Dla `GetStringAsync`, TResult jest ciągiem. Aby uzyskać więcej informacji na temat asynchronicznej metody zwracane typy, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
 Metody async umożliwiające zwracanie zadań Zwraca wystąpienie zadania podczas kontroli przewiduje się do obiektu wywołującego. Formant zwraca z metody asynchronicznej do swojego obiektu wywołującego albo gdy `await` napotkano operator wywołaną metodę lub gdy kończy się wywołaną metodę. Wyświetlanie linii, które są oznaczone jako "Trzy"do "SZEŚCIU" śledzenia to część procesu.  
  
### <a name="step-three"></a>Krok 3  
 W `AccessTheWebAsync`, metod asynchronicznych <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości na docelowej stronie sieci Web. Zwraca kontroli z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.  
  
 `client.GetStringAsync` Metoda zwraca ciąg, który jest przypisany do zadania `getStringTask` zmiennej w `AccessTheWebAsync`. Następujący wiersz w programie przykład zawiera wywołanie `client.GetStringAsync` oraz przypisanie.  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 Można traktować jako promise przez zadania `client.GetStringAsync` do tworzenia rzeczywistych ciągu po pewnym czasie. W międzyczasie Jeśli `AccessTheWebAsync` ma pracy, który nie jest zależny od uzgodnionej ciąg, z `client.GetStringAsync`, aby kontynuować pracę podczas `client.GetStringAsync` oczekuje. W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują możliwość wykonywania pracy, niezależnie od  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Następująca instrukcja wstrzymuje postęp w `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 Na poniższej ilustracji przedstawiono przepływu sterowania z `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` zastosowanie operatora await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")  
  
 Wyrażenie await zawiesi `AccessTheWebAsync` do momentu `client.GetStringAsync` zwraca. Tymczasem zwraca sterowania do wywołującego `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Zazwyczaj należy poczekać na wywołanie metody asynchronicznej natychmiast. Na przykład następujące przypisanie można zastąpić poprzedni kod, który tworzy, a następnie oczekiwanie `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`  
>   
>  W tym temacie operatora await jest stosowany później do uwzględnienia wiersze danych wyjściowych oznaczyć przepływu sterowania przez program.  
  
### <a name="step-four"></a>Krok 4  
 Zadeklarowany typ zwrotny `AccessTheWebAsync` jest `Task<int>`. W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej w celu `startButton_Click`. Należy pamiętać, że zwrócony zadań nie jest `getStringTask`. Zadanie zwracane jest nowe zadanie liczbę całkowitą reprezentującą, co ma odbywać się w metodzie wstrzymaną `AccessTheWebAsync`. Zadanie jest promise z `AccessTheWebAsync` wygenerowało całkowitą po zakończeniu zadania.  
  
 Następująca instrukcja przypisuje do tego zadania `getLengthTask` zmiennej.  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracy, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) do momentu zadania jest oczekiwane. Następujące wiersze danych wyjściowych reprezentują pracy.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 Postęp w `startButton_Click` zawieszone po `getLengthTask` jest oczekiwane. Następująca instrukcja przypisania wstrzymuje `startButton_Click` do momentu `AccessTheWebAsync` została ukończona.  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 Na poniższej ilustracji, strzałki oznaczają przepływu sterowania z wyrażenie await w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalnego przetwarzania w `startButton_Click` do momentu `getLengthTask` jest oczekiwane.  
  
 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "czterech AsyncTrace")  
  
### <a name="step-five"></a>Krok 5  
 Gdy `client.GetStringAsync` sygnały jest zakończone, przetwarzania w `AccessTheWebAsync` zwolnieniu od zawieszenie i można kontynuować mimo instrukcja await. Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Argument instrukcji return `urlContents.Length`, są przechowywane w zadaniu który `AccessTheWebAsync` zwraca. Wyrażenie await pobiera tej wartości od `getLengthTask` w `startButton_Click`.  
  
 Na poniższej ilustracji przedstawiono transfer kontroli po `client.GetStringAsync` (i `getStringTask`) są spełnione.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")  
  
 `AccessTheWebAsync` Zwraca używa do ukończenia i kontroli do `startButton_Click`, która oczekuje na zakończenie.  
  
### <a name="step-six"></a>Krok 6  
 Gdy `AccessTheWebAsync` sygnalizuje, że zakończeniu przetwarzania można kontynuować mimo instrukcja await w `startButton_Async`. W rzeczywistości program nie ma nic więcej robić.  
  
 Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania w `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Pobiera wyrażenie await z `getLengthTask` wartość całkowitą, która jest argument instrukcji return w `AccessTheWebAsync`. Następująca instrukcja przypisuje wartość tego `contentLength` zmiennej.  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 Na poniższej ilustracji przedstawiono zwracany formantu z `AccessTheWebAsync` do `startButton_Click`.  
  
 ![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace SZEŚCIU")  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchroniczne typy zwracane (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Przykład Async: Przepływ sterowania w aplikacjach asynchronicznych (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
