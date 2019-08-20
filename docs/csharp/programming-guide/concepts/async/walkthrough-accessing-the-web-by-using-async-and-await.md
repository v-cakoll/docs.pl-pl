---
title: 'Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 986f3985783c6ae941d437fe557998f67557f5af
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595511"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="ad06d-102">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()</span><span class="sxs-lookup"><span data-stu-id="ad06d-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="ad06d-103">Można łatwiej pisać programy asynchroniczne i intuicyjnie przy użyciu funkcji asynchronicznych/await.</span><span class="sxs-lookup"><span data-stu-id="ad06d-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="ad06d-104">Można napisać kod asynchroniczny, który wygląda podobnie do kodu synchronicznego i pozwolić kompilatorowi obsłużyć trudne funkcje wywołania zwrotnego i kontynuację, która zwykle wiąże się z kodem asynchronicznym.</span><span class="sxs-lookup"><span data-stu-id="ad06d-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="ad06d-105">Aby uzyskać więcej informacji o funkcji asynchronicznej, zobacz [programowanie asynchroniczne z Async i awaitC#()](./index.md).</span><span class="sxs-lookup"><span data-stu-id="ad06d-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="ad06d-106">Ten Instruktaż rozpoczyna się od synchronicznej aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów na liście witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad06d-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="ad06d-107">Następnie Instruktaż konwertuje aplikację na rozwiązanie asynchroniczne przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="ad06d-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="ad06d-108">Jeśli nie chcesz samodzielnie kompilować aplikacji, możesz pobrać [próbkę asynchroniczną: Uzyskiwanie dostępu do przewodnika sieciC# Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)(i Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ad06d-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="ad06d-109">Aby uruchomić przykłady, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="ad06d-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="ad06d-110">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="ad06d-110">Create a WPF application</span></span>

1. <span data-ttu-id="ad06d-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ad06d-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="ad06d-112">Na pasku menu wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="ad06d-113">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ad06d-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ad06d-114">W okienku **zainstalowane szablony** wybierz pozycję Wizualizacja C#, a następnie wybierz pozycję **Aplikacja WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="ad06d-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="ad06d-115">W polu tekstowym **Nazwa** wprowadź `AsyncExampleWPF`, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="ad06d-116">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="ad06d-117">Projektowanie prostego MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="ad06d-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="ad06d-118">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="ad06d-119">Jeśli okno **Przybornik** nie jest widoczne, otwórz menu **Widok** , a następnie wybierz **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="ad06d-120">Dodaj kontrolkę **przycisk** i kontrolkę **TextBox** do okna **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="ad06d-121">Zaznacz kontrolkę **TextBox** , a następnie w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ad06d-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="ad06d-122">Ustaw właściwość **Nazwa** na `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="ad06d-123">Ustaw właściwość **Height** na 250.</span><span class="sxs-lookup"><span data-stu-id="ad06d-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="ad06d-124">Ustaw właściwość **Width** na 500.</span><span class="sxs-lookup"><span data-stu-id="ad06d-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="ad06d-125">Na karcie **tekst** Określ czcionkę o stałej szerokości, taką jak Lucida Console lub globalne.</span><span class="sxs-lookup"><span data-stu-id="ad06d-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="ad06d-126">Zaznacz kontrolkę **przycisk** , a następnie w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ad06d-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="ad06d-127">Ustaw właściwość **Nazwa** na `startButton`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="ad06d-128">Zmień wartość właściwości **zawartości** z **przycisku** na **Rozpocznij**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="ad06d-129">Umieść pole tekstowe i przycisk tak, aby oba elementy pojawiły się w oknie **MainWindow** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="ad06d-130">Aby uzyskać więcej informacji na temat projektant XAML WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu Projektant XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ad06d-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="ad06d-131">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="ad06d-131">Add a reference</span></span>

1. <span data-ttu-id="ad06d-132">W **Eksplorator rozwiązań**zaznacz nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="ad06d-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="ad06d-133">Na pasku menu wybierz kolejno pozycje **projekt** > **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="ad06d-134">Zostanie wyświetlone okno dialogowe **Menedżer odwołań** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="ad06d-135">W górnej części okna dialogowego upewnij się, że projekt ma wartość docelową .NET Framework 4,5 lub wyższą.</span><span class="sxs-lookup"><span data-stu-id="ad06d-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="ad06d-136">W kategorii **zestawy** wybierz pozycję **Struktura** , jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="ad06d-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="ad06d-137">Na liście nazw, zaznacz pole wyboru **System .NET. http** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="ad06d-138">Wybierz przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="ad06d-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="ad06d-139">Dodaj wymagane dyrektywy using</span><span class="sxs-lookup"><span data-stu-id="ad06d-139">Add necessary using directives</span></span>

1. <span data-ttu-id="ad06d-140">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow.XAML.cs, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="ad06d-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="ad06d-141">Dodaj następujące `using` dyrektywy w górnej części pliku kodu, jeśli jeszcze nie istnieją.</span><span class="sxs-lookup"><span data-stu-id="ad06d-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="ad06d-142">Tworzenie aplikacji synchronicznej</span><span class="sxs-lookup"><span data-stu-id="ad06d-142">Create a synchronous app</span></span>

1. <span data-ttu-id="ad06d-143">W oknie projekt MainWindow. XAML kliknij dwukrotnie przycisk **Start** , aby utworzyć `startButton_Click` obsługę zdarzeń w MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="ad06d-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="ad06d-144">W MainWindow.xaml.cs Skopiuj następujący kod do treści `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="ad06d-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="ad06d-145">Kod wywołuje metodę, która steruje aplikacją, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do. `startButton_Click`</span><span class="sxs-lookup"><span data-stu-id="ad06d-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="ad06d-146">Kod rozwiązania synchronicznego zawiera następujące cztery metody:</span><span class="sxs-lookup"><span data-stu-id="ad06d-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="ad06d-147">`SumPageSizes`, który pobiera listę adresów URL strony sieci Web `SetUpURLList` z, a `GetURLContents` następnie `DisplayResults` wywołuje i przetwarza każdy adres URL.</span><span class="sxs-lookup"><span data-stu-id="ad06d-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="ad06d-148">`SetUpURLList`, co umożliwia i zwraca listę adresów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="ad06d-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="ad06d-149">`GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="ad06d-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="ad06d-150">`DisplayResults`, która wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="ad06d-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="ad06d-151">Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` obsługi zdarzeń w MainWindow.XAML.cs:</span><span class="sxs-lookup"><span data-stu-id="ad06d-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
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
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="ad06d-152">Testowanie rozwiązania synchronicznego</span><span class="sxs-lookup"><span data-stu-id="ad06d-152">Test the synchronous solution</span></span>

<span data-ttu-id="ad06d-153">Wybierz klawisz **F5** , aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="ad06d-154">Powinny pojawić się dane wyjściowe podobne do poniższej listy:</span><span class="sxs-lookup"><span data-stu-id="ad06d-154">Output that resembles the following list should appear:</span></span>

```text
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

<span data-ttu-id="ad06d-155">Należy zauważyć, że wyświetlanie liczników zajmuje kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="ad06d-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="ad06d-156">W tym czasie wątek interfejsu użytkownika jest blokowany podczas oczekiwania na pobranie żądanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="ad06d-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="ad06d-157">W związku z tym nie można przenieść, zmaksymalizować ani zminimalizować, a nawet zamknąć okno wyświetlania po wybraniu przycisku **Rozpocznij** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="ad06d-158">Te działania kończą się niepowodzeniem, dopóki liczba bajtów nie zostanie wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="ad06d-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="ad06d-159">Jeśli witryna sieci Web nie odpowiada, nie ma informacji o tym, która lokacja nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="ad06d-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="ad06d-160">Trudno jest nawet przestać czekać i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="ad06d-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="ad06d-161">Konwertuj GetURLContents na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="ad06d-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="ad06d-162">Aby przekonwertować rozwiązanie synchroniczne na rozwiązanie asynchroniczne, najlepszym miejscem do uruchomienia jest, ponieważ wywołania `GetURLContents` <xref:System.Net.HttpWebRequest> metody <xref:System.Net.HttpWebRequest.GetResponse%2A> i do <xref:System.IO.Stream> metody <xref:System.IO.Stream.CopyTo%2A> są, w których aplikacja uzyskuje dostęp do sieci Web. .</span><span class="sxs-lookup"><span data-stu-id="ad06d-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="ad06d-163">.NET Framework ułatwia konwersję, dostarczając asynchroniczną wersję obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="ad06d-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="ad06d-164">Aby uzyskać więcej informacji na temat metod, które są `GetURLContents`używane w <xref:System.Net.WebRequest>programie, zobacz.</span><span class="sxs-lookup"><span data-stu-id="ad06d-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ad06d-165">Po wykonaniu kroków opisanych w tym instruktażu wyświetlane są kilka błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad06d-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="ad06d-166">Można je zignorować i kontynuować z przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="ad06d-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="ad06d-167">Zmień metodę, która jest wywoływana w trzecim wierszu `GetURLContents` od z `GetResponse` do asynchronicznej metody opartej na <xref:System.Net.WebRequest.GetResponseAsync%2A> zadaniach.</span><span class="sxs-lookup"><span data-stu-id="ad06d-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="ad06d-168">`GetResponseAsync`Zwraca wartość <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="ad06d-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ad06d-169">W takim przypadku `TResult` *zmienna zwracająca zadanie*,, ma typ. <xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="ad06d-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="ad06d-170">Zadanie to obietnica do utworzenia rzeczywistego `WebResponse` obiektu po pobraniu żądanych danych, a zadanie zostało wykonane w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="ad06d-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="ad06d-171">Aby pobrać `WebResponse` wartość z zadania, Zastosuj operator [await](../../../language-reference/keywords/await.md) `GetResponseAsync`do wywołania, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad06d-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="ad06d-172">Operator wstrzymuje wykonywanie bieżącej `GetURLContents`metody, dopóki nie zostanie zakończone oczekiwane zadanie. `await`</span><span class="sxs-lookup"><span data-stu-id="ad06d-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="ad06d-173">W międzyczasie formant powraca do obiektu wywołującego bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="ad06d-174">W tym przykładzie bieżąca metoda to `GetURLContents`, a obiekt wywołujący ma `SumPageSizes`wartość.</span><span class="sxs-lookup"><span data-stu-id="ad06d-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="ad06d-175">Po zakończeniu zadania, obiekt przyrzeczonych `WebResponse` jest tworzony jako wartość oczekującego zadania i przypisany do zmiennej. `response`</span><span class="sxs-lookup"><span data-stu-id="ad06d-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="ad06d-176">Poprzednią instrukcję można podzielić na dwie następujące instrukcje, aby wyjaśnić, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="ad06d-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="ad06d-177">Wywołanie `webReq.GetResponseAsync` zwraca`Task(Of WebResponse)` lub .`Task<WebResponse>`</span><span class="sxs-lookup"><span data-stu-id="ad06d-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="ad06d-178">Następnie do zadania zostanie zastosowany operator await, aby pobrać `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="ad06d-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="ad06d-179">Jeśli metoda async działa tak, aby nie zależała od ukończenia zadania, Metoda może kontynuować działanie między tymi dwiema instrukcjami po wywołaniu metody asynchronicznej i przed `await` zastosowaniem operatora.</span><span class="sxs-lookup"><span data-stu-id="ad06d-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="ad06d-180">Aby zapoznać się z [przykładami, zobacz How to: Równoległe wykonywanie wielu żądań sieci Web za pomocą Async i awaitC#(](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ) [i instrukcje: Rozwiń Przewodnik asynchroniczny za pomocą polecenia Task. WhenAllC#(](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)).</span><span class="sxs-lookup"><span data-stu-id="ad06d-180">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="ad06d-181">Ze względu na `await` to, że dodano operator w poprzednim kroku, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ad06d-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="ad06d-182">Operatora można używać tylko w metodach, które są oznaczone modyfikatorem [Async](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ad06d-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ad06d-183">Zignoruj błąd podczas powtarzania kroków konwersji, aby zastąpić wywołanie `CopyTo` do `CopyToAsync`wywołania.</span><span class="sxs-lookup"><span data-stu-id="ad06d-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="ad06d-184">Zmień nazwę metody, która jest wywoływana do <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad06d-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="ad06d-185">Metoda `CopyTo` `content`or `CopyToAsync` Kopiuje bajty do argumentu, i nie zwraca wartości znaczącej.</span><span class="sxs-lookup"><span data-stu-id="ad06d-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="ad06d-186">W wersji synchronicznej wywołanie `CopyTo` jest prostą instrukcją, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="ad06d-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="ad06d-187">Asynchroniczna wersja, `CopyToAsync`, <xref:System.Threading.Tasks.Task>zwraca.</span><span class="sxs-lookup"><span data-stu-id="ad06d-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="ad06d-188">Zadanie działa jak "Task (void)" i umożliwia oczekiwanie metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="ad06d-189">Zastosuj `Await` lub `await` do wywołania`CopyToAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad06d-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="ad06d-190">Poprzednia instrukcja skraca następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="ad06d-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="ad06d-191">Wszystkie te, które pozostały `GetURLContents` do wykonania w programie, mają na celu dostosowanie sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="ad06d-192">`await` Operatora można używać tylko w metodach, które są oznaczone modyfikatorem [Async](../../../language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ad06d-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ad06d-193">Dodaj modyfikator, aby oznaczyć metodę jako *metodę asynchroniczną*, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="ad06d-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="ad06d-194">Zwracanym <xref:System.Threading.Tasks.Task>typem metody asynchronicznej może być tylko, <xref:System.Threading.Tasks.Task%601>, lub `void` w. C#</span><span class="sxs-lookup"><span data-stu-id="ad06d-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="ad06d-195">Zazwyczaj zwracany typ `void` jest używany tylko w asynchronicznym obsłudze zdarzeń, gdzie `void` jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="ad06d-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="ad06d-196">W innych przypadkach należy użyć `Task(T)` , jeśli metoda ukończona zawiera instrukcję [Return](../../../language-reference/keywords/return.md) , która zwraca wartość typu T, i jest używana `Task` , jeśli metoda zakończona nie zwraca wartości znaczącej.</span><span class="sxs-lookup"><span data-stu-id="ad06d-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="ad06d-197">Typ `Task` zwracany można traktować jako znaczenie "zadanie (void)".</span><span class="sxs-lookup"><span data-stu-id="ad06d-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="ad06d-198">Aby uzyskać więcej informacji, zobacz [asynchroniczne typy zwracaneC#()](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ad06d-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="ad06d-199">Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="ad06d-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="ad06d-200">W związku z tym zwracanym typem wersji asynchronicznej jest zadanie (T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="ad06d-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="ad06d-201">Wprowadź następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="ad06d-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="ad06d-202">Zmień zwracany typ na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="ad06d-203">Zgodnie z Konwencją metody asynchroniczne mają nazwy kończące się na "Async", więc Zmień `GetURLContentsAsync`nazwę metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="ad06d-204">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad06d-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="ad06d-205">Po wprowadzeniu tych zmian konwersja `GetURLContents` do metody asynchronicznej zostanie zakończona.</span><span class="sxs-lookup"><span data-stu-id="ad06d-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="ad06d-206">Konwertuj SumPageSizes na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="ad06d-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="ad06d-207">Powtórz kroki opisane w poprzedniej procedurze dla programu `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="ad06d-208">Najpierw Zmień wywołanie `GetURLContents` na wywołanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="ad06d-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="ad06d-209">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="ad06d-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="ad06d-210">Zastosuj `await` do zadania, które `GetURLContentsAsync` zwraca, aby uzyskać wartość tablicy bajtowej.</span><span class="sxs-lookup"><span data-stu-id="ad06d-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="ad06d-211">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad06d-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="ad06d-212">Poprzednie przypisanie skraca dwa następujące wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="ad06d-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="ad06d-213">Wprowadź następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="ad06d-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="ad06d-214">Oznacz metodę za pomocą `async` modyfikatora.</span><span class="sxs-lookup"><span data-stu-id="ad06d-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="ad06d-215">Dodaj wartość "Async" do nazwy metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="ad06d-216">Brak zmiennej zwracanej zadania, T, ten czas, ponieważ `SumPageSizesAsync` nie zwraca wartości dla T. (Metoda nie ma żadnej `return` instrukcji). Jednak metoda musi zwrócić element `Task` , aby można było oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="ad06d-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="ad06d-217">W związku z tym należy zmienić zwracany typ metody z `void` do `Task`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="ad06d-218">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad06d-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="ad06d-219">Konwersja do `SumPageSizes` `SumPageSizesAsync` programu została zakończona.</span><span class="sxs-lookup"><span data-stu-id="ad06d-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="ad06d-220">Konwertuj startButton_Click na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="ad06d-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="ad06d-221">W programie obsługi zdarzeń Zmień nazwę wywołanej metody z `SumPageSizes` na `SumPageSizesAsync`, jeśli jeszcze nie zostało to zrobione.</span><span class="sxs-lookup"><span data-stu-id="ad06d-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="ad06d-222">Ponieważ `SumPageSizesAsync` jest to Metoda asynchroniczna, Zmień kod w programie obsługi zdarzeń, aby oczekiwać na wynik.</span><span class="sxs-lookup"><span data-stu-id="ad06d-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="ad06d-223">Wywołanie `CopyToAsync` w celu `SumPageSizesAsync` odbicia duplikatu wywołania `GetURLContentsAsync`w.</span><span class="sxs-lookup"><span data-stu-id="ad06d-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="ad06d-224">Wywołanie zwraca, a `Task`nie a. `Task(T)`</span><span class="sxs-lookup"><span data-stu-id="ad06d-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="ad06d-225">Jak w poprzednich procedurach, można skonwertować wywołanie przy użyciu jednej instrukcji lub dwóch instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad06d-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="ad06d-226">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="ad06d-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="ad06d-227">Aby zapobiec przypadkowemu ponownemu wprowadzeniu operacji, Dodaj następującą instrukcję w górnej części `startButton_Click` , aby wyłączyć przycisk **Uruchom** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="ad06d-228">Przycisk można ponownie włączyć na końcu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="ad06d-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="ad06d-229">Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [Obsługa współużytkowania wątkowości w aplikacjachC#asynchronicznych ()](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="ad06d-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="ad06d-230">Na koniec Dodaj `async` modyfikator do deklaracji, aby program obsługi zdarzeń mógł oczekiwać `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="ad06d-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="ad06d-231">Zazwyczaj nazwy programów obsługi zdarzeń nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="ad06d-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="ad06d-232">Zwracany typ nie jest zmieniany `Task` na ponieważ procedury obsługi zdarzeń muszą `void`zwracać.</span><span class="sxs-lookup"><span data-stu-id="ad06d-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="ad06d-233">Konwersja projektu z synchronicznego na przetwarzanie asynchroniczne zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="ad06d-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="ad06d-234">Przetestuj rozwiązanie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="ad06d-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="ad06d-235">Wybierz klawisz **F5** , aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="ad06d-236">Powinny pojawić się dane wyjściowe podobne do danych wyjściowych rozwiązania synchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ad06d-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="ad06d-237">Jednak Zwróć uwagę na następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="ad06d-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="ad06d-238">Wyniki nie są wykonywane w tym samym czasie po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ad06d-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="ad06d-239">Na przykład oba programy zawierają wiersz `startButton_Click` , który czyści pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="ad06d-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="ad06d-240">Celem jest wyczyszczenie pola tekstowego między uruchomieniami w przypadku wybrania przycisku **Rozpocznij** po raz drugi, po wyświetleniu jednego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="ad06d-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="ad06d-241">W wersji synchronicznej, pole tekstowe jest czyszczone tuż przed wyświetleniem liczby po raz drugi, po ukończeniu pobierania, a wątek interfejsu użytkownika jest bezpłatny, aby wykonać inne czynności.</span><span class="sxs-lookup"><span data-stu-id="ad06d-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="ad06d-242">W wersji asynchronicznej, pole tekstowe czyści natychmiast po wybraniu przycisku **Rozpocznij** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="ad06d-243">Co najważniejsze, wątek interfejsu użytkownika nie jest blokowany podczas pobierania.</span><span class="sxs-lookup"><span data-stu-id="ad06d-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="ad06d-244">Możesz przenosić lub zmieniać rozmiar okna, gdy zasoby sieci Web są pobierane, zliczane i wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="ad06d-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="ad06d-245">Jeśli jedna z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając przycisk **Zamknij** (x w czerwono w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="ad06d-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="ad06d-246">Zastąp metodę GetURLContentsAsync metodą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ad06d-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="ad06d-247">.NET Framework 4,5 zawiera wiele metod asynchronicznych, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="ad06d-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="ad06d-248">Jednym z nich <xref:System.Net.Http.HttpClient> jest metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, która jest tylko potrzebne do tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="ad06d-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="ad06d-249">Można jej użyć zamiast `GetURLContentsAsync` metody utworzonej we wcześniejszej procedurze.</span><span class="sxs-lookup"><span data-stu-id="ad06d-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="ad06d-250">Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie. `SumPageSizesAsync`</span><span class="sxs-lookup"><span data-stu-id="ad06d-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="ad06d-251">Dodaj następującą deklarację na początku metody.</span><span class="sxs-lookup"><span data-stu-id="ad06d-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="ad06d-252">Zastąp wywołanie `GetURLContentsAsync` metody wywołaniem `HttpClient` metody. `SumPageSizesAsync,`</span><span class="sxs-lookup"><span data-stu-id="ad06d-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="ad06d-253">Usuń lub Skomentuj `GetURLContentsAsync` metodę, która została zapisana.</span><span class="sxs-lookup"><span data-stu-id="ad06d-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="ad06d-254">Wybierz klawisz **F5** , aby uruchomić program, a następnie wybierz przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="ad06d-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="ad06d-255">Zachowanie tej wersji projektu powinno być zgodne z zachowaniem, że procedura "Aby przetestować rozwiązanie asynchroniczne" opisuje, ale nawet mniej wysiłku od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ad06d-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="ad06d-256">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="ad06d-256">Example code</span></span>

<span data-ttu-id="ad06d-257">Poniższy kod zawiera pełny przykład konwersji z synchronicznego na asynchroniczne rozwiązanie przy użyciu metody asynchronicznej `GetURLContentsAsync` , która została zapisana.</span><span class="sxs-lookup"><span data-stu-id="ad06d-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="ad06d-258">Należy zauważyć, że silnie przypomina oryginalne, synchroniczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="ad06d-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

<span data-ttu-id="ad06d-259">Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody,. `GetByteArrayAsync`</span><span class="sxs-lookup"><span data-stu-id="ad06d-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ad06d-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad06d-260">See also</span></span>

- [<span data-ttu-id="ad06d-261">Przykład asynchroniczny: Uzyskiwanie dostępu do przewodnika sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ad06d-261">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="ad06d-262">async</span><span class="sxs-lookup"><span data-stu-id="ad06d-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="ad06d-263">await</span><span class="sxs-lookup"><span data-stu-id="ad06d-263">await</span></span>](../../../language-reference/keywords/await.md)
- [<span data-ttu-id="ad06d-264">Programowanie asynchroniczne z Async i Await (C#)</span><span class="sxs-lookup"><span data-stu-id="ad06d-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="ad06d-265">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="ad06d-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="ad06d-266">Programowanie asynchroniczne oparte na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="ad06d-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="ad06d-267">Instrukcje: Rozwiń Przewodnik asynchroniczny za pomocą zadania. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="ad06d-267">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="ad06d-268">Instrukcje: Równoległe wykonywanie wielu żądań sieci Web za pomocą Async i awaitC#()</span><span class="sxs-lookup"><span data-stu-id="ad06d-268">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
