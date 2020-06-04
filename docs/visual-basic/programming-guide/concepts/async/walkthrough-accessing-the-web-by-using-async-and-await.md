---
title: 'Wskazówki: uzyskiwanie dostępu do sieci za pomocą Async i Await'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 41ededd4d4335b78b8d7a33e8fe387c7d632cbee
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400748"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="f383a-102">Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="f383a-103">Można łatwiej pisać programy asynchroniczne i intuicyjnie przy użyciu funkcji asynchronicznych/await.</span><span class="sxs-lookup"><span data-stu-id="f383a-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="f383a-104">Można napisać kod asynchroniczny, który wygląda podobnie do kodu synchronicznego i pozwolić kompilatorowi obsłużyć trudne funkcje wywołania zwrotnego i kontynuację, która zwykle wiąże się z kodem asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="f383a-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="f383a-105">Aby uzyskać więcej informacji o funkcji asynchronicznej, zobacz [programowanie asynchroniczne z Async i Await (Visual Basic)](index.md).</span><span class="sxs-lookup"><span data-stu-id="f383a-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](index.md).</span></span>

<span data-ttu-id="f383a-106">Ten Instruktaż rozpoczyna się od synchronicznej aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów na liście witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f383a-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="f383a-107">Następnie Instruktaż konwertuje aplikację na rozwiązanie asynchroniczne przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="f383a-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="f383a-108">Jeśli nie chcesz samodzielnie kompilować aplikacji, możesz pobrać "przykład Async: uzyskiwanie dostępu do przewodnika sieci Web (C# i Visual Basic)" z [przykładów kodu dewelopera](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="f383a-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="f383a-109">W tym instruktażu wykonasz następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="f383a-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="f383a-110">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="f383a-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="f383a-111">Projektowanie prostego MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="f383a-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="f383a-112">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="f383a-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="f383a-113">Dodaj wymagane instrukcje importów</span><span class="sxs-lookup"><span data-stu-id="f383a-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="f383a-114">Tworzenie aplikacji synchronicznej</span><span class="sxs-lookup"><span data-stu-id="f383a-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="f383a-115">Testowanie rozwiązania synchronicznego</span><span class="sxs-lookup"><span data-stu-id="f383a-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="f383a-116">Konwertuj GetURLContents na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="f383a-117">Konwertuj SumPageSizes na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="f383a-118">Konwertuj startButton_Click na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="f383a-119">Przetestuj rozwiązanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="f383a-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="f383a-120">Zastąp metodę GetURLContentsAsync metodą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f383a-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="f383a-121">Zapoznaj się z sekcją [przykładową](#example) kompletnego przykładu asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="f383a-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f383a-122">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f383a-122">Prerequisites</span></span>

<span data-ttu-id="f383a-123">Na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="f383a-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="f383a-124">Aby uzyskać więcej informacji, zobacz stronę [pliki do pobrania](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f383a-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="f383a-125">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="f383a-125">Create a WPF application</span></span>

1. <span data-ttu-id="f383a-126">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f383a-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="f383a-127">Na pasku menu wybierz **plik**, **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="f383a-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="f383a-128">Zostanie otwarte okno dialogowe **Nowy projekt** .</span><span class="sxs-lookup"><span data-stu-id="f383a-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="f383a-129">W okienku **zainstalowane szablony** wybierz pozycję Visual Basic, a następnie wybierz pozycję **Aplikacja WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="f383a-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="f383a-130">W polu tekstowym **Nazwa** wprowadź `AsyncExampleWPF` , a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="f383a-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="f383a-131">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f383a-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="f383a-132">Projektowanie prostego MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="f383a-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="f383a-133">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="f383a-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="f383a-134">Jeśli okno **Przybornik** nie jest widoczne, otwórz menu **Widok** , a następnie wybierz **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="f383a-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="f383a-135">Dodaj kontrolkę **przycisk** i kontrolkę **TextBox** do okna **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="f383a-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="f383a-136">Zaznacz kontrolkę **TextBox** , a następnie w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f383a-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="f383a-137">Ustaw właściwość **Nazwa** na `resultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="f383a-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="f383a-138">Ustaw właściwość **Height** na 250.</span><span class="sxs-lookup"><span data-stu-id="f383a-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="f383a-139">Ustaw właściwość **Width** na 500.</span><span class="sxs-lookup"><span data-stu-id="f383a-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="f383a-140">Na karcie **tekst** Określ czcionkę o stałej szerokości, taką jak Lucida Console lub globalne.</span><span class="sxs-lookup"><span data-stu-id="f383a-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="f383a-141">Zaznacz kontrolkę **przycisk** , a następnie w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="f383a-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="f383a-142">Ustaw właściwość **Nazwa** na `startButton` .</span><span class="sxs-lookup"><span data-stu-id="f383a-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="f383a-143">Zmień wartość właściwości **zawartości** z **przycisku** na **Rozpocznij**.</span><span class="sxs-lookup"><span data-stu-id="f383a-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="f383a-144">Umieść pole tekstowe i przycisk tak, aby oba elementy pojawiły się w oknie **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="f383a-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="f383a-145">Aby uzyskać więcej informacji na temat projektant XAML WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="f383a-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="f383a-146">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="f383a-146">Add a reference</span></span>

1. <span data-ttu-id="f383a-147">W **Eksplorator rozwiązań**zaznacz nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="f383a-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="f383a-148">Na pasku menu wybierz **projekt**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="f383a-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="f383a-149">Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .</span><span class="sxs-lookup"><span data-stu-id="f383a-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="f383a-150">W górnej części okna dialogowego upewnij się, że projekt ma wartość docelową .NET Framework 4,5 lub wyższą.</span><span class="sxs-lookup"><span data-stu-id="f383a-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="f383a-151">W obszarze **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="f383a-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="f383a-152">Na liście nazw, zaznacz pole wyboru **System .NET. http** .</span><span class="sxs-lookup"><span data-stu-id="f383a-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="f383a-153">Wybierz przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="f383a-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="f383a-154">Dodaj wymagane instrukcje importów</span><span class="sxs-lookup"><span data-stu-id="f383a-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="f383a-155">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="f383a-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="f383a-156">Dodaj następujące `Imports` instrukcje w górnej części pliku kodu, jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="f383a-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="f383a-157">Tworzenie aplikacji synchronicznej</span><span class="sxs-lookup"><span data-stu-id="f383a-157">Create a synchronous application</span></span>

1. <span data-ttu-id="f383a-158">W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk **Start** , aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow. XAML. vb.</span><span class="sxs-lookup"><span data-stu-id="f383a-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="f383a-159">W MainWindow. XAML. vb Skopiuj następujący kod do treści `startButton_Click` :</span><span class="sxs-lookup"><span data-stu-id="f383a-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="f383a-160">Kod wywołuje metodę, która steruje aplikacją, `SumPageSizes` i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click` .</span><span class="sxs-lookup"><span data-stu-id="f383a-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="f383a-161">Kod rozwiązania synchronicznego zawiera następujące cztery metody:</span><span class="sxs-lookup"><span data-stu-id="f383a-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="f383a-162">`SumPageSizes`, który pobiera listę adresów URL strony sieci Web z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` przetwarza każdy adres URL.</span><span class="sxs-lookup"><span data-stu-id="f383a-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="f383a-163">`SetUpURLList`, co umożliwia i zwraca listę adresów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f383a-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="f383a-164">`GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="f383a-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="f383a-165">`DisplayResults`, która wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="f383a-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="f383a-166">Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` obsługi zdarzeń w MainWindow. XAML. vb:</span><span class="sxs-lookup"><span data-stu-id="f383a-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="f383a-167">Testowanie rozwiązania synchronicznego</span><span class="sxs-lookup"><span data-stu-id="f383a-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="f383a-168">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="f383a-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="f383a-169">Powinny pojawić się dane wyjściowe podobne do poniższej listy:</span><span class="sxs-lookup"><span data-stu-id="f383a-169">Output that resembles the following list should appear:</span></span>

    ```console
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

    <span data-ttu-id="f383a-170">Należy zauważyć, że wyświetlanie liczników zajmuje kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="f383a-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="f383a-171">W tym czasie wątek interfejsu użytkownika jest blokowany podczas oczekiwania na pobranie żądanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="f383a-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="f383a-172">W związku z tym nie można przenieść, zmaksymalizować ani zminimalizować, a nawet zamknąć okno wyświetlania po wybraniu przycisku **Rozpocznij** .</span><span class="sxs-lookup"><span data-stu-id="f383a-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="f383a-173">Te działania kończą się niepowodzeniem, dopóki liczba bajtów nie zostanie wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="f383a-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="f383a-174">Jeśli witryna sieci Web nie odpowiada, nie ma informacji o tym, która lokacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="f383a-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="f383a-175">Trudno jest nawet przestać czekać i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="f383a-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="f383a-176">Konwertuj GetURLContents na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="f383a-177">Aby przekonwertować rozwiązanie synchroniczne na rozwiązanie asynchroniczne, najlepszym miejscem do uruchomienia jest, `GetURLContents` ponieważ wywołania <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> metody i do <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> metody są, w których aplikacja uzyskuje dostęp do sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f383a-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="f383a-178">.NET Framework ułatwia konwersję, dostarczając asynchroniczną wersję obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="f383a-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="f383a-179">Aby uzyskać więcej informacji na temat metod, które są używane w programie `GetURLContents` , zobacz <xref:System.Net.WebRequest> .</span><span class="sxs-lookup"><span data-stu-id="f383a-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f383a-180">Po wykonaniu kroków opisanych w tym instruktażu wyświetlane są kilka błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f383a-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="f383a-181">Można je zignorować i kontynuować z przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="f383a-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="f383a-182">Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` od z `GetResponse` do asynchronicznej metody opartej na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="f383a-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="f383a-183">`GetResponseAsync`Zwraca wartość <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="f383a-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f383a-184">W takim przypadku *zmienna zwracająca zadanie*, `TResult` , ma typ <xref:System.Net.WebResponse> .</span><span class="sxs-lookup"><span data-stu-id="f383a-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="f383a-185">Zadanie to obietnica do utworzenia rzeczywistego `WebResponse` obiektu po pobraniu żądanych danych, a zadanie zostało wykonane w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="f383a-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="f383a-186">Aby pobrać `WebResponse` wartość z zadania, Zastosuj operator [await](../../../language-reference/operators/await-operator.md) do wywołania `GetResponseAsync` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f383a-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="f383a-187">`Await`Operator wstrzymuje wykonywanie bieżącej metody, `GetURLContents` dopóki nie zostanie zakończone oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="f383a-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="f383a-188">W międzyczasie formant powraca do obiektu wywołującego bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="f383a-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="f383a-189">W tym przykładzie bieżąca metoda to `GetURLContents` , a obiekt wywołujący ma wartość `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="f383a-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="f383a-190">Po zakończeniu zadania, `WebResponse` obiekt przyrzeczonych jest tworzony jako wartość oczekującego zadania i przypisany do zmiennej `response` .</span><span class="sxs-lookup"><span data-stu-id="f383a-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="f383a-191">Poprzednią instrukcję można podzielić na dwie następujące instrukcje, aby wyjaśnić, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="f383a-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="f383a-192">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>` .</span><span class="sxs-lookup"><span data-stu-id="f383a-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="f383a-193">Następnie do `Await` zadania zostanie zastosowany operator, aby pobrać `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="f383a-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="f383a-194">Jeśli metoda async działa tak, aby nie zależała od ukończenia zadania, Metoda może kontynuować działanie między tymi dwiema instrukcjami po wywołaniu metody asynchronicznej i przed zastosowaniem operatora await.</span><span class="sxs-lookup"><span data-stu-id="f383a-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="f383a-195">Aby zapoznać się z przykładami, zobacz [How to: równoległe wykonywanie wielu żądań sieci Web za pomocą Async i Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [instrukcje: rozszerzona instrukcja Async przy użyciu Task. WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="f383a-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="f383a-196">Ze względu na to, że dodano `Await` operator w poprzednim kroku, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f383a-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="f383a-197">Operatora można używać tylko w metodach, które są oznaczone modyfikatorem [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f383a-197">The operator can be used only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f383a-198">Zignoruj błąd podczas powtarzania kroków konwersji, aby zastąpić wywołanie do `CopyTo` wywołania `CopyToAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="f383a-199">Zmień nazwę metody, która jest wywoływana do <xref:System.IO.Stream.CopyToAsync%2A> .</span><span class="sxs-lookup"><span data-stu-id="f383a-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="f383a-200">`CopyTo`Metoda or `CopyToAsync` Kopiuje bajty do argumentu, `content` i nie zwraca wartości znaczącej.</span><span class="sxs-lookup"><span data-stu-id="f383a-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="f383a-201">W wersji synchronicznej wywołanie `CopyTo` jest prostą instrukcją, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="f383a-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="f383a-202">Asynchroniczna wersja, `CopyToAsync` , zwraca <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="f383a-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="f383a-203">Zadanie działa jak "Task (void)" i umożliwia oczekiwanie metody.</span><span class="sxs-lookup"><span data-stu-id="f383a-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="f383a-204">Zastosuj `Await` lub `await` do wywołania `CopyToAsync` , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f383a-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="f383a-205">Poprzednia instrukcja skraca następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="f383a-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="f383a-206">Wszystkie te, które pozostały do wykonania w programie, `GetURLContents` mają na celu dostosowanie sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="f383a-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="f383a-207">Operatora można używać `Await` tylko w metodach, które są oznaczone modyfikatorem [Async](../../../language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f383a-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="f383a-208">Dodaj modyfikator, aby oznaczyć metodę jako *metodę asynchroniczną*, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="f383a-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="f383a-209">Zwracany typ metody asynchronicznej może być tylko <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="f383a-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f383a-210">W Visual Basic Metoda musi być, `Function` która zwraca `Task` lub `Task(Of T)` , lub metoda musi być `Sub` .</span><span class="sxs-lookup"><span data-stu-id="f383a-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="f383a-211">Zazwyczaj `Sub` Metoda jest używana tylko w obsłudze zdarzeń asynchronicznych, gdzie `Sub` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="f383a-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="f383a-212">W innych przypadkach należy użyć, `Task(T)` Jeśli metoda ukończona zawiera instrukcję [Return](../../../language-reference/statements/return-statement.md) , która zwraca wartość typu T, i jest używana, `Task` Jeśli metoda zakończona nie zwraca wartości znaczącej.</span><span class="sxs-lookup"><span data-stu-id="f383a-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="f383a-213">Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracane (Visual Basic)](async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f383a-213">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>

    <span data-ttu-id="f383a-214">Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="f383a-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="f383a-215">W związku z tym zwracanym typem wersji asynchronicznej jest zadanie (T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="f383a-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="f383a-216">Wprowadź następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="f383a-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="f383a-217">Zmień zwracany typ na `Task(Of Byte())` .</span><span class="sxs-lookup"><span data-stu-id="f383a-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="f383a-218">Zgodnie z Konwencją metody asynchroniczne mają nazwy kończące się na "Async", więc Zmień nazwę metody `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="f383a-219">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="f383a-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="f383a-220">Po wprowadzeniu tych zmian konwersja `GetURLContents` do metody asynchronicznej zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="f383a-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="f383a-221">Konwertuj SumPageSizes na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="f383a-222">Powtórz kroki opisane w poprzedniej procedurze dla programu `SumPageSizes` .</span><span class="sxs-lookup"><span data-stu-id="f383a-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="f383a-223">Najpierw Zmień wywołanie na `GetURLContents` wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="f383a-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="f383a-224">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do, jeśli jeszcze tego nie zrobiono `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="f383a-225">Zastosuj `Await` do zadania, które `GetURLContentsAsync` zwraca, aby uzyskać wartość tablicy bajtowej.</span><span class="sxs-lookup"><span data-stu-id="f383a-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="f383a-226">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="f383a-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="f383a-227">Poprzednie przypisanie skraca dwa następujące wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="f383a-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="f383a-228">Wprowadź następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="f383a-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="f383a-229">Oznacz metodę za pomocą `Async` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f383a-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="f383a-230">Dodaj wartość "Async" do nazwy metody.</span><span class="sxs-lookup"><span data-stu-id="f383a-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="f383a-231">Brak zmiennej zwracanej do zadania, T, ten czas `SumPageSizesAsync` nie zwraca wartości dla T. (metoda nie ma żadnej `Return` instrukcji). Jednak metoda musi zwrócić element, `Task` Aby można było oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="f383a-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="f383a-232">W związku z tym Zmień typ metody z `Sub` na `Function` .</span><span class="sxs-lookup"><span data-stu-id="f383a-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="f383a-233">Zwracany typ funkcji to `Task` .</span><span class="sxs-lookup"><span data-stu-id="f383a-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="f383a-234">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="f383a-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="f383a-235">Konwersja do programu `SumPageSizes` `SumPageSizesAsync` została zakończona.</span><span class="sxs-lookup"><span data-stu-id="f383a-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="f383a-236">Konwertuj startButton_Click na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="f383a-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="f383a-237">W programie obsługi zdarzeń Zmień nazwę wywołanej metody z `SumPageSizes` na `SumPageSizesAsync` , jeśli jeszcze nie zostało to zrobione.</span><span class="sxs-lookup"><span data-stu-id="f383a-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="f383a-238">Ponieważ `SumPageSizesAsync` jest to Metoda asynchroniczna, Zmień kod w programie obsługi zdarzeń, aby oczekiwać na wynik.</span><span class="sxs-lookup"><span data-stu-id="f383a-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="f383a-239">Wywołanie w celu `SumPageSizesAsync` odbicia duplikatu wywołania `CopyToAsync` w `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="f383a-240">Wywołanie zwraca, a `Task` nie a `Task(T)` .</span><span class="sxs-lookup"><span data-stu-id="f383a-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="f383a-241">Jak w poprzednich procedurach, można skonwertować wywołanie przy użyciu jednej instrukcji lub dwóch instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f383a-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="f383a-242">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="f383a-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="f383a-243">Aby zapobiec przypadkowemu ponownemu wprowadzeniu operacji, Dodaj następującą instrukcję w górnej części, `startButton_Click` Aby wyłączyć przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="f383a-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="f383a-244">Przycisk można ponownie włączyć na końcu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f383a-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="f383a-245">Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)](handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f383a-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="f383a-246">Na koniec Dodaj `Async` modyfikator do deklaracji, aby program obsługi zdarzeń mógł oczekiwać `SumPagSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="f383a-247">Zazwyczaj nazwy programów obsługi zdarzeń nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="f383a-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="f383a-248">Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń muszą być `Sub` procedurami w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f383a-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="f383a-249">Konwersja projektu z synchronicznego na przetwarzanie asynchroniczne zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="f383a-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="f383a-250">Przetestuj rozwiązanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="f383a-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="f383a-251">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="f383a-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="f383a-252">Powinny pojawić się dane wyjściowe podobne do danych wyjściowych rozwiązania synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="f383a-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="f383a-253">Jednak Zwróć uwagę na następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="f383a-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="f383a-254">Wyniki nie są wykonywane w tym samym czasie po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="f383a-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="f383a-255">Na przykład oba programy zawierają wiersz `startButton_Click` , który czyści pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="f383a-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="f383a-256">Celem jest wyczyszczenie pola tekstowego między uruchomieniami w przypadku wybrania przycisku **Rozpocznij** po raz drugi, po wyświetleniu jednego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="f383a-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="f383a-257">W wersji synchronicznej, pole tekstowe jest czyszczone tuż przed wyświetleniem liczby po raz drugi, po ukończeniu pobierania, a wątek interfejsu użytkownika jest bezpłatny, aby wykonać inne czynności.</span><span class="sxs-lookup"><span data-stu-id="f383a-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="f383a-258">W wersji asynchronicznej, pole tekstowe czyści natychmiast po wybraniu przycisku **Rozpocznij** .</span><span class="sxs-lookup"><span data-stu-id="f383a-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="f383a-259">Co najważniejsze, wątek interfejsu użytkownika nie jest blokowany podczas pobierania.</span><span class="sxs-lookup"><span data-stu-id="f383a-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="f383a-260">Możesz przenosić lub zmieniać rozmiar okna, gdy zasoby sieci Web są pobierane, zliczane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="f383a-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="f383a-261">Jeśli jedna z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając przycisk **Zamknij** (x w czerwono w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="f383a-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="f383a-262">Zastąp metodę GetURLContentsAsync metodą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f383a-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="f383a-263">.NET Framework zawiera wiele metod asynchronicznych, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="f383a-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="f383a-264">Jednym z nich jest <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> Metoda, która jest tylko potrzebne do tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="f383a-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="f383a-265">Można jej użyć zamiast `GetURLContentsAsync` metody utworzonej we wcześniejszej procedurze.</span><span class="sxs-lookup"><span data-stu-id="f383a-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="f383a-266">Pierwszym krokiem jest utworzenie <xref:System.Net.Http.HttpClient> obiektu w `SumPageSizesAsync` metodzie.</span><span class="sxs-lookup"><span data-stu-id="f383a-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="f383a-267">Dodaj następującą deklarację na początku metody.</span><span class="sxs-lookup"><span data-stu-id="f383a-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="f383a-268">`SumPageSizesAsync,`Zastąp wywołanie `GetURLContentsAsync` metody wywołaniem metody `HttpClient` .</span><span class="sxs-lookup"><span data-stu-id="f383a-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="f383a-269">Usuń lub Skomentuj `GetURLContentsAsync` metodę, która została zapisana.</span><span class="sxs-lookup"><span data-stu-id="f383a-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="f383a-270">Wybierz klawisz F5, aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="f383a-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="f383a-271">Zachowanie tej wersji projektu powinno być zgodne z zachowaniem, że procedura "Aby przetestować rozwiązanie asynchroniczne" opisuje, ale nawet mniej wysiłku od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f383a-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="f383a-272">Przykład</span><span class="sxs-lookup"><span data-stu-id="f383a-272">Example</span></span>

<span data-ttu-id="f383a-273">Poniżej znajduje się pełny przykład przekonwertowanego rozwiązania asynchronicznego, które używa metody asynchronicznej `GetURLContentsAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="f383a-274">Należy zauważyć, że silnie przypomina oryginalne, synchroniczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="f383a-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

<span data-ttu-id="f383a-275">Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody, `GetByteArrayAsync` .</span><span class="sxs-lookup"><span data-stu-id="f383a-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

        ' Two-step async call.
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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="f383a-276">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f383a-276">See also</span></span>

- [<span data-ttu-id="f383a-277">Przykład asynchroniczny: uzyskiwanie dostępu do przewodnika sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="f383a-278">Operator await</span><span class="sxs-lookup"><span data-stu-id="f383a-278">Await Operator</span></span>](../../../language-reference/operators/await-operator.md)
- [<span data-ttu-id="f383a-279">Asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="f383a-279">Async</span></span>](../../../language-reference/modifiers/async.md)
- [<span data-ttu-id="f383a-280">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="f383a-281">Asynchroniczne typy zwracane (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-281">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="f383a-282">Programowanie asynchroniczne oparte na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="f383a-282">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="f383a-283">Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="f383a-284">Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f383a-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
