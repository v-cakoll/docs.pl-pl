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
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="9ab28-102">Przepływ sterowania w programach asynchroniczny (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab28-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="9ab28-103">Programy asynchroniczne można łatwiej pisać i obsługiwać `async` `await` za pomocą słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="9ab28-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="9ab28-104">Jednak wyniki mogą cię zaskoczyć, jeśli nie rozumiesz, jak działa program.</span><span class="sxs-lookup"><span data-stu-id="9ab28-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="9ab28-105">W tym temacie śledzenia przepływu kontroli za pośrednictwem prostego programu asynchronicznego, aby pokazać, kiedy kontrola przenosi się z jednej metody do drugiej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="9ab28-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="9ab28-106">Ogólnie rzecz biorąc, należy oznaczyć metody, które zawierają kod asynchroniczny z modyfikatora [async (C#).](../../../language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="9ab28-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="9ab28-107">W metodzie oznaczonej modyfikatorem asynchronicznym można użyć operatora [await (C#),](../../../language-reference/operators/await.md) aby określić, gdzie metoda wstrzymuje oczekiwanie na zakończenie procesu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="9ab28-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="9ab28-108">Aby uzyskać więcej informacji, zobacz [Programowanie asynchroniczne z async i await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="9ab28-108">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="9ab28-109">W poniższym przykładzie użyto metod asynchronicznej do pobierania zawartości określonej witryny sieci Web jako ciągu i wyświetlania długości ciągu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="9ab28-110">Przykład zawiera następujące dwie metody.</span><span class="sxs-lookup"><span data-stu-id="9ab28-110">The example contains the following two methods.</span></span>

- <span data-ttu-id="9ab28-111">`startButton_Click`, który `AccessTheWebAsync` wywołuje i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="9ab28-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="9ab28-112">`AccessTheWebAsync`, który pobiera zawartość witryny jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="9ab28-113">`AccessTheWebAsync`używa metody asynchronicznej, <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="9ab28-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="9ab28-114">Ponumerowane linie wyświetlania pojawiają się w strategicznych punktach w całym programie, aby pomóc Ci zrozumieć, jak działa program i wyjaśnić, co dzieje się w każdym zaznaczonym punkcie.</span><span class="sxs-lookup"><span data-stu-id="9ab28-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="9ab28-115">Linie wyświetlania są oznaczone jako "ONE" do "SIX".</span><span class="sxs-lookup"><span data-stu-id="9ab28-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="9ab28-116">Etykiety reprezentują kolejność, w jakiej program dociera do tych wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="9ab28-117">Poniższy kod przedstawia konspekt programu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-117">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="9ab28-118">Każda z oznaczonych lokalizacji, "ONE" do "SIX", wyświetla informacje o bieżącym stanie programu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="9ab28-119">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9ab28-119">The following output is produced:</span></span>

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

## <a name="set-up-the-program"></a><span data-ttu-id="9ab28-120">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="9ab28-120">Set up the program</span></span>

<span data-ttu-id="9ab28-121">Można pobrać kod, który ten temat używa z MSDN lub można go utworzyć samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="9ab28-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab28-122">Aby uruchomić przykład, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9ab28-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="9ab28-123">Pobierz program</span><span class="sxs-lookup"><span data-stu-id="9ab28-123">Download the program</span></span>

<span data-ttu-id="9ab28-124">Aplikację dla tego tematu można pobrać z [próbki asynchronicznej: Przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="9ab28-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="9ab28-125">Poniższe kroki otwierają i uruchamiają program.</span><span class="sxs-lookup"><span data-stu-id="9ab28-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="9ab28-126">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ab28-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="9ab28-127">Na pasku**Open** > menu wybierz pozycję Otwórz**projekt/rozwiązanie** **File** > .</span><span class="sxs-lookup"><span data-stu-id="9ab28-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="9ab28-128">Przejdź do folderu, w który znajduje się rozpakowany przykładowy kod, otwórz plik rozwiązania (.sln), a następnie wybierz klawisz **F5** do utworzenia i uruchomienia projektu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="9ab28-129">Stwórz program samodzielnie</span><span class="sxs-lookup"><span data-stu-id="9ab28-129">Create the program Yourself</span></span>

<span data-ttu-id="9ab28-130">Poniższy projekt Fundacji prezentacji systemu Windows (WPF) zawiera przykład kodu dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="9ab28-131">Aby uruchomić projekt, wykonaj następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="9ab28-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="9ab28-132">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ab28-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="9ab28-133">Na pasku menu wybierz pozycję **Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="9ab28-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="9ab28-134">Zostanie otwarte okno dialogowe **Nowy projekt.**</span><span class="sxs-lookup"><span data-stu-id="9ab28-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="9ab28-135">Wybierz kategorię **Zainstalowane** > **pulpitu systemu Windows** Visual**C#,** > a następnie wybierz **pozycję Aplikacja WPF** z listy szablonów projektów.</span><span class="sxs-lookup"><span data-stu-id="9ab28-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="9ab28-136">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="9ab28-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="9ab28-137">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="9ab28-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="9ab28-138">W Edytorze kodu programu Visual Studio wybierz kartę **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="9ab28-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="9ab28-139">Jeśli karta nie jest widoczna, otwórz menu skrótów mainwindow.xaml w **Eksploratorze rozwiązań**, a następnie wybierz pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="9ab28-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="9ab28-140">W widoku **XAML** MainWindow.xaml, zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="9ab28-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="9ab28-141">Proste okno zawierające pole tekstowe i przycisk pojawi się w widoku **projektowym** pliku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="9ab28-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="9ab28-142">Dodaj odwołanie <xref:System.Net.Http>do pliku .</span><span class="sxs-lookup"><span data-stu-id="9ab28-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="9ab28-143">W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="9ab28-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="9ab28-144">W MainWindow.xaml.cs należy zastąpić kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="9ab28-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="9ab28-145">Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="9ab28-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="9ab28-146">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="9ab28-146">The following output appears:</span></span>

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

## <a name="trace-the-program"></a><span data-ttu-id="9ab28-147">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="9ab28-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="9ab28-148">Kroki pierwsze i drugie</span><span class="sxs-lookup"><span data-stu-id="9ab28-148">Steps ONE and TWO</span></span>

<span data-ttu-id="9ab28-149">Pierwsze dwie linie wyświetlania `startButton_Click` śledzą `AccessTheWebAsync`ścieżkę jako wywołania i `AccessTheWebAsync` wywołają metodę <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>asynchroniczną .</span><span class="sxs-lookup"><span data-stu-id="9ab28-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="9ab28-150">Na poniższej ilustracji przedstawiono wywołania z metody na metodę.</span><span class="sxs-lookup"><span data-stu-id="9ab28-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="9ab28-151">![Kroki pierwsze i drugie](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="9ab28-151">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="9ab28-152">Typ zwracany `AccessTheWebAsync` obu `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>i jest .</span><span class="sxs-lookup"><span data-stu-id="9ab28-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="9ab28-153">Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="9ab28-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="9ab28-154">Dla `GetStringAsync`, TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="9ab28-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="9ab28-155">Aby uzyskać więcej informacji na temat typów zwracania metody asynchronicznej, zobacz [Async Return Types (C#).](./async-return-types.md)</span><span class="sxs-lookup"><span data-stu-id="9ab28-155">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="9ab28-156">Zwracana przez zadania metoda asynchroniczna zwraca wystąpienie zadania, gdy formant przenosi się z powrotem do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9ab28-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="9ab28-157">Control zwraca z metody asynchronicznej `await` do obiektu wywołującego, gdy operator zostanie napotkany w wywoływanej metody lub po zakończeniu wywoływanej metody.</span><span class="sxs-lookup"><span data-stu-id="9ab28-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="9ab28-158">Linie wyświetlania oznaczone jako "TRZY" do "SIX" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="9ab28-159">Krok trzeci</span><span class="sxs-lookup"><span data-stu-id="9ab28-159">Step THREE</span></span>

<span data-ttu-id="9ab28-160">W `AccessTheWebAsync`przypadku metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> asynchronicznej jest wywoływana w celu pobrania zawartości docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="9ab28-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="9ab28-161">Formant powraca `client.GetStringAsync` `AccessTheWebAsync` z `client.GetStringAsync` do when powraca.</span><span class="sxs-lookup"><span data-stu-id="9ab28-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="9ab28-162">Metoda `client.GetStringAsync` zwraca zadanie ciągu, który jest przypisany do zmiennej `getStringTask` w . `AccessTheWebAsync`</span><span class="sxs-lookup"><span data-stu-id="9ab28-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="9ab28-163">W poniższym wierszu w przykładowym programie przedstawiono wywołanie `client.GetStringAsync` i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="9ab28-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="9ab28-164">Można myśleć o zadaniu jako `client.GetStringAsync` obietnicy, aby wygenerować rzeczywisty ciąg ostatecznie.</span><span class="sxs-lookup"><span data-stu-id="9ab28-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="9ab28-165">W międzyczasie, `AccessTheWebAsync` jeśli ma pracy, aby to zrobić, że `client.GetStringAsync`nie zależy od `client.GetStringAsync` obiecanego ciągu z , że praca może być kontynuowana podczas oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9ab28-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="9ab28-166">W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "TRZY", stanowią możliwość wykonywania niezależnej pracy</span><span class="sxs-lookup"><span data-stu-id="9ab28-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="9ab28-167">Poniższa instrukcja zawiesza `AccessTheWebAsync` `getStringTask` postęp w czasie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="9ab28-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="9ab28-168">Na poniższej ilustracji przedstawiono `client.GetStringAsync` przepływ kontroli `getStringTask` z do `getStringTask` przypisania do i od utworzenia do stosowania operatora await.</span><span class="sxs-lookup"><span data-stu-id="9ab28-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="9ab28-169">![Krok trzeci](./media/asynctrace-three.png "AsyncTrace-Trzy")</span><span class="sxs-lookup"><span data-stu-id="9ab28-169">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="9ab28-170">Wyrażenie await zawiesza `AccessTheWebAsync` `client.GetStringAsync` się, dopóki nie powróci.</span><span class="sxs-lookup"><span data-stu-id="9ab28-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="9ab28-171">W międzyczasie kontrola powraca do `AccessTheWebAsync`obiektu `startButton_Click`wywołującego , .</span><span class="sxs-lookup"><span data-stu-id="9ab28-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="9ab28-172">Zazwyczaj oczekujesz wywołania metody asynchronicznej natychmiast.</span><span class="sxs-lookup"><span data-stu-id="9ab28-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="9ab28-173">Na przykład następujące przypisanie może zastąpić poprzedni kod, `getStringTask`który tworzy, a następnie oczekuje:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="9ab28-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="9ab28-174">W tym temacie operator await jest stosowany później, aby pomieścić linie wyjściowe, które oznaczają przepływ kontroli za pośrednictwem programu.</span><span class="sxs-lookup"><span data-stu-id="9ab28-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="9ab28-175">Krok czwarty</span><span class="sxs-lookup"><span data-stu-id="9ab28-175">Step FOUR</span></span>

<span data-ttu-id="9ab28-176">Zadeklarowany typ `AccessTheWebAsync` zwracany jest `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="9ab28-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="9ab28-177">W związku `AccessTheWebAsync` z tym po zawieszeniu zwraca `startButton_Click`zadanie liczby całkowitej do .</span><span class="sxs-lookup"><span data-stu-id="9ab28-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="9ab28-178">Należy zrozumieć, że zwrócone zadanie `getStringTask`nie jest .</span><span class="sxs-lookup"><span data-stu-id="9ab28-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="9ab28-179">Zwrócone zadanie jest nowe zadanie liczby całkowitej, która reprezentuje to, co `AccessTheWebAsync`pozostaje do zrobienia w zawieszonej metody .</span><span class="sxs-lookup"><span data-stu-id="9ab28-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="9ab28-180">Zadanie jest obietnicą `AccessTheWebAsync` do wyprodukowania liczby całkowitej po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="9ab28-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="9ab28-181">Następująca instrukcja przypisuje to `getLengthTask` zadanie do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9ab28-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="9ab28-182">Podobnie `AccessTheWebAsync`jak `startButton_Click` w , można kontynuować pracę, która nie zależy od`getLengthTask`wyników zadania asynchronicznego ( ) dopóki zadanie nie jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="9ab28-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="9ab28-183">Następujące wiersze wyjściowe reprezentują tę pracę.</span><span class="sxs-lookup"><span data-stu-id="9ab28-183">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="9ab28-184">Postęp `startButton_Click` w jest `getLengthTask` zawieszony, gdy jest oczekiwana.</span><span class="sxs-lookup"><span data-stu-id="9ab28-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="9ab28-185">Następująca instrukcja `startButton_Click` przypisania zawiesza się do czasu `AccessTheWebAsync` jego zakończenia.</span><span class="sxs-lookup"><span data-stu-id="9ab28-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="9ab28-186">Na poniższej ilustracji strzałki pokazują przepływ kontroli od `AccessTheWebAsync` wyrażenia await do `getLengthTask`przypisania wartości do `startButton_Click` `getLengthTask` , a następnie normalne przetwarzanie, dopóki nie będzie oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="9ab28-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="9ab28-187">![Krok czwarty](./media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="9ab28-187">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="9ab28-188">Krok piąty</span><span class="sxs-lookup"><span data-stu-id="9ab28-188">Step FIVE</span></span>

<span data-ttu-id="9ab28-189">Gdy `client.GetStringAsync` sygnalizuje, że jest `AccessTheWebAsync` kompletny, przetwarzanie jest zwolniony z zawieszenia i może kontynuować przeszłości await instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9ab28-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="9ab28-190">Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="9ab28-190">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="9ab28-191">Operand return instrukcji , `urlContents.Length`jest przechowywany w `AccessTheWebAsync` zadaniu, które zwraca.</span><span class="sxs-lookup"><span data-stu-id="9ab28-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="9ab28-192">Wyrażenie await pobiera tę `getLengthTask` wartość `startButton_Click`z in .</span><span class="sxs-lookup"><span data-stu-id="9ab28-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="9ab28-193">Na poniższej ilustracji przedstawiono `client.GetStringAsync` transfer `getStringTask`kontroli po zakończeniu (i ) .</span><span class="sxs-lookup"><span data-stu-id="9ab28-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="9ab28-194">![Krok piąty](./media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="9ab28-194">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="9ab28-195">`AccessTheWebAsync`biegnie do zakończenia, a `startButton_Click`kontrola powraca do , który oczekuje na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="9ab28-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="9ab28-196">Krok szósty</span><span class="sxs-lookup"><span data-stu-id="9ab28-196">Step SIX</span></span>

<span data-ttu-id="9ab28-197">Gdy `AccessTheWebAsync` sygnały, że jest zakończona, przetwarzanie może `startButton_Async`kontynuować przeszłości await instrukcji w .</span><span class="sxs-lookup"><span data-stu-id="9ab28-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="9ab28-198">W rzeczywistości program nie ma nic więcej do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="9ab28-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="9ab28-199">Następujące linie wyjściowe reprezentują wznowienie przetwarzania w: `startButton_Async`</span><span class="sxs-lookup"><span data-stu-id="9ab28-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="9ab28-200">Wyrażenie await pobiera `getLengthTask` z wartości całkowitej, która jest operand return `AccessTheWebAsync`instrukcji w .</span><span class="sxs-lookup"><span data-stu-id="9ab28-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="9ab28-201">Następująca instrukcja przypisuje tę `contentLength` wartość do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9ab28-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="9ab28-202">Na poniższej ilustracji przedstawiono `AccessTheWebAsync` `startButton_Click`powrót kontroli z do .</span><span class="sxs-lookup"><span data-stu-id="9ab28-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="9ab28-203">![Krok szósty](./media/asynctrace-six.png "AsyncTrace-6")</span><span class="sxs-lookup"><span data-stu-id="9ab28-203">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="9ab28-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ab28-204">See also</span></span>

- [<span data-ttu-id="9ab28-205">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab28-205">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="9ab28-206">Typy zwrotu asynchronicznego (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab28-206">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="9ab28-207">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab28-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9ab28-208">Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9ab28-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
