---
title: "Przepływ sterowania w aplikacjach asynchronicznych (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b975b75f9ff31f43e722d3ceb28d08ed3b6ce11
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="ab3b4-102">Przepływ sterowania w aplikacjach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3b4-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="ab3b4-103">Możesz wpisać i obsługa asynchroniczne programy łatwiej przy użyciu `async` i `await` słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="ab3b4-104">Jednak wyniki, może Cię zaskoczył Jeśli nie znasz sposób działania programu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="ab3b4-105">Ślady tego tematu, które przepływu sterowania za pośrednictwem programu async proste do wyświetlenia, gdy formant są przenoszone z jednej metody do innej i jakie informacje są przesyłane za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab3b4-106">`async` i `await` słowa kluczowe wprowadzono w programie Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="ab3b4-107">Ogólnie rzecz biorąc, możesz oznaczyć metody, które zawierają asynchroniczne kodu za pomocą [async (C#)](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ab3b4-108">W przypadku metody oznaczonej za pomocą modyfikatora async służy [await (C#)](../../../../csharp/language-reference/keywords/await.md) operatora, aby określić, gdzie metoda wstrzymuje oczekiwania na ukończenie wywołanego procesu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="ab3b4-109">Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab3b4-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="ab3b4-110">W poniższym przykładzie użyto metody asynchroniczne, aby pobrać zawartość z określonej witryny sieci Web jako ciąg i wyświetlić długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="ab3b4-111">Przykład zawiera następujących dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="ab3b4-112">`startButton_Click`, które wywołuje `AccessTheWebAsync` i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="ab3b4-113">`AccessTheWebAsync`, która pobiera zawartość witryny sieci Web w postaci ciągu i zwraca długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="ab3b4-114">`AccessTheWebAsync` korzysta z asynchronicznego <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, aby pobrać zawartość.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="ab3b4-115">Numerowane wyświetlania wiersze pojawiają się w punktach strategicznych w programie, aby lepiej zrozumieć, jak program zostanie uruchomiony i wyjaśniający, co się stanie w każdym punkcie, który jest oznaczony jako.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="ab3b4-116">Wyświetlanie linii są oznaczone jako "Jeden"do "sześć."</span><span class="sxs-lookup"><span data-stu-id="ab3b4-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="ab3b4-117">Etykiety opisania kolejności, w którym program osiągnie tych wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="ab3b4-118">Poniższy kod przedstawia konspektu programu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-118">The following code shows an outline of the program.</span></span>  
  
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
  
 <span data-ttu-id="ab3b4-119">Każdej z etykietą lokalizacji, "ONE"do "6," Wyświetla informacje o bieżącym stanie programu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="ab3b4-120">Są następujące wyniki.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="ab3b4-121">Konfigurowanie programu</span><span class="sxs-lookup"><span data-stu-id="ab3b4-121">Set Up the Program</span></span>  
 <span data-ttu-id="ab3b4-122">Kod, który korzysta z tego tematu możesz pobrać z MSDN lub można utworzyć ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab3b4-123">Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="ab3b4-124">Pobierz Program</span><span class="sxs-lookup"><span data-stu-id="ab3b4-124">Download the Program</span></span>  
 <span data-ttu-id="ab3b4-125">Możesz pobrać aplikację dla tego tematu z [próbki Async: przepływ sterowania w aplikacjach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span><span class="sxs-lookup"><span data-stu-id="ab3b4-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="ab3b4-126">Poniższe kroki Otwórz i uruchom program.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="ab3b4-127">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ab3b4-128">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="ab3b4-129">Przejdź do folderu, która przechowuje rozpakowane przykładowy kod, otwórz plik rozwiązania (sln), a następnie wybierz klawisz F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="ab3b4-130">Samodzielnie kompilacji programu</span><span class="sxs-lookup"><span data-stu-id="ab3b4-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="ab3b4-131">Następujący projekt Windows Presentation Foundation (WPF) zawiera przykładowy kod dla tego tematu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="ab3b4-132">Aby uruchomić projekt, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ab3b4-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="ab3b4-133">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="ab3b4-134">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="ab3b4-135">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="ab3b4-136">W **zainstalowane szablony** okienku wybierz **Visual C#**, a następnie wybierz pozycję **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="ab3b4-137">Wprowadź `AsyncTracer` jako nazwę projektu, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="ab3b4-138">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="ab3b4-139">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="ab3b4-140">Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="ab3b4-141">W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="ab3b4-142">Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="ab3b4-143">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="ab3b4-144">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="ab3b4-145">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
  
10. <span data-ttu-id="ab3b4-146">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="ab3b4-147">Następujące dane wyjściowe powinny być wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="ab3b4-148">Śledzenie programu</span><span class="sxs-lookup"><span data-stu-id="ab3b4-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="ab3b4-149">Kroki 1 i 2</span><span class="sxs-lookup"><span data-stu-id="ab3b4-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="ab3b4-150">Wyświetlanie pierwszych dwóch linii śledzenia ścieżkę jako `startButton_Click` wywołania `AccessTheWebAsync`, i `AccessTheWebAsync` wywołuje asynchroniczną <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="ab3b4-151">Poniższa ilustracja przedstawia wywołania metody metody.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="ab3b4-152">![Kroki 1 i 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="ab3b4-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="ab3b4-153">Zwracany typ `AccessTheWebAsync` i `client.GetStringAsync` jest <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ab3b4-154">Dla `AccessTheWebAsync`, TResult jest liczbą całkowitą.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="ab3b4-155">Dla `GetStringAsync`, TResult jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="ab3b4-156">Aby uzyskać więcej informacji na temat asynchronicznej metody zwracane typy, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ab3b4-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="ab3b4-157">Metody async umożliwiające zwracanie zadań Zwraca wystąpienie zadania podczas kontroli przewiduje się do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="ab3b4-158">Formant zwraca z metody asynchronicznej do swojego obiektu wywołującego albo gdy `await` napotkano operator wywołaną metodę lub gdy kończy się wywołaną metodę.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="ab3b4-159">Wyświetlanie linii, które są oznaczone jako "Trzy"do "SZEŚCIU" śledzenia to część procesu.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="ab3b4-160">Krok 3</span><span class="sxs-lookup"><span data-stu-id="ab3b4-160">Step THREE</span></span>  
 <span data-ttu-id="ab3b4-161">W `AccessTheWebAsync`, metod asynchronicznych <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> jest wywoływana w celu pobrania zawartości na docelowej stronie sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="ab3b4-162">Zwraca kontroli z `client.GetStringAsync` do `AccessTheWebAsync` podczas `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="ab3b4-163">`client.GetStringAsync` Metoda zwraca ciąg, który jest przypisany do zadania `getStringTask` zmiennej w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ab3b4-164">Następujący wiersz w programie przykład zawiera wywołanie `client.GetStringAsync` oraz przypisanie.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="ab3b4-165">Można traktować jako promise przez zadania `client.GetStringAsync` do tworzenia rzeczywistych ciągu po pewnym czasie.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="ab3b4-166">W międzyczasie Jeśli `AccessTheWebAsync` ma pracy, który nie jest zależny od uzgodnionej ciąg, z `client.GetStringAsync`, aby kontynuować pracę podczas `client.GetStringAsync` oczekuje.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="ab3b4-167">W tym przykładzie następujące wiersze danych wyjściowych, które są oznaczone jako "Trzy", reprezentują możliwość wykonywania pracy, niezależnie od</span><span class="sxs-lookup"><span data-stu-id="ab3b4-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="ab3b4-168">Następująca instrukcja wstrzymuje postęp w `AccessTheWebAsync` podczas `getStringTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="ab3b4-169">Na poniższej ilustracji przedstawiono przepływu sterowania z `client.GetStringAsync` do przypisania do `getStringTask` i od utworzenia `getStringTask` zastosowanie operatora await.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="ab3b4-170">![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace trzy")</span><span class="sxs-lookup"><span data-stu-id="ab3b4-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="ab3b4-171">Wyrażenie await zawiesi `AccessTheWebAsync` do momentu `client.GetStringAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="ab3b4-172">Tymczasem zwraca sterowania do wywołującego `AccessTheWebAsync`, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ab3b4-173">Zazwyczaj należy poczekać na wywołanie metody asynchronicznej natychmiast.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="ab3b4-174">Na przykład następujące przypisanie można zastąpić poprzedni kod, który tworzy, a następnie oczekiwanie `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="ab3b4-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="ab3b4-175">W tym temacie operatora await jest stosowany później do uwzględnienia wiersze danych wyjściowych oznaczyć przepływu sterowania przez program.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="ab3b4-176">Krok 4</span><span class="sxs-lookup"><span data-stu-id="ab3b4-176">Step FOUR</span></span>  
 <span data-ttu-id="ab3b4-177">Zadeklarowany typ zwrotny `AccessTheWebAsync` jest `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="ab3b4-178">W związku z tym, kiedy `AccessTheWebAsync` jest wstrzymana, zwraca zadanie liczby całkowitej w celu `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="ab3b4-179">Należy pamiętać, że zwrócony zadań nie jest `getStringTask`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="ab3b4-180">Zadanie zwracane jest nowe zadanie liczbę całkowitą reprezentującą, co ma odbywać się w metodzie wstrzymaną `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="ab3b4-181">Zadanie jest promise z `AccessTheWebAsync` wygenerowało całkowitą po zakończeniu zadania.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="ab3b4-182">Następująca instrukcja przypisuje do tego zadania `getLengthTask` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="ab3b4-183">Podobnie jak w `AccessTheWebAsync`, `startButton_Click` może kontynuować pracy, które nie są zależne od wyników zadania asynchronicznego (`getLengthTask`) do momentu zadania jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="ab3b4-184">Następujące wiersze danych wyjściowych reprezentują pracy.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="ab3b4-185">Postęp w `startButton_Click` zawieszone po `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="ab3b4-186">Następująca instrukcja przypisania wstrzymuje `startButton_Click` do momentu `AccessTheWebAsync` została ukończona.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="ab3b4-187">Na poniższej ilustracji, strzałki oznaczają przepływu sterowania z wyrażenie await w `AccessTheWebAsync` do przypisania wartości do `getLengthTask`, a następnie normalnego przetwarzania w `startButton_Click` do momentu `getLengthTask` jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="ab3b4-188">![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "czterech AsyncTrace")</span><span class="sxs-lookup"><span data-stu-id="ab3b4-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="ab3b4-189">Krok 5</span><span class="sxs-lookup"><span data-stu-id="ab3b4-189">Step FIVE</span></span>  
 <span data-ttu-id="ab3b4-190">Gdy `client.GetStringAsync` sygnały jest zakończone, przetwarzania w `AccessTheWebAsync` zwolnieniu od zawieszenie i można kontynuować mimo instrukcja await.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="ab3b4-191">Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="ab3b4-192">Argument instrukcji return `urlContents.Length`, są przechowywane w zadaniu który `AccessTheWebAsync` zwraca.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="ab3b4-193">Wyrażenie await pobiera tej wartości od `getLengthTask` w `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="ab3b4-194">Na poniższej ilustracji przedstawiono transfer kontroli po `client.GetStringAsync` (i `getStringTask`) są spełnione.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="ab3b4-195">![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 5")</span><span class="sxs-lookup"><span data-stu-id="ab3b4-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="ab3b4-196">`AccessTheWebAsync` Zwraca używa do ukończenia i kontroli do `startButton_Click`, która oczekuje na zakończenie.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="ab3b4-197">Krok 6</span><span class="sxs-lookup"><span data-stu-id="ab3b4-197">Step SIX</span></span>  
 <span data-ttu-id="ab3b4-198">Gdy `AccessTheWebAsync` sygnalizuje, że zakończeniu przetwarzania można kontynuować mimo instrukcja await w `startButton_Async`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="ab3b4-199">W rzeczywistości program nie ma nic więcej robić.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="ab3b4-200">Następujące wiersze danych wyjściowych reprezentują wznowienie przetwarzania w `startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="ab3b4-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="ab3b4-201">Pobiera wyrażenie await z `getLengthTask` wartość całkowitą, która jest argument instrukcji return w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ab3b4-202">Następująca instrukcja przypisuje wartość tego `contentLength` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="ab3b4-203">Na poniższej ilustracji przedstawiono zwracany formantu z `AccessTheWebAsync` do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="ab3b4-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="ab3b4-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="ab3b4-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab3b4-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab3b4-205">See Also</span></span>  
 [<span data-ttu-id="ab3b4-206">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3b4-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="ab3b4-207">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3b4-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="ab3b4-208">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="ab3b4-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="ab3b4-209">Przykład Async: Przepływ sterowania w aplikacjach asynchronicznych (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab3b4-209">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
