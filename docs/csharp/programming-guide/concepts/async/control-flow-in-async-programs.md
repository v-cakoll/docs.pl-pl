---
title: Przepływ sterowania w programach asynchronicznych (C#)
description: Dowiedz się więcej o przepływie sterowania w prostym asynchronicznym programie w języku C#, aby zrozumieć sposób pisania i konserwowania programów asynchronicznych przy użyciu słów kluczowych async i await.
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 3946db958466a9f9914a5fa7b37c0db3a64d4b3d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925374"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="efef0-103">Przepływ sterowania w programach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="efef0-103">Control flow in async programs (C#)</span></span>

<span data-ttu-id="efef0-104">Można łatwiej pisać i konserwować programy asynchroniczne przy użyciu `async` `await` słów kluczowych i.</span><span class="sxs-lookup"><span data-stu-id="efef0-104">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="efef0-105">Jednak wyniki mogą być niewidoczne, jeśli nie zrozumiesz, jak działa program.</span><span class="sxs-lookup"><span data-stu-id="efef0-105">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="efef0-106">Ten temat śledzi przepływ kontroli za pośrednictwem prostego programu asynchronicznego, aby pokazać, gdy kontrolka przechodzi z jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="efef0-106">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="efef0-107">Ogólnie rzecz biorąc, należy oznaczyć metody, które zawierają kod asynchroniczny za pomocą modyfikatora [Async (C#)](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="efef0-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="efef0-108">W metodzie, która jest oznaczona za pomocą modyfikatora asynchronicznego, można użyć operatora [Await (C#)](../../../language-reference/operators/await.md) , aby określić miejsce wstrzymania metody do oczekiwania na zakończenie wywołanego procesu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="efef0-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="efef0-109">Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="efef0-109">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="efef0-110">W poniższym przykładzie zastosowano metody asynchroniczne, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="efef0-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="efef0-111">Przykład zawiera poniższe dwie metody.</span><span class="sxs-lookup"><span data-stu-id="efef0-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="efef0-112">`startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetlają wynik.</span><span class="sxs-lookup"><span data-stu-id="efef0-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="efef0-113">`AccessTheWebAsync`, która pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="efef0-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="efef0-114">`AccessTheWebAsync`używa metody asynchronicznej <xref:System.Net.Http.HttpClient> , <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> Aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="efef0-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="efef0-115">Numerowane linie wyświetlania pojawiają się w punktach strategicznych w całym programie, aby pomóc zrozumieć, jak działa program, i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="efef0-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="efef0-116">Linie wyświetlania są oznaczone jako "ONE" do "SZÓSTe".</span><span class="sxs-lookup"><span data-stu-id="efef0-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="efef0-117">Etykiety reprezentują kolejność, w której program osiągnie te wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="efef0-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="efef0-118">Poniższy kod przedstawia kontur programu.</span><span class="sxs-lookup"><span data-stu-id="efef0-118">The following code shows an outline of the program.</span></span>

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

<span data-ttu-id="efef0-119">Każda z oznaczonych lokalizacji "jeden" do "SZÓSTy" wyświetla informacje o bieżącym stanie programu.</span><span class="sxs-lookup"><span data-stu-id="efef0-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="efef0-120">Zostaną wyświetlone następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="efef0-120">The following output is produced:</span></span>

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

## <a name="set-up-the-program"></a><span data-ttu-id="efef0-121">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="efef0-121">Set up the program</span></span>

<span data-ttu-id="efef0-122">Możesz pobrać kod, który jest wykorzystywany przez ten temat w witrynie MSDN, lub możesz utworzyć go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="efef0-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="efef0-123">Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="efef0-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="efef0-124">Pobierz program</span><span class="sxs-lookup"><span data-stu-id="efef0-124">Download the program</span></span>

<span data-ttu-id="efef0-125">Możesz pobrać aplikację dla tego tematu z [przykładu asynchronicznego: przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="efef0-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="efef0-126">Poniższe kroki otwierają i uruchamiają program.</span><span class="sxs-lookup"><span data-stu-id="efef0-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="efef0-127">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efef0-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="efef0-128">Na pasku menu wybierz **plik**  >  **Otwórz**  >  **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="efef0-128">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="efef0-129">Przejdź do folderu, który zawiera niespakowany przykładowy kod, Otwórz plik rozwiązania (. sln), a następnie wybierz klawisz **F5** , aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="efef0-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="efef0-130">Samodzielne tworzenie programu</span><span class="sxs-lookup"><span data-stu-id="efef0-130">Create the program Yourself</span></span>

<span data-ttu-id="efef0-131">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="efef0-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="efef0-132">Aby uruchomić projekt, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="efef0-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="efef0-133">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="efef0-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="efef0-134">Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.</span><span class="sxs-lookup"><span data-stu-id="efef0-134">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="efef0-135">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="efef0-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="efef0-136">Wybierz **zainstalowaną**  >  kategorię**Visual C#**  >  **Windows Desktop** , a następnie wybierz pozycję **Aplikacja WPF** z listy szablonów projektu.</span><span class="sxs-lookup"><span data-stu-id="efef0-136">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="efef0-137">Wprowadź `AsyncTracer` nazwę projektu, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="efef0-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="efef0-138">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="efef0-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="efef0-139">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="efef0-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="efef0-140">Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="efef0-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="efef0-141">W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="efef0-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="efef0-142">Proste okno zawierające pole tekstowe i przycisk pojawia się w widoku **projekt** MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="efef0-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="efef0-143">Dodaj odwołanie do <xref:System.Net.Http> .</span><span class="sxs-lookup"><span data-stu-id="efef0-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="efef0-144">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow.XAML.cs, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="efef0-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="efef0-145">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="efef0-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

10. <span data-ttu-id="efef0-146">Wybierz klawisz **F5** , aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="efef0-146">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="efef0-147">Wyświetlane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="efef0-147">The following output appears:</span></span>

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

## <a name="trace-the-program"></a><span data-ttu-id="efef0-148">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="efef0-148">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="efef0-149">Kroki jeden i dwa</span><span class="sxs-lookup"><span data-stu-id="efef0-149">Steps ONE and TWO</span></span>

<span data-ttu-id="efef0-150">Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync` i `AccessTheWebAsync` wywołania metody asynchronicznej <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> .</span><span class="sxs-lookup"><span data-stu-id="efef0-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="efef0-151">Na poniższej ilustracji przedstawiono wywołania metody do metody.</span><span class="sxs-lookup"><span data-stu-id="efef0-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="efef0-152">![Kroki jeden i dwa](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="efef0-152">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="efef0-153">Zwracany typ obu `AccessTheWebAsync` i `client.GetStringAsync` to <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="efef0-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="efef0-154">Dla `AccessTheWebAsync` , TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="efef0-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="efef0-155">Dla `GetStringAsync` , TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="efef0-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="efef0-156">Aby uzyskać więcej informacji na temat typów zwracanych przez metodę asynchroniczną, zobacz [asynchroniczne typy zwracane (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="efef0-156">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="efef0-157">Metoda asynchroniczna zwracająca zadanie zwraca wystąpienie zadania, gdy kontrolka przesunie się z powrotem do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="efef0-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="efef0-158">Kontrolka zwraca z metody asynchronicznej do obiektu wywołującego `await` , gdy w wywołanej metodzie zostanie napotkany operator lub gdy wywołana metoda zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="efef0-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="efef0-159">Linie wyświetlania oznaczone etykietą "trzy" do "sześć" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="efef0-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="efef0-160">Krok trzeci</span><span class="sxs-lookup"><span data-stu-id="efef0-160">Step THREE</span></span>

<span data-ttu-id="efef0-161">W programie `AccessTheWebAsync` wywoływana jest Metoda asynchroniczna, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> Aby pobrać zawartość docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="efef0-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="efef0-162">Kontrolka zwraca z `client.GetStringAsync` do, `AccessTheWebAsync` gdy `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="efef0-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="efef0-163">`client.GetStringAsync`Metoda zwraca zadanie ciągu, który jest przypisany do `getStringTask` zmiennej w `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="efef0-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="efef0-164">Poniższy wiersz w przykładowym programie pokazuje wywołanie `client.GetStringAsync` i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="efef0-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="efef0-165">Możesz traktować zadanie jako obietnicę, `client.GetStringAsync` Aby utworzyć rzeczywisty ciąg ostatecznie.</span><span class="sxs-lookup"><span data-stu-id="efef0-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="efef0-166">W międzyczasie, jeśli program `AccessTheWebAsync` ma pracę, która nie jest zależna od uzgodnionego ciągu z `client.GetStringAsync` , to działanie może być kontynuowane podczas `client.GetStringAsync` oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="efef0-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="efef0-167">W przykładzie następujące wiersze danych wyjściowych, które są oznaczone etykietą "trzy", reprezentują możliwość wykonania niezależnej pracy</span><span class="sxs-lookup"><span data-stu-id="efef0-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="efef0-168">Poniższa instrukcja zawiesza postęp w `AccessTheWebAsync` czasie `getStringTask` oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="efef0-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="efef0-169">Na poniższej ilustracji przedstawiono przepływ sterowania z `client.GetStringAsync` do przypisania do `getStringTask` i od tworzenia `getStringTask` do aplikacji operatora await.</span><span class="sxs-lookup"><span data-stu-id="efef0-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="efef0-170">![Krok trzeci](./media/asynctrace-three.png "AsyncTrace — trzy")</span><span class="sxs-lookup"><span data-stu-id="efef0-170">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="efef0-171">Wyrażenie await zawiesza się `AccessTheWebAsync` do momentu `client.GetStringAsync` powracania.</span><span class="sxs-lookup"><span data-stu-id="efef0-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="efef0-172">W międzyczasie sterowanie powraca do obiektu wywołującego `AccessTheWebAsync` , `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="efef0-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="efef0-173">Zwykle oczekujesz natychmiastowego wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="efef0-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="efef0-174">Na przykład następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask` :`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="efef0-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="efef0-175">W tym temacie operator await jest stosowany później, aby pomieścić linie wyjściowe, które oznaczają przepływ sterowania przez program.</span><span class="sxs-lookup"><span data-stu-id="efef0-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="efef0-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="efef0-176">Step FOUR</span></span>

<span data-ttu-id="efef0-177">Zadeklarowany zwracany typ `AccessTheWebAsync` to `Task<int>` .</span><span class="sxs-lookup"><span data-stu-id="efef0-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="efef0-178">W związku z tym, gdy `AccessTheWebAsync` zostanie zawieszone, zwraca zadanie z liczbą całkowitą do `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="efef0-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="efef0-179">Należy pamiętać, że zwrócone zadanie nie jest `getStringTask` .</span><span class="sxs-lookup"><span data-stu-id="efef0-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="efef0-180">Zwrócone zadanie to nowe zadanie liczb całkowitych, które reprezentuje, co pozostało do wykonania w metodzie zawieszonej `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="efef0-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="efef0-181">Zadanie jest obietnicą `AccessTheWebAsync` do wygenerowania liczby całkowitej po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="efef0-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="efef0-182">Poniższa instrukcja przypisuje to zadanie do `getLengthTask` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="efef0-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="efef0-183">Jak w programie `AccessTheWebAsync` , program `startButton_Click` może kontynuować pracę, która nie zależy od wyników zadania asynchronicznego ( `getLengthTask` ), dopóki zadanie nie zostanie oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="efef0-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="efef0-184">Poniższe wiersze danych wyjściowych przedstawiają tę działanie.</span><span class="sxs-lookup"><span data-stu-id="efef0-184">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="efef0-185">Postęp w programie `startButton_Click` jest zawieszony, gdy `getLengthTask` jest oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="efef0-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="efef0-186">Następująca instrukcja przypisania zawiesza `startButton_Click` się do momentu `AccessTheWebAsync` ukończenia.</span><span class="sxs-lookup"><span data-stu-id="efef0-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="efef0-187">Na poniższej ilustracji strzałki pokazują przepływ sterowania z wyrażenia await w `AccessTheWebAsync` do przypisywania wartości do `getLengthTask` , a następnie normalne przetwarzanie w `startButton_Click` do momentu `getLengthTask` oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="efef0-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="efef0-188">![Krok 4](./media/asynctrace-four.png "AsyncTrace — cztery")</span><span class="sxs-lookup"><span data-stu-id="efef0-188">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="efef0-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="efef0-189">Step FIVE</span></span>

<span data-ttu-id="efef0-190">Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest uwalniane z zawieszenia i może być kontynuowane za pomocą instrukcji Await.</span><span class="sxs-lookup"><span data-stu-id="efef0-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="efef0-191">Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="efef0-191">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="efef0-192">Operand instrukcji return `urlContents.Length` jest przechowywany w zadaniu, które `AccessTheWebAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="efef0-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="efef0-193">Wyrażenie await pobiera tę wartość z `getLengthTask` `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="efef0-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="efef0-194">Na poniższej ilustracji przedstawiono transfer kontroli po `client.GetStringAsync` zakończeniu (i `getStringTask` ).</span><span class="sxs-lookup"><span data-stu-id="efef0-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="efef0-195">![Krok 5](./media/asynctrace-five.png "AsyncTrace — pięć")</span><span class="sxs-lookup"><span data-stu-id="efef0-195">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="efef0-196">`AccessTheWebAsync`działa do ukończenia, a sterowanie powraca do `startButton_Click` , który oczekuje na ukończenie.</span><span class="sxs-lookup"><span data-stu-id="efef0-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="efef0-197">Krok SZÓSTy</span><span class="sxs-lookup"><span data-stu-id="efef0-197">Step SIX</span></span>

<span data-ttu-id="efef0-198">Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie może być kontynuowane po instrukcji Await w `startButton_Async` .</span><span class="sxs-lookup"><span data-stu-id="efef0-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="efef0-199">W rzeczywistości program nie ma niczego więcej.</span><span class="sxs-lookup"><span data-stu-id="efef0-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="efef0-200">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w `startButton_Async` :</span><span class="sxs-lookup"><span data-stu-id="efef0-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="efef0-201">Wyrażenie await pobiera z `getLengthTask` wartości całkowitej, która jest argumentem instrukcji return w `AccessTheWebAsync` .</span><span class="sxs-lookup"><span data-stu-id="efef0-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="efef0-202">Poniższa instrukcja przypisuje tę wartość do `contentLength` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="efef0-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="efef0-203">Na poniższej ilustracji przedstawiono powrót sterowania z `AccessTheWebAsync` do `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="efef0-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="efef0-204">![Krok SZÓSTy](./media/asynctrace-six.png "AsyncTrace — sześć")</span><span class="sxs-lookup"><span data-stu-id="efef0-204">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="efef0-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efef0-205">See also</span></span>

- [<span data-ttu-id="efef0-206">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="efef0-206">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="efef0-207">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="efef0-207">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="efef0-208">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="efef0-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="efef0-209">Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="efef0-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
