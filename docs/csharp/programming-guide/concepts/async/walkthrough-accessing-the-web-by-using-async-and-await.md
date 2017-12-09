---
title: "Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 85edc87bc8c5183f85618351034c0b043472b530
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="5c69d-102">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="5c69d-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="5c69d-103">Asynchroniczne programy można napisać łatwiejsze i bardziej intuicyjne za pomocą funkcji asynchronicznej/await.</span><span class="sxs-lookup"><span data-stu-id="5c69d-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="5c69d-104">Możesz zapisać asynchroniczne kod, który wygląda jak synchroniczne kodu i umożliwić kompilatora obsługiwać funkcje wywołania zwrotnego trudne i kontynuacje, które kod asynchroniczny zazwyczaj pociąga za sobą.</span><span class="sxs-lookup"><span data-stu-id="5c69d-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="5c69d-105">Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [programowanie asynchroniczne z async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="5c69d-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="5c69d-106">W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów w postaci listy witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5c69d-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="5c69d-107">Instruktaż następnie konwertuje aplikacji do asynchronicznego rozwiązania przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="5c69d-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="5c69d-108">Jeśli nie chcesz tworzyć aplikacje samodzielnie, możesz pobrać "Async próbki: uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)" z [przykłady kodu dewelopera](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="5c69d-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="5c69d-109">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="5c69d-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="5c69d-110">Aby utworzyć aplikację programu WPF</span><span class="sxs-lookup"><span data-stu-id="5c69d-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="5c69d-111">Projektowanie proste właściwości MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="5c69d-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="5c69d-112">Można dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="5c69d-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="5c69d-113">Aby dodać niezbędne przy użyciu dyrektyw</span><span class="sxs-lookup"><span data-stu-id="5c69d-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="5c69d-114">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="5c69d-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="5c69d-115">Aby przetestować synchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5c69d-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="5c69d-116">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="5c69d-117">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="5c69d-118">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="5c69d-119">Aby przetestować asynchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5c69d-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="5c69d-120">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5c69d-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="5c69d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c69d-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="5c69d-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5c69d-122">Prerequisites</span></span>  
 <span data-ttu-id="5c69d-123">Visual Studio 2012 lub nowszym należy skonfigurować na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5c69d-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="5c69d-124">Aby uzyskać więcej informacji, zobacz [witrynie internetowej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="5c69d-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <a name="CreateWPFApp"></a><span data-ttu-id="5c69d-125">Aby utworzyć aplikację programu WPF</span><span class="sxs-lookup"><span data-stu-id="5c69d-125">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="5c69d-126">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5c69d-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="5c69d-127">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="5c69d-128">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5c69d-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="5c69d-129">W **zainstalowane szablony** okienku, wybierz pozycję Visual C#, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-129">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="5c69d-130">W **nazwa** tekst wprowadź `AsyncExampleWPF`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="5c69d-131">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a><span data-ttu-id="5c69d-132">Projektowanie proste właściwości MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="5c69d-132">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="5c69d-133">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="5c69d-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="5c69d-134">Jeśli **przybornika** okno nie jest widoczne, otwórz **widoku** menu, a następnie wybierz pozycję **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="5c69d-135">Dodaj **przycisk** kontroli i **pole tekstowe** formant **właściwości MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="5c69d-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="5c69d-136">Wyróżnij **pole tekstowe** kontroli i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5c69d-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="5c69d-137">Ustaw **nazwa** właściwości `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="5c69d-138">Ustaw **wysokość** właściwości 250.</span><span class="sxs-lookup"><span data-stu-id="5c69d-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="5c69d-139">Ustaw **szerokość** właściwości do 500.</span><span class="sxs-lookup"><span data-stu-id="5c69d-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="5c69d-140">Na **tekst** karcie, określ czcionkę o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="5c69d-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="5c69d-141">Wyróżnij **przycisk** kontroli i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="5c69d-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="5c69d-142">Ustaw **nazwa** właściwości `startButton`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="5c69d-143">Zmień wartość **zawartości** właściwość z **przycisk** do **Start**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="5c69d-144">Ustaw pole tekstowe i przycisk Tak, aby znajdować się w **właściwości MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="5c69d-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="5c69d-145">Aby uzyskać więcej informacji na temat projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5c69d-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a><span data-ttu-id="5c69d-146">Można dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="5c69d-146">To add a reference</span></span>  
  
1.  <span data-ttu-id="5c69d-147">W **Eksploratora rozwiązań**, zaznacz nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="5c69d-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="5c69d-148">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="5c69d-149">**Menedżera odwołań** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5c69d-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="5c69d-150">W górnej części okna dialogowego Sprawdź, czy projekt jest docelowo programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="5c69d-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="5c69d-151">W **zestawy** obszarze, wybierz **Framework** Jeśli nie jest już wybrana.</span><span class="sxs-lookup"><span data-stu-id="5c69d-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="5c69d-152">Na liście nazw wybierz **System.Net.Http** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="5c69d-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="5c69d-153">Wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="5c69d-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a><span data-ttu-id="5c69d-154">Aby dodać niezbędne przy użyciu dyrektyw</span><span class="sxs-lookup"><span data-stu-id="5c69d-154">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="5c69d-155">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="5c69d-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="5c69d-156">Dodaj następujące `using` dyrektywy w górnej części pliku kodu, jeśli nie są one już istnieje.</span><span class="sxs-lookup"><span data-stu-id="5c69d-156">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a><span data-ttu-id="5c69d-157">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="5c69d-157">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="5c69d-158">W oknie projektowania MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="5c69d-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="5c69d-159">W MainWindow.xaml.cs, skopiuj następujący kod do treści `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="5c69d-159">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="5c69d-160">Kod wywołuje metodę dyski aplikacji, `SumPageSizes`i wyświetla komunikat, gdy formant powróci do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="5c69d-161">Kod dla rozwiązania synchroniczne zawiera następujących metod:</span><span class="sxs-lookup"><span data-stu-id="5c69d-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="5c69d-162">`SumPageSizes`, która pobiera listę adresów URL strony sieci Web z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="5c69d-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="5c69d-163">`SetUpURLList`, które tworzy i zwraca listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="5c69d-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="5c69d-164">`GetURLContents`, które pliki do pobrania zawartości z poszczególnych witryn i zwraca zawartość jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="5c69d-165">`DisplayResults`, które wskazuje liczbę bajtów w tablicy bajtów dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="5c69d-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="5c69d-166">Skopiuj następujące cztery metody, a następnie wklej je w obszarze `startButton_Click` obsługi zdarzeń w MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="5c69d-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
    ```csharp  
    private void SumPageSizes()  
    {  
        // Make a list of web addresses.  
        List<string> urlList = SetUpURLList();   
  
        var total = 0;  
        foreach (var url in urlList)  
        {  
            // GetURLContents returns the contents of url as a byte array.  
            byte[] urlContents = GetURLContents(url);  
  
            DisplayResults(url, urlContents);  
  
            // Update the total.  
            total += urlContents.Length;  
        }  
  
        // Display the total count for all of the web addresses.  
        resultsTextBox.Text +=   
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
  
    private List<string> SetUpURLList()  
    {  
        var urls = new List<string>   
        {   
            "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290136.aspx",  
            "http://msdn.microsoft.com/library/ee256749.aspx",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
  
    private byte[] GetURLContents(string url)  
    {  
        // The downloaded resource ends up in the variable named content.  
        var content = new MemoryStream();  
  
        // Initialize an HttpWebRequest for the current URL.  
        var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
        // Send the request to the Internet resource and wait for  
        // the response.  
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        using (WebResponse response = webReq.GetResponse())  
        {  
            // Get the data stream that is associated with the specified URL.  
            using (Stream responseStream = response.GetResponseStream())  
            {  
                // Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content);  
            }  
        }  
  
        // Return the result as a byte array.  
        return content.ToArray();  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a><span data-ttu-id="5c69d-167">Aby przetestować synchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5c69d-167">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="5c69d-168">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="5c69d-169">Powinna pojawić się dane wyjściowe podobne poniżej.</span><span class="sxs-lookup"><span data-stu-id="5c69d-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
    ```  
  
     <span data-ttu-id="5c69d-170">Zwróć uwagę, że ma kilka sekund, aby wyświetlić liczniki.</span><span class="sxs-lookup"><span data-stu-id="5c69d-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="5c69d-171">W tym czasie wątku interfejsu użytkownika jest zablokowane podczas oczekiwania wymagane zasoby do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="5c69d-172">W związku z tym nie można przenieść zmaksymalizować, zminimalizować lub nawet zamknąć okna po wybraniu **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="5c69d-173">Tych działań niepowodzeniem, dopóki zacząć występować liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="5c69d-174">Jeśli witryna sieci Web nie odpowiada, należy nie wskazuje witryn, które nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="5c69d-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="5c69d-175">Trudno jest nawet zatrzymać oczekiwania i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="5c69d-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a><span data-ttu-id="5c69d-176">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="5c69d-177">Aby przekonwertować synchroniczne rozwiązania do asynchronicznego rozwiązania, najlepiej zacząć znajduje się w `GetURLContents` ponieważ wywołań <xref:System.Net.HttpWebRequest> — metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> — metoda <xref:System.IO.Stream.CopyTo%2A> są, których aplikacja uzyskuje dostęp do sieci web .</span><span class="sxs-lookup"><span data-stu-id="5c69d-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="5c69d-178">.NET Framework ułatwia konwersję podając obu metod asynchronicznych wersji.</span><span class="sxs-lookup"><span data-stu-id="5c69d-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="5c69d-179">Aby uzyskać więcej informacji na temat metod, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="5c69d-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5c69d-180">Wykonaj kroki opisane w tym przewodniku, wyświetlane są kilka błędów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="5c69d-181">Można je zignorować i kontynuować z tym przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="5c69d-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="5c69d-182">Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, oparty na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="5c69d-183">`GetResponseAsync`Zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="5c69d-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="5c69d-184">W takim przypadku *zadań zwracanej zmiennej*, `TResult`, ma typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="5c69d-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="5c69d-185">Zadanie jest obietnicę w celu uzyskania rzeczywistego `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="5c69d-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="5c69d-186">Można pobrać `WebResponse` wartości z zadania, zastosuj [await](../../../../csharp/language-reference/keywords/await.md) operator wywołania `GetResponseAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5c69d-186">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="5c69d-187">`await` Operator wstrzymuje wykonywanie bieżącej metody `GetURLContents`, dopóki nie oczekiwano zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="5c69d-187">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="5c69d-188">Tymczasem kontroli zwraca do wywołującego bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="5c69d-189">W tym przykładzie jest bieżąca metoda `GetURLContents`, a element wywołujący jest `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="5c69d-190">Po zakończeniu zadania, uzgodnionej `WebResponse` obiekt został utworzony jako wartość oczekiwano zadań i przypisaną do zmiennej `response`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="5c69d-191">Poprzednia można podzielić na następujące dwie instrukcje wyjaśnienie, co się stanie.</span><span class="sxs-lookup"><span data-stu-id="5c69d-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="5c69d-192">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="5c69d-193">Następnie await operator jest stosowany do zadań, które można pobrać `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="5c69d-193">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="5c69d-194">Jeśli Twoje metody asynchronicznej pracy, który nie jest zależny od ukończenia zadania, metoda można kontynuować pracy między te dwie instrukcje po wywołaniu metody async i przed `await` zastosować operatora.</span><span class="sxs-lookup"><span data-stu-id="5c69d-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="5c69d-195">Przykłady można znaleźć [jak: wiele sieci Web żądania równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="5c69d-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="5c69d-196">Ponieważ dodano `await` wystąpi błąd kompilatora operatora w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-196">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="5c69d-197">Operator może być używana tylko w metody, które są oznaczone ikoną z [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5c69d-197">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="5c69d-198">Ignorowanie błędu podczas Powtórz kroki konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="5c69d-199">Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c69d-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="5c69d-200">`CopyTo` Lub `CopyToAsync` metody kopiuje bajtów do jej argument `content`i nie zwraca wartości łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="5c69d-201">W wersji synchroniczne wywołanie `CopyTo` jest proste instrukcja, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="5c69d-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="5c69d-202">Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="5c69d-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="5c69d-203">Zadanie funkcje takie jak "Task(void)" i umożliwia metoda jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="5c69d-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="5c69d-204">Zastosuj `Await` lub `await` wywołania `CopyToAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5c69d-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="5c69d-205">Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="5c69d-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="5c69d-206">Wszystkie opcje, które pozostanie w `GetURLContents` jest dostosowanie podpis metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="5c69d-207">Można użyć `await` operator tylko w metodach, które są oznaczone ikoną z [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5c69d-207">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="5c69d-208">Dodaj modyfikator do Oznacz metodę jako *metody asynchronicznej*, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5c69d-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="5c69d-209">Zwracany typ metody asynchronicznej może być tylko <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, lub `void` w języku C#.</span><span class="sxs-lookup"><span data-stu-id="5c69d-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="5c69d-210">Zazwyczaj typ zwracany `void` jest używana tylko w asynchronicznej obsłudze zdarzeń, gdzie `void` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="5c69d-210">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="5c69d-211">W pozostałych przypadkach można użyć `Task(T)` Jeśli ukończono metoda ma [zwracać](../../../../csharp/language-reference/keywords/return.md) instrukcji, która zwraca wartość typu T i używasz `Task` Jeśli ukończono — metoda nie zwraca wartości łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-211">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="5c69d-212">Można potraktować `Task` zwracany typ jako oznaczające "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="5c69d-212">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="5c69d-213">Aby uzyskać więcej informacji, zobacz [typy zwracać Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="5c69d-213">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="5c69d-214">Metoda `GetURLContents` zawiera instrukcję return i instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="5c69d-215">W związku z tym typ zwracany wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="5c69d-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="5c69d-216">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="5c69d-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="5c69d-217">Zmiana typu zwracanego na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-217">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="5c69d-218">Według Konwencji metod asynchronicznych mają nazwy, które kończą się "Async", aby zmienić nazwę metody `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="5c69d-219">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="5c69d-219">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="5c69d-220">Z tymi zmianami kilka konwersji `GetURLContents` do metody asynchronicznej jest pełny.</span><span class="sxs-lookup"><span data-stu-id="5c69d-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a><span data-ttu-id="5c69d-221">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="5c69d-222">Powtórz kroki z poprzedniej procedury `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="5c69d-223">Najpierw zmień wywołanie `GetURLContents` do wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="5c69d-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="5c69d-224">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="5c69d-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="5c69d-225">Zastosuj `await` zadania który `GetURLContentsAsync` zwraca uzyskanie bajt tablicy wartości.</span><span class="sxs-lookup"><span data-stu-id="5c69d-225">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="5c69d-226">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="5c69d-226">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="5c69d-227">Poprzednie przypisania Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="5c69d-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="5c69d-228">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="5c69d-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="5c69d-229">Oznacz metodę z `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="5c69d-229">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="5c69d-230">Dodaj "Async" w nazwie metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="5c69d-231">Brak nie zadań zwracanej zmiennej, T, teraz ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `return` instrukcji.) Jednak metoda musi zwracać `Task` jako oczekujący.</span><span class="sxs-lookup"><span data-stu-id="5c69d-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="5c69d-232">W związku z tym zmienić zwracany typ metody z `void` do `Task`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-232">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="5c69d-233">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="5c69d-233">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="5c69d-234">Konwersja typu `SumPageSizes` do `SumPageSizesAsync` została ukończona.</span><span class="sxs-lookup"><span data-stu-id="5c69d-234">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a><span data-ttu-id="5c69d-235">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="5c69d-235">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="5c69d-236">W obsłudze zdarzeń, Zmień nazwę metody wywoływane z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="5c69d-236">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="5c69d-237">Ponieważ `SumPageSizesAsync` jest to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.</span><span class="sxs-lookup"><span data-stu-id="5c69d-237">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="5c69d-238">Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-238">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="5c69d-239">Wywołanie zwraca `Task`, a nie `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-239">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="5c69d-240">Jak w poprzedniej procedury można przekonwertować wywołanie za pomocą jednej instrukcji lub dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="5c69d-240">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="5c69d-241">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="5c69d-241">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="5c69d-242">Aby uniknąć przypadkowego ponownego wprowadzania operacji, dodaj następującą instrukcję, w górnej części `startButton_Click` wyłączyć **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-242">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="5c69d-243">Można ponownie włączyć przycisk na końcu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c69d-243">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="5c69d-244">Aby uzyskać więcej informacji na temat ponownego rozpoczęcia, zobacz [Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="5c69d-244">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="5c69d-245">Na koniec należy dodać `async` modyfikatora w deklaracji, aby program obsługi zdarzeń można zdefiniować oczekiwania `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-245">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="5c69d-246">Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5c69d-246">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="5c69d-247">Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi zwracać `void`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-247">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="5c69d-248">Konwersja projektu przetwarzania synchronicznego do asynchronicznego zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="5c69d-248">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a><span data-ttu-id="5c69d-249">Aby przetestować asynchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5c69d-249">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="5c69d-250">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-250">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="5c69d-251">Powinna pojawić się dane wyjściowe podobne dane wyjściowe synchroniczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-251">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="5c69d-252">Jednak zauważyć następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="5c69d-252">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="5c69d-253">Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-253">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="5c69d-254">Na przykład oba programy zawierają wiersza w `startButton_Click` który czyści pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="5c69d-254">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="5c69d-255">W zamierzeniu, wyczyść pole tekstowe między działa, jeśli wybierzesz **Start** przycisk raz drugi, po pojawieniu się jeden zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="5c69d-255">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="5c69d-256">W to wersja synchroniczna pola tekstowego jest wyczyszczone tuż przed liczniki są wyświetlane po raz drugi, po zakończeniu pliki do pobrania i wątku interfejsu użytkownika będzie mógł wykonywać inne zadania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-256">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="5c69d-257">W wersjach asynchronicznych, pola tekstowego czyści natychmiast po wybraniu **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-257">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="5c69d-258">Przede wszystkim wątku interfejsu użytkownika nie jest blokowane podczas pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-258">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="5c69d-259">Można przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web zliczane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="5c69d-259">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="5c69d-260">Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisk (x w czerwonym pola w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="5c69d-260">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a><span data-ttu-id="5c69d-261">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5c69d-261">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="5c69d-262">.NET Framework 4.5 zapewnia wiele metod asynchronicznych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="5c69d-262">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="5c69d-263">Jeden z nich, <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, jest tylko dane potrzebne do tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="5c69d-263">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="5c69d-264">Możesz użyć jej zamiast `GetURLContentsAsync` metody utworzonego w procedurze wcześniej.</span><span class="sxs-lookup"><span data-stu-id="5c69d-264">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="5c69d-265">Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-265">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="5c69d-266">Dodaj następujące oświadczenie na początku metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-266">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="5c69d-267">W `SumPageSizesAsync,` Zastąp wywołanie Twojej `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="5c69d-267">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="5c69d-268">Usuń lub komentarz `GetURLContentsAsync` metody zapisane.</span><span class="sxs-lookup"><span data-stu-id="5c69d-268">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="5c69d-269">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="5c69d-269">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="5c69d-270">Zachowanie tej wersji projektu powinien zgodne zachowanie opisano procedury "Aby przetestować asynchroniczne rozwiązania", ale z nawet mniejszym wysiłku z Twojej.</span><span class="sxs-lookup"><span data-stu-id="5c69d-270">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a><span data-ttu-id="5c69d-271">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c69d-271">Example</span></span>  
 <span data-ttu-id="5c69d-272">Poniższy kod zawiera pełny przykład konwersji z synchronicznego do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metody zapisane.</span><span class="sxs-lookup"><span data-stu-id="5c69d-272">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="5c69d-273">Należy zauważyć, że silnie podobny oryginalnego synchroniczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="5c69d-273">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                byte[] urlContents = await GetURLContentsAsync(url);  
  
                // The previous line abbreviates the following two assignment statements.  
  
                // GetURLContentsAsync returns a Task<T>. At completion, the task  
                // produces a byte array.  
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.            
                total += urlContents.Length;  
            }  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.                  
            using (WebResponse response = await webReq.GetResponseAsync())  
  
            // The previous statement abbreviates the following two statements.  
  
            //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
            //using (WebResponse response = await responseTask)  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    // Read the bytes in responseStream and copy them to content.   
                    await responseStream.CopyToAsync(content);  
  
                    // The previous statement abbreviates the following two statements.  
  
                    // CopyToAsync returns a Task, not a Task<T>.  
                    //Task copyTask = responseStream.CopyToAsync(content);  
  
                    // When copyTask is completed, content contains a copy of  
                    // responseStream.  
                    //await copyTask;  
                }  
            }  
            // Return the result as a byte array.  
            return content.ToArray();  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="5c69d-274">Poniższy kod zawiera pełny przykład rozwiązania, która używa `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="5c69d-274">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Disable the button until the operation is complete.  
            startButton.IsEnabled = false;  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            //// Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
  
            // Reenable the button in case you want to run the operation again.  
            startButton.IsEnabled = true;  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            var total = 0;  
  
            foreach (var url in urlList)  
            {  
                // GetByteArrayAsync returns a task. At completion, the task  
                // produces a byte array.  
                byte[] urlContents = await client.GetByteArrayAsync(url);                 
  
                // The following two lines can replace the previous assignment statement.  
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
                //byte[] urlContents = await getContentsTask;  
  
                DisplayResults(url, urlContents);  
  
                // Update the total.  
                total += urlContents.Length;  
            }  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c69d-275">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c69d-275">See Also</span></span>  
 [<span data-ttu-id="5c69d-276">Przykład Async: Uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c69d-276">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](http://go.microsoft.com/fwlink/?LinkId=255191)  
 [<span data-ttu-id="5c69d-277">asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="5c69d-277">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
 [<span data-ttu-id="5c69d-278">await</span><span class="sxs-lookup"><span data-stu-id="5c69d-278">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="5c69d-279">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="5c69d-279">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="5c69d-280">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="5c69d-280">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="5c69d-281">Programowanie asynchroniczne opartego na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="5c69d-281">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="5c69d-282">Porady: rozszerzanie async wskazówki za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="5c69d-282">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="5c69d-283">Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="5c69d-283">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
