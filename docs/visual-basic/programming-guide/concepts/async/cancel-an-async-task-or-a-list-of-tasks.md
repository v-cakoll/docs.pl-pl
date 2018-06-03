---
title: Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: 2823514bc462f198a43316b40eb05bc1ffed0e72
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2018
ms.locfileid: "34728670"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="1ce87-102">Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce87-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="1ce87-103">Można skonfigurować przycisku, który służy do anulowania aplikacji async, jeśli nie chcesz czekać na jego zakończenie.</span><span class="sxs-lookup"><span data-stu-id="1ce87-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="1ce87-104">Wykonując poniższe przykłady w tym temacie, można dodać przycisk anulowania do aplikacji, która pobiera zawartość witryny lub listy witryn sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ce87-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="1ce87-105">W przykładach użyto interfejsu użytkownika który [Fine-Tuning Twoja aplikacja Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) opisuje.</span><span class="sxs-lookup"><span data-stu-id="1ce87-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1ce87-106">Uruchamianie przykładów, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="1ce87-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_CancelaTask"></a> <span data-ttu-id="1ce87-107">Anuluj zadanie</span><span class="sxs-lookup"><span data-stu-id="1ce87-107">Cancel a Task</span></span>  
 <span data-ttu-id="1ce87-108">W pierwszym przykładzie **anulować** przycisk z zadania jednego pobierania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="1ce87-109">Jeśli wybierzesz przycisk podczas pobierania zawartości aplikacji, pobieranie zostało anulowane.</span><span class="sxs-lookup"><span data-stu-id="1ce87-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="1ce87-110">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="1ce87-110">Downloading the Example</span></span>  
 <span data-ttu-id="1ce87-111">Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="1ce87-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1ce87-112">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ce87-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1ce87-113">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="1ce87-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1ce87-114">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="1ce87-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="1ce87-115">W **Eksploratora rozwiązań**, otwórz menu skrótów **CancelATask** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="1ce87-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1ce87-116">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="1ce87-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1ce87-117">Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="1ce87-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="1ce87-118">Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1ce87-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="1ce87-119">Tworzenie w przykładzie</span><span class="sxs-lookup"><span data-stu-id="1ce87-119">Building the Example</span></span>  
 <span data-ttu-id="1ce87-120">Dodaj następujące zmiany **anulować** przycisku do aplikacji, która pobiera witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ce87-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="1ce87-121">Jeśli nie chcesz pobrać lub utworzyć przykładzie, można przejrzeć produktu końcowego w sekcji "Przykłady pełną" na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1ce87-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="1ce87-122">Gwiazdki oznaczania zmian w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ce87-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="1ce87-123">Do tworzenia przykładzie samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie Example", ale wybierz **StarterCode** jako **projekt startowy** zamiast **CancelATask** .</span><span class="sxs-lookup"><span data-stu-id="1ce87-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="1ce87-124">Następnie należy dodać następujące zmiany do pliku MainWindow.xaml.vb tego projektu.</span><span class="sxs-lookup"><span data-stu-id="1ce87-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="1ce87-125">Deklarowanie `CancellationTokenSource` zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod, które do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="1ce87-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="1ce87-126">Dodaj następujące programu obsługi zdarzeń dla **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1ce87-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="1ce87-127">Program obsługi zdarzeń używa <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> metodę, aby powiadomić `cts` gdy użytkownik zażąda anulowania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="1ce87-128">Sprawdź poniższe zmiany w zdarzeniu programu obsługi dla **Start** przycisku `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="1ce87-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="1ce87-129">Utwórz wystąpienie `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="1ce87-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="1ce87-130">W wywołaniu `AccessTheWebAsync`, które pobierają zawartość z określonej witryny sieci Web, wysyłanie <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> właściwość `cts` jako argument.</span><span class="sxs-lookup"><span data-stu-id="1ce87-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="1ce87-131">`Token` Właściwość propaguje komunikat, jeśli żądanie anulowania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="1ce87-132">Dodaj blok catch, który wyświetla komunikat, jeśli użytkownik anuluje operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="1ce87-133">Poniższy kod przedstawia zmiany.</span><span class="sxs-lookup"><span data-stu-id="1ce87-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="1ce87-134">W `AccessTheWebAsync`, użyj <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> przeciążenia z `GetAsync` metoda <xref:System.Net.Http.HttpClient> typu w celu pobrania zawartości witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="1ce87-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="1ce87-135">Przekaż `ct`, <xref:System.Threading.CancellationToken> parametr `AccessTheWebAsync`, jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="1ce87-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="1ce87-136">Token niesie komunikat, jeśli użytkownik wybierze **anulować** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1ce87-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="1ce87-137">Poniższy kod przedstawia zmiany w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="1ce87-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="1ce87-138">Jeśli program nie jest anulowana, tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1ce87-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="1ce87-139">Jeśli wybierzesz **anulować** przycisk przed programem zakończeniu pobierania zawartości, program tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1ce87-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="1ce87-140">Anuluj listy zadań</span><span class="sxs-lookup"><span data-stu-id="1ce87-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="1ce87-141">Można rozszerzyć poprzedni przykład, aby anulować wiele zadań można skojarzyć takie same `CancellationTokenSource` wystąpienia z każdego zadania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="1ce87-142">Jeśli wybierzesz **anulować** przycisku Anuluj wszystkie zadania, które nie są jeszcze ukończone.</span><span class="sxs-lookup"><span data-stu-id="1ce87-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="1ce87-143">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="1ce87-143">Downloading the Example</span></span>  
 <span data-ttu-id="1ce87-144">Możesz pobrać pełną projekt Windows Presentation Foundation (WPF) z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj następujące kroki.</span><span class="sxs-lookup"><span data-stu-id="1ce87-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="1ce87-145">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1ce87-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="1ce87-146">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="1ce87-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="1ce87-147">W **Otwórz projekt** okno dialogowe, otwórz folder, który zawiera przykładowy kod, który można zdekompresować, a następnie otwórz plik rozwiązania (sln) dla AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="1ce87-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="1ce87-148">W **Eksploratora rozwiązań**, otwórz menu skrótów **CancelAListOfTasks** projektu, a następnie wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="1ce87-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="1ce87-149">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="1ce87-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="1ce87-150">Wybierz klucze Ctrl + F5, aby uruchomić projekt bez debugowania go.</span><span class="sxs-lookup"><span data-stu-id="1ce87-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="1ce87-151">Jeśli nie chcesz pobrać projekt, można przejrzeć plik MainWindow.xaml.vb na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="1ce87-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="1ce87-152">Tworzenie w przykładzie</span><span class="sxs-lookup"><span data-stu-id="1ce87-152">Building the Example</span></span>  
 <span data-ttu-id="1ce87-153">Aby rozszerzyć przykład samodzielnie krok po kroku, postępuj zgodnie z instrukcjami w sekcji "Pobieranie przykład", ale wybierz **CancelATask** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="1ce87-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="1ce87-154">Dodaj następujące zmiany do projektu.</span><span class="sxs-lookup"><span data-stu-id="1ce87-154">Add the following changes to that project.</span></span> <span data-ttu-id="1ce87-155">Gwiazdki oznaczyć zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="1ce87-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="1ce87-156">Dodaj metodę, aby utworzyć listę adresów internetowych.</span><span class="sxs-lookup"><span data-stu-id="1ce87-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  <span data-ttu-id="1ce87-157">Wywołaj metodę `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="1ce87-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="1ce87-158">Dodaj następującą pętlę w `AccessTheWebAsync` przetworzyć każdy adres sieci web na liście.</span><span class="sxs-lookup"><span data-stu-id="1ce87-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="1ce87-159">Ponieważ `AccessTheWebAsync` Wyświetla długości metody nie trzeba zwrócić żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="1ce87-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="1ce87-160">Usuń instrukcji return i zmienić zwracany typ metody <xref:System.Threading.Tasks.Task> zamiast <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="1ce87-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="1ce87-161">Wywołaj metodę z `startButton_Click` przy użyciu instrukcji zamiast wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1ce87-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="1ce87-162">Jeśli program nie jest anulowana, tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1ce87-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
    ```  
  
     <span data-ttu-id="1ce87-163">Jeśli wybierzesz **anulować** przycisk przed pliki do pobrania są spełnione, dane wyjściowe zawierają długości materiałów do pobrania, które zakończone przed anulowania.</span><span class="sxs-lookup"><span data-stu-id="1ce87-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="1ce87-164">Przykłady ukończone</span><span class="sxs-lookup"><span data-stu-id="1ce87-164">Complete Examples</span></span>  
 <span data-ttu-id="1ce87-165">Poniższe sekcje zawierają kod dla każdego z poprzednich przykładach.</span><span class="sxs-lookup"><span data-stu-id="1ce87-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="1ce87-166">Zwróć uwagę, że musisz dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="1ce87-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="1ce87-167">Można pobrać projektów z [próbki Async: poprawnie dostrajanie Twoja aplikacja](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="1ce87-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="1ce87-168">Anuluj przykładowe zadania</span><span class="sxs-lookup"><span data-stu-id="1ce87-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="1ce87-169">Poniższy kod jest pełny plik MainWindow.xaml.vb na przykład, który anuluje jedno zadanie.</span><span class="sxs-lookup"><span data-stu-id="1ce87-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="1ce87-170">Anuluj listę przykładowe zadania</span><span class="sxs-lookup"><span data-stu-id="1ce87-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="1ce87-171">Poniższy kod jest pełny plik MainWindow.xaml.vb na przykład, który anuluje listy zadań.</span><span class="sxs-lookup"><span data-stu-id="1ce87-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ce87-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ce87-172">See Also</span></span>  
 <xref:System.Threading.CancellationTokenSource>  
 <xref:System.Threading.CancellationToken>  
 [<span data-ttu-id="1ce87-173">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce87-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="1ce87-174">Dostrajanie aplikacji Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ce87-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [<span data-ttu-id="1ce87-175">Próbka asynchronicznych: Dostrajanie aplikacji dokładnej</span><span class="sxs-lookup"><span data-stu-id="1ce87-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
