---
title: 'Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 535b431fcf8ab5dafa134b8a3c1e2f7eacd6b427
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696510"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="a5a9b-102">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="a5a9b-103">Asynchroniczne programy można napisać łatwiejsze i bardziej intuicyjne za pomocą funkcji asynchronicznej/await.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="a5a9b-104">Możesz zapisać asynchroniczne kod, który wygląda jak synchroniczne kodu i umożliwić kompilatora obsługiwać funkcje wywołania zwrotnego trudne i kontynuacje, które kod asynchroniczny zazwyczaj pociąga za sobą.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="a5a9b-105">Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="a5a9b-106">W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów w postaci listy witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="a5a9b-107">Instruktaż następnie konwertuje aplikacji do asynchronicznego rozwiązania przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="a5a9b-108">Jeśli nie chcesz tworzyć aplikacje samodzielnie, możesz pobrać "Async próbki: uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)" z [przykłady kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
  
 <span data-ttu-id="a5a9b-109">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="a5a9b-110">Aby utworzyć aplikację programu WPF</span><span class="sxs-lookup"><span data-stu-id="a5a9b-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="a5a9b-111">Projektowanie proste właściwości MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="a5a9b-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="a5a9b-112">Można dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="a5a9b-113">Aby dodać niezbędne instrukcje importów</span><span class="sxs-lookup"><span data-stu-id="a5a9b-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="a5a9b-114">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="a5a9b-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="a5a9b-115">Aby przetestować synchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="a5a9b-116">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="a5a9b-117">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="a5a9b-118">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="a5a9b-119">Aby przetestować asynchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="a5a9b-120">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5a9b-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="a5a9b-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a9b-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="a5a9b-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a5a9b-122">Prerequisites</span></span>  
 <span data-ttu-id="a5a9b-123">Visual Studio 2012 lub nowszym należy skonfigurować na komputerze.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="a5a9b-124">Aby uzyskać więcej informacji, zobacz [witrynie internetowej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=235233).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <a name="CreateWPFApp"></a> <span data-ttu-id="a5a9b-125">Aby utworzyć aplikację programu WPF</span><span class="sxs-lookup"><span data-stu-id="a5a9b-125">To create a WPF application</span></span>  
  
1.  <span data-ttu-id="a5a9b-126">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a5a9b-127">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="a5a9b-128">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="a5a9b-129">W **zainstalowane szablony** okienku, wybierz pozycję Visual Basic, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="a5a9b-130">W **nazwa** tekst wprowadź `AsyncExampleWPF`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="a5a9b-131">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <a name="MainWindow"></a> <span data-ttu-id="a5a9b-132">Projektowanie proste właściwości MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="a5a9b-132">To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="a5a9b-133">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="a5a9b-134">Jeśli **przybornika** okno nie jest widoczne, otwórz **widoku** menu, a następnie wybierz pozycję **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="a5a9b-135">Dodaj **przycisk** kontroli i **pole tekstowe** formant **właściwości MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="a5a9b-136">Wyróżnij **pole tekstowe** kontroli i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="a5a9b-137">Ustaw **nazwa** właściwości `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="a5a9b-138">Ustaw **wysokość** właściwości 250.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="a5a9b-139">Ustaw **szerokość** właściwości do 500.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="a5a9b-140">Na **tekst** karcie, określ czcionkę o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="a5a9b-141">Wyróżnij **przycisk** kontroli i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="a5a9b-142">Ustaw **nazwa** właściwości `startButton`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="a5a9b-143">Zmień wartość **zawartości** właściwość z **przycisk** do **Start**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="a5a9b-144">Ustaw pole tekstowe i przycisk Tak, aby znajdować się w **właściwości MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="a5a9b-145">Aby uzyskać więcej informacji na temat projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <a name="AddRef"></a> <span data-ttu-id="a5a9b-146">Można dodać odwołania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-146">To add a reference</span></span>  
  
1.  <span data-ttu-id="a5a9b-147">W **Eksploratora rozwiązań**, zaznacz nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="a5a9b-148">Na pasku menu wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="a5a9b-149">**Menedżera odwołań** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="a5a9b-150">W górnej części okna dialogowego Sprawdź, czy projekt jest docelowo programu .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="a5a9b-151">W **zestawy** obszarze, wybierz **Framework** Jeśli nie jest już wybrana.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="a5a9b-152">Na liście nazw wybierz **System.Net.Http** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="a5a9b-153">Wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <a name="ImportsState"></a> <span data-ttu-id="a5a9b-154">Aby dodać niezbędne instrukcje importów</span><span class="sxs-lookup"><span data-stu-id="a5a9b-154">To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="a5a9b-155">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="a5a9b-156">Dodaj następujące `Imports` instrukcje w górnej części pliku kodu, jeśli nie są one już istnieje.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <a name="synchronous"></a> <span data-ttu-id="a5a9b-157">Aby utworzyć aplikację synchroniczne</span><span class="sxs-lookup"><span data-stu-id="a5a9b-157">To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="a5a9b-158">W oknie projektowania MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="a5a9b-159">W MainWindow.xaml.vb, skopiuj następujący kod do treści `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="a5a9b-160">Kod wywołuje metodę dyski aplikacji, `SumPageSizes`i wyświetla komunikat, gdy formant powróci do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="a5a9b-161">Kod dla rozwiązania synchroniczne zawiera następujących metod:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="a5a9b-162">`SumPageSizes`, która pobiera listę adresów URL strony sieci Web z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="a5a9b-163">`SetUpURLList`, które tworzy i zwraca listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="a5a9b-164">`GetURLContents`, które pliki do pobrania zawartości z poszczególnych witryn i zwraca zawartość jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="a5a9b-165">`DisplayResults`, które wskazuje liczbę bajtów w tablicy bajtów dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="a5a9b-166">Skopiuj następujące cztery metody, a następnie wklej je w obszarze `startButton_Click` obsługi zdarzeń w MainWindow.xaml.vb:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <a name="testSynch"></a> <span data-ttu-id="a5a9b-167">Aby przetestować synchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-167">To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="a5a9b-168">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="a5a9b-169">Powinna pojawić się dane wyjściowe podobne poniżej.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-169">Output that resembles the following list should appear.</span></span>  
  
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
  
     <span data-ttu-id="a5a9b-170">Zwróć uwagę, że ma kilka sekund, aby wyświetlić liczniki.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="a5a9b-171">W tym czasie wątku interfejsu użytkownika jest zablokowane podczas oczekiwania wymagane zasoby do pobrania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="a5a9b-172">W związku z tym nie można przenieść zmaksymalizować, zminimalizować lub nawet zamknąć okna po wybraniu **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="a5a9b-173">Tych działań niepowodzeniem, dopóki zacząć występować liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="a5a9b-174">Jeśli witryna sieci Web nie odpowiada, należy nie wskazuje witryn, które nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="a5a9b-175">Trudno jest nawet zatrzymać oczekiwania i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <a name="GetURLContents"></a> <span data-ttu-id="a5a9b-176">Aby przekonwertować GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-176">To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="a5a9b-177">Aby przekonwertować synchroniczne rozwiązania do asynchronicznego rozwiązania, najlepiej zacząć znajduje się w `GetURLContents` ponieważ wywołań <xref:System.Net.HttpWebRequest> — metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> — metoda <xref:System.IO.Stream.CopyTo%2A> są, których aplikacja uzyskuje dostęp do sieci web .</span><span class="sxs-lookup"><span data-stu-id="a5a9b-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="a5a9b-178">.NET Framework ułatwia konwersję podając obu metod asynchronicznych wersji.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="a5a9b-179">Aby uzyskać więcej informacji na temat metod, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a5a9b-180">Wykonaj kroki opisane w tym przewodniku, wyświetlane są kilka błędów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="a5a9b-181">Można je zignorować i kontynuować z tym przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="a5a9b-182">Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, oparty na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="a5a9b-183">`GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a5a9b-184">W takim przypadku *zadań zwracanej zmiennej*, `TResult`, ma typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="a5a9b-185">Zadanie jest obietnicę w celu uzyskania rzeczywistego `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="a5a9b-186">Można pobrać `WebResponse` wartości z zadania, zastosuj [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator wywołania `GetResponseAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
    ```vb  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
    ```  
  
     <span data-ttu-id="a5a9b-187">`Await` Operator wstrzymuje wykonywanie bieżącej metody `GetURLContents`, dopóki nie oczekiwano zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="a5a9b-188">Tymczasem kontroli zwraca do wywołującego bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="a5a9b-189">W tym przykładzie jest bieżąca metoda `GetURLContents`, a element wywołujący jest `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="a5a9b-190">Po zakończeniu zadania, uzgodnionej `WebResponse` obiekt został utworzony jako wartość oczekiwano zadań i przypisaną do zmiennej `response`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     <span data-ttu-id="a5a9b-191">Poprzednia można podzielić na następujące dwie instrukcje wyjaśnienie, co się stanie.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>  
  
    ```vb  
    'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
    'Using response As WebResponse = Await responseTask  
    ```  
  
     <span data-ttu-id="a5a9b-192">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="a5a9b-193">Następnie `Await` operator jest stosowany do zadań, które można pobrać `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     <span data-ttu-id="a5a9b-194">Jeśli Twoje metody asynchronicznej pracy, który nie jest zależny od ukończenia zadania, metoda można kontynuować pracy między te dwie instrukcje po wywołaniu metody asynchronicznej i przed zastosowaniem operatora await.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="a5a9b-195">Przykłady można znaleźć [jak: utworzyć wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
3.  <span data-ttu-id="a5a9b-196">Ponieważ dodano `Await` wystąpi błąd kompilatora operatora w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="a5a9b-197">Operator może być używana tylko w metody, które są oznaczone ikoną z [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="a5a9b-198">Ignorowanie błędu podczas Powtórz kroki konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="a5a9b-199">Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="a5a9b-200">`CopyTo` Lub `CopyToAsync` metody kopiuje bajtów do jej argument `content`i nie zwraca wartości łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="a5a9b-201">W wersji synchroniczne wywołanie `CopyTo` jest proste instrukcja, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="a5a9b-202">Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="a5a9b-203">Zadanie funkcje takie jak "Task(void)" i umożliwia metoda jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="a5a9b-204">Zastosuj `Await` lub `await` wywołania `CopyToAsync`, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
        ```vb  
        Await responseStream.CopyToAsync(content)  
        ```  
  
         <span data-ttu-id="a5a9b-205">Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
        ```vb  
        ' CopyToAsync returns a Task, not a Task<T>.  
        'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
        ' When copyTask is completed, content contains a copy of  
        ' responseStream.  
        'Await copyTask  
        ```  
  
4.  <span data-ttu-id="a5a9b-206">Wszystkie opcje, które pozostanie w `GetURLContents` jest dostosowanie podpis metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="a5a9b-207">Można użyć `Await` operator tylko w metodach, które są oznaczone ikoną z [Async](../../../../visual-basic/language-reference/modifiers/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="a5a9b-208">Dodaj modyfikator do Oznacz metodę jako *metody asynchronicznej*, jak pokazano w następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
    ```vb  
    Private Async Function GetURLContents(url As String) As Byte()  
    ```  
  
5.  <span data-ttu-id="a5a9b-209">Zwracany typ metody asynchronicznej może być tylko <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a5a9b-210">W języku Visual Basic, metoda musi być `Function` zwracającą `Task` lub `Task(Of T)`, lub metoda musi być `Sub`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="a5a9b-211">Zazwyczaj `Sub` metoda jest używana tylko w asynchronicznej obsłudze zdarzeń, gdzie `Sub` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="a5a9b-212">W pozostałych przypadkach można użyć `Task(T)` Jeśli ukończono metoda ma [zwracać](../../../../visual-basic/language-reference/statements/return-statement.md) instrukcji, która zwraca wartość typu T i używasz `Task` Jeśli ukończono — metoda nie zwraca wartości łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="a5a9b-213">Aby uzyskać więcej informacji, zobacz [Async zwracać typów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="a5a9b-214">Metoda `GetURLContents` zawiera instrukcję return i instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="a5a9b-215">W związku z tym typ zwracany wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="a5a9b-216">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-216">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="a5a9b-217">Zmiana typu zwracanego na `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-217">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="a5a9b-218">Według Konwencji metod asynchronicznych mają nazwy, które kończą się "Async", aby zmienić nazwę metody `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="a5a9b-219">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-219">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="a5a9b-220">Z tymi zmianami kilka konwersji `GetURLContents` do metody asynchronicznej jest pełny.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <a name="SumPageSizes"></a> <span data-ttu-id="a5a9b-221">Aby przekonwertować SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-221">To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="a5a9b-222">Powtórz kroki z poprzedniej procedury `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="a5a9b-223">Najpierw zmień wywołanie `GetURLContents` do wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="a5a9b-224">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="a5a9b-225">Zastosuj `Await` zadania który `GetURLContentsAsync` zwraca uzyskanie bajt tablicy wartości.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="a5a9b-226">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-226">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="a5a9b-227">Poprzednie przypisania Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-227">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
    ```  
  
2.  <span data-ttu-id="a5a9b-228">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="a5a9b-228">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="a5a9b-229">Oznacz metodę z `Async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-229">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="a5a9b-230">Dodaj "Async" w nazwie metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-230">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="a5a9b-231">Brak nie zadań zwracanej zmiennej, T, teraz ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `Return` instrukcji.) Jednak metoda musi zwracać `Task` jako oczekujący.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="a5a9b-232">W związku z tym zmienić typ metody z `Sub` do `Function`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="a5a9b-233">Zwracany typ funkcji jest `Task`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-233">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="a5a9b-234">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-234">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="a5a9b-235">Konwersja typu `SumPageSizes` do `SumPageSizesAsync` została ukończona.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <a name="startButton"></a> <span data-ttu-id="a5a9b-236">Aby przekonwertować startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="a5a9b-236">To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="a5a9b-237">W obsłudze zdarzeń, Zmień nazwę metody wywoływane z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="a5a9b-238">Ponieważ `SumPageSizesAsync` jest to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="a5a9b-239">Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="a5a9b-240">Wywołanie zwraca `Task`, a nie `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-240">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="a5a9b-241">Jak w poprzedniej procedury można przekonwertować wywołanie za pomocą jednej instrukcji lub dwie instrukcje.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="a5a9b-242">Poniższy kod przedstawia tych zmian.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-242">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="a5a9b-243">Aby uniknąć przypadkowego ponownego wprowadzania operacji, dodaj następującą instrukcję, w górnej części `startButton_Click` wyłączyć **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="a5a9b-244">Można ponownie włączyć przycisk na końcu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-244">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="a5a9b-245">Aby uzyskać więcej informacji na temat ponownego rozpoczęcia, zobacz [Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="a5a9b-246">Na koniec należy dodać `Async` modyfikatora w deklaracji, aby program obsługi zdarzeń można zdefiniować oczekiwania `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="a5a9b-247">Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="a5a9b-248">Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi być `Sub` procedury w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="a5a9b-249">Konwersja projektu przetwarzania synchronicznego do asynchronicznego zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <a name="testAsynch"></a> <span data-ttu-id="a5a9b-250">Aby przetestować asynchroniczne rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a5a9b-250">To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="a5a9b-251">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="a5a9b-252">Powinna pojawić się dane wyjściowe podobne dane wyjściowe synchroniczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="a5a9b-253">Jednak zauważyć następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-253">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="a5a9b-254">Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="a5a9b-255">Na przykład oba programy zawierają wiersza w `startButton_Click` który czyści pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="a5a9b-256">W zamierzeniu, wyczyść pole tekstowe między działa, jeśli wybierzesz **Start** przycisk raz drugi, po pojawieniu się jeden zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="a5a9b-257">W to wersja synchroniczna pola tekstowego jest wyczyszczone tuż przed liczniki są wyświetlane po raz drugi, po zakończeniu pliki do pobrania i wątku interfejsu użytkownika będzie mógł wykonywać inne zadania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="a5a9b-258">W wersjach asynchronicznych, pola tekstowego czyści natychmiast po wybraniu **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="a5a9b-259">Przede wszystkim wątku interfejsu użytkownika nie jest blokowane podczas pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="a5a9b-260">Można przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web zliczane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="a5a9b-261">Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisk (x w czerwonym pola w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="a5a9b-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <a name="GetURLContentsAsync"></a> <span data-ttu-id="a5a9b-262">Aby zastąpić metodę GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a5a9b-262">To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="a5a9b-263">.NET Framework 4.5 zapewnia wiele metod asynchronicznych, które są dostępne.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-263">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="a5a9b-264">Jeden z nich, <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, jest tylko dane potrzebne do tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-264">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="a5a9b-265">Możesz użyć jej zamiast `GetURLContentsAsync` metody utworzonego w procedurze wcześniej.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="a5a9b-266">Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-266">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="a5a9b-267">Dodaj następujące oświadczenie na początku metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-267">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="a5a9b-268">W `SumPageSizesAsync,` Zastąp wywołanie Twojej `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="a5a9b-269">Usuń lub komentarz `GetURLContentsAsync` metody zapisane.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="a5a9b-270">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="a5a9b-271">Zachowanie tej wersji projektu powinien zgodne zachowanie opisano procedury "Aby przetestować asynchroniczne rozwiązania", ale z nawet mniejszym wysiłku z Twojej.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <a name="BKMK_CompleteCodeExamples"></a> <span data-ttu-id="a5a9b-272">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5a9b-272">Example</span></span>  
 <span data-ttu-id="a5a9b-273">Poniższy kod zawiera pełny przykład konwersji z synchronicznego do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metody zapisane.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-273">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="a5a9b-274">Należy zauważyć, że silnie podobny oryginalnego synchroniczne rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-274">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
 <span data-ttu-id="a5a9b-275">Poniższy kod zawiera pełny przykład rozwiązania, która używa `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="a5a9b-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
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
            }  
        Return urls  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5a9b-276">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5a9b-276">See Also</span></span>  
 [<span data-ttu-id="a5a9b-277">Przykład Async: Uzyskiwanie dostępu do wskazówki sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)  
 [<span data-ttu-id="a5a9b-278">Await, operator</span><span class="sxs-lookup"><span data-stu-id="a5a9b-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="a5a9b-279">Async</span><span class="sxs-lookup"><span data-stu-id="a5a9b-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)  
 [<span data-ttu-id="a5a9b-280">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="a5a9b-281">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="a5a9b-282">Programowanie asynchroniczne opartego na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-282">Task-based Asynchronous Programming (TAP)</span></span>](http://go.microsoft.com/fwlink/?LinkId=204847)  
 [<span data-ttu-id="a5a9b-283">Porady: rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)  
 [<span data-ttu-id="a5a9b-284">Porady: wiele żądań sieci Web równolegle za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a5a9b-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
