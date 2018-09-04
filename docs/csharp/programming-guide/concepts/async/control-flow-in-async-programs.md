---
title: Przepływ sterowania w programach Async (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: b05bfbd231745caf9e8b6031ce8e063469d8898b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502505"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="6e136-102">Przepływ sterowania w programach Async (C#)</span><span class="sxs-lookup"><span data-stu-id="6e136-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="6e136-103">Pozwala pisać i łatwiej utrzymać asynchroniczne programy za pomocą `async` i `await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="6e136-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="6e136-104">Jednak wyniki mogą Cię zaskoczyć, jeśli nie rozumiesz sposobu działania programu.</span><span class="sxs-lookup"><span data-stu-id="6e136-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="6e136-105">W tym temacie omówiono, którą przepływ sterowania za pośrednictwem prostego programu asynchronicznego aby pokazać, kiedy sterowania przechodzi od jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="6e136-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e136-106">`async` i `await` słowa kluczowe zostały wprowadzone w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="6e136-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="6e136-107">Ogólnie rzecz biorąc Oznacz metody, które zawierają kod asynchroniczny [async (C#)](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="6e136-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="6e136-108">W metodzie, która jest oznaczona modyfikatorem asynchronicznym, można użyć [await (C#)](../../../../csharp/language-reference/keywords/await.md) operatora, aby określić, gdzie metoda wstrzymuje się oczekiwania wywołany proces asynchroniczny zakończyć.</span><span class="sxs-lookup"><span data-stu-id="6e136-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="6e136-109">Aby uzyskać więcej informacji, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e136-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="6e136-110">W poniższym przykładzie użyto metody asynchronicznej, aby pobrać zawartość określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="6e136-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="6e136-111">Przykład zawiera następujących dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="6e136-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="6e136-112">`startButton_Click`, która wywołuje metodę `AccessTheWebAsync` i wyświetla wynik.</span><span class="sxs-lookup"><span data-stu-id="6e136-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="6e136-113">`AccessTheWebAsync`, który pobiera zawartość witryny sieci Web jako ciąg i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="6e136-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="6e136-114">`AccessTheWebAsync` używa asynchronicznej <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="6e136-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="6e136-115">Ponumerowane wyświetlanych wierszy pojawiających się w strategiczny punktach w całym programie, aby lepiej zrozumieć, jak działa program i wyjaśnić, co się dzieje w każdym punkcie, który jest oznaczony.</span><span class="sxs-lookup"><span data-stu-id="6e136-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="6e136-116">Wyświetlane wiersze są oznaczone etykietami od "ONE"do "sześć."</span><span class="sxs-lookup"><span data-stu-id="6e136-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="6e136-117">Etykiety reprezentują kolejność, w jakiej program osiąga te wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="6e136-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="6e136-118">Poniższy kod przedstawia zarys programu.</span><span class="sxs-lookup"><span data-stu-id="6e136-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="6e136-119">Każda z etykietami lokalizacje "ONE"do "6," Wyświetla informacje dotyczące bieżącego stanu programu.</span><span class="sxs-lookup"><span data-stu-id="6e136-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="6e136-120">Następujące dane wyjściowe są generowane.</span><span class="sxs-lookup"><span data-stu-id="6e136-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="6e136-121">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="6e136-121">Set Up the Program</span></span>  
 <span data-ttu-id="6e136-122">Kod, który używa tego tematu możesz pobrać z witryny MSDN lub tworzyć je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="6e136-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e136-123">Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="6e136-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="6e136-124">Pobierz Program</span><span class="sxs-lookup"><span data-stu-id="6e136-124">Download the Program</span></span>  
 <span data-ttu-id="6e136-125">Możesz pobrać aplikację dotyczącą tego tematu z [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="6e136-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="6e136-126">Poniższe kroki, Otwórz i uruchom program.</span><span class="sxs-lookup"><span data-stu-id="6e136-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="6e136-127">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e136-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6e136-128">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="6e136-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="6e136-129">Przejdź do folderu, który posiada rozpakowany przykładowego kodu, otwórz plik rozwiązania (.sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="6e136-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="6e136-130">Sam Zbuduj Program</span><span class="sxs-lookup"><span data-stu-id="6e136-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="6e136-131">Poniższy projekt Windows Presentation Foundation (WPF) zawiera przykład kodu, w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="6e136-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="6e136-132">Aby uruchomić projekt, należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6e136-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="6e136-133">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6e136-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6e136-134">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="6e136-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="6e136-135">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="6e136-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="6e136-136">W **zainstalowane szablony** okienku wybierz **Visual C#**, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="6e136-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="6e136-137">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="6e136-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="6e136-138">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="6e136-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="6e136-139">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="6e136-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="6e136-140">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="6e136-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="6e136-141">W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6e136-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="6e136-142">Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="6e136-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="6e136-143">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="6e136-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="6e136-144">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="6e136-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="6e136-145">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="6e136-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="6e136-146">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="6e136-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="6e136-147">Powinien pojawić się następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6e136-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="6e136-148">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="6e136-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="6e136-149">Kroki 1 i 2</span><span class="sxs-lookup"><span data-stu-id="6e136-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="6e136-150">Pierwsze dwa wyświetlane wiersze śledzą ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="6e136-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="6e136-151">Poniższa ilustracja przedstawia wywołania z metody do metody.</span><span class="sxs-lookup"><span data-stu-id="6e136-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="6e136-152">![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="6e136-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="6e136-153">Zwracanym typem obu metod `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="6e136-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6e136-154">Aby uzyskać `AccessTheWebAsync`, TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="6e136-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="6e136-155">Aby uzyskać `GetStringAsync`, TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="6e136-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="6e136-156">Aby uzyskać więcej informacji na temat typów zwracanych w metodach asynchronicznych, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="6e136-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="6e136-157">Asynchroniczna metoda zwracania zadania Zwraca wystąpienie zadania Jeśli kontrola przechodzi do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="6e136-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="6e136-158">Formant powraca z metody asynchronicznej do obiektu wywołującego gdy `await` operator zostanie napotkany w metodzie wywoływanej, lub gdy metoda wywoływana się zakończy.</span><span class="sxs-lookup"><span data-stu-id="6e136-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="6e136-159">Wyświetlane wiersze, które są oznaczone jako "Trzy"do "6" śledzą tę część procesu.</span><span class="sxs-lookup"><span data-stu-id="6e136-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="6e136-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="6e136-160">Step THREE</span></span>  
 <span data-ttu-id="6e136-161">W `AccessTheWebAsync`, metoda asynchroniczna <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości docelowej strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6e136-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="6e136-162">Formant powraca z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="6e136-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="6e136-163">`client.GetStringAsync` Metoda zwraca zadanie ciągu, która jest przypisana do `getStringTask` zmienną `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="6e136-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="6e136-164">Następujący wiersz w programie przykładowym pokazuje wywołanie `client.GetStringAsync` i przypisania.</span><span class="sxs-lookup"><span data-stu-id="6e136-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="6e136-165">Można traktować zadanie jako zapowiedź `client.GetStringAsync` do produkcji rzeczywistego ciągu po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="6e136-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="6e136-166">W międzyczasie Jeśli `AccessTheWebAsync` ma robić prace, które nie są zależne od uzgodnionego ciągu z `client.GetStringAsync`, można kontynuować pracę podczas `client.GetStringAsync` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="6e136-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="6e136-167">W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują okazję do samodzielnej pracy</span><span class="sxs-lookup"><span data-stu-id="6e136-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="6e136-168">Poniższa instrukcja wstrzymuje `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6e136-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="6e136-169">Na poniższej ilustracji przedstawiono przepływ sterowania od `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` do zastosowania operatora await.</span><span class="sxs-lookup"><span data-stu-id="6e136-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="6e136-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")</span><span class="sxs-lookup"><span data-stu-id="6e136-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="6e136-171">Wyrażenie await wstrzymuje `AccessTheWebAsync` aż `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="6e136-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="6e136-172">W międzyczasie formant powraca do obiektu wywołującego `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="6e136-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e136-173">Zazwyczaj można oczekiwać wywołania metody asynchronicznej natychmiast.</span><span class="sxs-lookup"><span data-stu-id="6e136-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="6e136-174">Na przykład, następujące przypisanie może zastąpić poprzedni kod, który tworzy, a następnie czeka na `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="6e136-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="6e136-175">W tym temacie await operator jest stosowany później, aby pomieścić linie wyjściowych, oznaczające przepływ sterowania za pośrednictwem programu.</span><span class="sxs-lookup"><span data-stu-id="6e136-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="6e136-176">Krok czwarty</span><span class="sxs-lookup"><span data-stu-id="6e136-176">Step FOUR</span></span>  
 <span data-ttu-id="6e136-177">Deklarowanym typem zwracanym metody `AccessTheWebAsync` jest `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="6e136-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="6e136-178">W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="6e136-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="6e136-179">Należy zrozumieć, że zwracane zadanie nie jest `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="6e136-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="6e136-180">Zwracane zadanie jest nowym zadaniem liczby całkowitej określającej, co jeszcze pozostało do zrobienia WE wstrzymanej metodzie, `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="6e136-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="6e136-181">Zadanie jest obietnicą ze `AccessTheWebAsync` do utworzenia typu integer, po ukończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="6e136-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="6e136-182">Poniższa instrukcja przypisuje to zadanie `getLengthTask` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6e136-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="6e136-183">Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracę, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) dopóki trwa oczekiwanie na zadanie.</span><span class="sxs-lookup"><span data-stu-id="6e136-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="6e136-184">Poniższe wiersze danych wyjściowych przedstawiają tę pracę.</span><span class="sxs-lookup"><span data-stu-id="6e136-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="6e136-185">Postęp w `startButton_Click` jest zawieszony gdy `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6e136-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="6e136-186">Poniższa instrukcja przypisania wstrzymuje `startButton_Click` aż `AccessTheWebAsync` zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="6e136-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="6e136-187">Na poniższej ilustracji, strzałki pokazują przepływ sterowania z wyrażenia oczekującego w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalne przetwarzanie w `startButton_Click` aż `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="6e136-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="6e136-188">![Krok czwarty](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 4")</span><span class="sxs-lookup"><span data-stu-id="6e136-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="6e136-189">Krok piąty</span><span class="sxs-lookup"><span data-stu-id="6e136-189">Step FIVE</span></span>  
 <span data-ttu-id="6e136-190">Gdy `client.GetStringAsync` sygnalizuje zakończenie, przetwarzanie w `AccessTheWebAsync` jest zwalniane z zawieszenia i można kontynuować po instrukcji czekania.</span><span class="sxs-lookup"><span data-stu-id="6e136-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="6e136-191">Poniższe wiersze danych wyjściowych przedstawiają wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="6e136-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="6e136-192">Argument instrukcji return `urlContents.Length`, jest zapisywany w zadaniu, `AccessTheWebAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="6e136-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="6e136-193">Wyrażenie await pobiera tę wartość ze `getLengthTask` w `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="6e136-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="6e136-194">Poniższa ilustracja przedstawia przekazanie sterowania po `client.GetStringAsync` (i `getStringTask`) są kompletne.</span><span class="sxs-lookup"><span data-stu-id="6e136-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="6e136-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")</span><span class="sxs-lookup"><span data-stu-id="6e136-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="6e136-196">`AccessTheWebAsync` przebieg do ukończenia, a formant powraca do `startButton_Click`, która oczekuje na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="6e136-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="6e136-197">Krok SZÓSTY</span><span class="sxs-lookup"><span data-stu-id="6e136-197">Step SIX</span></span>  
 <span data-ttu-id="6e136-198">Gdy `AccessTheWebAsync` sygnalizuje zakończenie, przetwarzanie można kontynuować po instrukcji czekania w `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="6e136-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="6e136-199">W rzeczywistości program nie ma nic więcej do zrobienia.</span><span class="sxs-lookup"><span data-stu-id="6e136-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="6e136-200">Następujące wiersze danych wyjściowych przedstawiają wznowienie przetwarzania w metodzie `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="6e136-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="6e136-201">Wyrażenie await pobiera ze `getLengthTask` wartość całkowitą, która jest argumentem instrukcji return w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="6e136-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="6e136-202">Poniższa instrukcja przypisuje wartość do `contentLength` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="6e136-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="6e136-203">Poniższa ilustracja przedstawia powrót sterowania z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="6e136-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="6e136-204">![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace 6")</span><span class="sxs-lookup"><span data-stu-id="6e136-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e136-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e136-205">See Also</span></span>

- [<span data-ttu-id="6e136-206">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="6e136-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="6e136-207">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="6e136-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="6e136-208">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="6e136-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="6e136-209">Próbka asynchroniczna: Przepływ sterowania w programach Async (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6e136-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
