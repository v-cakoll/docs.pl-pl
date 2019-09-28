---
title: Przepływ sterowania w programach asynchronicznych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 74942ec3d293485ea6aae3940d1715af8de67c90
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71352113"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="ec64a-102">Przepływ sterowania w programach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec64a-102">Control Flow in Async Programs (Visual Basic)</span></span>

<span data-ttu-id="ec64a-103">Można łatwiej pisać i konserwować programy asynchroniczne przy użyciu słów kluczowych `Async` i `Await`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="ec64a-104">Jednak wyniki mogą być niewidoczne, jeśli nie zrozumiesz, jak działa program.</span><span class="sxs-lookup"><span data-stu-id="ec64a-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="ec64a-105">Ten temat śledzi przepływ kontroli za pośrednictwem prostego programu asynchronicznego, aby pokazać, gdy kontrolka przechodzi z jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="ec64a-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

> [!NOTE]
> <span data-ttu-id="ec64a-106">Słowa kluczowe `Async` i `Await` zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ec64a-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>

<span data-ttu-id="ec64a-107">Ogólnie rzecz biorąc, należy oznaczyć metody, które zawierają kod asynchroniczny z modyfikatorem [asynchronicznym](../../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ec64a-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="ec64a-108">W metodzie, która jest oznaczona za pomocą modyfikatora asynchronicznego, można użyć operatora [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) , aby określić miejsce wstrzymania metody do oczekiwania na zakończenie wywołanego procesu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ec64a-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="ec64a-109">Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec64a-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="ec64a-110">W poniższym przykładzie zastosowano metody asynchroniczne, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="ec64a-111">Przykład zawiera poniższe dwie metody.</span><span class="sxs-lookup"><span data-stu-id="ec64a-111">The example contains the following two methods.</span></span>

- <span data-ttu-id="ec64a-112">`startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="ec64a-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="ec64a-113">`AccessTheWebAsync`, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="ec64a-114">`AccessTheWebAsync` używa asynchronicznej metody <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="ec64a-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="ec64a-115">Numerowane linie wyświetlania pojawiają się w punktach strategicznych w całym programie, aby pomóc zrozumieć, jak działa program, i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="ec64a-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="ec64a-116">Linie wyświetlania są oznaczone jako "ONE" do "SZÓSTe".</span><span class="sxs-lookup"><span data-stu-id="ec64a-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="ec64a-117">Etykiety reprezentują kolejność, w której program osiągnie te wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-117">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="ec64a-118">Poniższy kod przedstawia kontur programu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-118">The following code shows an outline of the program.</span></span>

```vb
Class MainWindow

    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

        ' ONE
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

        ' FOUR
        Dim contentLength As Integer = Await getLengthTask

        ' SIX
        ResultsTextBox.Text &=
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)

    End Sub

    Async Function AccessTheWebAsync() As Task(Of Integer)

        ' TWO
        Dim client As HttpClient = New HttpClient()
        Dim getStringTask As Task(Of String) =
            client.GetStringAsync("https://msdn.microsoft.com")

        ' THREE
        Dim urlContents As String = Await getStringTask

        ' FIVE
        Return urlContents.Length
    End Function

End Class
```

<span data-ttu-id="ec64a-119">Każda z oznaczonych lokalizacji "jeden" do "SZÓSTy" wyświetla informacje o bieżącym stanie programu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="ec64a-120">Generowane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ec64a-120">The following output is produced:</span></span>

```console
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

## <a name="set-up-the-program"></a><span data-ttu-id="ec64a-121">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="ec64a-121">Set Up the Program</span></span>

<span data-ttu-id="ec64a-122">Możesz pobrać kod, który jest wykorzystywany przez ten temat w witrynie MSDN, lub możesz utworzyć go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="ec64a-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="ec64a-123">Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ec64a-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="ec64a-124">Pobierz program</span><span class="sxs-lookup"><span data-stu-id="ec64a-124">Download the Program</span></span>

<span data-ttu-id="ec64a-125">Możesz pobrać aplikację dla tego tematu z przykładu @no__t 0Async: Przepływ sterowania w programach asynchronicznych @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="ec64a-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="ec64a-126">Poniższe kroki otwierają i uruchamiają program.</span><span class="sxs-lookup"><span data-stu-id="ec64a-126">The following steps open and run the program.</span></span>

1. <span data-ttu-id="ec64a-127">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec64a-127">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="ec64a-128">Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="ec64a-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

3. <span data-ttu-id="ec64a-129">Przejdź do folderu, który zawiera niespakowany przykładowy kod, Otwórz plik rozwiązania (. sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="ec64a-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>

### <a name="build-the-program-yourself"></a><span data-ttu-id="ec64a-130">Kompiluj program samodzielnie</span><span class="sxs-lookup"><span data-stu-id="ec64a-130">Build the Program Yourself</span></span>

<span data-ttu-id="ec64a-131">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="ec64a-132">Aby uruchomić projekt, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ec64a-132">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="ec64a-133">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec64a-133">Start Visual Studio.</span></span>

2. <span data-ttu-id="ec64a-134">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ec64a-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="ec64a-135">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ec64a-135">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ec64a-136">W okienku **zainstalowane szablony** wybierz pozycję **Visual Basic**, a następnie wybierz pozycję **Aplikacja WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="ec64a-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="ec64a-137">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="ec64a-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

    <span data-ttu-id="ec64a-138">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ec64a-138">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="ec64a-139">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="ec64a-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

    <span data-ttu-id="ec64a-140">Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="ec64a-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="ec64a-141">W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="ec64a-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```vb
    <Window
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"
        Title="Control Flow Trace" Height="350" Width="525">
        <Grid>
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>

        </Grid>
    </Window>
    ```

    <span data-ttu-id="ec64a-142">Proste okno zawierające pole tekstowe i przycisk pojawia się w widoku **projekt** MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="ec64a-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="ec64a-143">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="ec64a-143">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="ec64a-144">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="ec64a-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

9. <span data-ttu-id="ec64a-145">W MainWindow. XAML. vb Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="ec64a-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add an Imports statement and a reference for System.Net.Http.
    Imports System.Net.Http

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click

            ' The display lines in the example lead you through the control shifts.
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &
                "           Calling AccessTheWebAsync." & vbCrLf

            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()

            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is started." & vbCrLf &
                "           About to await getLengthTask -- no caller to return to." & vbCrLf

            Dim contentLength As Integer = Await getLengthTask

            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &
                "           Task getLengthTask is finished." & vbCrLf &
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &
                "           About to display contentLength and exit." & vbCrLf

            ResultsTextBox.Text &=
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)
        End Sub

        Async Function AccessTheWebAsync() As Task(Of Integer)

            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."

            ' Declare an HttpClient object.
            Dim client As HttpClient = New HttpClient()

            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf

            ' GetStringAsync returns a Task(Of String).
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")

            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &
                "           Task getStringTask is started."

            ' AccessTheWebAsync can continue to work until getStringTask is awaited.

            ResultsTextBox.Text &=
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf

            ' Retrieve the website contents when task is complete.
            Dim urlContents As String = Await getStringTask

            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &
                vbCrLf & "           Task getStringTask is complete." &
                vbCrLf & "           Processing the return statement." &
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf

            Return urlContents.Length
        End Function

    End Class
    ```

10. <span data-ttu-id="ec64a-146">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="ec64a-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="ec64a-147">Powinny pojawić się następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="ec64a-147">The following output should appear:</span></span>

    ```console
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

## <a name="trace-the-program"></a><span data-ttu-id="ec64a-148">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="ec64a-148">Trace the Program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="ec64a-149">Kroki jeden i dwa</span><span class="sxs-lookup"><span data-stu-id="ec64a-149">Steps ONE and TWO</span></span>

<span data-ttu-id="ec64a-150">Pierwsze dwa wiersze wyświetlania śledzą ścieżkę jako `startButton_Click` wywołań `AccessTheWebAsync`, a `AccessTheWebAsync` wywołuje metodę asynchroniczną <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="ec64a-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="ec64a-151">Na poniższej ilustracji przedstawiono wywołania metody do metody.</span><span class="sxs-lookup"><span data-stu-id="ec64a-151">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="ec64a-152">![Kroki jeden i dwa](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="ec64a-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="ec64a-153">Zwracany typ obu `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ec64a-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ec64a-154">W przypadku `AccessTheWebAsync` TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="ec64a-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="ec64a-155">W przypadku `GetStringAsync` TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ec64a-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="ec64a-156">Aby uzyskać więcej informacji na temat typów zwracanych metody asynchronicznej, zobacz [asynchroniczne typy zwracane (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ec64a-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

<span data-ttu-id="ec64a-157">Metoda asynchroniczna zwracająca zadanie zwraca wystąpienie zadania, gdy kontrolka przesunie się z powrotem do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ec64a-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="ec64a-158">Kontrolka zwraca z metody asynchronicznej do jej obiektu wywołującego, gdy w wywołanej metodzie zostanie napotkany operator `Await` lub gdy wywoływana metoda zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="ec64a-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="ec64a-159">Linie wyświetlania oznaczone etykietą "trzy" do "sześć" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="ec64a-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="ec64a-160">Krok trzeci</span><span class="sxs-lookup"><span data-stu-id="ec64a-160">Step THREE</span></span>

<span data-ttu-id="ec64a-161">W `AccessTheWebAsync` Metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ec64a-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="ec64a-162">Kontrolka zwraca z `client.GetStringAsync` do `AccessTheWebAsync`, gdy `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ec64a-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

<span data-ttu-id="ec64a-163">Metoda `client.GetStringAsync` zwraca zadanie ciągu, który jest przypisany do zmiennej `getStringTask` w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ec64a-164">Poniższy wiersz w przykładowym programie pokazuje wywołanie `client.GetStringAsync` i przypisanie.</span><span class="sxs-lookup"><span data-stu-id="ec64a-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```vb
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")
```

<span data-ttu-id="ec64a-165">Możesz traktować zadanie jako obietnicę, `client.GetStringAsync` Aby utworzyć rzeczywisty ciąg ostatecznie.</span><span class="sxs-lookup"><span data-stu-id="ec64a-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="ec64a-166">W międzyczasie, jeśli `AccessTheWebAsync` ma pracę, która nie zależy od uzgodnionego ciągu z `client.GetStringAsync`, to działanie może być kontynuowane, gdy `client.GetStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="ec64a-167">W przykładzie następujące wiersze danych wyjściowych, które są oznaczone etykietą "trzy", reprezentują możliwość wykonania niezależnej pracy</span><span class="sxs-lookup"><span data-stu-id="ec64a-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```console
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="ec64a-168">Poniższa instrukcja zawiesza postęp w `AccessTheWebAsync`, gdy oczekiwano `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```vb
Dim urlContents As String = Await getStringTask
```

<span data-ttu-id="ec64a-169">Na poniższej ilustracji przedstawiono przepływ sterowania z `client.GetStringAsync` do przypisania do `getStringTask` i od tworzenia `getStringTask` do aplikacji operatora await.</span><span class="sxs-lookup"><span data-stu-id="ec64a-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>

<span data-ttu-id="ec64a-170">![Krok trzy](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace — trzy")</span><span class="sxs-lookup"><span data-stu-id="ec64a-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>

<span data-ttu-id="ec64a-171">Wyrażenie await wstrzymuje `AccessTheWebAsync` do momentu, gdy `client.GetStringAsync` zwróci wartość.</span><span class="sxs-lookup"><span data-stu-id="ec64a-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="ec64a-172">W międzyczasie sterowanie powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="ec64a-173">Zwykle oczekujesz natychmiastowego wywołania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="ec64a-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="ec64a-174">Na przykład następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="ec64a-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>
>
> <span data-ttu-id="ec64a-175">W tym temacie operator await jest stosowany później, aby pomieścić linie wyjściowe, które oznaczają przepływ sterowania przez program.</span><span class="sxs-lookup"><span data-stu-id="ec64a-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="ec64a-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="ec64a-176">Step FOUR</span></span>

<span data-ttu-id="ec64a-177">Zadeklarowany zwracany typ `AccessTheWebAsync` jest `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="ec64a-178">W związku z tym, gdy `AccessTheWebAsync` zostanie zawieszone, zwraca zadanie z liczbą całkowitą do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="ec64a-179">Należy pamiętać, że zwrócone zadanie nie jest `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="ec64a-180">Zwrócone zadanie jest nowym zadaniem liczby całkowitej, które reprezentuje, co pozostało do wykonania w metodzie zawieszonej, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="ec64a-181">Zadanie to obietnica z `AccessTheWebAsync`, aby utworzyć liczbę całkowitą, gdy zadanie zostanie ukończone.</span><span class="sxs-lookup"><span data-stu-id="ec64a-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="ec64a-182">Poniższa instrukcja przypisuje to zadanie do zmiennej `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```vb
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()
```

<span data-ttu-id="ec64a-183">Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, która nie jest zależna od wyników zadania asynchronicznego (`getLengthTask`) do momentu oczekiwania na zadanie.</span><span class="sxs-lookup"><span data-stu-id="ec64a-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="ec64a-184">Następujące wiersze danych wyjściowych przedstawiają te działania:</span><span class="sxs-lookup"><span data-stu-id="ec64a-184">The following output lines represent that work:</span></span>

```console
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

<span data-ttu-id="ec64a-185">Postęp w `startButton_Click` jest zawieszony, gdy jest oczekiwany `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="ec64a-186">Następująca instrukcja przypisania zawiesza `startButton_Click` do momentu ukończenia `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="ec64a-187">Na poniższej ilustracji strzałki pokazują przepływ sterowania z wyrażenia await w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` do momentu oczekiwania na `getLengthTask`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

<span data-ttu-id="ec64a-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace — cztery")</span><span class="sxs-lookup"><span data-stu-id="ec64a-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="ec64a-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="ec64a-189">Step FIVE</span></span>

<span data-ttu-id="ec64a-190">Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest uwalniane z zawieszenia i może być kontynuowane przy użyciu instrukcji Await.</span><span class="sxs-lookup"><span data-stu-id="ec64a-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="ec64a-191">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania:</span><span class="sxs-lookup"><span data-stu-id="ec64a-191">The following lines of output represent the resumption of processing:</span></span>

```console
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

<span data-ttu-id="ec64a-192">Operand instrukcji return, `urlContents.Length`, jest przechowywany w zadaniu, które zwraca `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="ec64a-193">Wyrażenie await pobiera tę wartość z `getLengthTask` w `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

<span data-ttu-id="ec64a-194">Na poniższej ilustracji przedstawiono transfer kontroli po wykonaniu `client.GetStringAsync` (i `getStringTask`).</span><span class="sxs-lookup"><span data-stu-id="ec64a-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

<span data-ttu-id="ec64a-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace — pięć")</span><span class="sxs-lookup"><span data-stu-id="ec64a-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

<span data-ttu-id="ec64a-196">`AccessTheWebAsync` przebiega do ukończenia, a sterowanie powraca do `startButton_Click`, co oczekuje na ukończenie.</span><span class="sxs-lookup"><span data-stu-id="ec64a-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="ec64a-197">Krok SZÓSTy</span><span class="sxs-lookup"><span data-stu-id="ec64a-197">Step SIX</span></span>

<span data-ttu-id="ec64a-198">Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie może być kontynuowane poza instrukcją await w `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="ec64a-199">W rzeczywistości program nie ma niczego więcej.</span><span class="sxs-lookup"><span data-stu-id="ec64a-199">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="ec64a-200">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="ec64a-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```console
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

<span data-ttu-id="ec64a-201">Wyrażenie await pobiera z `getLengthTask` wartości całkowitej, która jest argumentem instrukcji return w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ec64a-202">Poniższa instrukcja przypisuje tę wartość do zmiennej `contentLength`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-202">The following statement assigns that value to the `contentLength` variable.</span></span>

```vb
Dim contentLength As Integer = Await getLengthTask
```

<span data-ttu-id="ec64a-203">Na poniższej ilustracji przedstawiono powrót formantu z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ec64a-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

<span data-ttu-id="ec64a-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="ec64a-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="ec64a-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec64a-205">See also</span></span>

- [<span data-ttu-id="ec64a-206">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec64a-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="ec64a-207">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ec64a-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="ec64a-208">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ec64a-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="ec64a-209">Przykład asynchroniczny: Przepływ sterowania w programach asynchronicznychC# (i Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="ec64a-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
