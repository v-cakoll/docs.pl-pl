---
title: 'Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)'
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 42b09dab26fd514e184163eaf41aff117d3a463f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74281783"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="032e7-102">Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)</span><span class="sxs-lookup"><span data-stu-id="032e7-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="032e7-103">Możesz pisać programy asynchroniczne łatwiej i intuicyjnie za pomocą funkcji async / await.</span><span class="sxs-lookup"><span data-stu-id="032e7-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="032e7-104">Można napisać kod asynchroniczny, który wygląda jak kod synchroniczny i niech kompilator obsługi trudnych funkcji wywołania wywołania i kontynuacji, które zwykle pociąga za sobą kod asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="032e7-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="032e7-105">Aby uzyskać więcej informacji na temat funkcji Async, zobacz [Programowanie asynchroniczne z async i await (C#)](./index.md).</span><span class="sxs-lookup"><span data-stu-id="032e7-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="032e7-106">Ten instruktaż rozpoczyna się od synchronicznej aplikacji Windows Presentation Foundation (WPF), która sumuje liczbę bajtów na liście witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="032e7-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="032e7-107">Następnie instruktaż konwertuje aplikację na rozwiązanie asynchroniczne przy użyciu nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="032e7-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="032e7-108">Jeśli nie chcesz samodzielnie tworzyć aplikacji, możesz pobrać [przykład programu Async: Uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic).](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)</span><span class="sxs-lookup"><span data-stu-id="032e7-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="032e7-109">Aby uruchomić przykłady, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="032e7-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="032e7-110">Tworzenie aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="032e7-110">Create a WPF application</span></span>

1. <span data-ttu-id="032e7-111">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="032e7-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="032e7-112">Na pasku menu wybierz pozycję **Plik** > **nowy** > **projekt**.</span><span class="sxs-lookup"><span data-stu-id="032e7-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="032e7-113">Zostanie otwarte okno dialogowe **Nowy projekt.**</span><span class="sxs-lookup"><span data-stu-id="032e7-113">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="032e7-114">W okienku **Zainstalowane szablony** wybierz pozycję Visual C#, a następnie wybierz **pozycję Aplikacja WPF** z listy typów projektów.</span><span class="sxs-lookup"><span data-stu-id="032e7-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="032e7-115">W **Name** polu tekstowym `AsyncExampleWPF`Nazwa wprowadź klawisz , a następnie wybierz przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="032e7-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="032e7-116">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="032e7-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="032e7-117">Projektowanie prostego Okna Głównego WPF</span><span class="sxs-lookup"><span data-stu-id="032e7-117">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="032e7-118">W Edytorze kodu programu Visual Studio wybierz kartę **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="032e7-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="032e7-119">Jeśli okno **Przybornik** nie jest widoczne, otwórz menu **Widok,** a następnie wybierz polecenie **Przybornik**.</span><span class="sxs-lookup"><span data-stu-id="032e7-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="032e7-120">Dodaj **button** kontroli i **TextBox** formantu **do MainWindow** okna.</span><span class="sxs-lookup"><span data-stu-id="032e7-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="032e7-121">Wyróżnij kontrolki **TextBox** i w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="032e7-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="032e7-122">Ustaw **Name** właściwość Name `resultsTextBox`na .</span><span class="sxs-lookup"><span data-stu-id="032e7-122">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="032e7-123">Ustaw **właściwość Height** na 250.</span><span class="sxs-lookup"><span data-stu-id="032e7-123">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="032e7-124">Ustaw **width** właściwość 500.</span><span class="sxs-lookup"><span data-stu-id="032e7-124">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="032e7-125">Na karcie **Tekst** określ czcionkę jednoosyjną, taką jak Lucida Console lub Global Monospace.</span><span class="sxs-lookup"><span data-stu-id="032e7-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="032e7-126">Wyróżnij kontrolki **Button** i w oknie **Właściwości** ustaw następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="032e7-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="032e7-127">Ustaw **Name** właściwość Name `startButton`na .</span><span class="sxs-lookup"><span data-stu-id="032e7-127">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="032e7-128">Zmień wartość właściwości **Content** z **Button** na **Start**.</span><span class="sxs-lookup"><span data-stu-id="032e7-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="032e7-129">Umieść pole tekstowe i przycisk tak, aby oba były wyświetlane w oknie **MainWindow.**</span><span class="sxs-lookup"><span data-stu-id="032e7-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="032e7-130">Aby uzyskać więcej informacji na temat projektanta XAML WPF, zobacz [Tworzenie interfejsu użytkownika przy użyciu projektanta XAML](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="032e7-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="032e7-131">Dodawanie odwołania</span><span class="sxs-lookup"><span data-stu-id="032e7-131">Add a reference</span></span>

1. <span data-ttu-id="032e7-132">W **Eksploratorze rozwiązań**wyróżnij nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="032e7-132">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="032e7-133">Na pasku menu wybierz pozycję Dodaj**odwołanie** **do projektu** > .</span><span class="sxs-lookup"><span data-stu-id="032e7-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="032e7-134">Pojawi się okno **dialogowe Menedżera odwołań.**</span><span class="sxs-lookup"><span data-stu-id="032e7-134">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="032e7-135">W górnej części okna dialogowego sprawdź, czy projekt jest przeznaczony dla .NET Framework 4.5 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="032e7-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="032e7-136">W kategorii **Zestawy** wybierz **pozycję Framework,** jeśli nie jest jeszcze wybrana.</span><span class="sxs-lookup"><span data-stu-id="032e7-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="032e7-137">Na liście nazw zaznacz pole wyboru **System.Net.Http.**</span><span class="sxs-lookup"><span data-stu-id="032e7-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="032e7-138">Wybierz przycisk **OK,** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="032e7-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="032e7-139">Dodawanie niezbędnych za pomocą dyrektyw</span><span class="sxs-lookup"><span data-stu-id="032e7-139">Add necessary using directives</span></span>

1. <span data-ttu-id="032e7-140">W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz pozycję **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="032e7-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2. <span data-ttu-id="032e7-141">Dodaj następujące `using` dyrektywy w górnej części pliku kodu, jeśli nie są one jeszcze obecne.</span><span class="sxs-lookup"><span data-stu-id="032e7-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="032e7-142">Tworzenie aplikacji synchronicznej</span><span class="sxs-lookup"><span data-stu-id="032e7-142">Create a synchronous app</span></span>

1. <span data-ttu-id="032e7-143">W oknie projektu MainWindow.xaml kliknij dwukrotnie przycisk **Start,** aby utworzyć program obsługi `startButton_Click` zdarzeń w MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="032e7-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2. <span data-ttu-id="032e7-144">W MainWindow.xaml.cs skopiuj następujący `startButton_Click`kod do treści:</span><span class="sxs-lookup"><span data-stu-id="032e7-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="032e7-145">Kod wywołuje metodę, która napędza `SumPageSizes`aplikację, i wyświetla komunikat, `startButton_Click`gdy formant powraca do .</span><span class="sxs-lookup"><span data-stu-id="032e7-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="032e7-146">Kod rozwiązania synchronicznego zawiera następujące cztery metody:</span><span class="sxs-lookup"><span data-stu-id="032e7-146">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="032e7-147">`SumPageSizes`, który pobiera listę adresów `SetUpURLList` URL stron `GetURLContents` `DisplayResults` internetowych, a następnie wywołuje i przetwarza każdy adres URL.</span><span class="sxs-lookup"><span data-stu-id="032e7-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="032e7-148">`SetUpURLList`, który tworzy i zwraca listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="032e7-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="032e7-149">`GetURLContents`, który pobiera zawartość każdej witryny sieci Web i zwraca zawartość jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="032e7-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="032e7-150">`DisplayResults`, który wyświetla liczbę bajtów w tablicy bajtów dla każdego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="032e7-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="032e7-151">Skopiuj następujące cztery metody, a `startButton_Click` następnie wklej je w programie obsługi zdarzeń w MainWindow.xaml.cs:</span><span class="sxs-lookup"><span data-stu-id="032e7-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

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

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="032e7-152">Testowanie roztworu synchronicznego</span><span class="sxs-lookup"><span data-stu-id="032e7-152">Test the synchronous solution</span></span>

<span data-ttu-id="032e7-153">Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="032e7-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="032e7-154">Dane wyjściowe, które przypomina następującą listę powinny być wyświetlane:</span><span class="sxs-lookup"><span data-stu-id="032e7-154">Output that resembles the following list should appear:</span></span>

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

<span data-ttu-id="032e7-155">Należy zauważyć, że wyświetlenie liczby zajmuje kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="032e7-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="032e7-156">W tym czasie wątek interfejsu użytkownika jest blokowany, gdy czeka na żądane zasoby do pobrania.</span><span class="sxs-lookup"><span data-stu-id="032e7-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="032e7-157">W rezultacie po wybraniu przycisku **Start** nie można przenosić, maksymalizować, minimalizować ani nawet zamykać okna wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="032e7-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="032e7-158">Te wysiłki nie powiodą się, dopóki nie zaczną pojawiać się liczby bajtów.</span><span class="sxs-lookup"><span data-stu-id="032e7-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="032e7-159">Jeśli witryna sieci Web nie odpowiada, nie masz żadnych wskazówek, która witryna nie powiodła się.</span><span class="sxs-lookup"><span data-stu-id="032e7-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="032e7-160">Trudno nawet przestać czekać i zamknąć program.</span><span class="sxs-lookup"><span data-stu-id="032e7-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="032e7-161">Konwertowanie GetURLContents na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="032e7-161">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="032e7-162">Aby przekonwertować rozwiązanie synchroniczne na rozwiązanie asynchroniczne, `GetURLContents` najlepszym miejscem do <xref:System.Net.HttpWebRequest> <xref:System.Net.HttpWebRequest.GetResponse%2A> uruchomienia jest, ponieważ wywołania metody i <xref:System.IO.Stream> metody <xref:System.IO.Stream.CopyTo%2A> są, gdzie aplikacja uzyskuje dostęp do sieci web.</span><span class="sxs-lookup"><span data-stu-id="032e7-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="032e7-163">.NET Framework ułatwia konwersję, dostarczając asynchroniczne wersje obu metod.</span><span class="sxs-lookup"><span data-stu-id="032e7-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="032e7-164">Aby uzyskać więcej informacji na temat `GetURLContents`metod, które są używane w , zobacz <xref:System.Net.WebRequest>.</span><span class="sxs-lookup"><span data-stu-id="032e7-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="032e7-165">W miarę postępów w tym instruktażenie pojawia się kilka błędów kompilatora.</span><span class="sxs-lookup"><span data-stu-id="032e7-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="032e7-166">Można je zignorować i kontynuować instruktaż.</span><span class="sxs-lookup"><span data-stu-id="032e7-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="032e7-167">Zmień metodę, która jest wywoływana `GetURLContents` w `GetResponse` trzecim wierszu z asynchronicznej metody opartej na <xref:System.Net.WebRequest.GetResponseAsync%2A> zadaniach.</span><span class="sxs-lookup"><span data-stu-id="032e7-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2. <span data-ttu-id="032e7-168">`GetResponseAsync`zwraca <xref:System.Threading.Tasks.Task%601>wartość .</span><span class="sxs-lookup"><span data-stu-id="032e7-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="032e7-169">W takim przypadku *zmienna zwrotu zadania*, `TResult`ma typ <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="032e7-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="032e7-170">Zadanie jest obietnicą do `WebResponse` wyprodukowania rzeczywistego obiektu po pobraniu żądanych danych i zadanie zostało uruchomione do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="032e7-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="032e7-171">Aby pobrać `WebResponse` wartość z zadania, należy zastosować operator `GetResponseAsync` [await](../../../language-reference/operators/await.md) do wywołania , jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="032e7-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../language-reference/operators/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="032e7-172">Operator `await` zawiesza wykonanie bieżącej metody, `GetURLContents`do czasu zakończenia oczekiwanego zadania.</span><span class="sxs-lookup"><span data-stu-id="032e7-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="032e7-173">W międzyczasie formant powraca do obiektu wywołującego bieżącej metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="032e7-174">W tym przykładzie bieżąca `GetURLContents`metoda jest `SumPageSizes`, a obiekt wywołujący jest .</span><span class="sxs-lookup"><span data-stu-id="032e7-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="032e7-175">Po zakończeniu zadania przyrzeczony `WebResponse` obiekt jest tworzony jako wartość oczekiwanego zadania i `response`przypisany do zmiennej .</span><span class="sxs-lookup"><span data-stu-id="032e7-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="032e7-176">Poprzednia instrukcja może być podzielona na następujące dwie instrukcje, aby wyjaśnić, co się dzieje.</span><span class="sxs-lookup"><span data-stu-id="032e7-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="032e7-177">Wywołanie `webReq.GetResponseAsync` zwraca `Task(Of WebResponse)` ć `Task<WebResponse>`lub .</span><span class="sxs-lookup"><span data-stu-id="032e7-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="032e7-178">Następnie operator await jest stosowany do zadania, aby pobrać `WebResponse` wartość.</span><span class="sxs-lookup"><span data-stu-id="032e7-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="032e7-179">Jeśli metoda asynchroniczne ma do zrobienia, że nie zależy od zakończenia zadania, metoda może kontynuować tę pracę między tymi `await` dwiema instrukcjami, po wywołaniu metody asynchronicznej i przed zastosowaniem operatora.</span><span class="sxs-lookup"><span data-stu-id="032e7-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="032e7-180">Na przykład zobacz [Jak tworzyć wiele żądań sieci web równolegle przy użyciu asynchronii i await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) i Jak rozszerzyć [instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="032e7-180">For examples, see [How to make multiple web requests in parallel by using async and await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="032e7-181">Ponieważ dodano `await` operator w poprzednim kroku, występuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="032e7-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="032e7-182">Operator może być używany tylko w metodach, które są oznaczone modyfikatorem [asynchronii.](../../../language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="032e7-182">The operator can be used only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="032e7-183">Ignoruj błąd podczas powtarzania kroków `CopyTo` konwersji, aby `CopyToAsync`zastąpić wywołanie wywołaniem .</span><span class="sxs-lookup"><span data-stu-id="032e7-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="032e7-184">Zmień nazwę metody, która jest <xref:System.IO.Stream.CopyToAsync%2A>wywoływana do .</span><span class="sxs-lookup"><span data-stu-id="032e7-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="032e7-185">Lub `CopyTo` `CopyToAsync` metoda kopiuje bajty `content`do jego argumentu i nie zwraca znaczącej wartości.</span><span class="sxs-lookup"><span data-stu-id="032e7-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="032e7-186">W wersji synchronicznej wywołanie `CopyTo` jest prostą instrukcją, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="032e7-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="032e7-187">Wersja asynchroniczna `CopyToAsync`, <xref:System.Threading.Tasks.Task>zwraca wartość .</span><span class="sxs-lookup"><span data-stu-id="032e7-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="032e7-188">Funkcja zadania, taka jak "Task(void)" i umożliwia oczekiwanie na metodę.</span><span class="sxs-lookup"><span data-stu-id="032e7-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="032e7-189">Zastosuj `Await` lub `await` do wywołania `CopyToAsync`, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="032e7-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="032e7-190">Poprzednia instrukcja skraca następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="032e7-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4. <span data-ttu-id="032e7-191">Wszystko, co pozostaje `GetURLContents` do zrobienia w to, aby dostosować podpis metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="032e7-192">Operator `await` async można używać tylko w metodach oznaczonych modyfikatorem [asynchroni.](../../../language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="032e7-192">You can use the `await` operator only in methods that are marked with the [async](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="032e7-193">Dodaj modyfikator, aby oznaczyć metodę jako *metodę asynchronia*, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="032e7-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5. <span data-ttu-id="032e7-194">Zwracany typ metody asynchronicznej <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>może `void` być tylko , lub w języku C#.</span><span class="sxs-lookup"><span data-stu-id="032e7-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="032e7-195">Zazwyczaj zwracany typ `void` jest używany tylko w programie obsługi `void` zdarzeń asynchronicznego, gdzie jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="032e7-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="032e7-196">W innych przypadkach `Task(T)` można użyć, jeśli ukończona metoda ma [return](../../../language-reference/keywords/return.md) instrukcji, która `Task` zwraca wartość typu T i należy użyć, jeśli ukończona metoda nie zwraca wartość znaczącą.</span><span class="sxs-lookup"><span data-stu-id="032e7-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="032e7-197">Typ zwracany `Task` można pomyśleć jako "Zadanie(unieważnienie)".</span><span class="sxs-lookup"><span data-stu-id="032e7-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="032e7-198">Aby uzyskać więcej informacji, zobacz [Async Return Types (C#)](./async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="032e7-198">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>

     <span data-ttu-id="032e7-199">Metoda `GetURLContents` ma return instrukcji i instrukcji zwraca tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="032e7-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="032e7-200">W związku z tym zwracany typ wersji asynchronicznej jest Task(T), gdzie T jest tablicą bajtów.</span><span class="sxs-lookup"><span data-stu-id="032e7-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="032e7-201">Wyconajmi należy wprowadzić następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="032e7-201">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="032e7-202">Zmień typ zwracany na `Task<byte[]>`.</span><span class="sxs-lookup"><span data-stu-id="032e7-202">Change the return type to `Task<byte[]>`.</span></span>

    - <span data-ttu-id="032e7-203">Zgodnie z konwencją metody asynchroniczne mają nazwy, które kończą `GetURLContentsAsync`się na "Async", więc zmień nazwę metody .</span><span class="sxs-lookup"><span data-stu-id="032e7-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="032e7-204">Poniższy kod pokazuje te zmiany.</span><span class="sxs-lookup"><span data-stu-id="032e7-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="032e7-205">Z tych kilku zmian, `GetURLContents` konwersja do metody asynchronicznej jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="032e7-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="032e7-206">Konwertowanie sumpagesizes na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="032e7-206">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="032e7-207">Powtórz kroki z poprzedniej `SumPageSizes`procedury dla .</span><span class="sxs-lookup"><span data-stu-id="032e7-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="032e7-208">Najpierw zmień wywołanie `GetURLContents` do wywołania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="032e7-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="032e7-209">Zmień nazwę metody, która jest `GetURLContents` wywoływana z na `GetURLContentsAsync`, jeśli jeszcze tego nie zrobiłeś.</span><span class="sxs-lookup"><span data-stu-id="032e7-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="032e7-210">Zastosuj `await` do zadania, które `GetURLContentsAsync` zwraca, aby uzyskać wartość tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="032e7-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="032e7-211">Poniższy kod pokazuje te zmiany.</span><span class="sxs-lookup"><span data-stu-id="032e7-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="032e7-212">Poprzednie przypisanie skraca następujące dwa wiersze kodu.</span><span class="sxs-lookup"><span data-stu-id="032e7-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2. <span data-ttu-id="032e7-213">Wyczyć następujące zmiany w podpisie metody:</span><span class="sxs-lookup"><span data-stu-id="032e7-213">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="032e7-214">Oznacz metodę `async` modyfikatorem.</span><span class="sxs-lookup"><span data-stu-id="032e7-214">Mark the method with the `async` modifier.</span></span>

    - <span data-ttu-id="032e7-215">Dodaj "Async" do nazwy metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-215">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="032e7-216">Nie ma zmiennej zwrotu zadania, `SumPageSizesAsync` T, tym razem, ponieważ nie zwraca `return` wartość dla T. (Metoda nie ma instrukcji.) Jednak metoda musi `Task` zwrócić, aby być oczekiwany.</span><span class="sxs-lookup"><span data-stu-id="032e7-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="032e7-217">W związku z tym należy `void` zmienić `Task`typ zwracany metody z na .</span><span class="sxs-lookup"><span data-stu-id="032e7-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="032e7-218">Poniższy kod pokazuje te zmiany.</span><span class="sxs-lookup"><span data-stu-id="032e7-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="032e7-219">Konwersja `SumPageSizes` do `SumPageSizesAsync` jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="032e7-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="032e7-220">Konwertowanie startButton_Click na metodę asynchroniczną</span><span class="sxs-lookup"><span data-stu-id="032e7-220">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="032e7-221">W programie obsługi zdarzeń zmień nazwę `SumPageSizes` metody `SumPageSizesAsync`wywoływanej z na , jeśli jeszcze tego nie zrobiono.</span><span class="sxs-lookup"><span data-stu-id="032e7-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="032e7-222">Ponieważ `SumPageSizesAsync` jest metodą asynchronicznej, zmień kod w programie obsługi zdarzeń, aby oczekiwać na wynik.</span><span class="sxs-lookup"><span data-stu-id="032e7-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="032e7-223">Wywołanie `SumPageSizesAsync` do odzwierciedlenia wywołania `CopyToAsync` w `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="032e7-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="032e7-224">Wywołanie zwraca `Task`, `Task(T)`a nie .</span><span class="sxs-lookup"><span data-stu-id="032e7-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="032e7-225">Podobnie jak w poprzednich procedurach, można przekonwertować wywołanie przy użyciu jednej instrukcji lub dwóch instrukcji.</span><span class="sxs-lookup"><span data-stu-id="032e7-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="032e7-226">Poniższy kod pokazuje te zmiany.</span><span class="sxs-lookup"><span data-stu-id="032e7-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3. <span data-ttu-id="032e7-227">Aby zapobiec przypadkowemu ponownemu wprowadzeniu operacji, dodaj `startButton_Click` następującą instrukcję u góry, aby wyłączyć przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="032e7-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="032e7-228">Można ponownie włączyć przycisk na końcu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="032e7-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="032e7-229">Aby uzyskać więcej informacji na temat reentrancy, zobacz [Obsługa Reentrancy w Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span><span class="sxs-lookup"><span data-stu-id="032e7-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](./handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="032e7-230">Na koniec `async` dodaj modyfikator do deklaracji, `SumPagSizesAsync`aby program obsługi zdarzeń mógł poczekać .</span><span class="sxs-lookup"><span data-stu-id="032e7-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="032e7-231">Zazwyczaj nazwy programów obsługi zdarzeń nie są zmieniane.</span><span class="sxs-lookup"><span data-stu-id="032e7-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="032e7-232">Typ zwracany nie jest `Task` zmieniany, ponieważ `void`programy obsługi zdarzeń muszą zwracać .</span><span class="sxs-lookup"><span data-stu-id="032e7-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="032e7-233">Konwersja projektu z synchronicznego do przetwarzania asynchronicznego została zakończona.</span><span class="sxs-lookup"><span data-stu-id="032e7-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="032e7-234">Testowanie rozwiązania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="032e7-234">Test the asynchronous solution</span></span>

1. <span data-ttu-id="032e7-235">Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="032e7-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="032e7-236">Dane wyjściowe, które przypomina dane wyjściowe rozwiązania synchronicznego powinny pojawić się.</span><span class="sxs-lookup"><span data-stu-id="032e7-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="032e7-237">Należy jednak zauważyć następujące różnice.</span><span class="sxs-lookup"><span data-stu-id="032e7-237">However, notice the following differences.</span></span>

    - <span data-ttu-id="032e7-238">Wyniki nie wszystkie występują w tym samym czasie, po zakończeniu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="032e7-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="032e7-239">Na przykład oba programy zawierają `startButton_Click` wiersz, który czyści pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="032e7-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="032e7-240">Celem jest wyczyszczenie pola tekstowego między działami, jeśli wybierzesz przycisk **Start** po raz drugi, po pojawieniu się jednego zestawu wyników.</span><span class="sxs-lookup"><span data-stu-id="032e7-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="032e7-241">W wersji synchronicznej pole tekstowe jest wyczyszczone tuż przed pojawieniem się zliczania po raz drugi, po zakończeniu pobierania i wątku interfejsu użytkownika jest wolny do wykonywania innych prac.</span><span class="sxs-lookup"><span data-stu-id="032e7-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="032e7-242">W wersji asynchronicznej pole tekstowe zostanie wyczyszczone natychmiast po wybraniu przycisku **Start.**</span><span class="sxs-lookup"><span data-stu-id="032e7-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="032e7-243">Co najważniejsze, wątek interfejsu użytkownika nie jest blokowany podczas pobierania.</span><span class="sxs-lookup"><span data-stu-id="032e7-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="032e7-244">Okno można przenosić lub zmieniać rozmiar podczas pobierania, zliczania i wyświetlania zasobów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="032e7-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="032e7-245">Jeśli jedna z witryn sieci Web działa wolno lub nie odpowiada, możesz anulować operację, wybierając przycisk **Zamknij** (x w czerwonym polu w prawym górnym rogu).</span><span class="sxs-lookup"><span data-stu-id="032e7-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="032e7-246">Zamień metodę GetURLContentsAsync metodą .NET Framework</span><span class="sxs-lookup"><span data-stu-id="032e7-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1. <span data-ttu-id="032e7-247">.NET Framework 4.5 zawiera wiele metod asynchronii, których można użyć.</span><span class="sxs-lookup"><span data-stu-id="032e7-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="032e7-248">Jeden z <xref:System.Net.Http.HttpClient> nich, <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>metoda , robi to, czego potrzebujesz do tego instruktażenia.</span><span class="sxs-lookup"><span data-stu-id="032e7-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="032e7-249">Można go używać zamiast `GetURLContentsAsync` metody, która została utworzona we wcześniejszej procedurze.</span><span class="sxs-lookup"><span data-stu-id="032e7-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="032e7-250">Pierwszym krokiem jest `HttpClient` utworzenie obiektu `SumPageSizesAsync`w metodzie .</span><span class="sxs-lookup"><span data-stu-id="032e7-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="032e7-251">Dodaj następującą deklarację na początku metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2. <span data-ttu-id="032e7-252">W `SumPageSizesAsync,` zastąpić wywołanie `GetURLContentsAsync` metody z wywołaniem `HttpClient` metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3. <span data-ttu-id="032e7-253">Usuń lub skomentuj `GetURLContentsAsync` metodę, którą napisałeś.</span><span class="sxs-lookup"><span data-stu-id="032e7-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="032e7-254">Wybierz klawisz **F5,** aby uruchomić program, a następnie wybierz przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="032e7-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="032e7-255">Zachowanie tej wersji projektu powinny być zgodne z zachowaniem, które opisuje procedura "Aby przetestować rozwiązanie asynchroniczne", ale przy jeszcze mniejszym wysiłku ze strony ciebie.</span><span class="sxs-lookup"><span data-stu-id="032e7-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="032e7-256">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="032e7-256">Example code</span></span>

<span data-ttu-id="032e7-257">Poniższy kod zawiera pełny przykład konwersji z synchronicznego do rozwiązania asynchronicznego przy `GetURLContentsAsync` użyciu metody asynchronicznej, który został zanapisał.</span><span class="sxs-lookup"><span data-stu-id="032e7-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="032e7-258">Należy zauważyć, że bardzo przypomina oryginalne, synchroniczne rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="032e7-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

<span data-ttu-id="032e7-259">Poniższy kod zawiera pełny przykład rozwiązania, `HttpClient` które `GetByteArrayAsync`używa metody.</span><span class="sxs-lookup"><span data-stu-id="032e7-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="032e7-260">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="032e7-260">See also</span></span>

- <span data-ttu-id="032e7-261">[Przykład asynchroniczny: uzyskiwanie dostępu do instruktażu sieci Web (C# i Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="032e7-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/hh300224(v=vs.110))</span></span>
- [<span data-ttu-id="032e7-262">async</span><span class="sxs-lookup"><span data-stu-id="032e7-262">async</span></span>](../../../language-reference/keywords/async.md)
- [<span data-ttu-id="032e7-263">await</span><span class="sxs-lookup"><span data-stu-id="032e7-263">await</span></span>](../../../language-reference/operators/await.md)
- [<span data-ttu-id="032e7-264">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="032e7-264">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="032e7-265">Typy zwrotu asynchronicznego (C#)</span><span class="sxs-lookup"><span data-stu-id="032e7-265">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="032e7-266">Programowanie asynchroniczne oparte na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="032e7-266">Task-based Asynchronous Programming (TAP)</span></span>](https://www.microsoft.com/download/details.aspx?id=19957)
- [<span data-ttu-id="032e7-267">Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="032e7-267">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="032e7-268">Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)</span><span class="sxs-lookup"><span data-stu-id="032e7-268">How to make multiple web requests in parallel by using async and await (C#)</span></span>](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
