---
title: Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: b633e3cf9a499cd5f364692cd0461aed640fe54d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401893"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="8c76e-102">Obsługa ponownego rozpoczęcia w aplikacjach asynchronicznych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c76e-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="8c76e-103">Po dołączeniu asynchronicznego kodu w aplikacji należy wziąć pod uwagę i ewentualnie zapobiec współużytkowaniu wątkowości, która odwołuje się do ponownego wprowadzania operacji asynchronicznej, zanim została ukończona.</span><span class="sxs-lookup"><span data-stu-id="8c76e-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="8c76e-104">Jeśli nie zidentyfikujesz i obsłużysz możliwości współużytkowania wątkowości, może to spowodować nieoczekiwane wyniki.</span><span class="sxs-lookup"><span data-stu-id="8c76e-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="8c76e-105">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="8c76e-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="8c76e-106">Uznawanie współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="8c76e-106">Recognizing Reentrancy</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="8c76e-107">Obsługa współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="8c76e-107">Handling Reentrancy</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="8c76e-108">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="8c76e-108">Disable the Start Button</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="8c76e-109">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="8c76e-109">Cancel and Restart the Operation</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
    -   [<span data-ttu-id="8c76e-110">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8c76e-110">Run Multiple Operations and Queue the Output</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
-   [<span data-ttu-id="8c76e-111">Przeglądanie i uruchamianie aplikacji przykładowych</span><span class="sxs-lookup"><span data-stu-id="8c76e-111">Reviewing and Running the Example App</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
> [!NOTE]
>  <span data-ttu-id="8c76e-112">Aby uruchomić przykład, konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8c76e-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="8c76e-113">Uznawanie współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="8c76e-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="8c76e-114">W przykładzie w tym temacie, wybierz opcję użytkownicy **Start** przycisk, aby zainicjować asynchroniczną aplikację, która pobiera szereg witryn sieci Web, a następnie oblicza całkowita liczba bajtów, które są pobierane.</span><span class="sxs-lookup"><span data-stu-id="8c76e-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="8c76e-115">Synchroniczna wersja przykładu reaguje w taki sam sposób, bez względu ile razy użytkownik wybierze przycisk, ponieważ po pierwszym uruchomieniu wątek interfejsu użytkownika ignoruje te zdarzenia, dopóki nie zakończy się uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c76e-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="8c76e-116">W asynchronicznej aplikacji jednak wątku interfejsu użytkownika w dalszym ciągu odpowiada i można ponownie wprowadzić operację asynchroniczną przed jego ukończeniem.</span><span class="sxs-lookup"><span data-stu-id="8c76e-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="8c76e-117">Poniższy przykład ukazuje oczekiwane dane wyjściowe, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8c76e-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="8c76e-118">Zostanie wyświetlona lista pobranych stron internetowych z rozmiar, w bajtach, w każdej lokacji.</span><span class="sxs-lookup"><span data-stu-id="8c76e-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="8c76e-119">Całkowita liczba bajtów pojawia się na końcu.</span><span class="sxs-lookup"><span data-stu-id="8c76e-119">The total number of bytes appears at the end.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-120">Jednak jeśli użytkownik wybierze przycisk więcej niż jeden raz, program obsługi zdarzeń jest wywoływany kilkakrotnie i proces pobierania jest ponownie inicjowany każdorazowo.</span><span class="sxs-lookup"><span data-stu-id="8c76e-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="8c76e-121">W rezultacie kilka operacji asynchronicznych jest uruchomionych w tym samym czasie, dane wyjściowe przeplatają wyniki i całkowita liczba bajtów jest myląca ze.</span><span class="sxs-lookup"><span data-stu-id="8c76e-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-122">Możesz przejrzeć kod, który generuje te dane wyjściowe przewijając do końca tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8c76e-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="8c76e-123">Możesz eksperymentować z kodem pobierając rozwiązanie na komputer lokalny, a następnie uruchamiając projekt WebsiteDownload, lub za pomocą kodu na końcu tego tematu, aby utworzyć własny projekt, aby uzyskać więcej informacji oraz instrukcje, zobacz [ Przeglądanie i uruchamianie aplikacji przykładowych](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="8c76e-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="8c76e-124">Obsługa współużytkowania wątkowości</span><span class="sxs-lookup"><span data-stu-id="8c76e-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="8c76e-125">Może obsługiwać współużytkowanie wątkowości na wiele sposobów, w zależności od tego, co ma robić Twoja aplikacja.</span><span class="sxs-lookup"><span data-stu-id="8c76e-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="8c76e-126">Ten temat przedstawia następujące przykłady:</span><span class="sxs-lookup"><span data-stu-id="8c76e-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="8c76e-127">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="8c76e-127">Disable the Start Button</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="8c76e-128">Wyłącz **Start** przycisku, gdy operacja jest uruchomiony, dzięki czemu użytkownik nie mógł jej przerwać.</span><span class="sxs-lookup"><span data-stu-id="8c76e-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="8c76e-129">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="8c76e-129">Cancel and Restart the Operation</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="8c76e-130">Anulować wszelkie operacje, które wciąż działają, gdy użytkownik wybierze **Start** ponownie przycisk, a następnie kontynuuj umożliwiają niedawno żądanej operacji.</span><span class="sxs-lookup"><span data-stu-id="8c76e-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="8c76e-131">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8c76e-131">Run Multiple Operations and Queue the Output</span></span>](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645)  
  
     <span data-ttu-id="8c76e-132">Zezwalaj wszystkim wymaganym operacjom na uruchamianie asynchronicznie, ale Koordynuj dane wyjściowe, tak aby wyniki z każdej operacji były wyświetlane razem i w kolejności.</span><span class="sxs-lookup"><span data-stu-id="8c76e-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="8c76e-133">Wyłącz przycisk Start</span><span class="sxs-lookup"><span data-stu-id="8c76e-133">Disable the Start Button</span></span>  
 <span data-ttu-id="8c76e-134">Możesz zablokować **Start** przycisk uruchomionej operacji przez wyłączenie przycisku u góry `StartButton_Click` programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8c76e-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="8c76e-135">Następnie możesz ponownie włączyć przycisk od wewnątrz `Finally` blokować po zakończeniu operacji, dzięki czemu użytkownicy mogą uruchamiać aplikację ponownie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="8c76e-136">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="8c76e-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="8c76e-137">Zmiany można dodać do kodu na końcu tego tematu, można również pobrać gotową aplikację z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="8c76e-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="8c76e-138">Nazwa projektu to DisableStartButton.</span><span class="sxs-lookup"><span data-stu-id="8c76e-138">The project name is DisableStartButton.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-139">W wyniku zmian przycisk przestaje odpowiadać podczas `AccessTheWebAsync` pobiera strony internetowe, dzięki czemu nie trzeba ponownie wprowadzić ten proces.</span><span class="sxs-lookup"><span data-stu-id="8c76e-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="8c76e-140">Anuluj i ponownie uruchom operację</span><span class="sxs-lookup"><span data-stu-id="8c76e-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="8c76e-141">Zamiast wyłączać **Start** przycisku możesz zachować aktywny przycisk, ale, jeśli użytkownik wybierze ten przycisk ponownie, Anuluj operację, która jest już uruchomiona i umożliwić kontynuowanie operacji ostatnio rozpoczętej.</span><span class="sxs-lookup"><span data-stu-id="8c76e-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="8c76e-142">Aby uzyskać więcej informacji dotyczących anulowania, zobacz [aplikacji asynchronicznej Fine-Tuning (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="8c76e-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="8c76e-143">Aby skonfigurować ten scenariusz, należy wprowadzić następujące zmiany do kodu podstawowego, który znajduje się w [recenzowanie i uruchamianie aplikacji przykładowych](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span><span class="sxs-lookup"><span data-stu-id="8c76e-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645).</span></span> <span data-ttu-id="8c76e-144">Możesz również pobrać gotową aplikację z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="8c76e-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="8c76e-145">Nazwa tego projektu to CancelAndRestart.</span><span class="sxs-lookup"><span data-stu-id="8c76e-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="8c76e-146">Zadeklaruj <xref:System.Threading.CancellationTokenSource> zmiennej `cts`, który znajduje się w zakresie dla wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="8c76e-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="8c76e-147">W `StartButton_Click`, określić, czy operacja jest już w toku.</span><span class="sxs-lookup"><span data-stu-id="8c76e-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="8c76e-148">Jeśli wartość `cts` jest `Nothing`, żadna operacja nie jest już aktywny.</span><span class="sxs-lookup"><span data-stu-id="8c76e-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="8c76e-149">Jeśli wartość nie jest `Nothing`, operacja, która jest już uruchomiona zostanie anulowane.</span><span class="sxs-lookup"><span data-stu-id="8c76e-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="8c76e-150">Ustaw `cts` na inną wartość, która reprezentuje bieżący proces.</span><span class="sxs-lookup"><span data-stu-id="8c76e-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="8c76e-151">Na koniec `StartButton_Click`, bieżący proces się zakończy, więc ustaw wartość `cts` do `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="8c76e-152">Poniższy kod pokazuje wszystkie zmiany w `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="8c76e-153">Dodatki są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="8c76e-153">The additions are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-154">W `AccessTheWebAsync`, wprowadź następujące zmiany.</span><span class="sxs-lookup"><span data-stu-id="8c76e-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="8c76e-155">Dodaj parametr do akceptowania tokenu odwołania z `StartButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="8c76e-156">Użyj <xref:System.Net.Http.HttpClient.GetAsync%2A> metody do pobierania witryn sieci Web, ponieważ `GetAsync` akceptuje <xref:System.Threading.CancellationToken> argumentu.</span><span class="sxs-lookup"><span data-stu-id="8c76e-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="8c76e-157">Przed wywołaniem `DisplayResults` do wyświetlania wyników dla każdej pobranej witryny sieci Web, sprawdź `ct` Aby sprawdzić, czy bieżąca operacja nie została anulowana.</span><span class="sxs-lookup"><span data-stu-id="8c76e-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="8c76e-158">Poniższy kod przedstawia te zmiany, które są oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="8c76e-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-159">Jeśli wybierzesz **Start** przycisk kilka razy ta aplikacja jest uruchomiona, powinno to dawać wyniki podobne do następujących danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8c76e-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-160">Aby wyeliminować częściowe listy, Usuń komentarz z pierwszego wiersza kodu w `StartButton_Click` aby czyścić pole tekstowe za każdym razem, kiedy użytkownik uruchamia operację.</span><span class="sxs-lookup"><span data-stu-id="8c76e-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="8c76e-161">Uruchom wiele operacji i Zakolejkuj dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="8c76e-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="8c76e-162">Trzeci przykład jest najbardziej skomplikowany, w tym, że aplikacja rozpoczyna kolejną operację asynchroniczną za każdym razem, gdy użytkownik wybierze **Start** przycisk, a wszystkie operacje do zakończenia.</span><span class="sxs-lookup"><span data-stu-id="8c76e-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="8c76e-163">Wszystkie żądane operacje pobierają witryny sieci Web z listy asynchronicznie, ale dane wyjściowe operacji są przedstawiane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="8c76e-164">Oznacza to, że rzeczywiste działanie pobierania odbywa się z przeplotem, jako dane wyjściowe w [rozpoznawaniu współużytkowania wątkowości](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) pokazuje, ale lista wyników dla każdej grupy jest prezentowana oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="8c76e-165">Operacje współkorzystają z globalnego <xref:System.Threading.Tasks.Task>, `pendingWork`, który służy jako strażnik dla procesu wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="8c76e-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="8c76e-166">Możesz uruchomić ten przykład, wklejając zmiany do kodu w [Kompilowanie aplikacji](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub możesz postępować zgodnie z instrukcjami w [pobierając aplikację](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobrania próbki, a następnie uruchomić projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="8c76e-166">You can run this example by pasting the changes into the code in [Building the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="8c76e-167">Następujące dane wyjściowe pokazują wynik, jeśli użytkownik wybierze **Start** przycisk tylko raz.</span><span class="sxs-lookup"><span data-stu-id="8c76e-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="8c76e-168">Etykieta litery A, wskazuje, że wynik dotyczy po raz pierwszy **Start** wciśnięcia przycisku.</span><span class="sxs-lookup"><span data-stu-id="8c76e-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="8c76e-169">Liczby pokazują kolejność adresów URL na liście elementów docelowych pobierania.</span><span class="sxs-lookup"><span data-stu-id="8c76e-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-170">Jeśli użytkownik wybierze **Start** przycisk trzy razy, aplikacja generuje dane wyjściowe podobne do następujących wierszy.</span><span class="sxs-lookup"><span data-stu-id="8c76e-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="8c76e-171">Linie informacyjne, rozpoczynające się od znaku funta Zaloguj (#) śledzą postęp aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c76e-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-172">Grupy B i C uruchomić przed grupy A zostało zakończone, ale dane wyjściowe dla każdej grupy pojawiają się oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="8c76e-173">Wszystkie dane wyjściowe dla grupy A pojawiają się pierwsze, wszystkie dane wyjściowe dla grupy B, a następnie wszystkie dane wyjściowe dla grupy C. Aplikacja zawsze wyświetla grupy w kolejności i, dla każdej grupy zawsze wyświetla informacje o poszczególnych witrynach sieci Web w kolejności, adresy URL są wyświetlane na liście adresów URL.</span><span class="sxs-lookup"><span data-stu-id="8c76e-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="8c76e-174">Jednak nie można przewidzieć kolejności, w której rzeczywiście wystąpi pobieranie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="8c76e-175">Po uruchomieniu wielu grup zadań pobierania, które generują wszystkie są aktywne.</span><span class="sxs-lookup"><span data-stu-id="8c76e-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="8c76e-176">Nie można zakładać, że A-1 będą pobierane przed b-1 i nie można zakładać, że A-1 będą pobierane przed A-2.</span><span class="sxs-lookup"><span data-stu-id="8c76e-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="8c76e-177">Globalne definicje</span><span class="sxs-lookup"><span data-stu-id="8c76e-177">Global Definitions</span></span>  
 <span data-ttu-id="8c76e-178">Przykładowy kod zawiera poniższe dwie deklaracje globalne, które są widoczne ze wszystkich metod.</span><span class="sxs-lookup"><span data-stu-id="8c76e-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="8c76e-179">`Task` Zmiennej `pendingWork`, nadzoruje proces wyświetlania i zapobiega żadnej grupy zakłócania pracy wyświetlania innej grupy.</span><span class="sxs-lookup"><span data-stu-id="8c76e-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="8c76e-180">Zmienna znaku `group`, oznacza dane wyjściowe z różnych grup, aby sprawdzić, czy wyniki są wyświetlane w oczekiwanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8c76e-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="8c76e-181">Program obsługi zdarzeń kliknięcie</span><span class="sxs-lookup"><span data-stu-id="8c76e-181">The Click Event Handler</span></span>  
 <span data-ttu-id="8c76e-182">Program obsługi zdarzeń `StartButton_Click`, rośnie literę grupy za każdym razem, użytkownik wybierze **Start** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8c76e-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="8c76e-183">Następnie program obsługi zdarzeń wywołuje `AccessTheWebAsync` można uruchomić operację pobierania.</span><span class="sxs-lookup"><span data-stu-id="8c76e-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
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
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="8c76e-184">The AccessTheWebAsync Method</span><span class="sxs-lookup"><span data-stu-id="8c76e-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="8c76e-185">Ten przykład dzieli `AccessTheWebAsync` na dwie metody.</span><span class="sxs-lookup"><span data-stu-id="8c76e-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="8c76e-186">Pierwsza metoda `AccessTheWebAsync`, uruchamia wszystkie zadania pobierania dla grupy i konfiguruje `pendingWork` kontrolować proces wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="8c76e-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="8c76e-187">Metoda wykorzystuje Language Integrated Query (zapytanie LINQ) i <xref:System.Linq.Enumerable.ToArray%2A> można uruchomić zadania pobierania w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="8c76e-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="8c76e-188">`AccessTheWebAsync` następnie wywołuje `FinishOneGroupAsync` oczekiwać na zakończenie każdego pobrania i wyświetlić jego długość.</span><span class="sxs-lookup"><span data-stu-id="8c76e-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="8c76e-189">`FinishOneGroupAsync` Zwraca klasę task, która jest przypisana do `pendingWork` w `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="8c76e-190">Ta wartość zapobiega przerywaniu przez inną operację przed zakończeniem zadania.</span><span class="sxs-lookup"><span data-stu-id="8c76e-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
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
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="8c76e-191">Metoda FinishOneGroupAsync</span><span class="sxs-lookup"><span data-stu-id="8c76e-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="8c76e-192">Ta metoda przechodzi cyklicznie przez zadania pobierania w grupie, oczekujące na każdym z nich, wyświetlając długość pobranej witryny sieci Web i dodając długość do całkowitej.</span><span class="sxs-lookup"><span data-stu-id="8c76e-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="8c76e-193">Pierwsza instrukcja w `FinishOneGroupAsync` używa `pendingWork` aby upewnić się, że wprowadzenie metody nie koliduje z operacją, która jest już w procesie wyświetlania lub która już oczekuje.</span><span class="sxs-lookup"><span data-stu-id="8c76e-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="8c76e-194">Jeśli taka operacja jest w toku, wchodząca operacja musi czekać na swoją kolej.</span><span class="sxs-lookup"><span data-stu-id="8c76e-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
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
  
 <span data-ttu-id="8c76e-195">Możesz uruchomić ten przykład, wklejając zmiany do kodu w [Kompilowanie aplikacji](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub możesz postępować zgodnie z instrukcjami w [pobierając aplikację](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do pobrania próbki, a następnie uruchomić projekt QueueResults.</span><span class="sxs-lookup"><span data-stu-id="8c76e-195">You can run this example by pasting the changes into the code in [Building the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or you can follow the instructions in [Downloading the App](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="8c76e-196">Punktów orientacyjnych</span><span class="sxs-lookup"><span data-stu-id="8c76e-196">Points of Interest</span></span>  
 <span data-ttu-id="8c76e-197">Linie informacyjne, rozpoczynające się od znaku funta (#) w danych wyjściowych objaśnić, jak działa ten przykład.</span><span class="sxs-lookup"><span data-stu-id="8c76e-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="8c76e-198">Dane wyjściowe pokazują następujące wzorce.</span><span class="sxs-lookup"><span data-stu-id="8c76e-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="8c76e-199">Grupę można uruchomić podczas poprzedniej grupy jest wyświetlanie danych wyjściowych, ale wyświetlanie danych wyjściowych poprzedniej grupy nie zostanie przerwane.</span><span class="sxs-lookup"><span data-stu-id="8c76e-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
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
  
-   <span data-ttu-id="8c76e-200">`pendingWork` Zadanie jest `Nothing` na początku `FinishOneGroupAsync` tylko dla grupy A, uruchomionej w pierwszej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8c76e-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="8c76e-201">Grupa A jeszcze nie zakończyła wykonywania wyrażenia oczekiwania, po osiągnięciu `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="8c76e-202">W związku z tym, formant nie wrócił do `AccessTheWebAsync`, a pierwsze przypisanie do `pendingWork` nie wystąpiło.</span><span class="sxs-lookup"><span data-stu-id="8c76e-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="8c76e-203">Następujące dwa wiersze zawsze pojawiają się razem w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="8c76e-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="8c76e-204">Kod nigdy nie jest przerywany między rozpoczęciem operacji grupy `StartButton_Click` i przypisywaniem zadania dla grupy w celu `pendingWork`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="8c76e-205">Po przejściu grupy do stanu `StartButton_Click`, operacja nie kończy się i wyrażenie oczekuje, aż operacja wejdzie w stan `FinishOneGroupAsync`.</span><span class="sxs-lookup"><span data-stu-id="8c76e-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="8c76e-206">Dlatego żadna inna operacja może przejmować kontroli w tym segmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="8c76e-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="8c76e-207">Przeglądanie i uruchamianie aplikacji przykładowych</span><span class="sxs-lookup"><span data-stu-id="8c76e-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="8c76e-208">Aby lepiej zrozumieć przykładową aplikację, możesz ją pobrać, skompilować ją samodzielnie lub przejrzeć kod na końcu tego tematu bez wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c76e-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c76e-209">Aby uruchomić przykład jako aplikację pulpitu Windows Presentation Foundation (WPF), konieczne jest posiadanie programu Visual Studio 2012 lub nowszego oraz programu .NET Framework 4.5 lub nowszej zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="8c76e-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="8c76e-210">Pobieranie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8c76e-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="8c76e-211">Pobierz skompresowany plik z [próbki asynchroniczne: współużytkowania wątkowości w aplikacjach pulpitu .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span><span class="sxs-lookup"><span data-stu-id="8c76e-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="8c76e-212">Dekompresuje plik który został pobrany, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c76e-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="8c76e-213">Na pasku menu wybierz **pliku**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="8c76e-214">Przejdź do folderu, który posiada zdekompresowany kod przykładu, a następnie otwórz plik rozwiązania (.sln).</span><span class="sxs-lookup"><span data-stu-id="8c76e-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="8c76e-215">W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu, który chcesz uruchomić, a następnie wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="8c76e-216">Wybierz kombinację klawiszy CTRL + F5 Aby skompilować i uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="8c76e-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="8c76e-217">Kompilowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8c76e-217">Building the App</span></span>  
 <span data-ttu-id="8c76e-218">W poniższej sekcji przedstawiono kod, aby zbudować przykład jako aplikację WPF.</span><span class="sxs-lookup"><span data-stu-id="8c76e-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="8c76e-219">Aby utworzyć aplikację WPF</span><span class="sxs-lookup"><span data-stu-id="8c76e-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="8c76e-220">Uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8c76e-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="8c76e-221">Na pasku menu wybierz **pliku**, **New**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="8c76e-222">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8c76e-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="8c76e-223">W **zainstalowane szablony** okienku rozwiń **języka Visual Basic**, a następnie rozwiń węzeł **Windows**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="8c76e-224">Na liście typów projektów, wybierz opcję **aplikacji WPF**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="8c76e-225">Nadaj projektowi nazwę `WebsiteDownloadWPF`, a następnie wybierz **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="8c76e-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="8c76e-226">Nowy projekt, który pojawia się w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="8c76e-227">W edytorze programu Visual Studio Code wybierz **MainWindow.xaml** kartę.</span><span class="sxs-lookup"><span data-stu-id="8c76e-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="8c76e-228">Jeśli karta nie jest widoczna, otwórz menu skrótów dla pliku MainWindow.xaml w **Eksploratora rozwiązań**, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="8c76e-229">W **XAML** wyświetlić pliku mainwindow.XAML, Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="8c76e-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
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
  
     <span data-ttu-id="8c76e-230">Proste okno, które zawiera pole tekstowe i przycisk pojawia się w **projektowania** widoku MainWindow.xaml.</span><span class="sxs-lookup"><span data-stu-id="8c76e-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="8c76e-231">Dodaj odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="8c76e-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="8c76e-232">W **Eksploratora rozwiązań**, otwórz menu skrótów dla MainWindow.xaml.vb, a następnie wybierz **Wyświetl kod**.</span><span class="sxs-lookup"><span data-stu-id="8c76e-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="8c76e-233">W pliku MainWindow.xaml.vb Zastąp kod następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="8c76e-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
                "http://msdn.microsoft.com/library/hh191443.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/jj155761.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/hh524395.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="8c76e-234">Wybierz klawisze CTRL + F5, aby uruchomić program, a następnie wybierz **Start** przycisk kilka razy.</span><span class="sxs-lookup"><span data-stu-id="8c76e-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="8c76e-235">Wprowadź zmiany w [Wyłącz przycisk Start](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [anulowania i ponownego uruchamiania operacji](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), lub [uruchomić wiele operacji i kolejki danych wyjściowych](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) do obsługi współużytkowania wątkowości.</span><span class="sxs-lookup"><span data-stu-id="8c76e-235">Make the changes from [Disable the Start Button](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), [Cancel and Restart the Operation](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645), or [Run Multiple Operations and Queue the Output](https://msdn.microsoft.com/library/5b54de66-6be3-459e-b869-65070b020645) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c76e-236">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c76e-236">See Also</span></span>  
 [<span data-ttu-id="8c76e-237">Wskazówki: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c76e-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="8c76e-238">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c76e-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
