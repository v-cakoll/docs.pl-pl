---
title: 'Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)'
ms.date: 07/20/2015
ms.assetid: ff670fbf-a0ac-40c1-ab08-9ed53768f880
ms.openlocfilehash: bc334261dbea7759d1bb571cc61a5f00f84531a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-multithreading-with-the-backgroundworker-component-c"></a><span data-ttu-id="08497-102">Wskazówki: Wielowątkowość ze składnikiem BackgroundWorker (C#)</span><span class="sxs-lookup"><span data-stu-id="08497-102">Walkthrough: Multithreading with the BackgroundWorker Component (C#)</span></span>
<span data-ttu-id="08497-103">Ten przewodnik przedstawia sposób tworzenia aplikacji wielowątkowych formularzy systemu Windows, która wyszukuje plik tekstowy dla wystąpień słowa.</span><span class="sxs-lookup"><span data-stu-id="08497-103">This walkthrough demonstrates how to create a multithreaded Windows Forms application that searches a text file for occurrences of a word.</span></span> <span data-ttu-id="08497-104">Przedstawia on:</span><span class="sxs-lookup"><span data-stu-id="08497-104">It demonstrates:</span></span>  
  
-   <span data-ttu-id="08497-105">Definiowanie klas z metody, która może być wywoływany przez <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="08497-105">Defining a class with a method that can be called by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="08497-106">Obsługa zdarzeń zgłaszanych przez <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="08497-106">Handling events raised by the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
-   <span data-ttu-id="08497-107">Uruchamianie <xref:System.ComponentModel.BackgroundWorker> składnik do uruchomienia metody.</span><span class="sxs-lookup"><span data-stu-id="08497-107">Starting a <xref:System.ComponentModel.BackgroundWorker> component to run a method.</span></span>  
  
-   <span data-ttu-id="08497-108">Implementowanie `Cancel` przycisku, który zatrzymuje <xref:System.ComponentModel.BackgroundWorker> składnika.</span><span class="sxs-lookup"><span data-stu-id="08497-108">Implementing a `Cancel` button that stops the <xref:System.ComponentModel.BackgroundWorker> component.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="08497-109">Aby utworzyć interfejs użytkownika</span><span class="sxs-lookup"><span data-stu-id="08497-109">To create the user interface</span></span>  
  
1.  <span data-ttu-id="08497-110">Otwórz nowy projekt aplikacji formularzy systemu Windows C# i utworzenie formularza o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="08497-110">Open a new C# Windows Forms Application project, and create a form named `Form1`.</span></span>  
  
2.  <span data-ttu-id="08497-111">Dodawanie dwóch przycisków i cztery pola tekstowe do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="08497-111">Add two buttons and four text boxes to `Form1`.</span></span>  
  
3.  <span data-ttu-id="08497-112">Nazwy obiektów, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="08497-112">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="08497-113">Obiekt</span><span class="sxs-lookup"><span data-stu-id="08497-113">Object</span></span>|<span data-ttu-id="08497-114">Właściwość</span><span class="sxs-lookup"><span data-stu-id="08497-114">Property</span></span>|<span data-ttu-id="08497-115">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="08497-115">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="08497-116">Pierwszy przycisk</span><span class="sxs-lookup"><span data-stu-id="08497-116">First button</span></span>|<span data-ttu-id="08497-117">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-117">`Name`, `Text`</span></span>|<span data-ttu-id="08497-118">Start, uruchamia</span><span class="sxs-lookup"><span data-stu-id="08497-118">Start, Start</span></span>|  
    |<span data-ttu-id="08497-119">Drugi przycisk</span><span class="sxs-lookup"><span data-stu-id="08497-119">Second button</span></span>|<span data-ttu-id="08497-120">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-120">`Name`, `Text`</span></span>|<span data-ttu-id="08497-121">Anuluj, Anuluj</span><span class="sxs-lookup"><span data-stu-id="08497-121">Cancel, Cancel</span></span>|  
    |<span data-ttu-id="08497-122">Pierwsze pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="08497-122">First text box</span></span>|<span data-ttu-id="08497-123">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-123">`Name`, `Text`</span></span>|<span data-ttu-id="08497-124">SourceFile, ""</span><span class="sxs-lookup"><span data-stu-id="08497-124">SourceFile, ""</span></span>|  
    |<span data-ttu-id="08497-125">Drugie pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="08497-125">Second text box</span></span>|<span data-ttu-id="08497-126">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-126">`Name`, `Text`</span></span>|<span data-ttu-id="08497-127">CompareString, ""</span><span class="sxs-lookup"><span data-stu-id="08497-127">CompareString, ""</span></span>|  
    |<span data-ttu-id="08497-128">Trzecie pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="08497-128">Third text box</span></span>|<span data-ttu-id="08497-129">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-129">`Name`, `Text`</span></span>|<span data-ttu-id="08497-130">WordsCounted "0"</span><span class="sxs-lookup"><span data-stu-id="08497-130">WordsCounted, "0"</span></span>|  
    |<span data-ttu-id="08497-131">Czwarte pole tekstowe</span><span class="sxs-lookup"><span data-stu-id="08497-131">Fourth text box</span></span>|<span data-ttu-id="08497-132">`Name`, `Text`</span><span class="sxs-lookup"><span data-stu-id="08497-132">`Name`, `Text`</span></span>|<span data-ttu-id="08497-133">LinesCounted "0"</span><span class="sxs-lookup"><span data-stu-id="08497-133">LinesCounted, "0"</span></span>|  
  
4.  <span data-ttu-id="08497-134">Dodaj etykietę obok każdego pola tekstowego.</span><span class="sxs-lookup"><span data-stu-id="08497-134">Add a label next to each text box.</span></span> <span data-ttu-id="08497-135">Ustaw `Text` właściwości dla każdej etykiety, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="08497-135">Set the `Text` property for each label as shown in the following table.</span></span>  
  
    |<span data-ttu-id="08497-136">Obiekt</span><span class="sxs-lookup"><span data-stu-id="08497-136">Object</span></span>|<span data-ttu-id="08497-137">Właściwość</span><span class="sxs-lookup"><span data-stu-id="08497-137">Property</span></span>|<span data-ttu-id="08497-138">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="08497-138">Setting</span></span>|  
    |------------|--------------|-------------|  
    |<span data-ttu-id="08497-139">Pierwsza etykieta</span><span class="sxs-lookup"><span data-stu-id="08497-139">First label</span></span>|`Text`|<span data-ttu-id="08497-140">Plik źródłowy</span><span class="sxs-lookup"><span data-stu-id="08497-140">Source File</span></span>|  
    |<span data-ttu-id="08497-141">Drugi etykiety</span><span class="sxs-lookup"><span data-stu-id="08497-141">Second label</span></span>|`Text`|<span data-ttu-id="08497-142">Porównanie ciągów</span><span class="sxs-lookup"><span data-stu-id="08497-142">Compare String</span></span>|  
    |<span data-ttu-id="08497-143">Trzeci etykiety</span><span class="sxs-lookup"><span data-stu-id="08497-143">Third label</span></span>|`Text`|<span data-ttu-id="08497-144">Dopasowanie słów</span><span class="sxs-lookup"><span data-stu-id="08497-144">Matching Words</span></span>|  
    |<span data-ttu-id="08497-145">Czwarty etykiety</span><span class="sxs-lookup"><span data-stu-id="08497-145">Fourth label</span></span>|`Text`|<span data-ttu-id="08497-146">Wiersze zliczane</span><span class="sxs-lookup"><span data-stu-id="08497-146">Lines Counted</span></span>|  
  
### <a name="to-create-a-backgroundworker-component-and-subscribe-to-its-events"></a><span data-ttu-id="08497-147">Aby utworzyć składnika BackgroundWorker i subskrybowanie zdarzeń jego</span><span class="sxs-lookup"><span data-stu-id="08497-147">To create a BackgroundWorker component and subscribe to its events</span></span>  
  
1.  <span data-ttu-id="08497-148">Dodaj <xref:System.ComponentModel.BackgroundWorker> składnika z **składniki** sekcji **przybornika** do formularza.</span><span class="sxs-lookup"><span data-stu-id="08497-148">Add a <xref:System.ComponentModel.BackgroundWorker> component from the **Components** section of the **ToolBox** to the form.</span></span> <span data-ttu-id="08497-149">Pojawi się w części formularza na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="08497-149">It will appear in the form's component tray.</span></span>  
  
2.  <span data-ttu-id="08497-150">Ustaw następujące właściwości dla obiektu backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="08497-150">Set the following properties for the backgroundWorker1 object.</span></span>  
  
    |<span data-ttu-id="08497-151">Właściwość</span><span class="sxs-lookup"><span data-stu-id="08497-151">Property</span></span>|<span data-ttu-id="08497-152">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="08497-152">Setting</span></span>|  
    |--------------|-------------|  
    |`WorkerReportsProgress`|<span data-ttu-id="08497-153">True</span><span class="sxs-lookup"><span data-stu-id="08497-153">True</span></span>|  
    |`WorkerSupportsCancellation`|<span data-ttu-id="08497-154">True</span><span class="sxs-lookup"><span data-stu-id="08497-154">True</span></span>|  
  
3.  <span data-ttu-id="08497-155">Subskrybowanie zdarzeń obiektu backgroundWorker1.</span><span class="sxs-lookup"><span data-stu-id="08497-155">Subscribe to the events of the backgroundWorker1 object.</span></span> <span data-ttu-id="08497-156">W górnej części **właściwości** okna, kliknij przycisk **zdarzenia** ikony.</span><span class="sxs-lookup"><span data-stu-id="08497-156">At the top of the **Properties** window, click the **Events** icon.</span></span> <span data-ttu-id="08497-157">Kliknij dwukrotnie `RunWorkerCompleted` zdarzeń, aby utworzyć metoda obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="08497-157">Double-click the `RunWorkerCompleted` event to create an event handler method.</span></span> <span data-ttu-id="08497-158">Tym samym `ProgressChanged` i `DoWork` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="08497-158">Do the same for the `ProgressChanged` and `DoWork` events.</span></span>  
  
### <a name="to-define-the-method-that-will-run-on-a-separate-thread"></a><span data-ttu-id="08497-159">Aby zdefiniować metody, które zostanie uruchomione w oddzielnym wątku</span><span class="sxs-lookup"><span data-stu-id="08497-159">To define the method that will run on a separate thread</span></span>  
  
1.  <span data-ttu-id="08497-160">Z **projektu** menu, wybierz **Dodaj klasę** Aby dodać klasę do projektu.</span><span class="sxs-lookup"><span data-stu-id="08497-160">From the **Project** menu, choose **Add Class** to add a class to the project.</span></span> <span data-ttu-id="08497-161">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="08497-161">The **Add New Item** dialog box is displayed.</span></span>  
  
2.  <span data-ttu-id="08497-162">Wybierz **klasy** z okna Szablony, a następnie wprowadź `Words.cs` w polu Nazwa.</span><span class="sxs-lookup"><span data-stu-id="08497-162">Select **Class** from the templates window and enter `Words.cs` in the name field.</span></span>  
  
3.  <span data-ttu-id="08497-163">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="08497-163">Click **Add**.</span></span> <span data-ttu-id="08497-164">`Words` Wyświetlana klasy.</span><span class="sxs-lookup"><span data-stu-id="08497-164">The `Words` class is displayed.</span></span>  
  
4.  <span data-ttu-id="08497-165">Dodaj następujący kod do `Words` klasy:</span><span class="sxs-lookup"><span data-stu-id="08497-165">Add the following code to the `Words` class:</span></span>  
  
    ```csharp  
    public class Words  
    {  
        // Object to store the current state, for passing to the caller.  
        public class CurrentState  
        {  
            public int LinesCounted;  
            public int WordsMatched;  
        }  
  
        public string SourceFile;  
        public string CompareString;  
        private int WordCount;  
        private int LinesCounted;  
  
        public void CountWords(  
            System.ComponentModel.BackgroundWorker worker,  
            System.ComponentModel.DoWorkEventArgs e)  
        {  
            // Initialize the variables.  
            CurrentState state = new CurrentState();  
            string line = "";  
            int elapsedTime = 20;  
            DateTime lastReportDateTime = DateTime.Now;  
  
            if (CompareString == null ||  
                CompareString == System.String.Empty)  
            {  
                throw new Exception("CompareString not specified.");  
            }  
  
            // Open a new stream.  
            using (System.IO.StreamReader myStream = new System.IO.StreamReader(SourceFile))  
            {  
                // Process lines while there are lines remaining in the file.  
                while (!myStream.EndOfStream)  
                {  
                    if (worker.CancellationPending)  
                    {  
                        e.Cancel = true;  
                        break;  
                    }  
                    else  
                    {  
                        line = myStream.ReadLine();  
                        WordCount += CountInString(line, CompareString);  
                        LinesCounted += 1;  
  
                        // Raise an event so the form can monitor progress.  
                        int compare = DateTime.Compare(  
                            DateTime.Now, lastReportDateTime.AddMilliseconds(elapsedTime));  
                        if (compare > 0)  
                        {  
                            state.LinesCounted = LinesCounted;  
                            state.WordsMatched = WordCount;  
                            worker.ReportProgress(0, state);  
                            lastReportDateTime = DateTime.Now;  
                        }  
                    }  
                    // Uncomment for testing.  
                    //System.Threading.Thread.Sleep(5);  
                }  
  
                // Report the final count values.  
                state.LinesCounted = LinesCounted;  
                state.WordsMatched = WordCount;  
                worker.ReportProgress(0, state);  
            }  
        }  
  
        private int CountInString(  
            string SourceString,  
            string CompareString)  
        {  
            // This function counts the number of times  
            // a word is found in a line.  
            if (SourceString == null)  
            {  
                return 0;  
            }  
  
            string EscapedCompareString =  
                System.Text.RegularExpressions.Regex.Escape(CompareString);  
  
            System.Text.RegularExpressions.Regex regex;  
            regex = new System.Text.RegularExpressions.Regex(   
                // To count all occurrences of the string, even within words, remove  
                // both instances of @"\b" from the following line.  
                @"\b" + EscapedCompareString + @"\b",  
                System.Text.RegularExpressions.RegexOptions.IgnoreCase);  
  
            System.Text.RegularExpressions.MatchCollection matches;  
            matches = regex.Matches(SourceString);  
            return matches.Count;  
        }  
  
    }  
    ```  
  
### <a name="to-handle-events-from-the-thread"></a><span data-ttu-id="08497-166">Do obsługi zdarzeń z wątku</span><span class="sxs-lookup"><span data-stu-id="08497-166">To handle events from the thread</span></span>  
  
-   <span data-ttu-id="08497-167">Dodaj następujące programy obsługi zdarzeń do głównego formularza:</span><span class="sxs-lookup"><span data-stu-id="08497-167">Add the following event handlers to your main form:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_RunWorkerCompleted(object sender, RunWorkerCompletedEventArgs e)  
    {  
    // This event handler is called when the background thread finishes.  
    // This method runs on the main thread.  
    if (e.Error != null)  
        MessageBox.Show("Error: " + e.Error.Message);  
    else if (e.Cancelled)  
        MessageBox.Show("Word counting canceled.");  
    else  
        MessageBox.Show("Finished counting words.");  
    }  
  
    private void backgroundWorker1_ProgressChanged(object sender, ProgressChangedEventArgs e)  
    {  
        // This method runs on the main thread.  
        Words.CurrentState state =  
            (Words.CurrentState)e.UserState;  
        this.LinesCounted.Text = state.LinesCounted.ToString();  
        this.WordsCounted.Text = state.WordsMatched.ToString();  
    }  
    ```  
  
### <a name="to-start-and-call-a-new-thread-that-runs-the-wordcount-method"></a><span data-ttu-id="08497-168">Aby uruchomić i wywołać nowego wątku, który uruchamia metody WordCount</span><span class="sxs-lookup"><span data-stu-id="08497-168">To start and call a new thread that runs the WordCount method</span></span>  
  
1.  <span data-ttu-id="08497-169">Dodaj poniższe procedury służą do programu:</span><span class="sxs-lookup"><span data-stu-id="08497-169">Add the following procedures to your program:</span></span>  
  
    ```csharp  
    private void backgroundWorker1_DoWork(object sender, DoWorkEventArgs e)  
    {  
        // This event handler is where the actual work is done.  
        // This method runs on the background thread.  
  
        // Get the BackgroundWorker object that raised this event.  
        System.ComponentModel.BackgroundWorker worker;  
        worker = (System.ComponentModel.BackgroundWorker)sender;  
  
        // Get the Words object and call the main method.  
        Words WC = (Words)e.Argument;  
        WC.CountWords(worker, e);  
    }  
  
    private void StartThread()  
    {  
        // This method runs on the main thread.  
        this.WordsCounted.Text = "0";  
  
        // Initialize the object that the background worker calls.  
        Words WC = new Words();  
        WC.CompareString = this.CompareString.Text;  
        WC.SourceFile = this.SourceFile.Text;  
  
        // Start the asynchronous operation.  
        backgroundWorker1.RunWorkerAsync(WC);  
    }  
    ```  
  
2.  <span data-ttu-id="08497-170">Wywołanie `StartThread` metody z `Start` przycisk w formularzu:</span><span class="sxs-lookup"><span data-stu-id="08497-170">Call the `StartThread` method from the `Start` button on your form:</span></span>  
  
    ```csharp  
    private void Start_Click(object sender, EventArgs e)  
    {  
        StartThread();  
    }  
    ```  
  
    ##### <a name="to-implement-a-cancel-button-that-stops-the-thread"></a><span data-ttu-id="08497-171">Aby zaimplementować przycisk Anuluj, która kończy się wątek</span><span class="sxs-lookup"><span data-stu-id="08497-171">To implement a Cancel button that stops the thread</span></span>  
  
    -   <span data-ttu-id="08497-172">Wywołanie `StopThread` procedury z `Click` programu obsługi zdarzeń dla `Cancel` przycisku.</span><span class="sxs-lookup"><span data-stu-id="08497-172">Call the `StopThread` procedure from the `Click` event handler for the `Cancel` button.</span></span>  
  
        ```csharp  
        private void Cancel_Click(object sender, EventArgs e)  
        {  
            // Cancel the asynchronous operation.  
            this.backgroundWorker1.CancelAsync();  
        }  
        ```  
  
## <a name="testing"></a><span data-ttu-id="08497-173">Testowanie</span><span class="sxs-lookup"><span data-stu-id="08497-173">Testing</span></span>  
 <span data-ttu-id="08497-174">Teraz możesz przetestować aplikację, aby upewnić się, że działa on prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="08497-174">You can now test the application to make sure it works correctly.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="08497-175">Aby przetestować aplikację</span><span class="sxs-lookup"><span data-stu-id="08497-175">To test the application</span></span>  
  
1.  <span data-ttu-id="08497-176">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="08497-176">Press F5 to run the application.</span></span>  
  
2.  <span data-ttu-id="08497-177">Gdy formularz jest wyświetlany, podaj ścieżkę do pliku dla pliku, który chcesz przetestować w `sourceFile` pole.</span><span class="sxs-lookup"><span data-stu-id="08497-177">When the form is displayed, enter the file path for the file you want to test in the `sourceFile` box.</span></span> <span data-ttu-id="08497-178">Na przykład przy założeniu, że plik testu nosi nazwę Test.txt, wprowadź C:\Test.txt.</span><span class="sxs-lookup"><span data-stu-id="08497-178">For example, assuming your test file is named Test.txt, enter C:\Test.txt.</span></span>  
  
3.  <span data-ttu-id="08497-179">W drugim polu tekstowym wprowadź słowo lub frazę dla aplikacji, aby wyszukać w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="08497-179">In the second text box, enter a word or phrase for the application to search for in the text file.</span></span>  
  
4.  <span data-ttu-id="08497-180">Kliknij przycisk `Start` przycisku.</span><span class="sxs-lookup"><span data-stu-id="08497-180">Click the `Start` button.</span></span> <span data-ttu-id="08497-181">`LinesCounted` Przycisk powinien rozpocząć zwiększanie natychmiast.</span><span class="sxs-lookup"><span data-stu-id="08497-181">The `LinesCounted` button should begin incrementing immediately.</span></span> <span data-ttu-id="08497-182">Aplikacja wyświetla komunikat "Zakończono zliczania" po jej zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="08497-182">The application displays the message "Finished Counting" when it is done.</span></span>  
  
#### <a name="to-test-the-cancel-button"></a><span data-ttu-id="08497-183">Aby przetestować przycisku Anuluj</span><span class="sxs-lookup"><span data-stu-id="08497-183">To test the Cancel button</span></span>  
  
1.  <span data-ttu-id="08497-184">Naciśnij klawisz F5, aby uruchomić aplikację, a następnie wprowadź plik nazwę i wyszukaj słowo zgodnie z opisem w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="08497-184">Press F5 to start the application, and enter the file name and search word as described in the previous procedure.</span></span> <span data-ttu-id="08497-185">Upewnij się, że wybrany plik jest wystarczająco duże, aby upewnić się, że będzie czasu, aby anulować procedury przed zakończeniem.</span><span class="sxs-lookup"><span data-stu-id="08497-185">Make sure that the file you choose is large enough to ensure you will have time to cancel the procedure before it is finished.</span></span>  
  
2.  <span data-ttu-id="08497-186">Kliknij przycisk `Start` przycisk, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="08497-186">Click the `Start` button to start the application.</span></span>  
  
3.  <span data-ttu-id="08497-187">Kliknij przycisk `Cancel` przycisku.</span><span class="sxs-lookup"><span data-stu-id="08497-187">Click the `Cancel` button.</span></span> <span data-ttu-id="08497-188">Aplikacja ma zostać zatrzymana, licząc od razu.</span><span class="sxs-lookup"><span data-stu-id="08497-188">The application should stop counting immediately.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="08497-189">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="08497-189">Next Steps</span></span>  
 <span data-ttu-id="08497-190">Ta aplikacja zawiera niektóre obsługi podstawowych błędów.</span><span class="sxs-lookup"><span data-stu-id="08497-190">This application contains some basic error handling.</span></span> <span data-ttu-id="08497-191">Ta funkcja wykrywa ciągów wyszukiwania puste.</span><span class="sxs-lookup"><span data-stu-id="08497-191">It detects blank search strings.</span></span> <span data-ttu-id="08497-192">Możesz wprowadzić ten program bardziej niezawodne dzięki obsłudze inne błędy, takich jak przekroczenie maksymalnej liczby słów lub wierszy, które mogą być traktowane.</span><span class="sxs-lookup"><span data-stu-id="08497-192">You can make this program more robust by handling other errors, such as exceeding the maximum number of words or lines that can be counted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08497-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08497-193">See Also</span></span>  
 [<span data-ttu-id="08497-194">Wątkowość (C#)</span><span class="sxs-lookup"><span data-stu-id="08497-194">Threading (C#)</span></span>](../../../../csharp/programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="08497-195">Instrukcje: subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="08497-195">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)
