---
title: Przepływ sterowania w programach Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: c6afd7e166e08ea30637bd3f05026ef71d781ab6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624760"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="918c9-102">Przepływ sterowania w programach Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c9-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="918c9-103">Pozwala pisać i łatwiej utrzymać asynchroniczne programy za pomocą `Async` i `Await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="918c9-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="918c9-104">Jednak wyniki mogą Cię zaskoczyć, jeśli nie rozumiesz sposobu działania programu.</span><span class="sxs-lookup"><span data-stu-id="918c9-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="918c9-105">W tym temacie omówiono, którą przepływ sterowania za pośrednictwem prostego programu asynchronicznego aby pokazać, kiedy sterowania przechodzi od jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="918c9-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="918c9-106">`Async` i `Await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="918c9-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="918c9-107">Ogólnie rzecz biorąc Oznacz metody, które zawierają kod asynchroniczny [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="918c9-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="918c9-108">W metodzie, która jest oznaczona modyfikatorem asynchronicznym, można użyć [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operatora, aby określić, gdzie metoda wstrzymuje się oczekiwania wywołany proces asynchroniczny zakończyć.</span><span class="sxs-lookup"><span data-stu-id="918c9-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="918c9-109">Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="918c9-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="918c9-110">W poniższym przykładzie użyto metody asynchronicznej, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="918c9-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="918c9-111">Przykład zawiera następujących dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="918c9-111">The example contains the following two methods.</span></span>  
  
- <span data-ttu-id="918c9-112">`startButton_Click`, która wywołuje metodę `AccessTheWebAsync` i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="918c9-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
- <span data-ttu-id="918c9-113">`AccessTheWebAsync`, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="918c9-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="918c9-114">`AccessTheWebAsync` używa asynchronicznej <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="918c9-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="918c9-115">Ponumerowane wyświetlanych wierszy pojawiających się w strategiczny punktach w całym programie, aby lepiej zrozumieć, jak działa program i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="918c9-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="918c9-116">Wyświetlane wiersze są oznaczone etykietami od "ONE"do "sześć."</span><span class="sxs-lookup"><span data-stu-id="918c9-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="918c9-117">Etykiety reprezentują kolejność, w jakiej program osiąga te wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="918c9-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="918c9-118">Poniższy kod przedstawia zarys programu.</span><span class="sxs-lookup"><span data-stu-id="918c9-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="918c9-119">Każda z etykietami lokalizacje "ONE"do "6," Wyświetla informacje dotyczące bieżącego stanu programu.</span><span class="sxs-lookup"><span data-stu-id="918c9-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="918c9-120">Następujące dane wyjściowe są generowane.</span><span class="sxs-lookup"><span data-stu-id="918c9-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="918c9-121">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="918c9-121">Set Up the Program</span></span>  
 <span data-ttu-id="918c9-122">Kod, który używa tego tematu możesz pobrać z witryny MSDN lub tworzyć je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="918c9-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="918c9-123">Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="918c9-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="918c9-124">Pobierz Program</span><span class="sxs-lookup"><span data-stu-id="918c9-124">Download the Program</span></span>  
 <span data-ttu-id="918c9-125">Możesz pobrać aplikację dotyczącą tego tematu z [próbka asynchroniczna: Kontrolowanie Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="918c9-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="918c9-126">Poniższe kroki, Otwórz i uruchom program.</span><span class="sxs-lookup"><span data-stu-id="918c9-126">The following steps open and run the program.</span></span>  
  
1. <span data-ttu-id="918c9-127">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="918c9-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="918c9-128">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="918c9-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="918c9-129">Przejdź do folderu, który posiada rozpakowany przykładowego kodu, otwórz plik rozwiązania (.sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="918c9-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="918c9-130">Sam Zbuduj Program</span><span class="sxs-lookup"><span data-stu-id="918c9-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="918c9-131">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="918c9-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="918c9-132">Aby uruchomić projekt, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="918c9-132">To run the project, perform the following steps:</span></span>  
  
1. <span data-ttu-id="918c9-133">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="918c9-133">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="918c9-134">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="918c9-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="918c9-135">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="918c9-135">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="918c9-136">W **zainstalowane szablony** okienku wybierz **języka Visual Basic**, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="918c9-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="918c9-137">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="918c9-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="918c9-138">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="918c9-138">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="918c9-139">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="918c9-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="918c9-140">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="918c9-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6. <span data-ttu-id="918c9-141">W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="918c9-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="918c9-142">Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="918c9-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7. <span data-ttu-id="918c9-143">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="918c9-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8. <span data-ttu-id="918c9-144">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="918c9-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="918c9-145">W pliku MainWindow.xaml.vb Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="918c9-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="918c9-146">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="918c9-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="918c9-147">Powinien pojawić się następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="918c9-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="918c9-148">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="918c9-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="918c9-149">Kroki 1 i 2</span><span class="sxs-lookup"><span data-stu-id="918c9-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="918c9-150">Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="918c9-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="918c9-151">Poniższa ilustracja przedstawia wywołania z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="918c9-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="918c9-152">![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="918c9-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="918c9-153">Zwracanym typem obu metod `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="918c9-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="918c9-154">Aby uzyskać `AccessTheWebAsync`, TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="918c9-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="918c9-155">Aby uzyskać `GetStringAsync`, TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="918c9-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="918c9-156">Aby uzyskać więcej informacji na temat typów zwracanych w metodach asynchronicznych, zobacz [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="918c9-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="918c9-157">Asynchroniczna metoda zwracania zadania Zwraca wystąpienie zadania Jeśli kontrola przechodzi do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="918c9-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="918c9-158">Formant powraca z metody asynchronicznej do obiektu wywołującego gdy `Await` operator zostanie napotkany w metodzie wywoływanej, lub gdy metoda wywoływana się zakończy.</span><span class="sxs-lookup"><span data-stu-id="918c9-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="918c9-159">Wyświetlane wiersze, które są oznaczone jako "Trzy"do "6" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="918c9-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="918c9-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="918c9-160">Step THREE</span></span>  
 <span data-ttu-id="918c9-161">W `AccessTheWebAsync`, metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="918c9-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="918c9-162">Formant powraca z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="918c9-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="918c9-163">`client.GetStringAsync` Metoda zwraca zadanie ciągu, która jest przypisana do `getStringTask` zmienną `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="918c9-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="918c9-164">Następujący wiersz w programie przykładowym pokazuje wywołanie `client.GetStringAsync` i przypisania.</span><span class="sxs-lookup"><span data-stu-id="918c9-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 <span data-ttu-id="918c9-165">Można traktować zadanie jako zapowiedź `client.GetStringAsync` do produkcji rzeczywistego ciągu po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="918c9-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="918c9-166">W międzyczasie Jeśli `AccessTheWebAsync` ma robić prace, które nie są zależne od uzgodnionego ciągu z `client.GetStringAsync`, można kontynuować pracę podczas `client.GetStringAsync` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="918c9-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="918c9-167">W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują okazję do samodzielnej pracy</span><span class="sxs-lookup"><span data-stu-id="918c9-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="918c9-168">Poniższa instrukcja wstrzymuje `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="918c9-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 <span data-ttu-id="918c9-169">Na poniższej ilustracji przedstawiono przepływ sterowania od `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` do zastosowania operatora Await.</span><span class="sxs-lookup"><span data-stu-id="918c9-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="918c9-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")</span><span class="sxs-lookup"><span data-stu-id="918c9-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="918c9-171">Wyrażenie await wstrzymuje `AccessTheWebAsync` aż `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="918c9-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="918c9-172">W międzyczasie formant powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="918c9-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="918c9-173">Zazwyczaj można oczekiwać wywołania metody asynchronicznej natychmiast.</span><span class="sxs-lookup"><span data-stu-id="918c9-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="918c9-174">Na przykład, następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="918c9-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="918c9-175">W tym temacie await operator jest stosowany później, aby pomieścić linie wyjściowych, oznaczające przepływ sterowania za pośrednictwem programu.</span><span class="sxs-lookup"><span data-stu-id="918c9-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="918c9-176">Krok czwarty</span><span class="sxs-lookup"><span data-stu-id="918c9-176">Step FOUR</span></span>  
 <span data-ttu-id="918c9-177">Deklarowanym typem zwracanym metody `AccessTheWebAsync` jest `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="918c9-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="918c9-178">W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="918c9-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="918c9-179">Należy zrozumieć, że zwracane zadanie nie jest `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="918c9-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="918c9-180">Zwracane zadanie jest nowym zadaniem liczby całkowitej określającej, co jeszcze pozostało do zrobienia WE wstrzymanej metodzie, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="918c9-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="918c9-181">Zadanie jest obietnicą ze `AccessTheWebAsync` do utworzenia typu integer, po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="918c9-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="918c9-182">Poniższa instrukcja przypisuje to zadanie `getLengthTask` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="918c9-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 <span data-ttu-id="918c9-183">Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) dopóki trwa oczekiwanie na zadanie.</span><span class="sxs-lookup"><span data-stu-id="918c9-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="918c9-184">Poniższe wiersze danych wyjściowych przedstawiają tę pracę.</span><span class="sxs-lookup"><span data-stu-id="918c9-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="918c9-185">Postęp w `startButton_Click` jest zawieszony gdy `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="918c9-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="918c9-186">Poniższa instrukcja przypisania wstrzymuje `startButton_Click` aż `AccessTheWebAsync` zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="918c9-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="918c9-187">Na poniższej ilustracji, strzałki pokazują przepływ sterowania z wyrażenia oczekującego w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` aż `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="918c9-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="918c9-188">![Krok czwarty](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 4")</span><span class="sxs-lookup"><span data-stu-id="918c9-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="918c9-189">Krok piąty</span><span class="sxs-lookup"><span data-stu-id="918c9-189">Step FIVE</span></span>  
 <span data-ttu-id="918c9-190">Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest zwalniane z zawieszenia i można kontynuować po instrukcji czekania.</span><span class="sxs-lookup"><span data-stu-id="918c9-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="918c9-191">Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="918c9-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="918c9-192">Argument instrukcji return `urlContents.Length`, jest zapisywany w zadaniu, `AccessTheWebAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="918c9-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="918c9-193">Wyrażenie await pobiera tę wartość ze `getLengthTask` w `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="918c9-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="918c9-194">Poniższa ilustracja przedstawia przekazanie sterowania po `client.GetStringAsync` (i `getStringTask`) są kompletne.</span><span class="sxs-lookup"><span data-stu-id="918c9-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="918c9-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")</span><span class="sxs-lookup"><span data-stu-id="918c9-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="918c9-196">`AccessTheWebAsync` przebieg do ukończenia, a formant powraca do `startButton_Click`, która oczekuje na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="918c9-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="918c9-197">Krok SZÓSTY</span><span class="sxs-lookup"><span data-stu-id="918c9-197">Step SIX</span></span>  
 <span data-ttu-id="918c9-198">Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie można kontynuować po instrukcji czekania w `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="918c9-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="918c9-199">W rzeczywistości program nie ma nic więcej do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="918c9-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="918c9-200">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w metodzie `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="918c9-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="918c9-201">Wyrażenie await pobiera ze `getLengthTask` wartość całkowitą, która jest argumentem instrukcji return w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="918c9-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="918c9-202">Poniższa instrukcja przypisuje wartość do `contentLength` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="918c9-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="918c9-203">Poniższa ilustracja przedstawia powrót sterowania z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="918c9-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="918c9-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="918c9-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="918c9-205">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="918c9-205">See also</span></span>

- [<span data-ttu-id="918c9-206">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c9-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="918c9-207">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c9-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="918c9-208">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c9-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="918c9-209">Próbka asynchroniczna: Kontrolowanie Flow in Async Programs (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="918c9-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
