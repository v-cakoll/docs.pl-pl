---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: f2b43bd982b7dcd1f4641ae55f95595d14d70b0b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="3762a-102">Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="3762a-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="3762a-103">Po dołączeniu kodu asynchroniczne w aplikacji należy wziąć pod uwagę i prawdopodobnie zapobiec ponowne wejście, który odwołuje się do ponownego wprowadzania operację asynchroniczną, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="3762a-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="3762a-104">Jeśli nie identyfikowania i obsługi możliwości ponownego rozpoczęcia, może spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="3762a-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="3762a-105">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="3762a-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="3762a-106">Rozpoznawanie Wielobieżność</span><span class="sxs-lookup"><span data-stu-id="3762a-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="3762a-107">Obsługa ponownego rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="3762a-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="3762a-108">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="3762a-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="3762a-109">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="3762a-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="3762a-110">Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="3762a-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="3762a-111">Przeglądanie i uruchamianie przykładową aplikację</span><span class="sxs-lookup"><span data-stu-id="3762a-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="3762a-112">Aby uruchomić przykład, musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3762a-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="3762a-113">Rozpoznawanie Wielobieżność</span><span class="sxs-lookup"><span data-stu-id="3762a-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="3762a-114">W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchronicznego aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które zostaną pobrane.</span><span class="sxs-lookup"><span data-stu-id="3762a-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="3762a-115">Synchroniczną wersję przykładu będzie odpowiadać taki sam sposób niezależnie od ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątku interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się aplikacja działa.</span><span class="sxs-lookup"><span data-stu-id="3762a-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="3762a-116">W aplikacji asynchroniczne jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i może ponownie operację asynchroniczną, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="3762a-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="3762a-117">W poniższym przykładzie przedstawiono oczekiwanych danych wyjściowych, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3762a-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="3762a-118">Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiar w bajtach, w każdej lokacji.</span><span class="sxs-lookup"><span data-stu-id="3762a-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="3762a-119">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="3762a-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="3762a-120">Jednak jeśli użytkownik wybierze przycisk więcej niż raz, program obsługi zdarzeń jest wywoływany wielokrotnie i proces pobierania jest ponownie wprowadzić hasło zawsze.</span><span class="sxs-lookup"><span data-stu-id="3762a-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="3762a-121">W związku z tym kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przeplata wyniki, a całkowita liczba bajtów jest myląca.</span><span class="sxs-lookup"><span data-stu-id="3762a-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="3762a-122">Możesz przejrzeć kod, który generuje dane wyjściowe w tym przewijając na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="3762a-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="3762a-123">Możesz eksperymentować z kodem pobrać rozwiązanie na komputerze lokalnym, a następnie uruchamiając projekt WebsiteDownload lub przy użyciu kodu na końcu tego tematu, aby utworzyć własny projekt.</span><span class="sxs-lookup"><span data-stu-id="3762a-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="3762a-124">Aby uzyskać więcej informacji oraz instrukcje, zobacz [przeglądanie i uruchamianie aplikacji przykład](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="3762a-124">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="3762a-125">Obsługa ponownego rozpoczęcia</span><span class="sxs-lookup"><span data-stu-id="3762a-125">Handling Reentrancy</span></span>  
 <span data-ttu-id="3762a-126">Wielobieżność na różne sposoby, w zależności od tego, co ma aplikację w celu może obsłużyć.</span><span class="sxs-lookup"><span data-stu-id="3762a-126">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="3762a-127">W tym temacie przedstawiono następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="3762a-127">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="3762a-128">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="3762a-128">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="3762a-129">Wyłącz **Start** przycisk podczas operacji jest uruchomiona, dzięki czemu użytkownik nie może przerwać go.</span><span class="sxs-lookup"><span data-stu-id="3762a-129">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="3762a-130">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="3762a-130">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="3762a-131">Anuluj wszelkie operacje, który jest nadal uruchomiona, gdy użytkownik wybierze **Start** przycisk ponownie, a następnie kontynuuj let najbardziej ostatnio żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="3762a-131">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="3762a-132">Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="3762a-132">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="3762a-133">Zezwalaj na wszystkie żądane operacje wykonywane asynchronicznie, ale koordynuje wyświetlania danych wyjściowych, aby jednocześnie i w kolejności zostaną wyświetlone wyniki z każdej operacji.</span><span class="sxs-lookup"><span data-stu-id="3762a-133">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="3762a-134">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="3762a-134">Disable the Start Button</span></span>  
 <span data-ttu-id="3762a-135">Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku w górnej części `StartButton_Click` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="3762a-135">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="3762a-136">Następnie można ponownie włączyć za pomocą przycisku `finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą ponownie uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3762a-136">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="3762a-137">Aby skonfigurować ten scenariusz, wprowadź następujące zmiany do podstawowego kodu, który znajduje się w [przeglądanie i uruchamianie aplikacji przykład](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="3762a-137">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="3762a-138">Możesz również pobrać Zakończono aplikacji z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="3762a-138">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="3762a-139">Nazwa projektu jest DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="3762a-139">The name of the project is DisableStartButton.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Text = "";  
  
    // ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = false;   
  
    try  
    {  
        await AccessTheWebAsync();  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
    // ***Enable the Start button in case you want to run the program again.   
    finally  
    {  
        StartButton.IsEnabled = true;  
    }  
}  
```  
  
 <span data-ttu-id="3762a-140">W wyniku zmian, przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobierania witryny sieci Web, więc nie można ponownie wprowadzić hasło procesu.</span><span class="sxs-lookup"><span data-stu-id="3762a-140">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="3762a-141">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="3762a-141">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="3762a-142">Zamiast wyłączenie **Start** przycisku, można zachować aktywnego przycisku, ale, jeśli użytkownik wybierze ponownie, ten przycisk Anuluj operację, która jest już uruchomiona i kontynuowania operacji najbardziej ostatnio uruchomiono.</span><span class="sxs-lookup"><span data-stu-id="3762a-142">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="3762a-143">Aby uzyskać więcej informacji na temat anulowania, zobacz [Fine-Tuning Twoja aplikacja Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="3762a-143">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="3762a-144">Aby skonfigurować ten scenariusz, wprowadź następujące zmiany do podstawowego kodu, który znajduje się w [przeglądanie i uruchamianie aplikacji przykład](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="3762a-144">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="3762a-145">Możesz również pobrać Zakończono aplikacji z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="3762a-145">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="3762a-146">Nazwa projektu jest CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="3762a-146">The name of the project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="3762a-147">Deklarowanie <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="3762a-147">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="3762a-148">W `StartButton_Click`, określić, czy operacja jest już przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="3762a-148">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="3762a-149">Jeśli wartość `cts` jest wartość null, nie jest operacja już aktywne.</span><span class="sxs-lookup"><span data-stu-id="3762a-149">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="3762a-150">Jeśli wartość nie jest pusta, zostaną anulowane operacja, która jest już uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="3762a-150">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="3762a-151">Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="3762a-151">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="3762a-152">Na koniec `StartButton_Click`, bieżący proces zostanie zakończony, a więc ustaw wartość `cts` do wartości null.</span><span class="sxs-lookup"><span data-stu-id="3762a-152">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="3762a-153">Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="3762a-153">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="3762a-154">Dodatki są oznaczone gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="3762a-154">The additions are marked with asterisks.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // This line is commented out to make the results clearer in the output.  
    //ResultsTextBox.Clear();  
  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
  
    // *** Now set cts to cancel the current process if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
  
    try  
    {  
        // ***Send cts.Token to carry the message if there is a cancellation request.  
        await AccessTheWebAsync(cts.Token);  
  
    }  
    // *** Catch cancellations separately.  
    catch (OperationCanceledException)  
    {  
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";  
    }  
    // *** When the process is complete, signal that another process can proceed.  
    if (cts == newCTS)  
        cts = null;  
}  
```  
  
 <span data-ttu-id="3762a-155">W `AccessTheWebAsync`, wprowadź następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="3762a-155">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="3762a-156">Dodawanie parametru do akceptowania token anulowania z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="3762a-156">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="3762a-157">Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metodę, aby pobrać witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.</span><span class="sxs-lookup"><span data-stu-id="3762a-157">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="3762a-158">Przed wywołaniem `DisplayResults` do wyświetlenia wyników dla poszczególnych witryn pobrany, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="3762a-158">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="3762a-159">Poniższy kod przedstawia te zmiany, które są oznaczone ikoną z gwiazdki.</span><span class="sxs-lookup"><span data-stu-id="3762a-159">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```csharp  
// *** Provide a parameter for the CancellationToken from StartButton_Click.  
async Task AccessTheWebAsync(CancellationToken ct)  
{  
    // Declare an HttpClient object.  
    HttpClient client = new HttpClient();  
  
    // Make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
  
    var total = 0;  
    var position = 0;  
  
    foreach (var url in urlList)  
    {  
        // *** Use the HttpClient.GetAsync method because it accepts a   
        // cancellation token.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // *** Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // *** Check for cancellations before displaying information about the   
        // latest site.   
        ct.ThrowIfCancellationRequested();  
  
        DisplayResults(url, urlContents, ++position);  
  
        // Update the total.  
        total += urlContents.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}     
```  
  
 <span data-ttu-id="3762a-160">Jeśli wybierzesz **Start** przycisk kilka razy uruchomiona ta aplikacja powinna generować wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3762a-160">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="3762a-161">Aby wyeliminować częściowej listy, usuń znaczniki komentarza pierwszego wiersza kodu w `StartButton_Click` do wyczyść pola tekstowego użytkownik uruchamia ponownie wykonać operację.</span><span class="sxs-lookup"><span data-stu-id="3762a-161">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="3762a-162">Uruchamianie wielu operacji i danych wyjściowych w kolejce</span><span class="sxs-lookup"><span data-stu-id="3762a-162">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="3762a-163">W tym przykładzie trzeci jest najbardziej skomplikowanych, że operacja asynchroniczna za każdym razem, użytkownik zdecyduje się na uruchomieniu aplikacji **Start** przycisk, a wszystkie operacje uruchomienia aż do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="3762a-163">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="3762a-164">Żądanych operacji pobierania witryny sieci Web z listy asynchronicznie, ale dane wyjściowe z działania są prezentowane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="3762a-164">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="3762a-165">Oznacza to, że przeplatana rzeczywistego działania pobierania jako danych wyjściowych w [rozpoznawanie Wielobieżność](#BKMK_RecognizingReentrancy) pokazuje, ale lista wyników dla każdej grupy są przedstawione oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="3762a-165">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="3762a-166">Operacje udostępniania globalnym <xref:System.Threading.Tasks.Task>, `pendingWork`, która służy jako kontroler proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="3762a-166">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  

 <span data-ttu-id="3762a-167">Aby skonfigurować ten scenariusz, wprowadź następujące zmiany do podstawowego kodu, który znajduje się w [przeglądanie i uruchamianie aplikacji przykład](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="3762a-167">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="3762a-168">Możesz również pobrać Zakończono aplikacji z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="3762a-168">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="3762a-169">Nazwa projektu jest QueueResults.</span><span class="sxs-lookup"><span data-stu-id="3762a-169">The name of the project is QueueResults.</span></span>  
   
 <span data-ttu-id="3762a-170">Następujące dane wyjściowe przedstawia wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="3762a-170">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="3762a-171">Etykieta litera, A, wskazuje, że wynik jest od momentu pierwszego **Start** przycisk zostanie wybrany.</span><span class="sxs-lookup"><span data-stu-id="3762a-171">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="3762a-172">Numery wyświetlić kolejność adresów URL na liście elementów docelowych pobierania.</span><span class="sxs-lookup"><span data-stu-id="3762a-172">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="3762a-173">Jeśli użytkownik zdecyduje się **Start** trzy razy przycisk, aplikacja generuje dane wyjściowe podobne następujące wiersze.</span><span class="sxs-lookup"><span data-stu-id="3762a-173">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="3762a-174">Wiersze informacji rozpoczynających się od krzyżyk podpisać śledzenia (#) postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3762a-174">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="3762a-175">Grupy B i C uruchomić przed zakończył grupy A, ale dane wyjściowe dla każdej grupy jest wyświetlany osobno.</span><span class="sxs-lookup"><span data-stu-id="3762a-175">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="3762a-176">Wszystkie dane wyjściowe dla grupy A występuje jako pierwszy, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grup w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności adresy URL są wyświetlane na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="3762a-176">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="3762a-177">Jednak nie można przewidzieć kolejność, w którym rzeczywistego wystąpienia pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="3762a-177">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="3762a-178">Po uruchomieniu wielu grup zadań pobierania, które generują one są wszystkie aktywne.</span><span class="sxs-lookup"><span data-stu-id="3762a-178">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="3762a-179">Nie można zakładać, że a – 1 zostaną pobrane przed b-1 i nie można zakładać, że a – 1 zostaną pobrane przed A-2.</span><span class="sxs-lookup"><span data-stu-id="3762a-179">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="3762a-180">Definicje globalnej</span><span class="sxs-lookup"><span data-stu-id="3762a-180">Global Definitions</span></span>  
 <span data-ttu-id="3762a-181">Przykładowy kod zawiera następujące dwa deklaracje globalne, które są widoczne na wszystkie metody.</span><span class="sxs-lookup"><span data-stu-id="3762a-181">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="3762a-182">`Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i uniemożliwia dowolną grupę zakłócania pracy wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="3762a-182">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="3762a-183">Zmienna znak `group`, dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności etykiet.</span><span class="sxs-lookup"><span data-stu-id="3762a-183">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="3762a-184">Obsługi zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="3762a-184">The Click Event Handler</span></span>  
 <span data-ttu-id="3762a-185">Program obsługi zdarzeń, `StartButton_Click`, rośnie litery grupy za każdym razem, użytkownik wybierze **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3762a-185">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="3762a-186">Następnie wywołań obsługi `AccessTheWebAsync` się uruchomić operacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="3762a-186">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```csharp  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ***Verify that each group's results are displayed together, and that  
    // the groups display in order, by marking each group with a letter.  
    group = (char)(group + 1);  
    ResultsTextBox.Text += string.Format("\r\n\r\n#Starting group {0}.", group);  
  
    try  
    {  
        // *** Pass the group value to AccessTheWebAsync.  
        char finishedGroup = await AccessTheWebAsync(group);  
  
        // The following line verifies a successful return from the download and  
        // display procedures.   
        ResultsTextBox.Text += string.Format("\r\n\r\n#Group {0} is complete.\r\n", finishedGroup);  
    }  
    catch (Exception)  
    {  
        ResultsTextBox.Text += "\r\nDownloads failed.";  
    }  
}  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="3762a-187">The AccessTheWebAsync Method</span><span class="sxs-lookup"><span data-stu-id="3762a-187">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="3762a-188">W tym przykładzie dzieli `AccessTheWebAsync` do dwóch metod.</span><span class="sxs-lookup"><span data-stu-id="3762a-188">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="3762a-189">Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="3762a-189">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="3762a-190">Metoda używa języka zapytanie zintegrowanym (LINQ query) i <xref:System.Linq.Enumerable.ToArray%2A> uruchomić wszystkie zadania pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="3762a-190">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="3762a-191">`AccessTheWebAsync` następnie wywołuje `FinishOneGroupAsync` poczekać na ukończenie każdego pobrania i wyświetlenia jej długość.</span><span class="sxs-lookup"><span data-stu-id="3762a-191">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="3762a-192">`FinishOneGroupAsync` Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="3762a-192">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3762a-193">Czy wartość zapobiega przerwania przez inną operację przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="3762a-193">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```csharp  
private async Task<char> AccessTheWebAsync(char grp)  
{  
    HttpClient client = new HttpClient();  
  
    // Make a list of the web addresses to download.  
    List<string> urlList = SetUpURLList();  
  
    // ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();  
  
    // ***Call the method that awaits the downloads and displays the results.  
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);  
  
    ResultsTextBox.Text += string.Format("\r\n#Task assigned for group {0}. Download tasks are active.\r\n", grp);  
  
    // ***This task is complete when a group has finished downloading and displaying.  
    await pendingWork;  
  
    // You can do other work here or just return.  
    return grp;  
}  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="3762a-194">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="3762a-194">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="3762a-195">Ta metoda przełączanie po kolei zadania pobierania w grupie, oczekiwanie na każdym z nich, wyświetlanie długość pobrany witryny sieci Web i dodawanie długość do całkowitej.</span><span class="sxs-lookup"><span data-stu-id="3762a-195">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="3762a-196">Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzanie metody zakłócał operacja, która jest już w procesie wyświetlania lub już jest oczekiwane.</span><span class="sxs-lookup"><span data-stu-id="3762a-196">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="3762a-197">Jeśli takie działanie jest w toku, wprowadzając operacji oczekiwania kolei.</span><span class="sxs-lookup"><span data-stu-id="3762a-197">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```csharp  
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)  
{  
    // ***Wait for the previous group to finish displaying results.  
    if (pendingWork != null) await pendingWork;  
  
    int total = 0;  
  
    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    for (int i = 0; i < contentTasks.Length; i++)  
    {  
        // Await the download of a particular URL, and then display the URL and  
        // its length.  
        byte[] content = await contentTasks[i];  
        DisplayResults(urls[i], content, i, grp);  
        total += content.Length;  
    }  
  
    // Display the total count for all of the websites.  
    ResultsTextBox.Text +=  
        string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
}  
```  
  
   
#### <a name="points-of-interest"></a><span data-ttu-id="3762a-198">Ważne</span><span class="sxs-lookup"><span data-stu-id="3762a-198">Points of Interest</span></span>  
 <span data-ttu-id="3762a-199">Wiersze informacji rozpoczynające się znakiem numeru (#) w danych wyjściowych wyjaśnienie, jak działa w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3762a-199">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="3762a-200">Dane wyjściowe zawierają następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="3762a-200">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="3762a-201">Grupy można uruchomić podczas poprzedniej grupy są wyświetlane dane wyjściowe, ale nie jest przerywana wyświetlanie wynik poprzedniego grupy.</span><span class="sxs-lookup"><span data-stu-id="3762a-201">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="3762a-202">`pendingWork` Zadań ma wartość null na początku `FinishOneGroupAsync` tylko dla grupy A, które uruchamiane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="3762a-202">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="3762a-203">Grupy A jeszcze nie ukończone wyrażenie await, po osiągnięciu `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="3762a-203">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="3762a-204">W związku z tym kontroli nie zwróciła do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpił.</span><span class="sxs-lookup"><span data-stu-id="3762a-204">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="3762a-205">Następujące dwa wiersze zawsze występować razem w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3762a-205">The following two lines always appear together in the output.</span></span> <span data-ttu-id="3762a-206">Ten kod nie przerywa pracy między uruchamiania operacji grupy `StartButton_Click` i przypisywanie zadań dla grupy w celu `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="3762a-206">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="3762a-207">Po wprowadzeniu grupy `StartButton_Click`, operacja nie wykona wyrażenie await do czasu operacji wejścia `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="3762a-207">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="3762a-208">W związku z tym żadnych innych operacji przejąć kontrolę podczas tego segmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="3762a-208">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="3762a-209">Przeglądanie i uruchamianie przykładową aplikację</span><span class="sxs-lookup"><span data-stu-id="3762a-209">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="3762a-210">Aby lepiej zrozumieć przykładową aplikację, można go pobrać, kompilacji samodzielnie lub przejrzeć kod na końcu tego tematu bez stosowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3762a-210">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3762a-211">Do uruchomienia w przykładzie jako aplikację pulpitu systemu Windows Presentation Foundation (WPF), musi mieć program Visual Studio 2012 lub nowszej i .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="3762a-211">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="3762a-212">Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3762a-212">Downloading the App</span></span>  
  
1.  <span data-ttu-id="3762a-213">Pobierz skompresowany plik z [przykłady Async: ponownego rozpoczęcia w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="3762a-213">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="3762a-214">Dekompresja pobranego pliku, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3762a-214">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="3762a-215">Na pasku menu wybierz **pliku**, **Otwórz**, **projektu/rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="3762a-215">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="3762a-216">Przejdź do folderu, który przechowuje zdekompresowanych przykładowy kod, a następnie otwórz plik rozwiązania (sln).</span><span class="sxs-lookup"><span data-stu-id="3762a-216">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="3762a-217">W **Eksploratora rozwiązań**, otwórz menu skrótów projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="3762a-217">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="3762a-218">Wybierz klawisze CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="3762a-218">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="3762a-219">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="3762a-219">Building the App</span></span>  
 <span data-ttu-id="3762a-220">W poniższej sekcji przedstawiono kod służący do kompilacji w przykładzie jako aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="3762a-220">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="3762a-221">Do utworzenia aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="3762a-221">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="3762a-222">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3762a-222">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3762a-223">Na pasku menu wybierz **pliku**, **nowy**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="3762a-223">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="3762a-224">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3762a-224">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3762a-225">W **zainstalowane szablony** okienku rozwiń **Visual C#**, a następnie rozwiń węzeł **Windows**.</span><span class="sxs-lookup"><span data-stu-id="3762a-225">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="3762a-226">Lista typów projektów, wybranie **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="3762a-226">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="3762a-227">Nazwij projekt `WebsiteDownloadWPF`, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="3762a-227">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="3762a-228">Nowy projekt zostanie wyświetlony w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3762a-228">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="3762a-229">Wybierz w Visual Studio Code edytorze **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="3762a-229">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="3762a-230">Jeśli karta jest niewidoczna, otwórz menu skrótów MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz pozycję **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="3762a-230">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="3762a-231">W **XAML** widoku MainWindow.xaml, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="3762a-231">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="WebsiteDownloadWPF.MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="3762a-232">Proste okna, który zawiera pole tekstowe i przycisk pojawia się w **projekt** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="3762a-232">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="3762a-233">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="3762a-233">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="3762a-234">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="3762a-234">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="3762a-235">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="3762a-235">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
    using System.Threading;  
  
    namespace WebsiteDownloadWPF  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void StartButton_Click(object sender, RoutedEventArgs e)  
            {  
                // This line is commented out to make the results clearer in the output.  
                //ResultsTextBox.Text = "";  
  
                try  
                {  
                    await AccessTheWebAsync();  
                }  
                catch (Exception)  
                {  
                    ResultsTextBox.Text += "\r\nDownloads failed.";  
                }  
            }  
  
            private async Task AccessTheWebAsync()  
            {  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                // Make a list of web addresses.  
                List<string> urlList = SetUpURLList();  
  
                var total = 0;  
                var position = 0;  
  
                foreach (var url in urlList)  
                {  
                    // GetByteArrayAsync returns a task. At completion, the task  
                    // produces a byte array.  
                    byte[] urlContents = await client.GetByteArrayAsync(url);  
  
                    DisplayResults(url, urlContents, ++position);  
  
                    // Update the total.  
                    total += urlContents.Length;  
                }  
  
                // Display the total count for all of the websites.  
                ResultsTextBox.Text +=  
                    string.Format("\r\n\r\nTOTAL bytes returned:  {0}\r\n", total);  
            }  
  
            private List<string> SetUpURLList()  
            {  
                List<string> urls = new List<string>   
                {   
                    "http://msdn.microsoft.com/library/hh191443.aspx",  
                    "http://msdn.microsoft.com/library/aa578028.aspx",  
                    "http://msdn.microsoft.com/library/jj155761.aspx",  
                    "http://msdn.microsoft.com/library/hh290140.aspx",  
                    "http://msdn.microsoft.com/library/hh524395.aspx",  
                    "http://msdn.microsoft.com/library/ms404677.aspx",  
                    "http://msdn.microsoft.com",  
                    "http://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "http://".  
                var displayURL = url.Replace("http://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="3762a-236">Wybierz klawiszy CTRL + F5, uruchom program, a następnie wybierz pozycję **Start** przycisk kilka razy.</span><span class="sxs-lookup"><span data-stu-id="3762a-236">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="3762a-237">Wprowadź zmiany z [Wyłącz przycisk Start](#BKMK_DisableTheStartButton), [Anuluj i ponownie uruchom operację](#BKMK_CancelAndRestart), lub [uruchomić wiele operacji i kolejki danych wyjściowych](#BKMK_RunMultipleOperations) do obsługi ponownego rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="3762a-237">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3762a-238">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3762a-238">See Also</span></span>  
 [<span data-ttu-id="3762a-239">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="3762a-239">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="3762a-240">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="3762a-240">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
