---
title: 'Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: cb628941d53957356cfa49d81fb78f16369af86b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085215"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="1c9a7-102">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>
<span data-ttu-id="1c9a7-103">Asynchroniczne programy można napisać bardziej łatwo i intuicyjnie za pomocą funkcji async/await.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="1c9a7-104">Można napisać kod asynchroniczny, który wygląda jak synchroniczny kod i pozwolić kompilatorowi obsługi funkcji wywołania zwrotnego trudne i kontynuacje, które kodu asynchronicznego zazwyczaj pociąga za sobą.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="1c9a7-105">Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="1c9a7-106">W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczba bajtów na liście witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="1c9a7-107">Instruktaż następnie konwertuje ją do asynchronicznego rozwiązania przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="1c9a7-108">Jeśli nie chcesz samodzielnie tworzyć aplikacje, możesz pobrać [próbka asynchroniczna: dostęp do instruktażu sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="1c9a7-109">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="1c9a7-110">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="1c9a7-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="1c9a7-111">Aby zaprojektować proste MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="1c9a7-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="1c9a7-112">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="1c9a7-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="1c9a7-113">Aby dodać niezbędne dyrektyw using</span><span class="sxs-lookup"><span data-stu-id="1c9a7-113">To add necessary using directives</span></span>](#usingDir)  
  
-   [<span data-ttu-id="1c9a7-114">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="1c9a7-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="1c9a7-115">Aby przetestować rozwiązaniu synchronicznym</span><span class="sxs-lookup"><span data-stu-id="1c9a7-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="1c9a7-116">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="1c9a7-117">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="1c9a7-118">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="1c9a7-119">Aby przetestować rozwiązania asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1c9a7-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="1c9a7-120">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1c9a7-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="1c9a7-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c9a7-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
> [!NOTE]
>  <span data-ttu-id="1c9a7-122">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-122">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="1c9a7-123">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="1c9a7-123">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="1c9a7-124">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-124">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1c9a7-125">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-125">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="1c9a7-126">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-126">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="1c9a7-127">W **zainstalowane szablony** okienku wybierz pozycję Visual C#, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-127">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="1c9a7-128">W **nazwa** tekstu wprowadź `AsyncExampleWPF`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-128">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="1c9a7-129">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-129">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="1c9a7-130">Aby zaprojektować proste MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="1c9a7-130">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="1c9a7-131">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-131">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="1c9a7-132">Jeśli **przybornika** okno nie jest widoczna, otwórz **widoku** menu, a następnie wybierz **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-132">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="1c9a7-133">Dodaj **przycisk** kontroli i **TextBox** kontrolę **MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-133">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="1c9a7-134">Wyróżnij **TextBox** sterowania i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-134">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="1c9a7-135">Ustaw **nazwa** właściwość `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-135">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="1c9a7-136">Ustaw **wysokość** właściwości do 250.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-136">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="1c9a7-137">Ustaw **szerokość** właściwości do 500.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-137">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="1c9a7-138">Na **tekstu** Określ czcionki o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-138">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="1c9a7-139">Wyróżnij **przycisk** sterowania i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-139">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="1c9a7-140">Ustaw **nazwa** właściwość `startButton`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-140">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="1c9a7-141">Zmień wartość właściwości **zawartości** właściwość **przycisk** do **Start**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-141">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="1c9a7-142">Położenie pola tekstowego i przycisku Tak, aby znajdować się w **MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-142">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="1c9a7-143">Aby uzyskać więcej informacji dotyczących projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-143">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="1c9a7-144">Aby dodać odwołanie</span><span class="sxs-lookup"><span data-stu-id="1c9a7-144">To add a reference</span></span>  
  
1.  <span data-ttu-id="1c9a7-145">W **Eksploratora rozwiązań**, wyróżnij nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-145">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="1c9a7-146">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-146">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="1c9a7-147">**Menadżer odwołań** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-147">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="1c9a7-148">W górnej części okna dialogowego Sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-148">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="1c9a7-149">W **zestawy** obszaru, wybierz **Framework** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-149">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="1c9a7-150">Na liście nazw, wybierz **System.Net.Http** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-150">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="1c9a7-151">Wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-151">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="usingDir"></a> <span data-ttu-id="1c9a7-152">Aby dodać niezbędne dyrektyw using</span><span class="sxs-lookup"><span data-stu-id="1c9a7-152">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="1c9a7-153">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-153">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="1c9a7-154">Dodaj następujący kod `using` dyrektywy u góry pliku kodu, jeśli tak nie jest już obecny.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-154">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>  
  
    ```csharp  
    using System.Net.Http;  
    using System.Net;  
    using System.IO;  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="1c9a7-155">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="1c9a7-155">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="1c9a7-156">W oknie projektu, MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-156">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2.  <span data-ttu-id="1c9a7-157">W MainWindow.xaml.cs, skopiuj poniższy kod do treści `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-157">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    SumPageSizes();  
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";  
    ```  
  
     <span data-ttu-id="1c9a7-158">Kod wywołuje metodę, która napędza aplikację, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-158">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="1c9a7-159">Kod używany w rozwiązaniu synchronicznym zawiera poniższe cztery metody:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-159">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="1c9a7-160">`SumPageSizes`, która pobiera listę adresów URL strony sieci Web, z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-160">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="1c9a7-161">`SetUpURLList`, która tworzy i zwraca listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-161">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="1c9a7-162">`GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-162">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="1c9a7-163">`DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-163">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="1c9a7-164">Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-164">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>  
  
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
###  <a name="testSynch"></a> <span data-ttu-id="1c9a7-165">Aby przetestować rozwiązaniu synchronicznym</span><span class="sxs-lookup"><span data-stu-id="1c9a7-165">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="1c9a7-166">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-166">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="1c9a7-167">Powinien pojawić się dane wyjściowe podobne do poniższej listy.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-167">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="1c9a7-168">Należy zauważyć, że zajmuje kilka sekund, aby wyświetlić liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-168">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="1c9a7-169">W tym czasie wątku interfejsu użytkownika jest blokowany, aż do żądanych zasobów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-169">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="1c9a7-170">W rezultacie nie można przenieść zmaksymalizować, zminimalizować lub nawet Zamknij okna, po dokonaniu wyboru **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-170">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="1c9a7-171">Tych działań zakończyć się niepowodzeniem, dopóki nie pojawiają się rozpocząć liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-171">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="1c9a7-172">Jeśli witryna sieci Web nie odpowiada, masz żadne oznaki, witryn, które nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-172">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="1c9a7-173">Trudno jest nawet zakończyć oczekiwanie i zamknięcie programu.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-173">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="1c9a7-174">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-174">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1c9a7-175">Aby konwertować synchroniczne rozwiązanie do asynchronicznego rozwiązania, najlepszym miejscem do rozpoczęcia jest w `GetURLContents` ponieważ wywołania <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web .</span><span class="sxs-lookup"><span data-stu-id="1c9a7-175">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="1c9a7-176">.NET Framework ułatwia konwersję poprzez dostarczenie asynchronicznych wersji obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-176">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="1c9a7-177">Aby uzyskać więcej informacji o metodach, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-177">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1c9a7-178">Postępuj zgodnie z instrukcjami w tym przewodniku, wyświetlane są kilka błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-178">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="1c9a7-179">Można je zignorować i kontynuować z tym przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-179">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="1c9a7-180">Zmień metodę, która jest wywołana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, opartego na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-180">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```csharp  
    using (WebResponse response = webReq.GetResponseAsync())  
    ```  
  
2.  <span data-ttu-id="1c9a7-181">`GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-181">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1c9a7-182">W tym przypadku *zmiennej zwracanego zadania*, `TResult`, ma typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-182">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="1c9a7-183">Zadanie jest obietnicą utworzenia rzeczywistej `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-183">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="1c9a7-184">Aby pobrać `WebResponse` wartości z zadania, zastosuj [await](../../../../csharp/language-reference/keywords/await.md) operator wywołania do `GetResponseAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-184">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    using (WebResponse response = await webReq.GetResponseAsync())  
    ```  
  
     <span data-ttu-id="1c9a7-185">`await` Operator zawiesza wykonywanie bieżącej metody `GetURLContents`, aż oczekiwane zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-185">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="1c9a7-186">W międzyczasie formant powraca do obiektu wywołującego metody bieżącej.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-186">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="1c9a7-187">W tym przykładzie jest bieżąca metoda `GetURLContents`, a obiekt wywołujący jest `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-187">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="1c9a7-188">Po zakończeniu zadania, uzgodnionego `WebResponse` obiekt jest generowany z wartością oczekiwane zadanie i przypisana do zmiennej `response`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-188">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="1c9a7-189">Poprzednia instrukcja można podzielić na dwie poniższe instrukcje, aby wyjaśnić, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-189">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```csharp  
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();  
    //using (WebResponse response = await responseTask)  
    ```  
  
     <span data-ttu-id="1c9a7-190">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-190">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="1c9a7-191">Await operator jest stosowany do zadania do pobrania, a następnie `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-191">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="1c9a7-192">Jeśli metoda async ma robić prace, które nie są zależne od zakończenia tego zadania, metody można kontynuować pracę między te dwie instrukcje po wywołaniu metody async i przed `await` jest stosowany operator.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-192">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="1c9a7-193">Przykłady, zobacz [jak: wiele sieci Web żądania równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-193">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="1c9a7-194">Ponieważ dodałeś `await` występuje błąd kompilatora operatora w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-194">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="1c9a7-195">Operator może służyć tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-195">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="1c9a7-196">Ignorowanie błędu podczas Powtórz procedurę konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-196">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="1c9a7-197">Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-197">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="1c9a7-198">`CopyTo` Lub `CopyToAsync` metoda kopiuje bajtów do jej argument `content`i nie zwraca zrozumiałą wartość.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-198">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="1c9a7-199">W wersji synchroniczne wywołanie `CopyTo` jest prostą instrukcję, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-199">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="1c9a7-200">Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-200">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="1c9a7-201">Zadanie funkcje takie jak "Task(void)" i włącza metodę oczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-201">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="1c9a7-202">Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-202">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```csharp  
        await responseStream.CopyToAsync(content);  
        ```  
  
         <span data-ttu-id="1c9a7-203">Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-203">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```csharp  
        // CopyToAsync returns a Task, not a Task<T>.  
        //Task copyTask = responseStream.CopyToAsync(content);  
  
        // When copyTask is completed, content contains a copy of  
        // responseStream.  
        //await copyTask;  
        ```  
  
4.  <span data-ttu-id="1c9a7-204">Wszystkie opcje, które pozostają do wykonania `GetURLContents` jest dostosowanie podpis metody.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-204">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="1c9a7-205">Możesz użyć `await` operatora tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-205">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="1c9a7-206">Dodaj modyfikator do oznaczania metody jako *metody asynchronicznej*, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-206">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```csharp  
    private async byte[] GetURLContents(string url)  
    ```  
  
5.  <span data-ttu-id="1c9a7-207">Zwracany typ metody asynchronicznej może składać się wyłącznie <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, lub `void` w języku C#.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-207">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="1c9a7-208">Zwykle, zwracanym typem `void` jest używany tylko w przypadku programu async obsługi zdarzeń, gdzie `void` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-208">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="1c9a7-209">W innych przypadkach należy użyć `Task(T)` Jeśli metoda ukończone ma [zwracają](../../../../csharp/language-reference/keywords/return.md) instrukcję, która zwraca wartość typu T i używasz `Task` jeśli ukończone metoda nie zwraca zrozumiałą wartość.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-209">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="1c9a7-210">Można potraktować `Task` zwracany typ, co oznacza "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="1c9a7-210">You can think of the `Task` return type as meaning "Task(void)."</span></span>  
  
     <span data-ttu-id="1c9a7-211">Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-211">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="1c9a7-212">Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-212">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="1c9a7-213">W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-213">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="1c9a7-214">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-214">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="1c9a7-215">Zmień typ zwracany `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-215">Change the return type to `Task<byte[]>`.</span></span>  
  
    -   <span data-ttu-id="1c9a7-216">Zgodnie z Konwencją metod asynchronicznych mają nazwy, które kończą się na "Async", więc Zmień nazwę metody `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-216">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="1c9a7-217">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-217">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task<byte[]> GetURLContentsAsync(string url)  
    ```  
  
     <span data-ttu-id="1c9a7-218">Za pomocą tych kilku zmian konwersji `GetURLContents` metody asynchronicznej jest pełny.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-218">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="1c9a7-219">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-219">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1c9a7-220">Powtórz kroki z poprzedniej procedury, aby uzyskać `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-220">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="1c9a7-221">Najpierw należy zmienić wywołanie `GetURLContents` do wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-221">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="1c9a7-222">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-222">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="1c9a7-223">Zastosuj `await` do zadania, `GetURLContentsAsync` zwraca uzyskać bajt tablica wartości.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-223">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="1c9a7-224">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-224">The following code shows these changes.</span></span>  
  
    ```csharp  
    byte[] urlContents = await GetURLContentsAsync(url);  
    ```  
  
     <span data-ttu-id="1c9a7-225">Poprzednie przypisanie Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-225">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```csharp  
    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    // produces a byte array.  
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //byte[] urlContents = await getContentsTask;  
    ```  
  
2.  <span data-ttu-id="1c9a7-226">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="1c9a7-226">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="1c9a7-227">Oznacz metodę z `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-227">Mark the method with the `async` modifier.</span></span>  
  
    -   <span data-ttu-id="1c9a7-228">Dodaj "Async" w nazwie metody.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-228">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="1c9a7-229">Nie jest zmienną zwracany nie zadań, T, tym razem, ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `return` instrukcja.) Jednak metoda musi zwracać `Task` jako oczekujący.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-229">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="1c9a7-230">W związku z tym, zmień zwracany typ metody z `void` do `Task`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-230">Therefore, change the return type of the method from `void` to `Task`.</span></span>  
  
     <span data-ttu-id="1c9a7-231">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-231">The following code shows these changes.</span></span>  
  
    ```csharp  
    private async Task SumPageSizesAsync()  
    ```  
  
     <span data-ttu-id="1c9a7-232">Konwersja `SumPageSizes` do `SumPageSizesAsync` zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-232">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="1c9a7-233">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="1c9a7-233">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="1c9a7-234">W procedurze obsługi zdarzeń Zmień nazwę wywoływanej metody z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-234">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="1c9a7-235">Ponieważ `SumPageSizesAsync` to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-235">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="1c9a7-236">Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-236">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="1c9a7-237">To wywołanie zwraca `Task`, a nie `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-237">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="1c9a7-238">Tak jak w poprzednich procedur można przekonwertować wywołanie za pomocą jednej instrukcji lub dwóch instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-238">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="1c9a7-239">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-239">The following code shows these changes.</span></span>  
  
    ```csharp  
    // One-step async call.  
    await SumPageSizesAsync();  
  
    // Two-step async call.  
    //Task sumTask = SumPageSizesAsync();  
    //await sumTask;  
    ```  
  
3.  <span data-ttu-id="1c9a7-240">Aby uniknąć przypadkowego ponownego wprowadzania operacji, należy dodać następującą instrukcję w górnej części `startButton_Click` wyłączyć **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-240">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```csharp  
    // Disable the button until the operation is complete.  
    startButton.IsEnabled = false;  
    ```  
  
     <span data-ttu-id="1c9a7-241">Możesz włączyć przycisku na końcu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-241">You can reenable the button at the end of the event handler.</span></span>  
  
    ```csharp  
    // Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = true;  
    ```  
  
     <span data-ttu-id="1c9a7-242">Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [obsługi współużytkowania wątkowości w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-242">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="1c9a7-243">Na koniec należy dodać `async` modyfikator deklaracji, aby program obsługi zdarzeń może poczekać `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-243">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```csharp  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    ```  
  
     <span data-ttu-id="1c9a7-244">Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-244">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="1c9a7-245">Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi zwracać `void`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-245">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>  
  
     <span data-ttu-id="1c9a7-246">Konwersja przetwarzania synchronicznego w celu asynchronicznego projektu zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-246">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="1c9a7-247">Aby przetestować rozwiązania asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1c9a7-247">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="1c9a7-248">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-248">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="1c9a7-249">Dane wyjściowe podobne dane wyjściowe w rozwiązaniu synchronicznym powinna zostać wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-249">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="1c9a7-250">Jednak zauważyć następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-250">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="1c9a7-251">Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-251">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="1c9a7-252">Na przykład oba programy zawiera wiersz w `startButton_Click` , czyści pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-252">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="1c9a7-253">Celem jest czyścić pole tekstowe między działa, jeśli wybierzesz **Start** przycisk, aby po raz drugi, po pojawieniu się jeden zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-253">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="1c9a7-254">W to wersja synchroniczna pole tekstowe jest wyczyszczone przed zliczeń pojawiają się po raz drugi, gdy odbywa się pliki do pobrania i jest bezpłatna wykonywanie innych zadań w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-254">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="1c9a7-255">W wersjach asynchronicznych, pola tekstowego czyści natychmiast, po dokonaniu wyboru **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-255">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="1c9a7-256">Co najważniejsze wątek interfejsu użytkownika nie jest zablokowane podczas jej pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-256">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="1c9a7-257">Możesz przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web liczone, a wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-257">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="1c9a7-258">Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisku (x czerwone pola w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="1c9a7-258">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="1c9a7-259">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1c9a7-259">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="1c9a7-260">.NET Framework 4.5 zapewnia wiele metod asynchronicznych, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-260">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="1c9a7-261">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, wykonuje tylko potrzebne w ramach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-261">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="1c9a7-262">Można używać go zamiast `GetURLContentsAsync` metody, który został utworzony w wcześniejszym etapie procedury.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-262">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="1c9a7-263">Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-263">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="1c9a7-264">Dodaj następującą deklarację na początku metody.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-264">Add the following declaration at the start of the method.</span></span>  
  
    ```csharp  
    // Declare an HttpClient object and increase the buffer size. The  
    // default buffer size is 65,536.  
    HttpClient client =  
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
    ```  
  
2.  <span data-ttu-id="1c9a7-265">W `SumPageSizesAsync,` Zastąp wywołanie usługi `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-265">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```csharp  
    byte[] urlContents = await client.GetByteArrayAsync(url);  
    ```  
  
3.  <span data-ttu-id="1c9a7-266">Usunąć lub skomentować `GetURLContentsAsync` metodę, która powstała z jednego.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-266">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="1c9a7-267">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-267">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="1c9a7-268">Zachowanie tej wersji programu project powinien odpowiadać zachowanie, które opisano procedury "Aby test asynchronicznego rozwiązania", ale o jeszcze mniejszym nakładzie pracy ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-268">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="1c9a7-269">Przykład</span><span class="sxs-lookup"><span data-stu-id="1c9a7-269">Example</span></span>  
 <span data-ttu-id="1c9a7-270">Poniższy kod zawiera pełny przykład konwersja przez synchroniczny do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metodę, która powstała z jednego.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-270">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="1c9a7-271">Należy zauważyć, że silnie przypomina oryginalnej, synchroniczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-271">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
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
  
 <span data-ttu-id="1c9a7-272">Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="1c9a7-272">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c9a7-273">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c9a7-273">See Also</span></span>

- [<span data-ttu-id="1c9a7-274">Próbka asynchroniczna: Dostęp do instruktażu sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-274">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
- [<span data-ttu-id="1c9a7-275">async</span><span class="sxs-lookup"><span data-stu-id="1c9a7-275">async</span></span>](../../../../csharp/language-reference/keywords/async.md)  
- [<span data-ttu-id="1c9a7-276">await</span><span class="sxs-lookup"><span data-stu-id="1c9a7-276">await</span></span>](../../../../csharp/language-reference/keywords/await.md)  
- [<span data-ttu-id="1c9a7-277">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-277">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="1c9a7-278">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-278">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
- [<span data-ttu-id="1c9a7-279">Programowanie asynchroniczne opartego na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-279">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)  
- [<span data-ttu-id="1c9a7-280">Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-280">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
- [<span data-ttu-id="1c9a7-281">Porady: wiele żądań sieci Web równolegle za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="1c9a7-281">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
