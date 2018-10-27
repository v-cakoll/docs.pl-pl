---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: c641c217b01e820e9a68065b0a56277a656ccc25
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034471"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="4a731-102">Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (C#)</span><span class="sxs-lookup"><span data-stu-id="4a731-102">Handling Reentrancy in Async Apps (C#)</span></span>
<span data-ttu-id="4a731-103">Po dołączeniu asynchronicznego kodu w aplikacji należy wziąć pod uwagę i ewentualnie zapobiec współużytkowaniu wątkowości, która odwołuje się do ponownego wprowadzania operacji asynchronicznej, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="4a731-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="4a731-104">Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="4a731-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="4a731-105">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="4a731-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="4a731-106">Uznawanie współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="4a731-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="4a731-107">Obsługa współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="4a731-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="4a731-108">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="4a731-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="4a731-109">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="4a731-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="4a731-110">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4a731-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="4a731-111">Przeglądanie i uruchamianie aplikacji przykładowych</span><span class="sxs-lookup"><span data-stu-id="4a731-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="4a731-112">Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4a731-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="4a731-113">Uznawanie współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="4a731-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="4a731-114">W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchroniczną aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które są pobierane.</span><span class="sxs-lookup"><span data-stu-id="4a731-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="4a731-115">Synchroniczna wersja przykładu reaguje w taki sam sposób, bez względu ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątek interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a731-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="4a731-116">W asynchronicznej aplikacji jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i można ponownie wprowadzić operację asynchroniczną przed jego ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="4a731-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="4a731-117">Poniższy przykład ukazuje oczekiwane dane wyjściowe, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4a731-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="4a731-118">Zostanie wyświetlona lista pobranych stron internetowych z rozmiar, w bajtach, w każdej lokacji.</span><span class="sxs-lookup"><span data-stu-id="4a731-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="4a731-119">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="4a731-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="4a731-120">Jednak jeśli użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany kilkakrotnie i proces pobierania jest ponownie inicjowany każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="4a731-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="4a731-121">W rezultacie kilka operacji asynchronicznych jest uruchomionych w tym samym czasie, dane wyjściowe przeplatają wyniki i całkowita liczba bajtów jest myląca ze.</span><span class="sxs-lookup"><span data-stu-id="4a731-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="4a731-122">Możesz przejrzeć kod, który generuje te dane wyjściowe przewijając do końca tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4a731-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="4a731-123">Możesz eksperymentować z kodem pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload, lub za pomocą kodu na końcu tego tematu, aby utworzyć własny projekt.</span><span class="sxs-lookup"><span data-stu-id="4a731-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="4a731-124">Aby uzyskać więcej informacji oraz instrukcje, zobacz [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="4a731-124">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="4a731-125">Obsługa współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="4a731-125">Handling Reentrancy</span></span>  
 <span data-ttu-id="4a731-126">Może obsługiwać współużytkowanie wątkowości na wiele sposobów, w zależności od tego, co ma robić Twoja aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4a731-126">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="4a731-127">Ten temat przedstawia następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="4a731-127">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="4a731-128">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="4a731-128">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="4a731-129">Wyłącz **Start** przycisku, gdy operacja jest uruchomiony, dzięki czemu użytkownik nie mógł jej przerwać.</span><span class="sxs-lookup"><span data-stu-id="4a731-129">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="4a731-130">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="4a731-130">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="4a731-131">Anulować wszelkie operacje, które wciąż działają, gdy użytkownik wybierze **Start** ponownie przycisk, a następnie kontynuuj umożliwiają niedawno żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="4a731-131">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="4a731-132">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4a731-132">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="4a731-133">Zezwalaj wszystkim wymaganym operacjom na uruchamianie asynchronicznie, ale Koordynuj dane wyjściowe, tak aby wyniki z każdej operacji były wyświetlane razem i w kolejności.</span><span class="sxs-lookup"><span data-stu-id="4a731-133">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="4a731-134">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="4a731-134">Disable the Start Button</span></span>  
 <span data-ttu-id="4a731-135">Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku u góry `StartButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a731-135">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="4a731-136">Następnie możesz ponownie włączyć przycisk od wewnątrz `finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą uruchamiać aplikację ponownie.</span><span class="sxs-lookup"><span data-stu-id="4a731-136">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="4a731-137">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="4a731-137">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4a731-138">Możesz również pobrać gotową aplikację z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="4a731-138">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4a731-139">Nazwa projektu to DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="4a731-139">The name of the project is DisableStartButton.</span></span>  
  
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
  
 <span data-ttu-id="4a731-140">W wyniku zmian przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobiera strony internetowe, dzięki czemu nie trzeba ponownie wprowadzić ten proces.</span><span class="sxs-lookup"><span data-stu-id="4a731-140">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="4a731-141">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="4a731-141">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="4a731-142">Zamiast wyłączać **Start** przycisku możesz zachować aktywny przycisk, ale, jeśli użytkownik wybierze ten przycisk ponownie, Anuluj operację, która jest już uruchomiona i umożliwić kontynuowanie operacji ostatnio rozpoczętej.</span><span class="sxs-lookup"><span data-stu-id="4a731-142">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="4a731-143">Aby uzyskać więcej informacji dotyczących anulowania, zobacz [Fine-Tuning aplikacji asynchronicznej (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="4a731-143">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="4a731-144">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="4a731-144">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4a731-145">Możesz również pobrać gotową aplikację z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="4a731-145">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4a731-146">Nazwa projektu to CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="4a731-146">The name of the project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="4a731-147">Zadeklaruj <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="4a731-147">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window   // Or class MainPage  
    {  
        // *** Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="4a731-148">W `StartButton_Click`, określić, czy operacja jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="4a731-148">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="4a731-149">Jeśli wartość `cts` jest wartość null, operacja nie jest już aktywny.</span><span class="sxs-lookup"><span data-stu-id="4a731-149">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="4a731-150">Jeśli wartość nie jest null, operacja, która jest już uruchomiona zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="4a731-150">If the value isn't null, the operation that is already running is canceled.</span></span>  
  
    ```csharp  
    // *** If a download process is already underway, cancel it.  
    if (cts != null)  
    {  
        cts.Cancel();  
    }  
    ```  
  
3.  <span data-ttu-id="4a731-151">Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="4a731-151">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```csharp  
    // *** Now set cts to a new value that you can use to cancel the current process  
    // if the button is chosen again.  
    CancellationTokenSource newCTS = new CancellationTokenSource();  
    cts = newCTS;  
    ```  
  
4.  <span data-ttu-id="4a731-152">Na koniec `StartButton_Click`, bieżący proces się zakończy, więc ustaw wartość `cts` powrót do wartości null.</span><span class="sxs-lookup"><span data-stu-id="4a731-152">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>  
  
    ```csharp  
    // *** When the process is complete, signal that another process can begin.  
    if (cts == newCTS)  
        cts = null;  
    ```  
  
 <span data-ttu-id="4a731-153">Poniższy kod pokazuje wszystkie zmiany w `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4a731-153">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="4a731-154">Dodatki są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="4a731-154">The additions are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="4a731-155">W `AccessTheWebAsync`, wprowadź następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="4a731-155">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="4a731-156">Dodaj parametr do akceptowania tokenu odwołania z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4a731-156">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="4a731-157">Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody do pobierania witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.</span><span class="sxs-lookup"><span data-stu-id="4a731-157">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="4a731-158">Przed wywołaniem `DisplayResults` do wyświetlania wyników dla każdej pobranej witryny sieci Web, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="4a731-158">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="4a731-159">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="4a731-159">The following code shows these changes, which are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="4a731-160">Jeśli wybierzesz **Start** przycisk kilka razy ta aplikacja jest uruchomiona, powinno to dawać wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4a731-160">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="4a731-161">Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w `StartButton_Click` aby czyścić pole tekstowe za każdym razem, kiedy użytkownik uruchamia operację.</span><span class="sxs-lookup"><span data-stu-id="4a731-161">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="4a731-162">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4a731-162">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="4a731-163">Trzeci przykład jest najbardziej skomplikowany, w tym, że aplikacja rozpoczyna kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze **Start** przycisk, a wszystkie operacje do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="4a731-163">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="4a731-164">Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są przedstawiane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="4a731-164">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="4a731-165">Oznacza to, że rzeczywiste działanie pobierania odbywa się z przeplotem, jako dane wyjściowe w [rozpoznawaniu współużytkowania wątkowości](#BKMK_RecognizingReentrancy) pokazuje, ale lista wyników dla każdej grupy jest prezentowana oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="4a731-165">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="4a731-166">Operacje współkorzystają z globalnego <xref:System.Threading.Tasks.Task>, `pendingWork`, który służy jako strażnik dla procesu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="4a731-166">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  

 <span data-ttu-id="4a731-167">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="4a731-167">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="4a731-168">Możesz również pobrać gotową aplikację z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="4a731-168">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="4a731-169">Nazwa projektu jest QueueResults.</span><span class="sxs-lookup"><span data-stu-id="4a731-169">The name of the project is QueueResults.</span></span>  
   
 <span data-ttu-id="4a731-170">Następujące dane wyjściowe pokazują wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="4a731-170">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="4a731-171">Etykieta litery A, wskazuje, że wynik dotyczy po raz pierwszy **Start** wciśnięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="4a731-171">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="4a731-172">Liczby pokazują kolejność adresów URL na liście elementów docelowych pobierania.</span><span class="sxs-lookup"><span data-stu-id="4a731-172">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="4a731-173">Jeśli użytkownik wybierze **Start** przycisk trzy razy, aplikacja generuje dane wyjściowe podobne do następujących wierszy.</span><span class="sxs-lookup"><span data-stu-id="4a731-173">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="4a731-174">Linie informacyjne, rozpoczynające się od znaku funta Zaloguj (#) śledzą postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a731-174">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="4a731-175">Grupy B i C uruchomić przed grupy A zostało zakończone, ale dane wyjściowe dla każdej grupy pojawiają się oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="4a731-175">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="4a731-176">Wszystkie dane wyjściowe dla grupy A pojawiają się pierwsze, wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i, dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, adresy URL są wyświetlane na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="4a731-176">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="4a731-177">Jednak nie można przewidzieć kolejności, w której rzeczywiście wystąpi pobieranie.</span><span class="sxs-lookup"><span data-stu-id="4a731-177">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="4a731-178">Po uruchomieniu wielu grup zadań pobierania, które generują wszystkie są aktywne.</span><span class="sxs-lookup"><span data-stu-id="4a731-178">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="4a731-179">Nie można zakładać, że A-1 będą pobierane przed b-1 i nie można zakładać, że A-1 będą pobierane przed A-2.</span><span class="sxs-lookup"><span data-stu-id="4a731-179">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="4a731-180">Globalne definicje</span><span class="sxs-lookup"><span data-stu-id="4a731-180">Global Definitions</span></span>  
 <span data-ttu-id="4a731-181">Przykładowy kod zawiera poniższe dwie deklaracje globalne, które są widoczne ze wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="4a731-181">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```csharp  
public partial class MainWindow : Window  // Class MainPage in Windows Store app.  
{  
    // ***Declare the following variables where all methods can access them.   
    private Task pendingWork = null;     
    private char group = (char)('A' - 1);  
```  
  
 <span data-ttu-id="4a731-182">`Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i zapobiega żadnej grupy zakłócania pracy wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="4a731-182">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="4a731-183">Zmienna znaku `group`, oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4a731-183">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="4a731-184">Program obsługi zdarzeń kliknięcie</span><span class="sxs-lookup"><span data-stu-id="4a731-184">The Click Event Handler</span></span>  
 <span data-ttu-id="4a731-185">Program obsługi zdarzeń `StartButton_Click`, rośnie literę grupy za każdym razem, użytkownik wybierze **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4a731-185">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="4a731-186">Następnie program obsługi zdarzeń wywołuje `AccessTheWebAsync` można uruchomić operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="4a731-186">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
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
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="4a731-187">The AccessTheWebAsync Method</span><span class="sxs-lookup"><span data-stu-id="4a731-187">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="4a731-188">Ten przykład dzieli `AccessTheWebAsync` na dwie metody.</span><span class="sxs-lookup"><span data-stu-id="4a731-188">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="4a731-189">Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania dla grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="4a731-189">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="4a731-190">Metoda wykorzystuje Language Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> można uruchomić zadania pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="4a731-190">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="4a731-191">`AccessTheWebAsync` następnie wywołuje `FinishOneGroupAsync` oczekiwać na zakończenie każdego pobrania i wyświetlić jego długość.</span><span class="sxs-lookup"><span data-stu-id="4a731-191">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="4a731-192">`FinishOneGroupAsync` Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="4a731-192">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="4a731-193">Ta wartość zapobiega przerywaniu przez inną operację przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="4a731-193">That value prevents interruption by another operation before the task is complete.</span></span>  
  
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
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="4a731-194">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="4a731-194">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="4a731-195">Ta metoda przechodzi cyklicznie przez zadania pobierania w grupie, oczekujące na każdym z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do całkowitej.</span><span class="sxs-lookup"><span data-stu-id="4a731-195">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="4a731-196">Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub która już oczekuje.</span><span class="sxs-lookup"><span data-stu-id="4a731-196">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="4a731-197">Jeśli taka operacja jest w toku, wchodząca operacja musi czekać na swoją kolej.</span><span class="sxs-lookup"><span data-stu-id="4a731-197">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
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
  
   
#### <a name="points-of-interest"></a><span data-ttu-id="4a731-198">Punktów orientacyjnych</span><span class="sxs-lookup"><span data-stu-id="4a731-198">Points of Interest</span></span>  
 <span data-ttu-id="4a731-199">Linie informacyjne, rozpoczynające się od znaku funta (#) w danych wyjściowych objaśnić, jak działa ten przykład.</span><span class="sxs-lookup"><span data-stu-id="4a731-199">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="4a731-200">Dane wyjściowe pokazują następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="4a731-200">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="4a731-201">Grupę można uruchomić podczas poprzedniej grupy jest wyświetlanie danych wyjściowych, ale wyświetlanie danych wyjściowych poprzedniej grupy nie zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="4a731-201">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="4a731-202">`pendingWork` Zadania ma wartość null na początku `FinishOneGroupAsync` tylko dla grupy A, uruchomionej w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="4a731-202">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="4a731-203">Grupa A jeszcze nie zakończyła wykonywania wyrażenia oczekiwania, po osiągnięciu `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="4a731-203">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="4a731-204">W związku z tym, formant nie wrócił do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpiło.</span><span class="sxs-lookup"><span data-stu-id="4a731-204">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="4a731-205">Następujące dwa wiersze zawsze pojawiają się razem w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4a731-205">The following two lines always appear together in the output.</span></span> <span data-ttu-id="4a731-206">Kod nigdy nie jest przerywany między rozpoczęciem operacji grupy `StartButton_Click` i przypisywaniem zadania dla grupy w celu `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="4a731-206">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="4a731-207">Po przejściu grupy do stanu `StartButton_Click`, operacja nie kończy się i wyrażenie oczekuje, aż operacja wejdzie w stan `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="4a731-207">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="4a731-208">Dlatego żadna inna operacja może przejmować kontroli w tym segmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="4a731-208">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="4a731-209">Przeglądanie i uruchamianie aplikacji przykładowych</span><span class="sxs-lookup"><span data-stu-id="4a731-209">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="4a731-210">Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować ją samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4a731-210">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a731-211">Aby uruchomić przykład jako aplikację pulpitu Windows Presentation Foundation (WPF), konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="4a731-211">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="4a731-212">Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a731-212">Downloading the App</span></span>  
  
1.  <span data-ttu-id="4a731-213">Pobierz skompresowany plik z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="4a731-213">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="4a731-214">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a731-214">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="4a731-215">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="4a731-215">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="4a731-216">Przejdź do folderu, który posiada zdekompresowany kod przykładu, a następnie otwórz plik rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="4a731-216">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="4a731-217">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="4a731-217">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="4a731-218">Wybierz kombinację klawiszy CTRL + F5 Aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="4a731-218">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="4a731-219">Kompilowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="4a731-219">Building the App</span></span>  
 <span data-ttu-id="4a731-220">W poniższej sekcji przedstawiono kod, aby zbudować przykład jako aplikację WPF.</span><span class="sxs-lookup"><span data-stu-id="4a731-220">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="4a731-221">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="4a731-221">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="4a731-222">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a731-222">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4a731-223">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="4a731-223">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="4a731-224">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="4a731-224">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="4a731-225">W **zainstalowane szablony** okienku rozwiń **Visual C#**, a następnie rozwiń węzeł **Windows**.</span><span class="sxs-lookup"><span data-stu-id="4a731-225">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="4a731-226">Na liście typów projektów, wybierz opcję **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="4a731-226">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="4a731-227">Nadaj projektowi nazwę `WebsiteDownloadWPF`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="4a731-227">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="4a731-228">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4a731-228">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="4a731-229">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="4a731-229">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="4a731-230">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="4a731-230">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="4a731-231">W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4a731-231">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="4a731-232">Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="4a731-232">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="4a731-233">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="4a731-233">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="4a731-234">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="4a731-234">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="4a731-235">W MainWindow.xaml.cs Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="4a731-235">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
                    "https://msdn.microsoft.com/library/hh191443.aspx",  
                    "https://msdn.microsoft.com/library/aa578028.aspx",  
                    "https://msdn.microsoft.com/library/jj155761.aspx",  
                    "https://msdn.microsoft.com/library/hh290140.aspx",  
                    "https://msdn.microsoft.com/library/hh524395.aspx",  
                    "https://msdn.microsoft.com/library/ms404677.aspx",  
                    "https://msdn.microsoft.com",  
                    "https://msdn.microsoft.com/library/ff730837.aspx"  
                };  
                return urls;  
            }  
  
            private void DisplayResults(string url, byte[] content, int pos)  
            {  
                // Display the length of each website. The string format is designed  
                // to be used with a monospaced font, such as Lucida Console or   
                // Global Monospace.  
  
                // Strip off the "https://".  
                var displayURL = url.Replace("https://", "");  
                // Display position in the URL list, the URL, and the number of bytes.  
                ResultsTextBox.Text += string.Format("\n{0}. {1,-58} {2,8}", pos, displayURL, content.Length);  
            }  
        }  
    }  
    ```  
  
11. <span data-ttu-id="4a731-236">Wybierz klawisze CTRL + F5, aby uruchomić program, a następnie wybierz **Start** przycisk kilka razy.</span><span class="sxs-lookup"><span data-stu-id="4a731-236">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="4a731-237">Wprowadź zmiany w [Wyłącz przycisk Start](#BKMK_DisableTheStartButton), [anulowania i ponownego uruchamiania operacji](#BKMK_CancelAndRestart), lub [uruchomić wiele operacji i kolejki danych wyjściowych](#BKMK_RunMultipleOperations) do obsługi współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="4a731-237">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a731-238">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a731-238">See Also</span></span>

- [<span data-ttu-id="4a731-239">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="4a731-239">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="4a731-240">Programowanie asynchroniczne z async i await (C#)</span><span class="sxs-lookup"><span data-stu-id="4a731-240">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
