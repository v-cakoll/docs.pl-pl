---
title: "Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4cd9b2a-f924-470e-a16e-50274709b40e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb0734b4bbf3f8bf5b27305754829f1a9f29f42a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-visual-basic"></a><span data-ttu-id="072bc-102">Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="072bc-102">Walkthrough: Multithreading with the BackgroundWorker Component (Visual Basic)</span></span>
<span data-ttu-id="072bc-103">Ten przewodnik przedstawia sposób tworzenia aplikacji wielowątkowych formularzy systemu Windows, która wyszukuje plik tekstowy dla wystąpień słowa.</span><span class="sxs-lookup"><span data-stu-id="072bc-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="072bc-104">Przedstawia on:</span><span class="sxs-lookup"><span data-stu-id="072bc-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="072bc-105">Definiowanie klas z metody, która może być wywoływany przez <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="072bc-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="072bc-106">Obsługa zdarzeń zgłaszanych przez <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="072bc-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="072bc-107">Uruchamianie <xref:System.ComponentModel.BackgroundWorker> składnik do uruchomienia metody.</span><span class="sxs-lookup"><span data-stu-id="072bc-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="072bc-108">Implementowanie `Cancel` przycisku, który zatrzymuje <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="072bc-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="072bc-109">Aby utworzyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="072bc-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="072bc-110">Otwórz nowy projekt aplikacji formularzy systemu Windows w języku Visual Basic i tworzenia formularza o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="072bc-110">Open a new Visual Basic Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="072bc-111">Dodawanie dwóch przycisków i cztery pola tekstowe do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="072bc-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="072bc-112">Nazwy obiektów, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="072bc-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="072bc-113">Obiekt</span><span class="sxs-lookup"><span data-stu-id="072bc-113">Object</span></span>|<span data-ttu-id="072bc-114">Właściwość</span><span class="sxs-lookup"><span data-stu-id="072bc-114">Property</span></span>|<span data-ttu-id="072bc-115">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="072bc-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="072bc-116">Pierwszy przycisk</span><span class="sxs-lookup"><span data-stu-id="072bc-116">First button</span></span>|<span data-ttu-id="072bc-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-117">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-118">Start, uruchamia</span><span class="sxs-lookup"><span data-stu-id="072bc-118">Start, Start</span></span>|  
    |<span data-ttu-id="072bc-119">Drugi przycisk</span><span class="sxs-lookup"><span data-stu-id="072bc-119">Second button</span></span>|<span data-ttu-id="072bc-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-120">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-121">Anuluj, Anuluj</span><span class="sxs-lookup"><span data-stu-id="072bc-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="072bc-122">Pierwsze pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="072bc-122">First text box</span></span>|<span data-ttu-id="072bc-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-123">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="072bc-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="072bc-125">Drugie pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="072bc-125">Second text box</span></span>|<span data-ttu-id="072bc-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-126">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="072bc-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="072bc-128">Trzecie pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="072bc-128">Third text box</span></span>|<span data-ttu-id="072bc-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-129">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-130">WordsCounted "0"</span><span class="sxs-lookup"><span data-stu-id="072bc-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="072bc-131">Czwarte pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="072bc-131">Fourth text box</span></span>|<span data-ttu-id="072bc-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="072bc-132">`Name`, `Text`</span></span>|<span data-ttu-id="072bc-133">LinesCounted "0"</span><span class="sxs-lookup"><span data-stu-id="072bc-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="072bc-134">Dodaj etykietę obok każdego pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="072bc-134">Add a label next to each text box.</span></span> <span data-ttu-id="072bc-135">Ustaw `Text` właściwości dla każdej etykiety, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="072bc-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="072bc-136">Obiekt</span><span class="sxs-lookup"><span data-stu-id="072bc-136">Object</span></span>|<span data-ttu-id="072bc-137">Właściwość</span><span class="sxs-lookup"><span data-stu-id="072bc-137">Property</span></span>|<span data-ttu-id="072bc-138">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="072bc-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="072bc-139">Pierwsza etykieta</span><span class="sxs-lookup"><span data-stu-id="072bc-139">First label</span></span>|`Text`|<span data-ttu-id="072bc-140">Plik źródłowy</span><span class="sxs-lookup"><span data-stu-id="072bc-140">Source File</span></span>|  
    |<span data-ttu-id="072bc-141">Drugi etykiety</span><span class="sxs-lookup"><span data-stu-id="072bc-141">Second label</span></span>|`Text`|<span data-ttu-id="072bc-142">Porównanie ciągów</span><span class="sxs-lookup"><span data-stu-id="072bc-142">Compare String</span></span>|  
    |<span data-ttu-id="072bc-143">Trzeci etykiety</span><span class="sxs-lookup"><span data-stu-id="072bc-143">Third label</span></span>|`Text`|<span data-ttu-id="072bc-144">Dopasowanie słów</span><span class="sxs-lookup"><span data-stu-id="072bc-144">Matching Words</span></span>|  
    |<span data-ttu-id="072bc-145">Czwarty etykiety</span><span class="sxs-lookup"><span data-stu-id="072bc-145">Fourth label</span></span>|`Text`|<span data-ttu-id="072bc-146">Wiersze zliczane</span><span class="sxs-lookup"><span data-stu-id="072bc-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="072bc-147">Aby utworzyć składnika BackgroundWorker i subskrybowanie zdarzeń jego</span><span class="sxs-lookup"><span data-stu-id="072bc-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="072bc-148">Dodaj <xref:System.ComponentModel.BackgroundWorker> składnika z **składniki** sekcji **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="072bc-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="072bc-149">Pojawi się w części formularza na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="072bc-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="072bc-150">Ustaw następujące właściwości dla obiektu BackgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="072bc-150">Set the following properties for the BackgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="072bc-151">Właściwość</span><span class="sxs-lookup"><span data-stu-id="072bc-151">Property</span></span>|<span data-ttu-id="072bc-152">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="072bc-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="072bc-153">Wartość true</span><span class="sxs-lookup"><span data-stu-id="072bc-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="072bc-154">Wartość true</span><span class="sxs-lookup"><span data-stu-id="072bc-154">True</span></span>|  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="072bc-155">Aby zdefiniować metody, które zostanie uruchomione w oddzielnym wątku</span><span class="sxs-lookup"><span data-stu-id="072bc-155">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="072bc-156">Z **projektu** menu, wybierz **Dodaj klasę** Aby dodać klasę do projektu.</span><span class="sxs-lookup"><span data-stu-id="072bc-156">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="072bc-157">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="072bc-157">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="072bc-158">Wybierz **klasy** z okna Szablony, a następnie wprowadź `Words.vb` w polu Nazwa.</span><span class="sxs-lookup"><span data-stu-id="072bc-158">Select **Class** from the templates window and enter `Words.vb` in the name field.</span></span>  
  
3.  <span data-ttu-id="072bc-159">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="072bc-159">Click **Add**.</span></span> <span data-ttu-id="072bc-160">`Words` Wyświetlana klasy.</span><span class="sxs-lookup"><span data-stu-id="072bc-160">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="072bc-161">Dodaj następujący kod do `Words` klasy:</span><span class="sxs-lookup"><span data-stu-id="072bc-161">Add the following code to the `Words` class:</span></span>  
  
    ```vb  
    Public Class Words  
        ' Object to store the current state, for passing to the caller.  
        Public Class CurrentState  
            Public LinesCounted As Integer  
            Public WordsMatched As Integer  
        End Class  
  
        Public SourceFile As String  
        Public CompareString As String  
        Private WordCount As Integer = 0  
        Private LinesCounted As Integer = 0  
  
        Public Sub CountWords(  
            ByVal worker As System.ComponentModel.BackgroundWorker,  
            ByVal e As System.ComponentModel.DoWorkEventArgs  
        )  
            ' Initialize the variables.  
            Dim state As New CurrentState  
            Dim line = ""  
            Dim elapsedTime = 20  
            Dim lastReportDateTime = Now  
  
            If CompareString Is Nothing OrElse  
               CompareString = System.String.Empty Then  
  
               Throw New Exception("CompareString not specified.")  
            End If  
  
            Using myStream As New System.IO.StreamReader(SourceFile)  
  
                ' Process lines while there are lines remaining in the file.  
                Do While Not myStream.EndOfStream  
                    If worker.CancellationPending Then  
                        e.Cancel = True  
                        Exit Do  
                    Else  
                        line = myStream.ReadLine  
                        WordCount += CountInString(line, CompareString)  
                        LinesCounted += 1  
  
                        ' Raise an event so the form can monitor progress.  
                        If Now > lastReportDateTime.AddMilliseconds(elapsedTime) Then  
                            state.LinesCounted = LinesCounted  
                            state.WordsMatched = WordCount  
                            worker.ReportProgress(0, state)  
                            lastReportDateTime = Now  
                        End If  
  
                        ' Uncomment for testing.  
                        'System.Threading.Thread.Sleep(5)  
                    End If  
                Loop  
  
                ' Report the final count values.  
                state.LinesCounted = LinesCounted  
                state.WordsMatched = WordCount  
                worker.ReportProgress(0, state)  
            End Using  
        End Sub  
  
        Private Function CountInString(  
            ByVal SourceString As String,  
            ByVal CompareString As String  
        ) As Integer  
            ' This function counts the number of times  
            ' a word is found in a line.  
            If SourceString Is Nothing Then  
                Return 0  
            End If  
  
            Dim EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString)  
  
            ' To count all occurrences of the string, even within words, remove  
            ' both instances of "\b".  
            Dim regex As New System.Text.RegularExpressions.Regex(  
                "\b" + EscapedCompareString + "\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase)  
  
            Dim matches As System.Text.RegularExpressions.MatchCollection  
            matches = regex.Matches(SourceString)  
            Return matches.Count  
        End Function  
    End Class  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="072bc-162">Do obsługi zdarzeń z wątku</span><span class="sxs-lookup"><span data-stu-id="072bc-162">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="072bc-163">Dodaj następujące programy obsługi zdarzeń do głównego formularza:</span><span class="sxs-lookup"><span data-stu-id="072bc-163">Add the following event handlers to your main form:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_RunWorkerCompleted(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.RunWorkerCompletedEventArgs  
      ) Handles BackgroundWorker1.RunWorkerCompleted  
  
        ' This event handler is called when the background thread finishes.  
        ' This method runs on the main thread.  
        If e.Error IsNot Nothing Then  
            MessageBox.Show("Error: " & e.Error.Message)  
        ElseIf e.Cancelled Then  
            MessageBox.Show("Word counting canceled.")  
        Else  
            MessageBox.Show("Finished counting words.")  
        End If  
    End Sub  
  
    Private Sub BackgroundWorker1_ProgressChanged(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.ProgressChangedEventArgs  
      ) Handles BackgroundWorker1.ProgressChanged  
  
        ' This method runs on the main thread.  
        Dim state As Words.CurrentState =   
            CType(e.UserState, Words.CurrentState)  
        Me.LinesCounted.Text = state.LinesCounted.ToString  
        Me.WordsCounted.Text = state.WordsMatched.ToString  
    End Sub  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="072bc-164">Aby uruchomić i wywołać nowego wątku, który uruchamia metody WordCount</span><span class="sxs-lookup"><span data-stu-id="072bc-164">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="072bc-165">Dodaj poniższe procedury służą do programu:</span><span class="sxs-lookup"><span data-stu-id="072bc-165">Add the following procedures to your program:</span></span>  
  
    ```vb  
    Private Sub BackgroundWorker1_DoWork(   
        ByVal sender As Object,   
        ByVal e As System.ComponentModel.DoWorkEventArgs  
      ) Handles BackgroundWorker1.DoWork  
  
        ' This event handler is where the actual work is done.  
        ' This method runs on the background thread.  
  
        ' Get the BackgroundWorker object that raised this event.  
        Dim worker As System.ComponentModel.BackgroundWorker  
        worker = CType(sender, System.ComponentModel.BackgroundWorker)  
  
        ' Get the Words object and call the main method.  
        Dim WC As Words = CType(e.Argument, Words)  
        WC.CountWords(worker, e)  
    End Sub  
  
    Sub StartThread()  
        ' This method runs on the main thread.  
        Me.WordsCounted.Text = "0"  
  
        ' Initialize the object that the background worker calls.  
        Dim WC As New Words  
        WC.CompareString = Me.CompareString.Text  
        WC.SourceFile = Me.SourceFile.Text  
  
        ' Start the asynchronous operation.  
        BackgroundWorker1.RunWorkerAsync(WC)  
    End Sub  
    ```  
  
2.  <span data-ttu-id="072bc-166">Wywołanie `StartThread` metody z `Start` przycisk w formularzu:</span><span class="sxs-lookup"><span data-stu-id="072bc-166">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```vb  
    Private Sub Start_Click() Handles Start.Click  
        StartThread()  
    End Sub  
    ```  
  
### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="072bc-167">Aby zaimplementować przycisk Anuluj, która kończy się wątek</span><span class="sxs-lookup"><span data-stu-id="072bc-167">To implement a Cancel button that stops the thread</span></span>  
  
-   <span data-ttu-id="072bc-168">Wywołanie `StopThread` procedury z `Click` programu obsługi zdarzeń dla `Cancel` przycisku.</span><span class="sxs-lookup"><span data-stu-id="072bc-168">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
    ```vb  
    Private Sub Cancel_Click() Handles Cancel.Click  
        ' Cancel the asynchronous operation.  
        Me.BackgroundWorker1.CancelAsync()  
    End Sub  
    ```  
  
## <a name="testing"></a><span data-ttu-id="072bc-169">Testowanie</span><span class="sxs-lookup"><span data-stu-id="072bc-169">Testing</span></span>  
 <span data-ttu-id="072bc-170">Teraz możesz przetestować aplikację, aby upewnić się, że działa on prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="072bc-170">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="072bc-171">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="072bc-171">To test the application</span></span>  
  
1.  <span data-ttu-id="072bc-172">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="072bc-172">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="072bc-173">Gdy formularz jest wyświetlany, podaj ścieżkę do pliku dla pliku, który chcesz przetestować w `sourceFile` pole.</span><span class="sxs-lookup"><span data-stu-id="072bc-173">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="072bc-174">Na przykład przy założeniu, że plik testu nosi nazwę Test.txt, wprowadź C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="072bc-174">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="072bc-175">W drugim polu tekstowym wprowadź słowo lub frazę dla aplikacji, aby wyszukać w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="072bc-175">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="072bc-176">Kliknij przycisk `Start` przycisku.</span><span class="sxs-lookup"><span data-stu-id="072bc-176">Click the `Start` button.</span></span> <span data-ttu-id="072bc-177">`LinesCounted` Przycisk powinien rozpocząć zwiększanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="072bc-177">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="072bc-178">Aplikacja wyświetla komunikat "Zakończono zliczania" po jej zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="072bc-178">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="072bc-179">Aby przetestować przycisku Anuluj</span><span class="sxs-lookup"><span data-stu-id="072bc-179">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="072bc-180">Naciśnij klawisz F5, aby uruchomić aplikację, a następnie wprowadź plik nazwę i wyszukaj słowo zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="072bc-180">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="072bc-181">Upewnij się, że wybrany plik jest wystarczająco duże, aby upewnić się, że będzie czasu, aby anulować procedury przed zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="072bc-181">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="072bc-182">Kliknij przycisk `Start` przycisk, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="072bc-182">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="072bc-183">Kliknij przycisk `Cancel` przycisku.</span><span class="sxs-lookup"><span data-stu-id="072bc-183">Click the `Cancel` button.</span></span> <span data-ttu-id="072bc-184">Aplikacja ma zostać zatrzymana, licząc od razu.</span><span class="sxs-lookup"><span data-stu-id="072bc-184">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="072bc-185">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="072bc-185">Next Steps</span></span>  
 <span data-ttu-id="072bc-186">Ta aplikacja zawiera niektóre obsługi podstawowych błędów.</span><span class="sxs-lookup"><span data-stu-id="072bc-186">This application contains some basic error handling.</span></span> <span data-ttu-id="072bc-187">Ta funkcja wykrywa ciągów wyszukiwania puste.</span><span class="sxs-lookup"><span data-stu-id="072bc-187">It detects blank search strings.</span></span> <span data-ttu-id="072bc-188">Możesz wprowadzić ten program bardziej niezawodne dzięki obsłudze inne błędy, takich jak przekroczenie maksymalnej liczby słów lub wierszy, które mogą być traktowane.</span><span class="sxs-lookup"><span data-stu-id="072bc-188">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="072bc-189">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="072bc-189">See Also</span></span>  
 [<span data-ttu-id="072bc-190">Wątkowość (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="072bc-190">Threading (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="072bc-191">Wskazówki: Tworzenie prostego składnika wielowątkowości za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="072bc-191">Walkthrough: Authoring a Simple Multithreaded Component with Visual Basic</span></span>](http://msdn.microsoft.com/library/05693b70-3566-4d91-9f2c-c9bc4ccb3001)  
 [<span data-ttu-id="072bc-192">Porady: subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="072bc-192">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
