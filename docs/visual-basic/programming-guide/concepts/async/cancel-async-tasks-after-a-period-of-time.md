---
title: Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
ms.openlocfilehash: 636e8ffc86ce2849d563094bb780943f57d9cfa4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69958134"
---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="5f73e-102">Anulowanie zadań asynchronicznych po upływie czasu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f73e-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>
<span data-ttu-id="5f73e-103">Istnieje możliwość anulowania operacji asynchronicznej po upływie okresu czasu przy użyciu <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, jeśli nie chcesz czekać na zakończenie operacji.</span><span class="sxs-lookup"><span data-stu-id="5f73e-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="5f73e-104">Ta metoda służy do planowania anulowania wszystkich skojarzonych zadań, które nie zostały ukończone w okresie wyznaczonym przez `CancelAfter` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5f73e-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="5f73e-105">Ten przykład dodaje do kodu, który został opracowany w wyniku [anulowania zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) , aby pobrać listę witryn sieci Web i wyświetlić długość zawartości każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="5f73e-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f73e-106">Aby uruchomić przykłady, musisz mieć zainstalowany program Visual Studio 2012 lub nowszy oraz .NET Framework 4,5 lub nowszy na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5f73e-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="5f73e-107">Pobieranie przykładu</span><span class="sxs-lookup"><span data-stu-id="5f73e-107">Downloading the Example</span></span>  
 <span data-ttu-id="5f73e-108">Możesz pobrać kompletny projekt Windows Presentation Foundation (WPF) z [próbki asynchronicznej: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) , a następnie wykonaj poniższe kroki.</span><span class="sxs-lookup"><span data-stu-id="5f73e-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="5f73e-109">Dekompresuj pobrany plik, a następnie uruchom program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5f73e-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="5f73e-110">Na pasku menu wybierz **plik**, **Otwórz**, **projekt/rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="5f73e-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="5f73e-111">W oknie dialogowym **Otwórz projekt** Otwórz folder, w którym znajduje się przykładowy kod, który został zdekompresowany, a następnie otwórz plik rozwiązania (. sln) dla AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="5f73e-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="5f73e-112">W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu **CancelAfterTime** , a następnie wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="5f73e-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="5f73e-113">Wybierz klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="5f73e-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="5f73e-114">Naciśnij klawisze CTRL + F5, aby uruchomić projekt bez debugowania.</span><span class="sxs-lookup"><span data-stu-id="5f73e-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="5f73e-115">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych.</span><span class="sxs-lookup"><span data-stu-id="5f73e-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="5f73e-116">Jeśli nie chcesz pobierać projektu, możesz przejrzeć plik MainWindow. XAML. vb na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5f73e-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="5f73e-117">Kompilowanie przykładu</span><span class="sxs-lookup"><span data-stu-id="5f73e-117">Building the Example</span></span>  
 <span data-ttu-id="5f73e-118">Przykład w tym temacie dodaje do projektu, który został opracowany w [wyniku anulowania zadania asynchronicznego lub listy zadań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) , aby anulować listę zadań.</span><span class="sxs-lookup"><span data-stu-id="5f73e-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="5f73e-119">W przykładzie użyto tego samego interfejsu użytkownika, chociaż przycisk **Anuluj** nie jest używany jawnie.</span><span class="sxs-lookup"><span data-stu-id="5f73e-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="5f73e-120">Aby zbudować przykład samodzielnie, krok po kroku, postępuj zgodnie z instrukcjami w sekcji Pobieranie przykładu, ale wybierz **CancelAListOfTasks** jako **projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="5f73e-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="5f73e-121">Dodaj zmiany w tym temacie do tego projektu.</span><span class="sxs-lookup"><span data-stu-id="5f73e-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="5f73e-122">Aby określić maksymalny czas, po jakim zadania są oznaczane jako anulowane, należy dodać `CancelAfter` wywołanie `startButton_Click`do, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5f73e-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="5f73e-123">Dodanie jest oznaczone gwiazdkami.</span><span class="sxs-lookup"><span data-stu-id="5f73e-123">The addition is marked with asterisks.</span></span>  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
        Await AccessTheWebAsync(cts.Token)  
        resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
    Catch ex As OperationCanceledException  
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
    Catch ex As Exception  
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
    End Try  
  
    ' Set the CancellationTokenSource to Nothing when the download is complete.  
    cts = Nothing  
End Sub  
```  
  
 <span data-ttu-id="5f73e-124">Uruchom program kilka razy, aby sprawdzić, czy dane wyjściowe mogą zawierać dane wyjściowe dla wszystkich witryn sieci Web, braku witryn internetowych lub niektórych witryn internetowych.</span><span class="sxs-lookup"><span data-stu-id="5f73e-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="5f73e-125">Oto przykład danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="5f73e-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="5f73e-126">Kompletny przykład</span><span class="sxs-lookup"><span data-stu-id="5f73e-126">Complete Example</span></span>  
 <span data-ttu-id="5f73e-127">Poniższy kod jest pełnym tekstem pliku MainWindow. XAML. vb dla przykładu.</span><span class="sxs-lookup"><span data-stu-id="5f73e-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="5f73e-128">Gwiazdki oznaczają elementy, które zostały dodane do tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="5f73e-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="5f73e-129">Należy zauważyć, że należy dodać odwołanie do <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="5f73e-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="5f73e-130">Możesz pobrać projekt z [przykładu asynchronicznego: Dostosuj aplikację](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="5f73e-130">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f73e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f73e-131">See also</span></span>

- [<span data-ttu-id="5f73e-132">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f73e-132">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="5f73e-133">Przewodnik: Uzyskiwanie dostępu do sieci Web za pomocą Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f73e-133">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="5f73e-134">Anulowanie zadania asynchronicznego lub listy zadań (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f73e-134">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [<span data-ttu-id="5f73e-135">Dostrajanie aplikacji asynchronicznej (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f73e-135">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="5f73e-136">Przykład asynchroniczny: Dostrajanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="5f73e-136">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
