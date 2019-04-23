---
title: 'Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: eac19135c2506fdd324a2f425c23548690189ed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59306732"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="d2ad1-102">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="d2ad1-103">Asynchroniczne programy można napisać bardziej łatwo i intuicyjnie za pomocą funkcji async/await.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="d2ad1-104">Można napisać kod asynchroniczny, który wygląda jak synchroniczny kod i pozwolić kompilatorowi obsługi funkcji wywołania zwrotnego trudne i kontynuacje, które kodu asynchronicznego zazwyczaj pociąga za sobą.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="d2ad1-105">Aby uzyskać więcej informacji na temat funkcji asynchronicznych, zobacz [Asynchronous Programming with async i await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="d2ad1-106">W tym przewodniku rozpoczyna się od synchroniczne aplikacji Windows Presentation Foundation (WPF), która sumuje liczba bajtów na liście witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="d2ad1-107">Instruktaż następnie konwertuje ją do asynchronicznego rozwiązania przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="d2ad1-108">Jeśli nie chcesz samodzielnie tworzyć aplikacje, możesz pobrać [próbka asynchroniczna: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="d2ad1-109">Aby uruchomić przykłady, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="d2ad1-110">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="d2ad1-110">Create a WPF application</span></span>

1. <span data-ttu-id="d2ad1-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="d2ad1-112">Na pasku menu wybierz **pliku** > **New** > **projektu**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="d2ad1-113">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="d2ad1-114">W **zainstalowane szablony** okienku wybierz pozycję Visual C#, a następnie wybierz **aplikacji WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="d2ad1-115">W **nazwa** tekstu wprowadź `AsyncExampleWPF`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="d2ad1-116">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="d2ad1-117">Projektowanie proste MainWindow WPF</span><span class="sxs-lookup"><span data-stu-id="d2ad1-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="d2ad1-118">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="d2ad1-119">Jeśli **przybornika** okno nie jest widoczna, otwórz **widoku** menu, a następnie wybierz **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="d2ad1-120">Dodaj **przycisk** kontroli i **TextBox** kontrolę **MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="d2ad1-121">Wyróżnij **TextBox** sterowania i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="d2ad1-122">Ustaw **nazwa** właściwość `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-122">Set the **Name** property to `resultsTextBox`.</span></span>

    -   <span data-ttu-id="d2ad1-123">Ustaw **wysokość** właściwości do 250.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-123">Set the **Height** property to 250.</span></span>

    -   <span data-ttu-id="d2ad1-124">Ustaw **szerokość** właściwości do 500.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-124">Set the **Width** property to 500.</span></span>

    -   <span data-ttu-id="d2ad1-125">Na **tekstu** Określ czcionki o stałej szerokości, takich jak konsola New lub globalnego o stałej szerokości.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="d2ad1-126">Wyróżnij **przycisk** sterowania i w **właściwości** okna, ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="d2ad1-127">Ustaw **nazwa** właściwość `startButton`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-127">Set the **Name** property to `startButton`.</span></span>

    -   <span data-ttu-id="d2ad1-128">Zmień wartość właściwości **zawartości** właściwość **przycisk** do **Start**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="d2ad1-129">Położenie pola tekstowego i przycisku Tak, aby znajdować się w **MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="d2ad1-130">Aby uzyskać więcej informacji dotyczących projektanta XAML w WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="d2ad1-131">Dodaj odwołanie</span><span class="sxs-lookup"><span data-stu-id="d2ad1-131">Add a reference</span></span>

1. <span data-ttu-id="d2ad1-132">W **Eksploratora rozwiązań**, wyróżnij nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="d2ad1-133">Na pasku menu wybierz **projektu** > **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="d2ad1-134">**Menadżer odwołań** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="d2ad1-135">W górnej części okna dialogowego Sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="d2ad1-136">W **zestawy** kategorii, wybierz **Framework** Jeśli nie została jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="d2ad1-137">Na liście nazw, wybierz **System.Net.Http** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="d2ad1-138">Wybierz **OK** przycisk, aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="d2ad1-139">Dodaj to konieczne, dyrektyw using</span><span class="sxs-lookup"><span data-stu-id="d2ad1-139">Add necessary using directives</span></span>

1. <span data-ttu-id="d2ad1-140">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="d2ad1-141">Dodaj następujący kod `using` dyrektywy u góry pliku kodu, jeśli tak nie jest już obecny.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="d2ad1-142">Tworzenie aplikacji synchroniczne</span><span class="sxs-lookup"><span data-stu-id="d2ad1-142">Create a synchronous app</span></span>

1. <span data-ttu-id="d2ad1-143">W oknie projektu, MainWindow.xaml, kliknij dwukrotnie **Start** przycisk, aby utworzyć `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="d2ad1-144">W MainWindow.xaml.cs, skopiuj poniższy kod do treści `startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="d2ad1-145">Kod wywołuje metodę, która napędza aplikację, `SumPageSizes`i wyświetla komunikat, gdy sterowanie powraca do `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="d2ad1-146">Kod używany w rozwiązaniu synchronicznym zawiera poniższe cztery metody:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-146">The code for the synchronous solution contains the following four methods:</span></span>

    -   <span data-ttu-id="d2ad1-147">`SumPageSizes`, która pobiera listę adresów URL strony sieci Web, z `SetUpURLList` , a następnie wywołuje `GetURLContents` i `DisplayResults` do przetworzenia każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    -   <span data-ttu-id="d2ad1-148">`SetUpURLList`, która tworzy i zwraca listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    -   <span data-ttu-id="d2ad1-149">`GetURLContents`, która pobiera zawartość każdej witryny sieci Web i zwraca zawartość w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    -   <span data-ttu-id="d2ad1-150">`DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtowej dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="d2ad1-151">Skopiuj poniższe cztery metody, a następnie wklej je w obszarze `startButton_Click` programu obsługi zdarzeń w MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="d2ad1-152">Testowanie rozwiązania synchroniczne</span><span class="sxs-lookup"><span data-stu-id="d2ad1-152">Test the synchronous solution</span></span>

<span data-ttu-id="d2ad1-153">Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="d2ad1-154">Powinien pojawić się dane wyjściowe podobne do poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-154">Output that resembles the following list should appear:</span></span>

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

<span data-ttu-id="d2ad1-155">Należy zauważyć, że zajmuje kilka sekund, aby wyświetlić liczby elementów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="d2ad1-156">W tym czasie wątku interfejsu użytkownika jest blokowany, aż do żądanych zasobów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="d2ad1-157">W rezultacie nie można przenieść zmaksymalizować, zminimalizować lub nawet Zamknij okna, po dokonaniu wyboru **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="d2ad1-158">Tych działań zakończyć się niepowodzeniem, dopóki nie pojawiają się rozpocząć liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="d2ad1-159">Jeśli witryna sieci Web nie odpowiada, masz żadne oznaki, witryn, które nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="d2ad1-160">Trudno jest nawet zakończyć oczekiwanie i zamknięcie programu.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="d2ad1-161">Konwertuj GetURLContents metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="d2ad1-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="d2ad1-162">Aby konwertować synchroniczne rozwiązanie do asynchronicznego rozwiązania, najlepszym miejscem do rozpoczęcia jest w `GetURLContents` ponieważ wywołania <xref:System.Net.HttpWebRequest> metoda <xref:System.Net.HttpWebRequest.GetResponse%2A> i <xref:System.IO.Stream> metoda <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web .</span><span class="sxs-lookup"><span data-stu-id="d2ad1-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="d2ad1-163">.NET Framework ułatwia konwersję poprzez dostarczenie asynchronicznych wersji obu tych metod.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="d2ad1-164">Aby uzyskać więcej informacji o metodach, które są używane w `GetURLContents`, zobacz <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d2ad1-165">Postępuj zgodnie z instrukcjami w tym przewodniku, wyświetlane są kilka błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="d2ad1-166">Można je zignorować i kontynuować z tym przewodnikiem.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="d2ad1-167">Zmień metodę, która jest wywołana w trzecim wierszu `GetURLContents` z `GetResponse` do asynchronicznego, opartego na zadaniach <xref:System.Net.WebRequest.GetResponseAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="d2ad1-168">`GetResponseAsync` Zwraca <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d2ad1-169">W tym przypadku *zmiennej zwracanego zadania*, `TResult`, ma typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="d2ad1-170">Zadanie jest obietnicą utworzenia rzeczywistej `WebResponse` obiektu po pobraniu żądanych danych i zadanie zostało uruchomione w celu ukończenia.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="d2ad1-171">Aby pobrać `WebResponse` wartości z zadania, zastosuj [await](../../../../csharp/language-reference/keywords/await.md) operator wywołania do `GetResponseAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="d2ad1-172">`await` Operator zawiesza wykonywanie bieżącej metody `GetURLContents`, aż oczekiwane zadanie zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="d2ad1-173">W międzyczasie formant powraca do obiektu wywołującego metody bieżącej.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="d2ad1-174">W tym przykładzie jest bieżąca metoda `GetURLContents`, a obiekt wywołujący jest `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="d2ad1-175">Po zakończeniu zadania, uzgodnionego `WebResponse` obiekt jest generowany z wartością oczekiwane zadanie i przypisana do zmiennej `response`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="d2ad1-176">Poprzednia instrukcja można podzielić na dwie poniższe instrukcje, aby wyjaśnić, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="d2ad1-177">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` lub `Task<WebResponse>`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="d2ad1-178">Await operator jest stosowany do zadania do pobrania, a następnie `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="d2ad1-179">Jeśli metoda async ma robić prace, które nie są zależne od zakończenia tego zadania, metody można kontynuować pracę między te dwie instrukcje po wywołaniu metody async i przed `await` jest stosowany operator.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="d2ad1-180">Aby uzyskać przykłady, zobacz [jak: Wiele żądań sieci Web równolegle za pomocą async i await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i [jak: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-180">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="d2ad1-181">Ponieważ dodałeś `await` występuje błąd kompilatora operatora w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="d2ad1-182">Operator może służyć tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-182">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="d2ad1-183">Ignorowanie błędu podczas Powtórz procedurę konwersji, Zastąp wywołanie `CopyTo` wywołaniem `CopyToAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    -   <span data-ttu-id="d2ad1-184">Zmień nazwę metody, która jest wywoływana w celu <xref:System.IO.Stream.CopyToAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    -   <span data-ttu-id="d2ad1-185">`CopyTo` Lub `CopyToAsync` metoda kopiuje bajtów do jej argument `content`i nie zwraca zrozumiałą wartość.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="d2ad1-186">W wersji synchroniczne wywołanie `CopyTo` jest prostą instrukcję, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="d2ad1-187">Wersja asynchroniczna `CopyToAsync`, zwraca <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d2ad1-188">Zadanie funkcje takie jak "Task(void)" i włącza metodę oczekiwanie.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="d2ad1-189">Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="d2ad1-190">Poprzednia instrukcja Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="d2ad1-191">Wszystkie opcje, które pozostają do wykonania `GetURLContents` jest dostosowanie podpis metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="d2ad1-192">Możesz użyć `await` operatora tylko w przypadku metod, które są oznaczone [async](../../../../csharp/language-reference/keywords/async.md) modyfikator.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-192">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="d2ad1-193">Dodaj modyfikator do oznaczania metody jako *metody asynchronicznej*, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="d2ad1-194">Zwracany typ metody asynchronicznej może składać się wyłącznie <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, lub `void` w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="d2ad1-195">Zwykle, zwracanym typem `void` jest używany tylko w przypadku programu async obsługi zdarzeń, gdzie `void` jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="d2ad1-196">W innych przypadkach należy użyć `Task(T)` Jeśli metoda ukończone ma [zwracają](../../../../csharp/language-reference/keywords/return.md) instrukcję, która zwraca wartość typu T i używasz `Task` jeśli ukończone metoda nie zwraca zrozumiałą wartość.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="d2ad1-197">Można potraktować `Task` zwracany typ, co oznacza "Task(void)."</span><span class="sxs-lookup"><span data-stu-id="d2ad1-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="d2ad1-198">Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-198">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

     <span data-ttu-id="d2ad1-199">Metoda `GetURLContents` zawiera instrukcję return, a instrukcja zwraca tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="d2ad1-200">W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="d2ad1-201">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-201">Make the following changes in the method signature:</span></span>

    -   <span data-ttu-id="d2ad1-202">Zmień typ zwracany `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-202">Change the return type to `Task<byte[]>`.</span></span>

    -   <span data-ttu-id="d2ad1-203">Zgodnie z Konwencją metod asynchronicznych mają nazwy, które kończą się na "Async", więc Zmień nazwę metody `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="d2ad1-204">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="d2ad1-205">Za pomocą tych kilku zmian konwersji `GetURLContents` metody asynchronicznej jest pełny.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="d2ad1-206">Konwertuj SumPageSizes metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="d2ad1-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="d2ad1-207">Powtórz kroki z poprzedniej procedury, aby uzyskać `SumPageSizes`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="d2ad1-208">Najpierw należy zmienić wywołanie `GetURLContents` do wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    -   <span data-ttu-id="d2ad1-209">Zmień nazwę metody, która jest wywoływana z `GetURLContents` do `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    -   <span data-ttu-id="d2ad1-210">Zastosuj `await` do zadania, `GetURLContentsAsync` zwraca uzyskać bajt tablica wartości.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="d2ad1-211">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="d2ad1-212">Poprzednie przypisanie Wyświetla trzyliterowy skrót następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="d2ad1-213">W podpisie metody, należy wprowadzić następujące zmiany:</span><span class="sxs-lookup"><span data-stu-id="d2ad1-213">Make the following changes in the method's signature:</span></span>

    -   <span data-ttu-id="d2ad1-214">Oznacz metodę z `async` modyfikator.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-214">Mark the method with the `async` modifier.</span></span>

    -   <span data-ttu-id="d2ad1-215">Dodaj "Async" w nazwie metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-215">Add "Async" to the method name.</span></span>

    -   <span data-ttu-id="d2ad1-216">Nie jest zmienną zwracany nie zadań, T, tym razem, ponieważ `SumPageSizesAsync` nie zwraca wartości na T. (Nie ma metody `return` instrukcja.) Jednak metoda musi zwracać `Task` jako oczekujący.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="d2ad1-217">W związku z tym, zmień zwracany typ metody z `void` do `Task`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="d2ad1-218">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="d2ad1-219">Konwersja `SumPageSizes` do `SumPageSizesAsync` zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a><span data-ttu-id="d2ad1-220">Konwertuj startButton_Click metody asynchronicznej</span><span class="sxs-lookup"><span data-stu-id="d2ad1-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="d2ad1-221">W procedurze obsługi zdarzeń Zmień nazwę wywoływanej metody z `SumPageSizes` do `SumPageSizesAsync`, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="d2ad1-222">Ponieważ `SumPageSizesAsync` to metoda asynchroniczna, Zmień kod w obsłudze zdarzeń, aby poczekać na wynik.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="d2ad1-223">Wywołanie `SumPageSizesAsync` odzwierciedla wywołanie `CopyToAsync` w `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="d2ad1-224">To wywołanie zwraca `Task`, a nie `Task(T)`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="d2ad1-225">Tak jak w poprzednich procedur można przekonwertować wywołanie za pomocą jednej instrukcji lub dwóch instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="d2ad1-226">Poniższy kod przedstawia te zmiany.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="d2ad1-227">Aby uniknąć przypadkowego ponownego wprowadzania operacji, należy dodać następującą instrukcję w górnej części `startButton_Click` wyłączyć **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="d2ad1-228">Możesz włączyć przycisku na końcu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="d2ad1-229">Aby uzyskać więcej informacji na temat współużytkowania wątkowości, zobacz [obsługi współużytkowania wątkowości w aplikacjach asynchronicznych (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="d2ad1-230">Na koniec należy dodać `async` modyfikator deklaracji, aby program obsługi zdarzeń może poczekać `SumPagSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="d2ad1-231">Zazwyczaj nie ulegają zmianie nazwy programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="d2ad1-232">Zwracany typ nie jest zmieniany na `Task` ponieważ procedury obsługi zdarzeń musi zwracać `void`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="d2ad1-233">Konwersja przetwarzania synchronicznego w celu asynchronicznego projektu zostało ukończone.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="d2ad1-234">Testowanie rozwiązania asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="d2ad1-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="d2ad1-235">Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="d2ad1-236">Dane wyjściowe podobne dane wyjściowe w rozwiązaniu synchronicznym powinna zostać wyświetlona.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="d2ad1-237">Jednak zauważyć następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-237">However, notice the following differences.</span></span>

    -   <span data-ttu-id="d2ad1-238">Wyniki nie występują w tym samym czasie, po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="d2ad1-239">Na przykład oba programy zawiera wiersz w `startButton_Click` , czyści pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="d2ad1-240">Celem jest czyścić pole tekstowe między działa, jeśli wybierzesz **Start** przycisk, aby po raz drugi, po pojawieniu się jeden zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="d2ad1-241">W to wersja synchroniczna pole tekstowe jest wyczyszczone przed zliczeń pojawiają się po raz drugi, gdy odbywa się pliki do pobrania i jest bezpłatna wykonywanie innych zadań w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="d2ad1-242">W wersjach asynchronicznych, pola tekstowego czyści natychmiast, po dokonaniu wyboru **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    -   <span data-ttu-id="d2ad1-243">Co najważniejsze wątek interfejsu użytkownika nie jest zablokowane podczas jej pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="d2ad1-244">Możesz przenieść lub zmienić rozmiar okna podczas pobierania zasobów sieci web liczone, a wyświetlane.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="d2ad1-245">Jeśli jeden z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając **Zamknij** przycisku (x czerwone pola w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="d2ad1-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="d2ad1-246">Replace — metoda GetURLContentsAsync za pomocą metody .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d2ad1-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="d2ad1-247">.NET Framework 4.5 zapewnia wiele metod asynchronicznych, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="d2ad1-248">Jeden z nich, <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, wykonuje tylko potrzebne w ramach tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="d2ad1-249">Można używać go zamiast `GetURLContentsAsync` metody, który został utworzony w wcześniejszym etapie procedury.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="d2ad1-250">Pierwszym krokiem jest utworzenie `HttpClient` obiektu w metodzie `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="d2ad1-251">Dodaj następującą deklarację na początku metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="d2ad1-252">W `SumPageSizesAsync,` Zastąp wywołanie usługi `GetURLContentsAsync` metody za pomocą wywołania `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="d2ad1-253">Usunąć lub skomentować `GetURLContentsAsync` metodę, która powstała z jednego.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="d2ad1-254">Wybierz **F5** klawisz, aby uruchomić program, a następnie wybierz **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="d2ad1-255">Zachowanie tej wersji programu project powinien odpowiadać zachowanie, które opisano procedury "Aby test asynchronicznego rozwiązania", ale o jeszcze mniejszym nakładzie pracy ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="d2ad1-256">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="d2ad1-256">Example code</span></span>

<span data-ttu-id="d2ad1-257">Poniższy kod zawiera pełny przykład konwersja przez synchroniczny do asynchronicznego rozwiązania przy użyciu asynchroniczną `GetURLContentsAsync` metodę, która powstała z jednego.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="d2ad1-258">Należy zauważyć, że silnie przypomina oryginalnej, synchroniczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

<span data-ttu-id="d2ad1-259">Poniższy kod zawiera pełny przykład rozwiązania, które używa `HttpClient` metody `GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="d2ad1-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2ad1-260">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d2ad1-260">See also</span></span>

- [<span data-ttu-id="d2ad1-261">Próbka asynchroniczna: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-261">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="d2ad1-262">async</span><span class="sxs-lookup"><span data-stu-id="d2ad1-262">async</span></span>](../../../../csharp/language-reference/keywords/async.md)
- [<span data-ttu-id="d2ad1-263">await</span><span class="sxs-lookup"><span data-stu-id="d2ad1-263">await</span></span>](../../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="d2ad1-264">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-264">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="d2ad1-265">Asynchroniczne typy zwracane (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-265">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [<span data-ttu-id="d2ad1-266">Programowanie asynchroniczne opartego na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/en-us/download/details.aspx?id=19957)
- [<span data-ttu-id="d2ad1-267">Instrukcje: Rozszerzanie wskazówek asynchronicznych za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-267">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="d2ad1-268">Instrukcje: Wiele żądań sieci Web równolegle za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="d2ad1-268">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
