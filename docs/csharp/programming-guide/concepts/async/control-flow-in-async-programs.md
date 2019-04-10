---
title: Przepływ sterowania w programach Async (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 6a7b8f3f41b2096e3e7524d03217bdc123f26f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326206"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="fe599-102">Przepływ sterowania w programach async (C#)</span><span class="sxs-lookup"><span data-stu-id="fe599-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="fe599-103">Pozwala pisać i łatwiej utrzymać asynchroniczne programy za pomocą `async` i `await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="fe599-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="fe599-104">Jednak wyniki mogą Cię zaskoczyć, jeśli nie rozumiesz sposobu działania programu.</span><span class="sxs-lookup"><span data-stu-id="fe599-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="fe599-105">W tym temacie omówiono, którą przepływ sterowania za pośrednictwem prostego programu asynchronicznego aby pokazać, kiedy sterowania przechodzi od jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="fe599-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="fe599-106">Ogólnie rzecz biorąc Oznacz metody, które zawierają kod asynchroniczny [async (C#)](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="fe599-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="fe599-107">W metodzie, która jest oznaczona modyfikatorem asynchronicznym, można użyć [await (C#)](../../../../csharp/language-reference/keywords/await.md) operatora, aby określić, gdzie metoda wstrzymuje się oczekiwania wywołany proces asynchroniczny zakończyć.</span><span class="sxs-lookup"><span data-stu-id="fe599-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="fe599-108">Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fe599-108">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="fe599-109">W poniższym przykładzie użyto metody asynchronicznej, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="fe599-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="fe599-110">Przykład zawiera następujących dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="fe599-110">The example contains the following two methods.</span></span>

-   `startButton_Click`<span data-ttu-id="fe599-111">, która wywołuje metodę `AccessTheWebAsync` i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="fe599-111">, which calls `AccessTheWebAsync` and displays the result.</span></span>

-   `AccessTheWebAsync`<span data-ttu-id="fe599-112">, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="fe599-112">, which downloads the contents of a website as a string and returns the length of the string.</span></span> `AccessTheWebAsync` <span data-ttu-id="fe599-113">używa asynchronicznej <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="fe599-113">uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="fe599-114">Ponumerowane wyświetlanych wierszy pojawiających się w strategiczny punktach w całym programie, aby lepiej zrozumieć, jak działa program i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="fe599-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="fe599-115">Wyświetlane wiersze są oznaczone etykietami od "ONE"do "sześć."</span><span class="sxs-lookup"><span data-stu-id="fe599-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="fe599-116">Etykiety reprezentują kolejność, w jakiej program osiąga te wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="fe599-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="fe599-117">Poniższy kod przedstawia zarys programu.</span><span class="sxs-lookup"><span data-stu-id="fe599-117">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="fe599-118">Każda z etykietami lokalizacje "ONE"do "6," Wyświetla informacje dotyczące bieżącego stanu programu.</span><span class="sxs-lookup"><span data-stu-id="fe599-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="fe599-119">Są następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fe599-119">The following output is produced:</span></span>

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

## <a name="set-up-the-program"></a><span data-ttu-id="fe599-120">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="fe599-120">Set up the program</span></span>

<span data-ttu-id="fe599-121">Kod, który używa tego tematu możesz pobrać z witryny MSDN lub tworzyć je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="fe599-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="fe599-122">Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fe599-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="fe599-123">Pobierz program</span><span class="sxs-lookup"><span data-stu-id="fe599-123">Download the program</span></span>

<span data-ttu-id="fe599-124">Możesz pobrać aplikację dotyczącą tego tematu z [próbka asynchroniczna: Kontrolowanie Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="fe599-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="fe599-125">Poniższe kroki, Otwórz i uruchom program.</span><span class="sxs-lookup"><span data-stu-id="fe599-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="fe599-126">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe599-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="fe599-127">Na pasku menu wybierz **pliku** > **Otwórz** > **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="fe599-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="fe599-128">Przejdź do folderu, który posiada rozpakowany przykładowego kodu, otwórz plik rozwiązania (.sln), a następnie wybierz **F5** klawisz, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="fe599-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="fe599-129">Utwórz program, samodzielnie</span><span class="sxs-lookup"><span data-stu-id="fe599-129">Create the program Yourself</span></span>

<span data-ttu-id="fe599-130">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="fe599-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="fe599-131">Aby uruchomić projekt, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe599-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="fe599-132">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe599-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="fe599-133">Na pasku menu wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="fe599-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="fe599-134">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="fe599-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="fe599-135">Wybierz **zainstalowane** > **Visual C#** > **pulpitu Windows** kategorii, a następnie wybierz **aplikacja WPF** z listy szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="fe599-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="fe599-136">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="fe599-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="fe599-137">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fe599-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="fe599-138">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="fe599-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="fe599-139">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="fe599-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="fe599-140">W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="fe599-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="fe599-141">Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="fe599-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="fe599-142">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="fe599-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="fe599-143">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="fe599-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="fe599-144">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="fe599-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="fe599-145">Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="fe599-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="fe599-146">Zostanie wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="fe599-146">The following output appears:</span></span>

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

## <a name="trace-the-program"></a><span data-ttu-id="fe599-147">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="fe599-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="fe599-148">Kroki 1 i 2</span><span class="sxs-lookup"><span data-stu-id="fe599-148">Steps ONE and TWO</span></span>

<span data-ttu-id="fe599-149">Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="fe599-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="fe599-150">Poniższa ilustracja przedstawia wywołania z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="fe599-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="fe599-151">![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="fe599-151">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="fe599-152">Zwracanym typem obu metod `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="fe599-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="fe599-153">Aby uzyskać `AccessTheWebAsync`, TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="fe599-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="fe599-154">Aby uzyskać `GetStringAsync`, TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fe599-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="fe599-155">Aby uzyskać więcej informacji na temat typów zwracanych w metodach asynchronicznych, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="fe599-155">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="fe599-156">Asynchroniczna metoda zwracania zadania Zwraca wystąpienie zadania Jeśli kontrola przechodzi do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fe599-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="fe599-157">Formant powraca z metody asynchronicznej do obiektu wywołującego gdy `await` operator zostanie napotkany w metodzie wywoływanej, lub gdy metoda wywoływana się zakończy.</span><span class="sxs-lookup"><span data-stu-id="fe599-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="fe599-158">Wyświetlane wiersze, które są oznaczone jako "Trzy"do "6" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="fe599-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="fe599-159">Krok 3</span><span class="sxs-lookup"><span data-stu-id="fe599-159">Step THREE</span></span>

<span data-ttu-id="fe599-160">W `AccessTheWebAsync`, metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="fe599-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="fe599-161">Formant powraca z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="fe599-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="fe599-162">`client.GetStringAsync` Metoda zwraca zadanie ciągu, która jest przypisana do `getStringTask` zmienną `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="fe599-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="fe599-163">Następujący wiersz w programie przykładowym pokazuje wywołanie `client.GetStringAsync` i przypisania.</span><span class="sxs-lookup"><span data-stu-id="fe599-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="fe599-164">Można traktować zadanie jako zapowiedź `client.GetStringAsync` do produkcji rzeczywistego ciągu po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="fe599-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="fe599-165">W międzyczasie Jeśli `AccessTheWebAsync` ma robić prace, które nie są zależne od uzgodnionego ciągu z `client.GetStringAsync`, można kontynuować pracę podczas `client.GetStringAsync` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="fe599-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="fe599-166">W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują okazję do samodzielnej pracy</span><span class="sxs-lookup"><span data-stu-id="fe599-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="fe599-167">Poniższa instrukcja wstrzymuje `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="fe599-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="fe599-168">Na poniższej ilustracji przedstawiono przepływ sterowania od `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` do zastosowania operatora await.</span><span class="sxs-lookup"><span data-stu-id="fe599-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="fe599-169">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")</span><span class="sxs-lookup"><span data-stu-id="fe599-169">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="fe599-170">Wyrażenie await wstrzymuje `AccessTheWebAsync` aż `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="fe599-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="fe599-171">W międzyczasie formant powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="fe599-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="fe599-172">Zazwyczaj można oczekiwać wywołania metody asynchronicznej natychmiast.</span><span class="sxs-lookup"><span data-stu-id="fe599-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="fe599-173">Na przykład, następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`:</span><span class="sxs-lookup"><span data-stu-id="fe599-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`:</span></span> `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> <span data-ttu-id="fe599-174">W tym temacie await operator jest stosowany później, aby pomieścić linie wyjściowych, oznaczające przepływ sterowania za pośrednictwem programu.</span><span class="sxs-lookup"><span data-stu-id="fe599-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="fe599-175">Krok czwarty</span><span class="sxs-lookup"><span data-stu-id="fe599-175">Step FOUR</span></span>

<span data-ttu-id="fe599-176">Deklarowanym typem zwracanym metody `AccessTheWebAsync` jest `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="fe599-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="fe599-177">W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="fe599-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="fe599-178">Należy zrozumieć, że zwracane zadanie nie jest `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="fe599-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="fe599-179">Zwracane zadanie jest nowym zadaniem liczby całkowitej określającej, co jeszcze pozostało do zrobienia WE wstrzymanej metodzie, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="fe599-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="fe599-180">Zadanie jest obietnicą ze `AccessTheWebAsync` do utworzenia typu integer, po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="fe599-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="fe599-181">Poniższa instrukcja przypisuje to zadanie `getLengthTask` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fe599-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="fe599-182">Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) dopóki trwa oczekiwanie na zadanie.</span><span class="sxs-lookup"><span data-stu-id="fe599-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="fe599-183">Poniższe wiersze danych wyjściowych przedstawiają tę pracę.</span><span class="sxs-lookup"><span data-stu-id="fe599-183">The following output lines represent that work.</span></span>

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="fe599-184">Postęp w `startButton_Click` jest zawieszony gdy `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="fe599-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="fe599-185">Poniższa instrukcja przypisania wstrzymuje `startButton_Click` aż `AccessTheWebAsync` zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="fe599-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="fe599-186">Na poniższej ilustracji, strzałki pokazują przepływ sterowania z wyrażenia oczekującego w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` aż `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="fe599-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="fe599-187">![Krok czwarty](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 4")</span><span class="sxs-lookup"><span data-stu-id="fe599-187">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="fe599-188">Krok piąty</span><span class="sxs-lookup"><span data-stu-id="fe599-188">Step FIVE</span></span>

<span data-ttu-id="fe599-189">Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest zwalniane z zawieszenia i można kontynuować po instrukcji czekania.</span><span class="sxs-lookup"><span data-stu-id="fe599-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="fe599-190">Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="fe599-190">The following lines of output represent the resumption of processing.</span></span>

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="fe599-191">Argument instrukcji return `urlContents.Length`, jest zapisywany w zadaniu, `AccessTheWebAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="fe599-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="fe599-192">Wyrażenie await pobiera tę wartość ze `getLengthTask` w `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="fe599-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="fe599-193">Poniższa ilustracja przedstawia przekazanie sterowania po `client.GetStringAsync` (i `getStringTask`) są kompletne.</span><span class="sxs-lookup"><span data-stu-id="fe599-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="fe599-194">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")</span><span class="sxs-lookup"><span data-stu-id="fe599-194">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 `AccessTheWebAsync` <span data-ttu-id="fe599-195">przebieg do ukończenia, a formant powraca do `startButton_Click`, która oczekuje na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="fe599-195">runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="fe599-196">Krok SZÓSTY</span><span class="sxs-lookup"><span data-stu-id="fe599-196">Step SIX</span></span>

<span data-ttu-id="fe599-197">Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie można kontynuować po instrukcji czekania w `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="fe599-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="fe599-198">W rzeczywistości program nie ma nic więcej do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="fe599-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="fe599-199">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w metodzie `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="fe599-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="fe599-200">Wyrażenie await pobiera ze `getLengthTask` wartość całkowitą, która jest argumentem instrukcji return w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="fe599-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="fe599-201">Poniższa instrukcja przypisuje wartość do `contentLength` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fe599-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="fe599-202">Poniższa ilustracja przedstawia powrót sterowania z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="fe599-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="fe599-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="fe599-203">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="fe599-204">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fe599-204">See also</span></span>

- [<span data-ttu-id="fe599-205">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="fe599-205">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="fe599-206">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="fe599-206">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="fe599-207">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="fe599-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="fe599-208">Próbka asynchroniczna: Przepływ sterowania w aplikacjach asynchronicznych (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fe599-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
