---
title: Obsługa reentrancy w aplikacjach Async (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: d46a87ed2200dc92b8e3d23be80306a31a01e501
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738305"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="5db15-102">Obsługa reentrancy w aplikacjach Async (C#)</span><span class="sxs-lookup"><span data-stu-id="5db15-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="5db15-103">Po dołączeniu kodu asynchroniowego w aplikacji, należy rozważyć i ewentualnie zapobiec reentrancy, który odnosi się do ponownego wniesienia operacji asynchroniiowej przed jej zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="5db15-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="5db15-104">Jeśli nie zidentyfikujesz i nie poradzisz sobie z możliwościami ponownego wniesienia, może to spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="5db15-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="5db15-105">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="5db15-105">**In this topic**</span></span>

- [<span data-ttu-id="5db15-106">Rozpoznawanie reentrancy</span><span class="sxs-lookup"><span data-stu-id="5db15-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="5db15-107">Obsługa reentrancy</span><span class="sxs-lookup"><span data-stu-id="5db15-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - [<span data-ttu-id="5db15-108">Wyłączanie przycisku Start</span><span class="sxs-lookup"><span data-stu-id="5db15-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  - [<span data-ttu-id="5db15-109">Anulowanie i ponowne uruchomienie operacji</span><span class="sxs-lookup"><span data-stu-id="5db15-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="5db15-110">Uruchamianie wielu operacji i kolejkowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="5db15-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="5db15-111">Przeglądanie i uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="5db15-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="5db15-112">Aby uruchomić przykład, musisz mieć visual studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5db15-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="5db15-113">Transport Layer Security (TLS) w wersji 1.2 jest teraz minimalną wersją do użycia w rozwoju aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5db15-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="5db15-114">Jeśli aplikacja jest przeznaczona dla wersji programu .NET Framework wcześniejszej niż 4.7, zapoznaj się z poniższym artykułem, aby zapoznać się [z najlepszymi rozwiązaniami dotyczących zabezpieczeń warstwy transportu (TLS) z programem .NET Framework.](../../../../framework/network-programming/tls.md)</span><span class="sxs-lookup"><span data-stu-id="5db15-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="5db15-115">Rozpoznawanie reentrancy</span><span class="sxs-lookup"><span data-stu-id="5db15-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="5db15-116">W przykładzie w tym temacie użytkownicy wybierają przycisk **Start,** aby zainicjować asynchroniczną aplikację, która pobiera serię witryn sieci Web i oblicza całkowitą liczbę pobranych bajtów.</span><span class="sxs-lookup"><span data-stu-id="5db15-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="5db15-117">Synchroniczne wersji przykładu będzie reagować w ten sam sposób, niezależnie od tego, ile razy użytkownik wybiera przycisk, ponieważ po pierwszym czasie wątku interfejsu użytkownika ignoruje te zdarzenia, dopóki aplikacja zakończy się uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="5db15-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="5db15-118">W aplikacji asynchroniiowej jednak wątek interfejsu użytkownika nadal odpowiadać i może ponownie wreżyserować operację asynchroniza.</span><span class="sxs-lookup"><span data-stu-id="5db15-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="5db15-119">Poniższy przykład pokazuje oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5db15-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="5db15-120">Pojawi się lista pobranych witryn sieci Web o rozmiarze w bajtach każdej witryny.</span><span class="sxs-lookup"><span data-stu-id="5db15-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="5db15-121">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="5db15-121">The total number of bytes appears at the end.</span></span>

```output
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

<span data-ttu-id="5db15-122">Jednak jeśli użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany wielokrotnie, a proces pobierania jest ponownie wprowadzany za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="5db15-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="5db15-123">W rezultacie kilka operacji asynchronicznych są uruchomione w tym samym czasie, dane wyjściowe przeplata wyniki, a całkowita liczba bajtów jest mylące.</span><span class="sxs-lookup"><span data-stu-id="5db15-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```output
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

<span data-ttu-id="5db15-124">Można przejrzeć kod, który tworzy ten wynik, przewijając do końca tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5db15-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="5db15-125">Można eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub używając kodu na końcu tego tematu, aby utworzyć własny projekt.</span><span class="sxs-lookup"><span data-stu-id="5db15-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="5db15-126">Aby uzyskać więcej informacji i instrukcji, zobacz [Przeglądanie i uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="5db15-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="5db15-127">Obsługa reentrancy</span><span class="sxs-lookup"><span data-stu-id="5db15-127">Handling Reentrancy</span></span>

<span data-ttu-id="5db15-128">Możesz obsługiwać reentrancy na różne sposoby, w zależności od tego, co aplikacja ma zrobić.</span><span class="sxs-lookup"><span data-stu-id="5db15-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="5db15-129">W tym temacie przedstawiono następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="5db15-129">This topic presents the following examples:</span></span>

- [<span data-ttu-id="5db15-130">Wyłączanie przycisku Start</span><span class="sxs-lookup"><span data-stu-id="5db15-130">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="5db15-131">Wyłącz przycisk **Start,** gdy operacja jest uruchomiona, aby użytkownik nie mógł jej przerwać.</span><span class="sxs-lookup"><span data-stu-id="5db15-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="5db15-132">Anulowanie i ponowne uruchomienie operacji</span><span class="sxs-lookup"><span data-stu-id="5db15-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="5db15-133">Anuluj dowolną operację, która jest nadal uruchomiona, gdy użytkownik ponownie wybierze przycisk **Start,** a następnie pozwól, aby ostatnio żądana operacja była kontynuowana.</span><span class="sxs-lookup"><span data-stu-id="5db15-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="5db15-134">Uruchamianie wielu operacji i kolejkowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="5db15-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="5db15-135">Zezwalaj na uruchamianie wszystkich żądanych operacji asynchronicznie, ale koordynuje wyświetlanie danych wyjściowych, tak aby wyniki z każdej operacji były wyświetlane razem i w kolejności.</span><span class="sxs-lookup"><span data-stu-id="5db15-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="5db15-136">Wyłączanie przycisku Start</span><span class="sxs-lookup"><span data-stu-id="5db15-136">Disable the Start Button</span></span>

<span data-ttu-id="5db15-137">Można zablokować **przycisk Start,** gdy operacja jest uruchomiona, wyłączając `StartButton_Click` przycisk w górnej części programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="5db15-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="5db15-138">Następnie można ponownie uruchomić przycisk z `finally` poziomu bloku po zakończeniu operacji, dzięki czemu użytkownicy mogą ponownie uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5db15-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="5db15-139">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w kodzie podstawowym, który jest dostarczany w [przeglądowi i uruchamianiu przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="5db15-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="5db15-140">Gotową aplikację można również pobrać z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="5db15-140">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="5db15-141">Nazwa projektu to DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="5db15-141">The name of the project is DisableStartButton.</span></span>

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

<span data-ttu-id="5db15-142">W wyniku zmian przycisk nie odpowiada podczas `AccessTheWebAsync` pobierania witryn sieci Web, więc nie można ponownie wprowadzić procesu.</span><span class="sxs-lookup"><span data-stu-id="5db15-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a><span data-ttu-id="5db15-143">Anulowanie i ponowne uruchomienie operacji</span><span class="sxs-lookup"><span data-stu-id="5db15-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="5db15-144">Zamiast wyłączać przycisk **Start,** można zachować aktywny przycisk, ale jeśli użytkownik wybierze ten przycisk ponownie, anuluj operację, która jest już uruchomiona i pozwól kontynuować ostatnio rozpoczętą operację.</span><span class="sxs-lookup"><span data-stu-id="5db15-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="5db15-145">Aby uzyskać więcej informacji na temat anulowania, zobacz [Dostrajanie aplikacji Asynchronii (C#)](./fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="5db15-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="5db15-146">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w kodzie podstawowym, który jest dostarczany w [przeglądowi i uruchamianiu przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="5db15-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="5db15-147">Gotową aplikację można również pobrać z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="5db15-147">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="5db15-148">Nazwa projektu to CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="5db15-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="5db15-149">Deklaruj zmienną, <xref:System.Threading.CancellationTokenSource> `cts`czyli w zakresie dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="5db15-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="5db15-150">W `StartButton_Click`, określić, czy operacja jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="5db15-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="5db15-151">Jeśli wartość `cts` ma wartość null, żadna operacja nie jest już aktywna.</span><span class="sxs-lookup"><span data-stu-id="5db15-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="5db15-152">Jeśli wartość nie jest null, operacja, która jest już uruchomiona jest anulowana.</span><span class="sxs-lookup"><span data-stu-id="5db15-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="5db15-153">Ustaw `cts` inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="5db15-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="5db15-154">Na końcu `StartButton_Click`, bieżący proces jest zakończony, `cts` więc ustawić wartość z powrotem do null.</span><span class="sxs-lookup"><span data-stu-id="5db15-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="5db15-155">Poniższy kod pokazuje wszystkie `StartButton_Click`zmiany w .</span><span class="sxs-lookup"><span data-stu-id="5db15-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="5db15-156">Dodatki są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="5db15-156">The additions are marked with asterisks.</span></span>

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

<span data-ttu-id="5db15-157">W `AccessTheWebAsync`, wprowadzać następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="5db15-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="5db15-158">Dodaj parametr, aby zaakceptować `StartButton_Click`token anulowania z .</span><span class="sxs-lookup"><span data-stu-id="5db15-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="5db15-159">Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody, aby pobrać `GetAsync` witryny <xref:System.Threading.CancellationToken> sieci Web, ponieważ akceptuje argument.</span><span class="sxs-lookup"><span data-stu-id="5db15-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="5db15-160">Przed `DisplayResults` wywołaniem, aby wyświetlić wyniki `ct` dla każdej pobranej witryny sieci Web, sprawdź, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="5db15-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

<span data-ttu-id="5db15-161">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="5db15-161">The following code shows these changes, which are marked with asterisks.</span></span>

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
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

<span data-ttu-id="5db15-162">Jeśli wybierzesz **przycisk Start** kilka razy, gdy ta aplikacja jest uruchomiona, powinien ono uzyskać wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5db15-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

```output
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

<span data-ttu-id="5db15-163">Aby wyeliminować listy częściowe, odkomentuj `StartButton_Click` pierwszy wiersz kodu, aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchomi operację.</span><span class="sxs-lookup"><span data-stu-id="5db15-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="5db15-164">Uruchamianie wielu operacji i kolejkowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="5db15-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="5db15-165">Ten trzeci przykład jest najbardziej skomplikowane, ponieważ aplikacja uruchamia inną operację asynchroniczną za każdym razem, gdy użytkownik wybiera **przycisk Start** i wszystkie operacje uruchamiane do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="5db15-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="5db15-166">Wszystkie żądane operacje pobierają strony internetowe z listy asynchronicznie, ale dane wyjściowe z operacji są prezentowane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="5db15-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="5db15-167">Oznacza to, że rzeczywista aktywność pobierania jest przeplotem, jak pokazuje dane wyjściowe w [rozpoznawaniu reentrancy,](#BKMK_RecognizingReentrancy) ale lista wyników dla każdej grupy jest przedstawiona oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="5db15-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="5db15-168">Operacje mają wspólny <xref:System.Threading.Tasks.Task> `pendingWork`globalny , który służy jako strażnik dla procesu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="5db15-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="5db15-169">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany w kodzie podstawowym, który jest dostarczany w [przeglądowi i uruchamianiu przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="5db15-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="5db15-170">Gotową aplikację można również pobrać z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="5db15-170">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="5db15-171">Nazwa projektu to QueueResults.</span><span class="sxs-lookup"><span data-stu-id="5db15-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="5db15-172">Poniższe dane wyjściowe pokazuje wynik, jeśli użytkownik wybiera **przycisk Start** tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5db15-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="5db15-173">Etykieta litery A wskazuje, że wynik pochodzi od pierwszego wybrania przycisku **Start.**</span><span class="sxs-lookup"><span data-stu-id="5db15-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="5db15-174">Liczby pokazują kolejność adresów URL na liście docelowych pobierania.</span><span class="sxs-lookup"><span data-stu-id="5db15-174">The numbers show the order of the URLs in the list of download targets.</span></span>

```output
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

<span data-ttu-id="5db15-175">Jeśli użytkownik wybierze przycisk **Start** trzy razy, aplikacja generuje dane wyjściowe, które przypominają następujące wiersze.</span><span class="sxs-lookup"><span data-stu-id="5db15-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="5db15-176">Linie informacyjne rozpoczynające się od znaku funta (#) śledzą postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5db15-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```output
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

<span data-ttu-id="5db15-177">Grupy B i C rozpoczynają się przed zakończeniem grupy A, ale dane wyjściowe dla każdej grupy są wyświetlane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="5db15-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="5db15-178">Najpierw pojawia się cały wynik dla grupy A, a następnie wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, wny są wyświetlane na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="5db15-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="5db15-179">Jednak nie można przewidzieć kolejność, w jakiej pliki do pobrania rzeczywiście się zdarzyć.</span><span class="sxs-lookup"><span data-stu-id="5db15-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="5db15-180">Po uruchomieniu wielu grup wszystkie generowane przez nie zadania pobierania są aktywne.</span><span class="sxs-lookup"><span data-stu-id="5db15-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="5db15-181">Nie można zakładać, że A-1 zostanie pobrany przed B-1 i nie można zakładać, że A-1 zostanie pobrany przed A-2.</span><span class="sxs-lookup"><span data-stu-id="5db15-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="5db15-182">Definicje globalne</span><span class="sxs-lookup"><span data-stu-id="5db15-182">Global Definitions</span></span>

<span data-ttu-id="5db15-183">Przykładowy kod zawiera następujące dwie deklaracje globalne, które są widoczne ze wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="5db15-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="5db15-184">Zmienna `Task` `pendingWork`nadzoruje proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="5db15-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="5db15-185">Zmienna znakowa , oznacza dane wyjściowe z różnych grup, `group`aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="5db15-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="5db15-186">Obsługa zdarzeń kliknięć</span><span class="sxs-lookup"><span data-stu-id="5db15-186">The Click Event Handler</span></span>

<span data-ttu-id="5db15-187">Program obsługi `StartButton_Click`zdarzeń , zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="5db15-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="5db15-188">Następnie program `AccessTheWebAsync` obsługi wywołuje uruchomienie operacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="5db15-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="5db15-189">AccessTheWebAsync Metoda</span><span class="sxs-lookup"><span data-stu-id="5db15-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="5db15-190">W tym `AccessTheWebAsync` przykładzie dzieli się na dwie metody.</span><span class="sxs-lookup"><span data-stu-id="5db15-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="5db15-191">Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania dla grupy `pendingWork` i konfiguruje do sterowania procesem wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="5db15-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="5db15-192">Metoda używa kwerendy zintegrowanej języka (LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> uruchomić wszystkie zadania pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="5db15-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="5db15-193">`AccessTheWebAsync`następnie `FinishOneGroupAsync` wywołuje, aby oczekiwać na zakończenie każdego pobrania i wyświetlić jego długość.</span><span class="sxs-lookup"><span data-stu-id="5db15-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="5db15-194">`FinishOneGroupAsync`zwraca zadanie przypisane w `pendingWork` pliku `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="5db15-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="5db15-195">Ta wartość zapobiega przerwaniu przez inną operację przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="5db15-195">That value prevents interruption by another operation before the task is complete.</span></span>

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

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="5db15-196">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="5db15-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="5db15-197">Ta metoda przechodzi przez zadania pobierania w grupie, oczekując na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do sumy.</span><span class="sxs-lookup"><span data-stu-id="5db15-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="5db15-198">Pierwsza instrukcja `FinishOneGroupAsync` w `pendingWork` użyciu, aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub który już czeka.</span><span class="sxs-lookup"><span data-stu-id="5db15-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="5db15-199">Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na swoją kolej.</span><span class="sxs-lookup"><span data-stu-id="5db15-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

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
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a><span data-ttu-id="5db15-200">Punkty szczególne</span><span class="sxs-lookup"><span data-stu-id="5db15-200">Points of Interest</span></span>

<span data-ttu-id="5db15-201">Linie informacyjne, które zaczynają się od znaku funta (#) w danych wyjściowych, wyjaśniają, jak działa ten przykład.</span><span class="sxs-lookup"><span data-stu-id="5db15-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="5db15-202">Dane wyjściowe pokazuje następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="5db15-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="5db15-203">Grupę można uruchomić, gdy poprzednia grupa wyświetla swoje dane wyjściowe, ale wyświetlanie danych wyjściowych poprzedniej grupy nie jest przerywane.</span><span class="sxs-lookup"><span data-stu-id="5db15-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

    ```output
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

- <span data-ttu-id="5db15-204">Zadanie `pendingWork` jest null na `FinishOneGroupAsync` początku tylko dla grupy A, która rozpoczęła się jako pierwsza.</span><span class="sxs-lookup"><span data-stu-id="5db15-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="5db15-205">Grupa A nie ukończyła jeszcze wyrażenia await `FinishOneGroupAsync`po osiągnięciu .</span><span class="sxs-lookup"><span data-stu-id="5db15-205">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="5db15-206">W związku z tym formantu nie wrócił do `AccessTheWebAsync`, a pierwsze przypisanie nie `pendingWork` wystąpiło.</span><span class="sxs-lookup"><span data-stu-id="5db15-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="5db15-207">Następujące dwa wiersze są zawsze wyświetlane razem na wyjściu.</span><span class="sxs-lookup"><span data-stu-id="5db15-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="5db15-208">Kod nigdy nie jest przerywany między uruchomieniem operacji grupy `StartButton_Click` a przypisaniem zadania dla grupy do `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="5db15-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="5db15-209">Po wprowadzeniu `StartButton_Click`grupy operacja nie kończy wyrażenia await, dopóki nie `FinishOneGroupAsync`zostanie wprowadzona operacja .</span><span class="sxs-lookup"><span data-stu-id="5db15-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="5db15-210">W związku z tym żadna inna operacja może uzyskać kontrolę podczas tego segmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="5db15-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="5db15-211">Przeglądanie i uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="5db15-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="5db15-212">Aby lepiej zrozumieć przykładowej aplikacji, można go pobrać, skompilować go samodzielnie lub przejrzeć kod na końcu tego tematu bez implementowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5db15-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="5db15-213">Aby uruchomić przykład jako windows presentation foundation (WPF) aplikacji klasycznej, musisz mieć Visual Studio 2012 lub nowsze i .NET Framework 4.5 lub nowsze zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5db15-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="5db15-214">Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5db15-214">Downloading the App</span></span>

1. <span data-ttu-id="5db15-215">Pobierz skompresowany plik z [async samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="5db15-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="5db15-216">Rozpakuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5db15-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="5db15-217">Na pasku menu wybierz **pozycję Plik**, **Otwórz,** **Projekt/Rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5db15-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="5db15-218">Przejdź do folderu, w który znajduje się zdekompresowany przykładowy kod, a następnie otwórz plik rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="5db15-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="5db15-219">W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz pozycję **Ustaw jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="5db15-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="5db15-220">Wybierz klawisze CTRL+F5, aby utworzyć i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="5db15-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a><span data-ttu-id="5db15-221">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5db15-221">Building the App</span></span>

<span data-ttu-id="5db15-222">Poniższa sekcja zawiera kod do tworzenia przykładu jako aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="5db15-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="5db15-223">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="5db15-223">To build a WPF app</span></span>

1. <span data-ttu-id="5db15-224">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5db15-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="5db15-225">Na pasku menu wybierz pozycję **Plik**, **Nowy**, **Projekt**.</span><span class="sxs-lookup"><span data-stu-id="5db15-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="5db15-226">Zostanie otwarte okno dialogowe **Nowy projekt.**</span><span class="sxs-lookup"><span data-stu-id="5db15-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="5db15-227">W okienku **Zainstalowane szablony** rozwiń węzeł **Visual C#**, a następnie rozwiń pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="5db15-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="5db15-228">Na liście typów projektów wybierz pozycję **Aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="5db15-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="5db15-229">Nazwij `WebsiteDownloadWPF`projekt , wybierz .NET Framework wersję 4.6 lub nowszą, a następnie kliknij przycisk **OK.**</span><span class="sxs-lookup"><span data-stu-id="5db15-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="5db15-230">Nowy projekt pojawi się w **Eksploratorze rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="5db15-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="5db15-231">W Edytorze kodów programu Visual Studio wybierz kartę **MainWindow.xaml.**</span><span class="sxs-lookup"><span data-stu-id="5db15-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="5db15-232">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratorze rozwiązań,** a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="5db15-232">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="5db15-233">W widoku **XAML** mainwindow.xaml zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5db15-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

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

     <span data-ttu-id="5db15-234">Proste okno zawierające pole tekstowe i przycisk pojawi się w widoku **Projekt** mainwindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="5db15-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="5db15-235">W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy **odwołania** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="5db15-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="5db15-236">Dodaj odwołanie <xref:System.Net.Http>dla , jeśli nie jest już zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="5db15-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="5db15-237">W **Eksploratorze rozwiązań**otwórz menu skrótów dla MainWindow.xaml.cs, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="5db15-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="5db15-238">W MainWindow.xaml.cs zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="5db15-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
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
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
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
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. <span data-ttu-id="5db15-239">Wybierz klawisze CTRL+F5, aby uruchomić program, a następnie wybierz kilka razy przycisk **Start.**</span><span class="sxs-lookup"><span data-stu-id="5db15-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="5db15-240">[Wykonuj](#BKMK_DisableTheStartButton)zmiany z przycisku Wyłącz przycisk Start , [Anuluj i uruchom ponownie operację](#BKMK_CancelAndRestart)lub Uruchom wiele operacji i [kolejka danych wyjściowych](#BKMK_RunMultipleOperations) do obsługi reentrancy.</span><span class="sxs-lookup"><span data-stu-id="5db15-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="5db15-241">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5db15-241">See also</span></span>

- [<span data-ttu-id="5db15-242">Przewodnik: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwania (C#)</span><span class="sxs-lookup"><span data-stu-id="5db15-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="5db15-243">Programowanie asynchroniczne z asynchnc i await (C#)</span><span class="sxs-lookup"><span data-stu-id="5db15-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
