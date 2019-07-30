---
title: Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: bc8156b1d2baa53255870364e680d62d7b93a50f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630938"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="c44f7-102">Obsługa współużytkowania wątkowości w aplikacjach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c44f7-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="c44f7-103">Po dołączeniu kodu asynchronicznego do aplikacji należy rozważyć i prawdopodobnie zapobiec współużytkowania wątkowości, który odwołuje się do ponownego wprowadzania operacji asynchronicznej przed ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="c44f7-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="c44f7-104">Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="c44f7-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="c44f7-105">Aby uruchomić przykład, musisz mieć zainstalowany na komputerze program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="c44f7-106">Rozpoznawanie współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="c44f7-106">Recognizing Reentrancy</span></span>

<span data-ttu-id="c44f7-107">W przykładzie w tym temacie użytkownicy wybierają przycisk **Start** , aby zainicjować aplikację asynchroniczną, która pobiera serię witryn sieci Web i oblicza łączną liczbę pobieranych bajtów.</span><span class="sxs-lookup"><span data-stu-id="c44f7-107">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="c44f7-108">Synchroniczna wersja przykładu reaguje w taki sam sposób, niezależnie od tego, ile razy użytkownik wybierze przycisk, ponieważ po raz pierwszy wątek interfejsu użytkownika ignoruje te zdarzenia do momentu zakończenia działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-108">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="c44f7-109">W aplikacji asynchronicznej jednak wątek interfejsu użytkownika nadal odpowiada i można ponownie wprowadzić operację asynchroniczną przed jej ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="c44f7-109">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="c44f7-110">W poniższym przykładzie pokazano oczekiwane dane wyjściowe, jeśli użytkownik wybierze przycisk **Start** tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c44f7-110">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="c44f7-111">Zostanie wyświetlona lista pobranych witryn sieci Web z rozmiarem w bajtach każdej lokacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-111">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="c44f7-112">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="c44f7-112">The total number of bytes appears at the end.</span></span>

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

<span data-ttu-id="c44f7-113">Jeśli jednak użytkownik wybierze przycisk więcej niż raz, program obsługi zdarzeń jest wywoływany wielokrotnie, a proces pobierania jest ponownie wprowadzany za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="c44f7-113">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="c44f7-114">W związku z tym kilka operacji asynchronicznych jest uruchomionych w tym samym czasie, dane wyjściowe pozostawią wyniki, a całkowita liczba bajtów jest myląca.</span><span class="sxs-lookup"><span data-stu-id="c44f7-114">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

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

<span data-ttu-id="c44f7-115">Możesz przejrzeć kod tworzący dane wyjściowe, przewijając do końca tego tematu.</span><span class="sxs-lookup"><span data-stu-id="c44f7-115">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="c44f7-116">Można eksperymentować z kodem, pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload lub korzystając z kodu na końcu tego tematu, aby utworzyć własny projekt, aby uzyskać więcej informacji i instrukcje, zobacz [przeglądanie i Uruchamianie przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="c44f7-116">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="c44f7-117">Obsługa współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="c44f7-117">Handling Reentrancy</span></span>

<span data-ttu-id="c44f7-118">Możesz obsłużyć współużytkowania wątkowości na różne sposoby, w zależności od tego, co aplikacja ma robić.</span><span class="sxs-lookup"><span data-stu-id="c44f7-118">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="c44f7-119">W tym temacie przedstawiono następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="c44f7-119">This topic presents the following examples:</span></span>

- [<span data-ttu-id="c44f7-120">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="c44f7-120">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="c44f7-121">Wyłącz przycisk **Start** , gdy operacja jest uruchomiona, aby użytkownik nie mógł go przerwać.</span><span class="sxs-lookup"><span data-stu-id="c44f7-121">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="c44f7-122">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="c44f7-122">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="c44f7-123">Anuluj wszystkie operacje, które nadal działają, gdy użytkownik wybierze ponownie przycisk **Start** , a następnie pozwól na kontynuowanie ostatnio żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-123">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="c44f7-124">Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="c44f7-124">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="c44f7-125">Zezwalaj na działanie wszystkich żądanych operacji asynchronicznie, ale koordynuj wyświetlanie danych wyjściowych, tak aby wyniki każdej operacji były wyświetlane razem i w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c44f7-125">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="c44f7-126">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="c44f7-126">Disable the Start Button</span></span>

<span data-ttu-id="c44f7-127">Można zablokować przycisk **Start** , gdy operacja jest uruchomiona, wyłączając przycisk w górnej części `StartButton_Click` procedury obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c44f7-127">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="c44f7-128">Następnie można ponownie włączyć przycisk `Finally` w bloku po zakończeniu operacji, aby umożliwić użytkownikom ponowne uruchomienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-128">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="c44f7-129">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="c44f7-129">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="c44f7-130">Możesz dodać zmiany do kodu na końcu tego tematu lub można pobrać ukończoną aplikację z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c44f7-130">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="c44f7-131">Nazwa projektu to DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="c44f7-131">The project name is DisableStartButton.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' This line is commented out to make the results clearer in the output.
    'ResultsTextBox.Text = ""

    ' ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = False

    Try
        Await AccessTheWebAsync()

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    ' ***Enable the Start button in case you want to run the program again.
    Finally
        StartButton.IsEnabled = True

    End Try
End Sub
```

<span data-ttu-id="c44f7-132">W wyniku zmian przycisk nie odpowiada, podczas gdy `AccessTheWebAsync` pobiera witryny sieci Web, więc nie można ponownie wprowadzić tego procesu.</span><span class="sxs-lookup"><span data-stu-id="c44f7-132">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="c44f7-133">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="c44f7-133">Cancel and Restart the Operation</span></span>

<span data-ttu-id="c44f7-134">Zamiast wyłączać przycisk **Start** , można zachować aktywny przycisk, ale jeśli użytkownik ponownie wybierze ten przycisk, należy anulować operację, która jest już uruchomiona, i pozostawić ostatnio uruchomioną operację.</span><span class="sxs-lookup"><span data-stu-id="c44f7-134">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="c44f7-135">Aby uzyskać więcej informacji na temat anulowania, zobacz [dostrajanie aplikacji asynchronicznej (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="c44f7-135">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="c44f7-136">Aby skonfigurować ten scenariusz, wprowadź następujące zmiany w kodzie podstawowym, który jest dostępny podczas [przeglądania i uruchamiania przykładowej aplikacji](#BKMD_SettingUpTheExample).</span><span class="sxs-lookup"><span data-stu-id="c44f7-136">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="c44f7-137">Możesz również pobrać ukończoną aplikację z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c44f7-137">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="c44f7-138">Nazwa tego projektu to CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="c44f7-138">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="c44f7-139">Zadeklaruj `cts`zmienną, która znajduje się w zakresie dla wszystkich metod. <xref:System.Threading.CancellationTokenSource></span><span class="sxs-lookup"><span data-stu-id="c44f7-139">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="c44f7-140">W `StartButton_Click`programie Ustal, czy operacja jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="c44f7-140">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="c44f7-141">Jeśli wartość `cts` jest `Nothing`równa, żadna operacja nie jest już aktywna.</span><span class="sxs-lookup"><span data-stu-id="c44f7-141">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="c44f7-142">Jeśli wartość nie `Nothing`jest, operacja, która jest już uruchomiona, została anulowana.</span><span class="sxs-lookup"><span data-stu-id="c44f7-142">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="c44f7-143">Ustaw `cts` inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="c44f7-143">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="c44f7-144">Na koniec `StartButton_Click`bieżący proces jest zakończony, więc ustaw wartość z `cts` powrotem na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c44f7-144">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="c44f7-145">Poniższy kod przedstawia wszystkie zmiany w `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="c44f7-145">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="c44f7-146">Dodatki są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="c44f7-146">The additions are marked with asterisks.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

    ' This line is commented out to make the results clearer.
    'ResultsTextBox.Text = ""

    ' *** If a download process is underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If

    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS

    Try
        ' *** Send a token to carry the message if the operation is canceled.
        Await AccessTheWebAsync(cts.Token)

    Catch ex As OperationCanceledException
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    End Try

    ' *** When the process is complete, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
End Sub
```

<span data-ttu-id="c44f7-147">Wprowadź `AccessTheWebAsync`następujące zmiany w programie.</span><span class="sxs-lookup"><span data-stu-id="c44f7-147">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="c44f7-148">Dodaj parametr, aby zaakceptować token anulowania z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="c44f7-148">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="c44f7-149">Użyj metody <xref:System.Net.Http.HttpClient.GetAsync%2A> , aby pobrać witryny sieci Web `GetAsync` , ponieważ <xref:System.Threading.CancellationToken> akceptuje argument.</span><span class="sxs-lookup"><span data-stu-id="c44f7-149">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="c44f7-150">Przed wywołaniem `DisplayResults` , aby wyświetlić wyniki dla każdej pobranej witryny `ct` sieci Web, sprawdź, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="c44f7-150">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="c44f7-151">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="c44f7-151">The following code shows these changes, which are marked with asterisks.</span></span>

```vb
' *** Provide a parameter for the CancellationToken from StartButton_Click.
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task

    ' Declare an HttpClient object.
    Dim client = New HttpClient()

    ' Make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()

    Dim total = 0
    Dim position = 0

    For Each url In urlList
        ' *** Use the HttpClient.GetAsync method because it accepts a
        ' cancellation token.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' *** Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' *** Check for cancellations before displaying information about the
        ' latest site.
        ct.ThrowIfCancellationRequested()

        position += 1
        DisplayResults(url, urlContents, position)

        ' Update the total.
        total += urlContents.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="c44f7-152">Jeśli wybierzesz przycisk **Start** kilka razy podczas działania tej aplikacji, powinny one generować wyniki podobne do następujących.</span><span class="sxs-lookup"><span data-stu-id="c44f7-152">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

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

<span data-ttu-id="c44f7-153">Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w `StartButton_Click` , aby wyczyścić pole tekstowe za każdym razem, gdy użytkownik ponownie uruchomi operację.</span><span class="sxs-lookup"><span data-stu-id="c44f7-153">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="c44f7-154">Uruchamianie wielu operacji i Kolejkowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="c44f7-154">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="c44f7-155">Trzeci przykład to najbardziej skomplikowany sposób, w jaki aplikacja uruchamia kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze przycisk **Start** , a wszystkie operacje są wykonywane do ukończenia.</span><span class="sxs-lookup"><span data-stu-id="c44f7-155">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="c44f7-156">Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są prezentowane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="c44f7-156">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="c44f7-157">Oznacza to, że rzeczywista czynność pobierania jest przeplatana, ponieważ dane wyjściowe [rozpoznawania współużytkowania wątkowości](#BKMK_RecognizingReentrancy) są wyświetlane, ale lista wyników dla każdej grupy jest prezentowana osobno.</span><span class="sxs-lookup"><span data-stu-id="c44f7-157">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="c44f7-158">Operacje współużytkują globalny <xref:System.Threading.Tasks.Task>, `pendingWork`, który służy jako strażnik dla procesu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-158">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="c44f7-159">Możesz uruchomić ten przykład, wklejając zmiany do kodu w trakcie [tworzenia aplikacji](#BKMK_BuildingTheApp), lub postępuj zgodnie z instrukcjami w temacie [Pobieranie aplikacji](#BKMK_DownloadingTheApp) , aby pobrać przykład, a następnie Uruchom projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="c44f7-159">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="c44f7-160">Poniższe dane wyjściowe pokazują wynik, jeśli użytkownik wybierze przycisk **Start** tylko raz.</span><span class="sxs-lookup"><span data-stu-id="c44f7-160">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="c44f7-161">Etykieta litery, A, wskazuje, że wynik jest z pierwszego momentu wybrania przycisku **Start** .</span><span class="sxs-lookup"><span data-stu-id="c44f7-161">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="c44f7-162">Liczby pokazują kolejność adresów URL na liście celów pobierania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-162">The numbers show the order of the URLs in the list of download targets.</span></span>

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

<span data-ttu-id="c44f7-163">Jeśli użytkownik wybierze przycisk **Start** trzy razy, aplikacja generuje dane wyjściowe podobne do następujących wierszy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-163">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="c44f7-164">Linie informacyjne, które zaczynają się od znaku funta (#) śledzą postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-164">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

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

<span data-ttu-id="c44f7-165">Grupy B i C rozpoczynają się przed zakończeniem grupy A, ale dane wyjściowe dla każdej grupy są wyświetlane oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="c44f7-165">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="c44f7-166">Wszystkie dane wyjściowe dla grupy A są wyświetlane jako pierwsze, po których następuje wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i, dla każdej grupy, zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, w jakiej znajdują się na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="c44f7-166">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="c44f7-167">Nie można jednak przewidzieć kolejności, w której istnieją pliki do pobrania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-167">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="c44f7-168">Po rozpoczęciu wielu grup zadania pobierania, które generują, są aktywne.</span><span class="sxs-lookup"><span data-stu-id="c44f7-168">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="c44f7-169">Nie można założyć, że wartość-1 zostanie pobrana przed B-1 i nie można założyć, że A-1 zostanie pobrane przed-2.</span><span class="sxs-lookup"><span data-stu-id="c44f7-169">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="c44f7-170">Definicje globalne</span><span class="sxs-lookup"><span data-stu-id="c44f7-170">Global Definitions</span></span>

<span data-ttu-id="c44f7-171">Przykładowy kod zawiera następujące dwie deklaracje globalne, które są widoczne dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="c44f7-171">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="c44f7-172">`Task` Zmienna ,`pendingWork`, widzi proces wyświetlania i uniemożliwia każdej grupie przerwanie operacji wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-172">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="c44f7-173">Zmienna znaku, `group`, oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c44f7-173">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="c44f7-174">Procedura obsługi zdarzeń kliknięcia</span><span class="sxs-lookup"><span data-stu-id="c44f7-174">The Click Event Handler</span></span>

<span data-ttu-id="c44f7-175">Program obsługi zdarzeń, `StartButton_Click`, zwiększa literę grupy za każdym razem, gdy użytkownik wybierze przycisk **Start** .</span><span class="sxs-lookup"><span data-stu-id="c44f7-175">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="c44f7-176">Następnie procedura obsługi wywołuje `AccessTheWebAsync` do uruchomienia operacji pobierania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-176">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' ***Verify that each group's results are displayed together, and that
    ' the groups display in order, by marking each group with a letter.
    group = ChrW(AscW(group) + 1)
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)

    Try
        ' *** Pass the group value to AccessTheWebAsync.
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)

        ' The following line verifies a successful return from the download and
        ' display procedures.
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."

    End Try
End Sub
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="c44f7-177">The AccessTheWebAsync Method</span><span class="sxs-lookup"><span data-stu-id="c44f7-177">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="c44f7-178">Ten przykład dzieli `AccessTheWebAsync` na dwie metody.</span><span class="sxs-lookup"><span data-stu-id="c44f7-178">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="c44f7-179">Pierwsza metoda `AccessTheWebAsync`,, uruchamia wszystkie zadania pobierania dla grupy i `pendingWork` konfiguruje, aby kontrolować proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-179">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="c44f7-180">Metoda używa języka Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> do uruchamiania wszystkich zadań pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="c44f7-180">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="c44f7-181">`AccessTheWebAsync`następnie wywołuje `FinishOneGroupAsync` do czeka na zakończenie każdego pobierania i wyświetla jego długość.</span><span class="sxs-lookup"><span data-stu-id="c44f7-181">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="c44f7-182">`FinishOneGroupAsync`zwraca zadanie, które jest przypisane do `pendingWork` elementu `AccessTheWebAsync`w.</span><span class="sxs-lookup"><span data-stu-id="c44f7-182">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="c44f7-183">Ta wartość uniemożliwia przerwanie przez inną operację przed ukończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="c44f7-183">That value prevents interruption by another operation before the task is complete.</span></span>

```vb
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)

    Dim client = New HttpClient()

    ' Make a list of the web addresses to download.
    Dim urlList As List(Of String) = SetUpURLList()

    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Dim getContentTasks As Task(Of Byte())() =
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()

    ' ***Call the method that awaits the downloads and displays the results.
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)

    ResultsTextBox.Text &=
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)

    ' ***This task is complete when a group has finished downloading and displaying.
    Await pendingWork

    ' You can do other work here or just return.
    Return grp
End Function
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="c44f7-184">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="c44f7-184">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="c44f7-185">Ta metoda przechodzi przez zadania pobierania w grupie, czekające na każdą z nich, wyświetlając długość pobranej witryny sieci Web i dodając do niej długość.</span><span class="sxs-lookup"><span data-stu-id="c44f7-185">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="c44f7-186">Pierwsza instrukcja w programie `FinishOneGroupAsync` używa `pendingWork` do upewnienia się, że wprowadzenie metody nie zakłóca operacji, która jest już w procesie wyświetlania lub już oczekuje.</span><span class="sxs-lookup"><span data-stu-id="c44f7-186">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="c44f7-187">Jeśli taka operacja jest w toku, operacja wprowadzania musi czekać na jej włączenie.</span><span class="sxs-lookup"><span data-stu-id="c44f7-187">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```vb
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task

    ' Wait for the previous group to finish displaying results.
    If pendingWork IsNot Nothing Then
        Await pendingWork
    End If

    Dim total = 0

    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    For i As Integer = 0 To contentTasks.Length - 1
        ' Await the download of a particular URL, and then display the URL and
        ' its length.
        Dim content As Byte() = Await contentTasks(i)
        DisplayResults(urls(i), content, i, grp)
        total += content.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="c44f7-188">Możesz uruchomić ten przykład, wklejając zmiany do kodu w trakcie [tworzenia aplikacji](#BKMK_BuildingTheApp), lub postępuj zgodnie z instrukcjami podanymi w temacie [Pobieranie aplikacji](#BKMK_DownloadingTheApp) , aby pobrać przykład, a następnie Uruchom projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="c44f7-188">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="c44f7-189">Punkty orientacyjne</span><span class="sxs-lookup"><span data-stu-id="c44f7-189">Points of Interest</span></span>

<span data-ttu-id="c44f7-190">Linie informacyjne, które zaczynają się od znaku funta (#) w danych wyjściowych, wyjaśniają sposób działania tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="c44f7-190">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="c44f7-191">Dane wyjściowe przedstawiają następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="c44f7-191">The output shows the following patterns.</span></span>

- <span data-ttu-id="c44f7-192">Grupę można uruchomić, gdy poprzednia grupa wyświetla dane wyjściowe, ale nie przerywa się wyświetlania danych wyjściowych poprzedniej grupy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-192">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

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

- <span data-ttu-id="c44f7-193">Zadanie jest `Nothing` na początku`FinishOneGroupAsync` tylko dla grupy A, która rozpoczęła się w pierwszej kolejności. `pendingWork`</span><span class="sxs-lookup"><span data-stu-id="c44f7-193">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="c44f7-194">Grupa A jeszcze nie ukończyła wyrażenia await, gdy osiągnie `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="c44f7-194">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="c44f7-195">W związku z tym formant nie `AccessTheWebAsync`został zwrócony do i pierwsze przypisanie `pendingWork` do nie zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="c44f7-195">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="c44f7-196">Dwa następujące wiersze są zawsze wyświetlane razem w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c44f7-196">The following two lines always appear together in the output.</span></span> <span data-ttu-id="c44f7-197">Kod nigdy nie zostanie przerwany między rozpoczęciem operacji grupy w `StartButton_Click` i przypisaniem zadania dla grupy do. `pendingWork`</span><span class="sxs-lookup"><span data-stu-id="c44f7-197">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="c44f7-198">Po wprowadzeniu `StartButton_Click`grupy operacja nie kończy wyrażenia await do momentu wejścia `FinishOneGroupAsync`operacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-198">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="c44f7-199">W związku z tym żadna inna operacja nie może uzyskać kontroli podczas tego segmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="c44f7-199">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="c44f7-200">Przeglądanie i uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="c44f7-200">Reviewing and Running the Example App</span></span>

<span data-ttu-id="c44f7-201">Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c44f7-201">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="c44f7-202">Aby uruchomić przykład jako aplikację klasyczną Windows Presentation Foundation (WPF), na komputerze musi być zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-202">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="c44f7-203">Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c44f7-203">Downloading the App</span></span>

1. <span data-ttu-id="c44f7-204">Pobierz skompresowany plik z [próbek asynchronicznych: Współużytkowania wątkowości w aplikacjach](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)klasycznych platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="c44f7-204">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="c44f7-205">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c44f7-205">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="c44f7-206">Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-206">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="c44f7-207">Przejdź do folderu, który zawiera zdekompresować przykładowy kod, a następnie otwórz plik rozwiązania (. sln).</span><span class="sxs-lookup"><span data-stu-id="c44f7-207">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="c44f7-208">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz polecenie **Ustaw jako StartUpProject**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-208">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="c44f7-209">Wybierz kombinację klawiszy CTRL + F5, aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="c44f7-209">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="c44f7-210">Kompilowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c44f7-210">Building the App</span></span>

<span data-ttu-id="c44f7-211">Poniższa sekcja zawiera kod służący do kompilowania przykładu jako aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="c44f7-211">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="c44f7-212">Aby skompilować aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="c44f7-212">To build a WPF app</span></span>

1. <span data-ttu-id="c44f7-213">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c44f7-213">Start Visual Studio.</span></span>

2. <span data-ttu-id="c44f7-214">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-214">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="c44f7-215">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="c44f7-215">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="c44f7-216">W okienku **zainstalowane szablony** rozwiń węzeł **Visual Basic**, a następnie rozwiń pozycję **Windows**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-216">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="c44f7-217">Na liście typów projektów wybierz pozycję **Aplikacja WPF**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-217">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="c44f7-218">Nazwij projekt `WebsiteDownloadWPF`, a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="c44f7-218">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="c44f7-219">Nowy projekt zostanie wyświetlony w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-219">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="c44f7-220">W edytorze Visual Studio Code wybierz kartę **MainWindow. XAML** .</span><span class="sxs-lookup"><span data-stu-id="c44f7-220">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="c44f7-221">Jeśli karta nie jest widoczna, otwórz menu skrótów dla MainWindow. XAML w **Eksplorator rozwiązań**, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-221">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="c44f7-222">W widoku **XAML** MainWindow. XAML Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="c44f7-222">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```xaml
    <Window x:Class="MainWindow"
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

     <span data-ttu-id="c44f7-223">Proste okno zawierające pole tekstowe i przycisk pojawia się w widoku **projekt** MainWindow. XAML.</span><span class="sxs-lookup"><span data-stu-id="c44f7-223">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="c44f7-224">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="c44f7-224">Add a reference for <xref:System.Net.Http>.</span></span>

9. <span data-ttu-id="c44f7-225">W **Eksplorator rozwiązań**Otwórz menu skrótów dla MainWindow. XAML. vb, a następnie wybierz polecenie **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="c44f7-225">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="c44f7-226">W MainWindow. XAML. vb Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="c44f7-226">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            ' This line is commented out to make the results clearer in the output.
            'ResultsTextBox.Text = ""

            Try
                Await AccessTheWebAsync()

            Catch ex As Exception
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."

            End Try
        End Sub

        Private Async Function AccessTheWebAsync() As Task

            ' Declare an HttpClient object.
            Dim client = New HttpClient()

            ' Make a list of web addresses.
            Dim urlList As List(Of String) = SetUpURLList()

            Dim total = 0
            Dim position = 0

            For Each url In urlList
                ' GetByteArrayAsync returns a task. At completion, the task
                ' produces a byte array.
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

                position += 1
                DisplayResults(url, urlContents, position)

                ' Update the total.
                total += urlContents.Length
            Next

            ' Display the total count for all of the websites.
            ResultsTextBox.Text &=
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
        End Function

        Private Function SetUpURLList() As List(Of String)
            Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. <span data-ttu-id="c44f7-227">Naciśnij klawisze CTRL + F5, aby uruchomić program, a następnie wybierz przycisk **Start** kilka razy.</span><span class="sxs-lookup"><span data-stu-id="c44f7-227">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="c44f7-228">Wprowadź zmiany, aby [wyłączyć przycisk Start](#BKMK_DisableTheStartButton), [anulować i ponownie uruchomić operację](#BKMK_CancelAndRestart)albo [uruchomić wiele operacji i kolejkować dane wyjściowe](#BKMK_RunMultipleOperations) , aby obsłużyć współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="c44f7-228">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="c44f7-229">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c44f7-229">See also</span></span>

- [<span data-ttu-id="c44f7-230">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c44f7-230">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="c44f7-231">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c44f7-231">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
